
# Helm 설치 가이드

## 구성 요소 및 버전

## Prerequisites
helm repository server

## 폐쇄망 설치 가이드
설치에 필요한 바이너리를 준비 합니다.

1. Helm 바이너리 파일을 다운받고 설치 합니다.

   - 작업 디렉토리 생성 및 환경 설정

   ```bash
   mkdir -p ~/helm
   export HELM_HOME=~/helm
   cd $HELM_HOME
   ```

   - 외부 네트워크 통신이 가능한 환경에서 필요한 바이너리를 다운로드 받습니다.

   ```bash
   https://github.com/helm/helm/releases 에서 파일을 다운 받습니다.
   ```

2. 폐쇄망으로 파일(.tar)을 옮깁니다.

3. 폐쇄망에서 .tar 압축을 풀고 설치 합니다.

   ```bash
   tar -xvf  helm-{version}-{arch}.tar.gz
   압축풀린 폴더 내부에 진입 합니다.
   helm 바이너리를 /usr/local/bin으로 옮깁니다.
   ```
   - 비고: helm version은 3을 기준으로 합니다.

## Install Steps (Public)
1. [helm 바이너리 다운 및 설치](#Step-1-helm-바이너리-다운-및-설치)

## Step 1. helm 바이너리 다운 및 설치
- 목적 : `helm 바이너리 다운 및 설치`
- 생성 순서 : 
    - https://github.com/helm/helm/releases 에서 바이너리를 다운 받습니다.
    - 해당 파일을 압축 풀고 내부의 helm 바이너리를 옮깁니다.
      ```bash
      tar -xvf  helm-{version}-{arch}.tar.gz
      압축풀린 폴더 내부에 진입 합니다.
      helm 바이너리를 /usr/local/bin으로 옮깁니다.
      ```
- 비고: helm version은 3을 기준으로 합니다.

## Helm 기본 명령어 (Helm 3.x 버전 기준)
1. Repo 조회
    ```bash
    helm repo list
    ```
2. Repo 추가
    ```bash
    helm repo add {repo_name} http://{repo_ip}:{repo_port}
    ```
3. Repo 정보 업데이트
    ```bash
    helm repo update
    ```
4. Repo 삭제
    ```bash
    helm repo remove {repo_name}
    ```
5. Chart 정보 가져오기
    ```
    helm search repo
    ```
6. Chart 설치
    ```
    helm install {install_name} {repo_name}/{chart_name} --namespace {namespace} --version {chart_version}
    ```
7. Chart 삭제
    ```
    helm uninstall {install_name} --namespace {namespace}
    ```
8. Chart 설치 확인
    ```
    helm list -A
    ```
- 비고 : 자세한 건, https://helm.sh/docs/helm/ 의 Helm Commands 참고