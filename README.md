# Laravel 샘플 프로젝트 구성 방법

---

## 시스템 설정

라라벨 기동에 필요한 `PHP` 와 `MySQL` 을 개발 환경에 설치한다. 
 

### PHP 7.3 설치 

1. [PHP 다운로드](https://windows.php.net/download#php-7.3) 에서 `VC15 x64 Non Thread Safe` 버전을 다운로드한다.
2. 다운로드한 파일의 압축을 해제한다.
3. 압축 해제된 디렉토리를 시스템 환경변수 `Path` 에 추가한다.

### PHP 7.3 Extension 활성화 

Laravel 기동에 필요한 Extension 디렉토리 설정 및  필수 Extension 들을 활성화한다. 




1. **PHP 7.3 설치** 에서 환경 변수에 추가한 디렉토리의 `php.ini` 파일을 문서 편집기로 연다.
2. `php.ini-development` 파일의 이름을 `php.ini` 로 변경한다.
3. `extension_dir` 의 값을 `PHP 7.3 설치` 섹션에서 설치한 디렉토리의 `ext` 디렉토리 설정한다. (예. C:php\php-7.3 이 설치 디렉토리인 경우 C:\php\php-7.3\ext)
3. `php.ini` 파일의 `Dynamic Extensions` 섹션에서 아래의 항목들을 주석 해제한다.(주석 해제는 앞의 세미콜론(;) 기호를 제거하면 된다.)
	- bz2
	- curl
	- fileinfo
	- gd2
	- mbstring
	- pdo_mysql
	- openssl 
	
	


### MariaDB 설치 

라라벨 데이터베이스로 사용할 `MariaDB` 을 아래 링크에서 다운로드하여 설치한다.

`MariaDB`는 `MySQL`와 동일하지만 오픈소스로 개발되는 프로젝트이다. (`MySQL` 은 오라클에서 관리된다.)

[https://mariadb.org/download/](https://mariadb.org/download/)

*다운로드 후 설치를 진행하되 비밀번호를 통해 로그인이 가능한 형태로 설치한다.*


**데이터베이스 생성**

`MySQL Client (Command Prompt)` 를 이용하여 데이터베이스를 생성한다.

```
MariaDB [(none)]> create database laravel

```

위와 같이 하면 데이터베이스가 생성된다.


### Git 설치 

개발 버전관리 도구인 `git` 을 설치한다. 아래 링크에서 다운로드하여 설치한다.

[https://www.git-scm.com/download/win](https://www.git-scm.com/download/win)


### SourceTree 다운로드 

`git` GUI 도구인 `소스트리`를 설치한다. 아래 링크에서 다운로드하여 설치한다. 

[https://www.sourcetreeapp.com/](https://www.sourcetreeapp.com/)



### Nodejs 다운로드 

`Javascript` 패키지 관리 도구인 `npm` 모듈을 이용하기 위해 `nodejs`를 다운로드하여 설치한다.

[https://nodejs.org/ko/](https://nodejs.org/ko/)

### 개발 환경 검증 

`git` 이 정상적으로 설치된 경우라면 파일 탐색기에서 `마우스 우 클릭` 을 하면 `Git bash here` 메뉴가 추가된다. 해당 메뉴를 실행한다. 

```

$ php --version 
PHP 7.3.10 (cli) (built: Sep 24 2019 11:58:16) ( NTS MSVC15 (Visual C++ 2017) x64 )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.3.10, Copyright (c) 1998-2018 Zend Technologies

$ mysql --version
C:\Program Files\MariaDB 10.3\bin\mysql.exe  Ver 15.1 Distrib 10.3.9-MariaDB, for Win64 (AMD64), source revision ca26f91bcaa21933147974c823852a2e1c2e2bd7


$ git --version
git version 2.23.0.windows.1
```

시스템에 개발 도구들이 올바르게 설치되었다면 아래 섹션으로 이동하여 개발 소스를 다운로드하도록 한다. 그렇지 않은 경우 설치 섹션을 다시 진행한다.

---

## 초기 프로젝트 다운로드 

VB의 개발 프로젝트는 `github`로 관리하며 `github`의 비공개 저장소에서 다운로드 할 수 있다. 


### 원격 저장소 소스 다운로드 

`github`에 업로드되어 있는 소스를 로컬에 내려 받는다. 내려 받는 방법은 `소스트리`를 이용하는 방법과 `Git bash` 를 이용하는 방법이 있다.

```
# git bash 를 이용하는 방법 

$ git clone https://github.com/venturebridge/laravel-sample

```


### Javascript 패키지 설치 

기본 라라벨에서는 `Javascript` 가 `jQuery` 를 사용하는 방식이 아닌 `Vue` 라이브러리를 이용하는 방식으로 제공된다. 그렇기 때문에 `Javascript` 패키지를 설치해야 한다.

```
$ npm install 

npm WARN deprecated resolve-url-loader@2.3.1: package is bloated with temp files (fixed in 2.3.2)
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.9 (node_modules\fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.9: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})

added 1009 packages from 486 contributors and audited 17160 packages in 45.796s
found 0 vulnerabilities


$ npm run dev 

> @ dev D:\php-work\laravel-sample
> npm run development


> @ development D:\php-work\laravel-sample
> cross-env NODE_ENV=development node_modules/webpack/bin/webpack.js --progress --hide-modules --config=node_modules/laravel-mix/setup/webpack.config.js

98% after emitting SizeLimitsPlugin

 DONE  Compiled successfully in 5972ms                                                                                                                                                                                                                               5:43:20 PM

       Asset      Size   Chunks             Chunk Names
/css/app.css   173 KiB  /js/app  [emitted]  /js/app
  /js/app.js  1.38 MiB  /js/app  [emitted]  /js/app

```

위와 같이 출력되면 `Javascript` 패키지 설치가 완료된것이다. 

### 설정 파일 변경 

1. `.env.example` 파일의 이름을 `.env` 로 변경한다. 
2. `.env` 파일에서 `DB_PASSWORD` 값을 MariaDB 설치시 입력했던 `root` 계정의 비밀번호로 변경한다.


### 데이터베이스 초기값 입력 

`Laravel`에서는 데이터베이스 이력 관리 기능을 제공한다. 기본 설치 후 필요한 데이터베이스 정보를 입력한다.

```
$ php artisan migrate
```


### 로컬 서버 기동 

`artisan` 명령을 이용하면 개발 서버를 간편하게 기동이 가능하다.

```
$ php artisan serve 
```

`로그인` 버튼과 `회원가입` 버튼이 표시되면 정상적으로 기동이 된것이다.

