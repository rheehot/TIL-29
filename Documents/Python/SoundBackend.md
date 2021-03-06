송은우 님의 **깔끔한 파이썬 탄탄한 백엔드** 서적을 통해 공부한 내용 정리

<details>
  <summary>Chapter 3. 첫 API 개발 시작 </summary>

# Chapter 3 첫 API 개발 시작

## ping 엔드포인트 구현하기

### 엔드포인트란?

엔드포인트는 API 서버가 제공하는 통신 채널 혹은 접점이라고 할 수 있다.

프론트엔드 서버 등의 클라이언트가 백엔드 API 서버와 통신할 때 엔드포인트에 접속하는 형태로 통신하게 된다.

각 엔드포인트는 고유의 URL 주소를 가지게 되며, 고유의 URL 주소를 통해 해당 엔드포인트에 접속할 수 있다.

일반적으로 각 엔드포인트는 고유의 기능을 담당하고 있다. 그리고 이러한 엔드포인트들이 모여서 하나의 API를 구성하는 것이다.

- 예: SNS 서비스를 위한 API는 사용자 sign up 엔드포인트, 사용자 로그인 엔드포인트, 새로운 포스팅 생성 엔드포인트, 다른 사요자와 친구 맺기 엔드포인트 등
- cf) 최근에 나온 기술인 GraphQL(Graph Query Language)은 여러 엔드포인트로 구성되어 있지 않고 단 하나의 엔드포인트로 모든 기능을 제공하는 형태로 구성된다.

### ping 엔드포인트

ping 엔드포인트는 단순히 "pong" 이라는 텍스트를 리턴(return) 하는 엔드포인트다. 이름 그대로 ping pong 처럼, ping 엔드포인트를 호출하면 "pong"이라고 응답하는 것이다.

ping 엔드포인트는 주로 API 서버가 현재 운행되고 있는지 아니면 정지된 상태인지를 간단하게 확인할 때 사용된다.

이러한 기능을 하는 엔드포인트를 헬스 체크(health check) 엔드포인트라고 한다. API 서버에 접속하지 않고 해당 API의 정상 운행 여부를 간단하게 체크하는 엔드포인트다.

### 로컬 호스트

로컬 호스트는 시스템이 실행되고 있는 해당 컴퓨터를 이야기한다. 로컬 호스트의 IP 주소는 127.0.0.1 이다. 컴퓨터 환경에선느 자기 자신을 접근하는 경우가 굉장히 자주 있기 때문에 운영 시스템(OS)에서 항상 고정된 호스트 이름과 IP 주소를 제공하는데 이것이 바로 로컬 호스트와 127.0.0.1 이다. 그러므로 127.0.0.1 IP 주소는 예약(reserved)된 IP 주소이며 인터넷상에서 일반 IP로는 쓰일 수 없다.

## 3장 정리

- Flask는 파이썬 웹 애플리케이션을 구현할 때 사용되는 프레임워크이며, Django와 다르게 웹 애플리케이션을 구현할 때 꼭 필요한 기능만을 제공하는 프레임워크다. 그러므로 학습 곡선이 비교적 낮다.
- 파이썬 개발을 할 때에는 먼저 파이썬 가상 환경을 생성한 후 항상 활성화시킨 상태에서 개발, 실행, 테스트를 해야 한다. 파이썬 가상 환경을 생성하는 방법은 여러 가지가 있지만, 콘다를 사용하여 파이썬 개발 환경을 생성하는 것이 선호된다.
- Flask에서는 일반적으로 route 데코레이터를 사용해서 함수들을 엔드포인트로 등록하는 방식이 사용된다. 즉, Flask에서 엔드포인트를 구현한단느 것은 결국은 일반 함수를 구현하는 것과 마찬가지다. 그러므로 백엔드 API 개발도 구조적으로는 크게 어렵거나 복잡할 것이 없다. 해당 API가 제공하는 서비스, 즉 비즈니스 로직 (business logic)을 구현하는 함수들을 개발하는 것이 백엔드 API에서 차지하는 가장 큰 부분이 된다.
- 백엔드 API 개발 입문에서 중요한 것은 먼저 기본적인 개념을 먼저 잘 이해하고, 그러고 난 후 API 코드의 전체적인 구조에 대해서 이해하는 것이 핵심이다. API의 개념을 잘 이해해서 구조를 잘 잡고 나면 그 다음은 필요한 비즈니스 로직을 함수를 통해 구현하기만 하면 된다. API 코드의 전체적인 구조가 일단 잡히면 그 다음부터는 엔드포인트들, 즉 함수들을 구현하는 것이 개발의 대부분이다. 함수를 구현하는 것은 개념적이나 구조적으로는 어려울 것이 없다.
- API를 개발하기 위해 필수적인 기본 개념들 중 가장 중요한 것 하나가 바로 HTTP다 왜냐하면 API는 기본적으로 HTTP 통신에 기반을 두고 있기 때문이다.
</details>

<details>
  <summary>Chapter 4. HTTP의 구조 및 핵심 요소</summary>

# Chapter 4 HTTP의 구조 및 핵심 요소

프론트엔드 시스템과 백엔드 API 시스템은 일반적으로 HTTP 프로토콜을 기반으로 통신한다.

# HTTP

HTTP는 HyperText Transfer Protocol의 약자로, 웹상에서 서로 다른 서버 간에 하이퍼텍스트 문서, 즉 HTML을 서로 주고받을 수 있도록 만들어진 프로토콜, 통신 규약임

# HTTP 통신 방식

HTTP 통신 방식에는 2가지 특징이 있음.

1. HTTP의 요청(request)와 응답(response) 방식임
2. stateless임

## 1) HTTP 요청과 응답

HTTP는 기본적으로 요청과 응답의 구조로 되어 있음

클라이언트가 먼저 HTTP 요청을 서버에 보내면 서버는 요청을 처리한 후 결과에 따른 HTTP 응답을 클라이언트에게 보냄으로써 하나의 HTTP 통신이 됨

그러므로 백엔드 API 시스템의 엔드포인트 구현도 기본적으로 HTTP 요청을 인풋으로 받아서 HTTP 응답을 아웃풋으로 리턴하는 구조로 구현하게 됨

Flask가 HTTP 부분을 자동으로 처리해 주기 때문에, Flask를 사용하면 개발자는 최대한 일반 함수를 구현하듯이 엔드포인트를 구현할 수 있다.

## 2) stateless

HTTP 통신은 "stateless"다.

stateless라는 말 그대로 상태(state)가 없다는 뜻으로, HTTP 통신에서는 상태의 개념이 존재하지 않는다.

클라이언트와 서버는 HTTP 통신을 여러 번 주고받는 것이 일반적인데, HTTP 프로토콜에서는 동일한 클라이언트와 서버가 주고받은 HTTP 통신들이라도 서로 연결되어 있지 않다.

즉, 각각의 HTTP 통신은 독립적이며 그 전에 처리된 HTTP 통신에 대해서 전혀 알지 못한다. 그래서 HTTP 프로토콜은 stateless라고 하는 것이다.

HTTP 프로토콜이 stateless 이기 때문에 서버 디자인이 훨씬 간단해지고 효과적인 장점이 있다.

- HTTP 통신들의 상태를 서버에서 저장할 필요가 없으므로 여러 다른 HTTP 통신 간의 진행이나 연결 상태의 처리나 저장을 구현 및 관리하지 않아도 되기 때문이다.
- 오직 각각의 HTTP 요청에 대해 독립적으로 응답만 보내 주면 된다.

다만 단점은 stateless 이기 때문에 HTTP 요청을 보낼 때는 해당 요청을 처리하기 위해 필요한 모든 데이터를 매번 포함시켜여 요청을 보내야 한다는 점이다.

- 예를 들어, 어떤 HTTP 요청을 처리하기 위해서 해당 사용자가 로그인이 되어야 한다고 가정 해보자.
- 해당 사용자가 이미 그 전의 HTTP 통신을 통해서 로그인을 한 상태라고 하더라도 HTTP는 stateless 이기 때문에 새로 보내는 HTTP 통신에서는 해당 사용자가 그 전 HTTP 통신에서 로그인했다는 사실을 알지 못한다.
- 그러므로 새로운 HTTP 요청을 보낼 때 해당 사용자의 로그인 사실 여부를 포함시켜서 보내야 한다.
- 사용자의 로그인 사실 여부를 포함시켜서 HTTP 요청을 보내기 위해서는 클라이언트가 사용자의 로그인 사실 여부를 기억하고 있어야 한다.

이러한 점들을 해결하기 위해서 쿠키(cookie)나 세션(session) 등을 사용하여 HTTP 요청을 처리할 때 필요한 진행 과정이나 데이터를 저장한다.

- 쿠키(cookie)는 웹 브라우저가 웹사이트에서 보내온 정보를 저장할 수 있도록 하는 조그마한 파일을 말한다. 웹 브라우저는 쿠키라고 하는 파일을 사용해서 필요한 정보를 저장한다.
- 세션(session)은 쿠키와 마찬가지로 HTTP 통신상에서 필요한 데이터를 저장할 수 있게 하는 매커니즘이다. 쿠키는 웹 브라우저, 즉 클라이언트 측에서 데이터를 저장하는 반면에 세션은 웹 서버에서 데이터를 저장한다.

# HTTP 요청 구조

HTTP 요청 메시지는 크게 다음의 세 부분으로 구성되어 있다.

1. Start Line
2. Headers
3. Body

예시:

```
POST /payment-sync HTTP/1.1   #  Start Line

Accept: application/json           # Headers
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 83
Content-Type: application/json
Host: intropython.com
User-Agent: HTTPie/0.9.3

{                                 # Body
	"imp_uid": "imp_123456789,
	"merchant_uid": "order_id_82373532",
	"status": "paid"
}
```

cf) HTTP 요청과 응답 메시지의 모든 부분을 직접 구현할 필요는 없다. Flask(혹은 Django 등의 다른 웹 프레임워크)가 거의 대부분을 알아서 처리해 준다. 일반적으로 개발자가 직접 지정해야 하는 부분은 HTTP 메소드와 status code, 몇 개의 헤더 정보, 그리고 body 부분이다 하지만 그래도 HTTP 응답과 요청의 구조와 내용을 이해는 하고 있어야 한다.

## 1. Start Line

이름 그대로 HTTP 요청의 시작줄임.

예를 들어, "search" 엔드포인트에 GET HTTP 요청을 보낸다면 해당 HTTP 요청의 start line은 다음과 같다.

`GET /search HTTP/1.1`

start line은 세 부분으로 구성되어 있다.

### **1) HTTP 메소드**

- 해당 HTTP 요청이 의도하는 액션(action)을 정의하는 부분
- 서버로부터 어떤 데이터를 받고자 한다면 GET 요청을 보내고, 서버에 새로운 데이터를 저장하고자 한다면 POST 요청을 보내는 식
- GET, POST, PUT, DELETE, OPTION 등 여러 메소드들이 있음. 그 중 GET과 POST가 가장 널리 쓰임

### **2) Request target**

- 해당 HTTP 요청이 전송되는 목표 주소
- "search" 엔드포인트에 보내는 HTTP 요청의 경우 request target은 "/search"가 됨

### **3) HTTP version**

- 해당 요청의 HTTP 버젼을 나타냄
- 현재 "1.0", "1.1", 그리고 "2.0"이 있음
- 버젼을 명시하는 이유는 HTTP 버젼에 따라 HTTP 요청 메시지의 구조나 데이터가 약간씩 다를 수 있으므로 서버가 받은 요청의 HTTP version에 맞추어서 응답을 보낼 수 있도록 하기 위함임

## 2. Header

start line 다음에 나오는 부분은 헤더(header)임

헤더 정보는 HTTP 요청 그 자체에 대한 정보를 담고 있음. ex) HTTP 요청 메시지의 전체 크기(Content-Length)

헤더는 파이썬의 dictionary처럼 key와 value로 되어 있음. `key:value` 로 표현됨

### **다양한 헤더의 종류**

- **Host**
  - 요청이 전송되는 target의 호스트의 URL 주소를 알려줌
  - 예: Host: google.co
- **User-Agent**
  - 요청을 보내는 클라이언트에 대한 정보: ex) 웹 브라우저에 대한 정보
- **Accept**
  - 해당 요청이 받을 수 있는 응답(response) body 데이터 타입을 알려줌
  - MIME (Multipurpose Internet Mail Extension) type이 value로 지정됨. 예를 들어 JSON 데이터 타입을 요청하는 경우에는 application/json MIME type을 value로 지정해 주면 됨. 모든 데이터 타입을 다 허용하는 경우는 \*/ \*로 지정해주면 됨
  - API에서 자주 사용되는 MIME type: application/json, application/octet-stream, text/csv, text/html, image/jpeg, image/png, text/plain, application/xml
  - 예: Accept: \*/\*
- **Connection**
  - 해당 요청이 끝난 후에 클라이언트와 서버가 계속해서 네트워크 연결을 유지할 것인지 아니면 끊을 것인지에 대해 알려 줌
  - HTTP 통신에서 서버 간에 네트워크 연결하는 과정이 다른 작업에 비해 시간이 걸리는 부분이므로 HTTP 요청 때마다 네트워크 연결을 새로 만들지 않고 HTTP 요청이 계속되는 한 처음 만든 연결을 재사용하는 것이 선호되는데, 이에 관한 정보를 전달하는 헤더임
  - connection 헤더의 값이 keep-alive 이면 앞으로도 계속해서 HTTP 요청을 보낼 예정이므로 네트워크 연결을 유지하라는 뜻임
  - 값이 close 라고 지정되면 더 이상 HTTP 요청을 보내지 않을 것이므로 네트워크 연결을 닫아도 된다는 뜻임
  - 예: Connection: keep-alive
- **Content-Type**
  - HTTP 요청이 보내는 메시지 body의 타입을 알려 줌
  - Accept 헤더와 마찬가지로 MIME type이 사용됨.
  - 예: Content-Type: application/json
- **Content-Length**
  - HTTP 요청이 보내는 메시지 body의 총 사이즈를 알려 줌
  - 예: Content-Length: 257

## 3. Body

HTTP 요청 메시지에서 body 부분은 HTTP 요청이 전송하는 데이터를 담고 있는 부분임. 전송하는 데이터가 없다면 body 부분은 비어 있게 됨

# HTTP 응답 구조

HTTP 응답 메시지의 구조도 요청 메시지와 마찬가지로 크게 세 부분으로 구성되어 있음

1. Status Line
2. Headers
3. Body

예시

```
HTTP/1.1 404 Not Found     # Status Line

Connection: close          # Headers
Content-Length: 1573
Content-TYpe: text/html; charset=UTF-8
Date: Mon, 19 Oct 2020 09:53:05 GMT

<!DOCTYPE html>           # Body
###HTML 내용
```

## 1. Status Line

HTTP 응답 메시지의 상태를 간략하게 요약하여 알려 주는 부분

HTTP 요청의 start line과 마찬가지로 status line도 세 부분으로 구성되어 있다

### **1) HTTP Version**

- 사용되고 있는 HTTP 버젼

### **2) Status Code**

- HTTP 응답 상태를 미리 지정되어 있는 숫자로 된 코드로 나타냄
- 예: 요청이 정상적으로 처리된 경우 - 200

### **3) Status Text**

- HTTP 응답 상태를 간략하게 글로 설명해 주는 부분
- 예: 요청이 정상적으로 처리된 경우 - OK

**Status Line** **예시**

```
HTTP/1.1 404 Not Found
```

## 2. Header

HTTP 요청의 헤더 부분과 동일. 다만 HTTP 응답에서만 사용되는 헤더 값들이 있다.

예를 들어, HTTP 응답에는 User-Agent 헤더 대신에 Server 헤더가 사용됨

## 3. Body

HTTP 요청 메시지의 body와 동일. 요청 메시지와 마찬가지로 전송하는 데이터가 없다면 body 부분은 비어있게 됨.

# 자주 사용되는 HTTP 메소드

## GET

- POST 메소드와 함께 가장 자주 사용되는 메소드
- 어떤 데이터를 서버로부터 요청할 때 주로 사용
- 데이터의 생성이나 수정, 그리고 삭제 등의 변경 사항 없이 단순히 데이터를 받아 오는 요청이 주로 GET 메소드로 요청됨
- 해당 HTTP 요청의 body가 비어 있는 경우가 많음

## POST

- GET 메소드와 함께 가장 자주 사용되는 메소드
- 데이터를 생성하거나 수정 및 삭제 요청할 때 사용

## OPTIONS

- 주로 특정 엔드포인트에서 허용하는 메소드들이 무엇이 있는지 알고자 할 때 사용
- 엔드포인트는 허용하는 HTTP 메소드가 지정되도록 되어 있으며, 허용하지 않는 HTTP 메소드의 요청이 들어오면 **405 Method Not Allowed** 응답을 보내게 됨
- 예: ping 엔드포인트에 OPTIONS 요청을 보내면 받는 응답

```
HTTP/1.0 200 OK

Allow: GET, HEAD, OPTIONS
Content-Length: 0
Content-Type: text/html; charset=utf-8
Date: Mon, 19 Oct 2020 14:18:26 GMT
Server: Werkzeug/1.0.1 Python/3.7.9
```

ping 엔드포인트르 구현할 때 GET 메소드만 허용하도록 구현했는데 HEAD OPTIONS 메소드까지 허용되어 있음. Flask가 자동으로 HEAD와 OPTIONS 요청에 대한 응답을 구현해주기 때문. 개발자가 직접 OPTIONS 메소드에 대한 처리를 구현하지 않아도 됨

## PUT

- 데이터를 새로 생성할 때 사용 (POST와 비슷한 의미)
- POST와 중복되는 의미이므로 데이터를 새로 생성하는 HTTP 요청을 보낼 때 굳이 PUT을 사용하지 않고 모든 데이터 생성 및 수정 관련한 요청은 다 POST로 통일해서 사용하는 시스템이 많아지고 있음

## DELETE

- 데이터 삭제 요청을 보낼 때 사용
- PUT과 마찬가지로, POST에 밀려서 잘 사용되지 않음

# 자주 사용되는 HTTP Status Code와 Text

## 200 OK

- HTTP 요청이 문제 없이 성공적으로 잘 처리 되었을 때 보내는 status code

## 301 Moved Permanently

- HTTP 요청을 보낸 엔드포인트의 URL 주소가 바뀌었다는 것을 나타냄
- 301 status code의 HTTP 응답은 Location 헤더가 포함되는 것이 일반적인데, Location 헤더에 해당 엔드포인트의 새로운 주소가 포함되어 나옴
- 301 요청을 받은 클라이언트는 Location 헤더의 엔드포인트의 새로운 주소에 해당 요청을 다시 보내게 됨. 이러한 과정을 "redirection" 이라고 함.

```
HTTP/1.1 301 Moved Permanently
Location: http://www.example.org/index.asp
```

## 400 Bad Request

- HTTP 요청이 잘못된 요청일 때 보냄
- 주로 요청에 포함된 인풋 값들이 잘못된 경우 사용
- 예: 사용자의 전화번호를 저장하는 HTTP 요청인데 전화번호에 숫자가 아닌 글자가 포함되었을 경우

## 401 Unauthorized

- 해당 요청을 보내는 주체(사용자 혹은 클라이언트)의 신분(credential) 확인이 요구되는 경우에 이를 확인할 수 없었을 때 보냄
- 주로 해당 HTTP 요청을 보내는 사용자가 로그인이 필요한 경우 401 응답을 보냄

## 403 Forbidden

- 요청을 보내는 주체가 해당 요청에 대한 권한이 없음을 나타냄
- 예: 비용을 지불한 사용자만 볼 수 있는 데이터에 대한 HTTP 요청을 보낸 사용자가 아직 비용을 지불하지 않은 상태일 경우

## 404 Not Found

- HTTP 요청을 보내고자 하는 URL이 존재하지 않을 떄 보냄
- 예: "해당 페이지를 찾을 수 없습니다" 라는 메시지가 적인 페이지 = 404 페이지

## 500 Internal Server Error

- 내부 서버 오류가 발생했다는 것을 알려 줌
- HTTP 요청을 받은 서버에서 해당 요청을 처리하는 과정에서 서버 오류가 나서 해당 요청을 처리할 수 없을 때 사용

# API 엔드포인트 아키텍처 패턴

API의 엔드포인트 구조를 구현하는 널리 알려진 패턴에는 크게 2가지가 있음

- REST 방식: 가장 널리 사용되는 API 엔드포인트 아키텍처 패턴임.
- GraphQL: 페이스북이 개발한 기술로 비교적 최근에 나온 기술

## RESTful HTTP API

REST(Representational State Transfer)ful HTTP API

API에서 전송하는 리소스를 URI(Uniform Resource Identifier)로 표현하고 해당 리소스에 행하고자 하는 의도를 HTTP 메소드로 정의하는 방식

각 엔드포인트는 처리하는 리소스를 표현하는 고유의 URI 주소를 가지고 있으며, 해당 리소스에 행할 수 있는 행위를 표현하는 HTTP 메소드를 처리할 수 있게 됨

예: 사용자 정보를 리턴하는 "/users" 라는 엔드포인트에서 사용자 정보를 받아 오는 HTTP 요청은 다음과 같이 표현할 수 있음

```
HTTP GET /users
GET /users
```

새로운 사용자를 생성하는 엔드포인트는 URI를 "/user/로 정하고 HTTP 요청은 다음과 같이 표현할 수 있음

```
POST /user
{
	"name"  : "박성재"
	"email" : "1234@gmail.com"
```

이러한 구조로 설계된 API를 RESTful API라고 함

### 장점

자기 설명력(self-descriptiveness)

- 엔드포인트의 구조만 보더라도 해당 엔드포인트가 제공하는 리소스와 기능을 파악할 수 있음
- API를 구현하다 보면 엔드포인트의 수가 많아지면서 엔드포인트의 역할고 기능 파악이 쉽지 않은데, REST 방식으로 구현하면 구조가 훨씬 직관적이며 간단해짐

## GraphQL

REST 방식으로 구현해도 여전히 구조적으로 생기는 문제들이 있음.

가장 자주 생기는 문제는 API의 구조가 특정 클라이언트에 맞추어져서 다른 클라이언트에서 사용하기에 적합하지 않게 된다는 점임

REST 방식의 API에서는 클라이언트들이 API가 엔드포인트들을 통해 구현해 놓은 틀에 맞추어 사용해야 하다 보니 그 틀에서 벗어나는 사용은 어려워 진다.

이러한 문제를 해결하기 위해서 페이스북은 GraphQL을 만들게 된다.

GraphQL은

- 엔드포인트가 오직 하나
- 엔드포인트에 클라이언트가 필요한 것을 정의해서 요청
- 기존 REST 방식의 API와 반대(서버가 정의한 틀에서 클라이언트가 요청하는 것이 아니라, 클라이언트가 필요한 것을 서버에 요청하는 방식)

### 예시

아이디가 1인 사용자의 정보와 그의 친구들의 이름 정보를 API로부터 받아와야 하는 경우

REST 방식 API - 아래와 같이 두 번의 HTTP 요청을 보내야 함

```
GET /users/1
GET /users/1/friends
```

위의 요청을 한 번의 HTTP 요청으로 줄이기 위해서는 아래와 같이 보내야 함

```
GET /users/1?include=friends.name
```

둘 다 비효율적이고 불필요하게 복잡함.

만일 사용자 정보들 중 다 필요하지 않고 이름만 필요하든가 혹은, 친구들의 이름 외에도 친구들의 이메일도 필요하다면 HTTP 요청은 더 복잡해질 것임

GraphQL을 사용하면 아래와 같이 HTTP 요청을 보내면 됨

```
POST /graphql

{
	user(id: 1) {
		name
		age
		friends {
			name
		}
	}
}
```

만일 사용자 정보는 이름만 필요하고, 대신 친구들의 이름과 이메일이 필요한 경우

```
POST /graphql

{
	user(id: 1) {
		name
		friends {
			name
			email
		}
	}
}
```

GraphQL은 장점이 많지만, REST에 비해서는 나온 지 오래 되지 않은 기술이므로 REST 만큼은 널리 사요되고 있지 않음. 그에 비해 REST는 알려진 지 오래 되었으므로 이미 여러 시스템에서 사용되고 있음

# 4장 정리

- HTTP 통신은 요청과 응답으로 이루어져 있음. 클라이언트가 HTTP 요청을 보내면 서버는 해당 요청에 대한 응답을 보내는 것이 하나의 HTTP 통신임
- HTTP 통신은 stateless 임. 클라이언트와 서버는 통신을 여러 번 주고받는 것이 일반적인데, HTP 프로토콜에서는 동일한 클라이언트와 서버가 주고 받은 HTTP 통신들이라도 서로 연결되어 있지 않음. 즉, 각각의 HTTP 통신은 독립적이며, 그 전에 처리된 HTTP 통신에 대해서 전혀 알지 못함
- HTTP 요청 메시지는 크게 세 부분으로 구성되어 있음
  - Start Line
  - Header
  - Body
- HTTP 응답 메시지도 세 부분으로 구성되어 있음
  - Status Line
  - Header
  - Body
- 자주 사용되는 HTTP 메소드에는 GET, POST, OPTIONS, PUT, DELETE 등이 있음
- 자주 사용되는 HTTP 응답 코드와 응답 텍스트에는 200 OK, 301 Moved Permanently, 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 500 Internal Server Error 등이 있음
- API 엔드포인트 아키텍쳐 패턴 중 가장 널리 사용되는 패턴은 REST임. REST는 엔드포인트의 고유 주소(URI)와 허용하는 HTTP 메소드를 통해서 제공하는 리소스와 기능을 알 수 있게 해줌으로써 클라이언트가 API를 더 쉽게 이해하고 사용할 수 있게 해줌
- GraphQL은 REST보다 더 유연한 엔드포인트 구조를 구현할 수 있지만, REST 보다는 아직 널리 사용되고 있지 않음

</details>

<details>
  <summary>Chapter 5. 본격적으로 API 개발하기</summary>

# Chapter 5. 본격적으로 API 개발하기

구현할 API 시스템은 미니터(미니 트위터)

# 미니터의 기능

- 회원가입
- 로그인
- 트윗(tweet)
- 다른 회원 팔로우하기
- 다른 회원 언팔로우 하기
- 타임라인(해당 사용자와 사용자가 팔로우하는 사용자들의 트윗들)

실제 트위터처럼 많은 수의 동시 접속이나 HTTP 요청 처리 속도를 고려한 구현은 포함하지 않음

# 회원가입

사용자에게 이름, 이메일, 비밀번호 등의 기본적인 회원 정보를 HTTP 요청을 통해 받은 후 시스템상에 저장

- id
- name
- email
- password
- profile

## 회원가입 기능 구현 엔드포인트

```python
from flask import Flask, jsonify, request # 1

app = Flask(__name__)
app.users = {} # 2
app.id_count = 1 # 3

@app.route("/sign-up", methods=['POST']) # 4
def sign_up():
	new_user = request.json # 5
	new_user["id"] = app.id_count # 6
	app.users[app.id_count] = new_user # 7
	app.id_count = app.id_count + 1 # 8

	return jsonify(new_user) # 9
```

1. 필요한 Flask의 모듈들 임포트
   - request를 통해 사용자가 HTTP 요청을 통해 전송한 JSON 데이터를 읽어들일 수 있음.
   - jsonify는 dictionary 객체를 JSON으로 변환하여 HTTP 응답으로 보낼 수 있게 됨
2. 새로 가입한 사용자를 저장할 dictionary를 users 라는 변수에 정의
   - 키(key) = 사용자 아이디, 값(value) = dictionary에 저장되어 있는 사용자 정보가 될 것임
3. 회원가입하는 사용자의 id 값을 저장하는 변수
   - id는 1부터 시작하며 새로운 사용자가 회원가입을 할 때마다 id 값이 하나씩 증가
   - CF) 엄밀히 말하면 문제가 있을 수 있음. 만일 HTTP 요청들이 동시에 전송될 경우 id 값이 잘못 지정될 가능성이 있음. 이를 예방하기 위해서 atomic increment operation(여러 스레드가 동시에 값을 증가시킬 수 없고, 한 번에 한 스레드만 값을 증가시키는 것)을 사용해야 함.
   - 그러나 미니터에서 데이터베이스에 데이터를 저장할 것이고, id 값은 데이터베이스에서 자동 생성 해준다. atomic 연산은 API 개발 입문과는 직접 관련 X. 개인적으로 알아보기
4. route 데코레이터를 사용해서 엔드포인트 정의
   - 엔드포인트의 고유 주소는 "/sign-up"으로 정의하고, HTTP 메소드는 POST로 함
5. HTTP 요청을 통해 전송된 회원 정보를 읽어 들임
   - request는 엔드포인트에 전송된 HTTP 요청 정보(헤더, body 등)를 저장하고 있음
   - request.json은 해당 HTTP 요청을 통해 전송된 JSON 데이터를 파이썬 dictionary 형태로 변환해 줌
6. HTTP 요청으로 전송된 회원가입 정보에 id 값을 더해 줌
7. 회원가입하는 사용자의 정보를 #2 에서 생성한 dictionary에 저장
8. id_count, 즉 id 값에 1을 더해 줌.
   - 다음 회원 id 값이 이미 회원가입한 사용자들의 id 값과 겹치지 않게 함
9. 회원가입한 사용자의 정보를 JSON 형태로 전송함
   - jsonify를 사용해 dictionary를 JSON 형태로 변환
   - status code는 200이 됨. 원래는 status code도 지정해 주어야 하지만, 만일 지정해 주지 않으면 디폴트 값으로 200이 리턴 됨

## 실행

터미널을 열고 해당 파일이 있는 디렉토리로 이동 후 파이썬 가상 환경 활성화 후 Flask 실행

```
(api) [api] FLASK_ENV=development FLASK_APP=app.py flask run

 * Serving Flask app "app.py" (lazy loading)
 * Environment: development
 * Debug mode: on
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 270-073-916
```

FLASK_ENV는 Flask가 실행되는 개발 스테이지를 뜻함

- "developement"로 정해 놓으면 debug mode가 실행됨. debug mode가 실행되면 코드가 수정될 때마다 Flask가 자동으로 재실행되어 수정된 코드가 반영되도록 해줌

## 회원가입 요청 보내기

httpie를 사용하여 터미널에서 회원가입 HTTP 요청 보내기

```
(api) [api] http -v POST localhost:5000/sign-up name=박성재 email=1234@gmail.com password=test1234

POST /sign-up HTTP/1.1
Accept: application/json, */*;q=0.5
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 81
Content-Type: application/json
Host: localhost:5000
User-Agent: HTTPie/2.2.0

{
    "email": "1234@gmail.com",
    "name": "박성재",
    "password": "test1234"
}

HTTP/1.0 200 OK
Content-Length: 104
Content-Type: application/json
Date: Tue, 20 Oct 2020 07:41:27 GMT
Server: Werkzeug/1.0.1 Python/3.7.9

{
    "email": "1234@gmail.com",
    "id": 1,
    "name": "박성재",
    "password": "test1234"
}
```

httpie를 사용해서 POST로 JSON 데이터를 보내는 것은 아주 간단함.

- HTTP 요청을 보내는 엔드포인트 주소 다음에 field=value 의 형태로 보내면 됨
- 예를 들어 "name" 필드의 값을 "박성재"로 JSON 데이터 형태로 전송하기 위해서는 name=박성재 라고 지정해 주면 됨

# 300자 제한 트윗 올리기

메인 기능인 300자 제한 트윗 글 올리기 엔드포인트 구현

- 사용자는 300자를 초과하지 않는 글을 올릴 수 있음
- 만일 300자를 초과하면 엔드포인트는 400 Bad Request 응답을 보내야 함
- 사용자가 300자 이내의 글을 전송하면 엔드포인트는 사용자의 글을 저장하고 있어야 하고 사용자의 타임라인 엔드포인트를 통해서 읽을 수 있어야 함

## Tweet 엔드포인트를 호출할 때 전송하는 JSON 데이터

```
{
	"id" : 1,                    # 1
	"tweet" : "My First Tweet"   # 2
}
```

1. 트윗을 보내는 사용자의 아이디
2. 트윗 내용

## 트윗 엔드포인트 구현

```python
app.tweets = []   # 1

@app.route('/tweet', methods=['POST']) # 2
def tweet():
	payload = request.json
	user_id = int(payload['user_id'])
	tweet = payload['tweet'] # 3

	if user_id not in app.users:   # 4
		return '사용자가 존재하지 않습니다', 400

	if len(tweet) > 300:   # 5
		return '300자를 초과했습니다', 400

	app.tweets.append({
		'user_id' : user_id,
		'tweet' : tweet
		})

	return '', 200
```

1. 사용자들의 트윗들을 저장할 디렉토리. key는 사용자 아이디
   - key는 사용자 아이디, value는 사용자들의 트윗을 담고 있는 리스트
2. 엔드포인트의 주소는 "/tweet", HTTP 메소드는 POST
3. HTTP 요청으로 전송된 JSON 데이터에서 "tweet" 필드를 읽어 들임
4. 만일 해당 사용자 아이디가 존재하지 않으면 400 Bad Request 오류 메시지를 전송함
5. 만일 해당 사용자의 트윗이 300자를 넘었으면 "300자를 초과했습니다"라는 메시지와 함께 400 Bad Request 응답을 보냄
6. HTTP 요청으로 전송된 JSON 데이터에서 사용자 아이디를 읽어 들임
7. 해당 사용자 아이디와 트윗을 딕셔너리로 생성해서 app.tweets 리스트에 저장함.
   - 이후 타임라인 엔드포인트에서 app.tweets 리스트를 읽어 들임

## 실행

```
(api) [api] http -v POST localhost:5000/tweet id=1 tweet="My First Tweet"

POST /tweet HTTP/1.1
Accept: application/json, */*;q=0.5
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 38
Content-Type: application/json
Host: localhost:5000
User-Agent: HTTPie/2.2.0

{
    "id": "1",
    "tweet": "My First Tweet"
}

HTTP/1.0 400 BAD REQUEST
Content-Length: 38
Content-Type: text/html; charset=utf-8
Date: Tue, 20 Oct 2020 09:19:12 GMT
Server: Werkzeug/1.0.1 Python/3.7.9

사용자가 존재하지 않습니다
```

사용자가 생성이 안 되어서 400 Bad Request 오류가 난다.

회원가입 엔드포인트를 통해 사용자를 추가한 뒤 다시 시도해 보자

- 이미 사용자를 생성했다고 하더라도 만일 API가 재실행되면 기존에 생성했던 사용자 및 데이터들은 전부 지워짐
- 아직 데이터베이스에 데이터들을 저장하는 것이 아니라 메모리 상에서만 저장하는 것이므로 서버가 재실행되는 순간 메모리 상의 데이터들은 전부 지워짐

```
(api) [api] http -v POST localhost:5000/tweet id=1 tweet="My First Tweet"

POST /tweet HTTP/1.1
Accept: application/json, */*;q=0.5
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 38
Content-Type: application/json
Host: localhost:5000
User-Agent: HTTPie/2.2.0

{
    "id": "1",
    "tweet": "My First Tweet"
}

HTTP/1.0 200 OK
Content-Length: 0
Content-Type: text/html; charset=utf-8
Date: Tue, 20 Oct 2020 09:23:51 GMT
Server: Werkzeug/1.0.1 Python/3.7.9
```

200 OK 응답이 오면 정상적으로 구현된 것임

# 팔로우와 언팔로우 엔드포인트

미니터에서 중요한 부분중 하나가

- 다른 트위터들을 팔로우(혹은 언팔로우)하고,
- 팔로우하는 사용자들의 글과 사진을 타임라인에서 볼 수 있는 기능

팔로우 혹은 언팔로우 하고 싶은 사용자의 아이디를 HTTP 요청으로 보내면 API에서 해당 요청을 처리하는 방식으로 구현

## 팔로우 엔드포인트에 전송할 JSON 데이터

```json
{
  "id": 1,
  "folow": 2
}
```

- id : 해당 사용자의 아이디
- follow : 팔로우하고자 하는 사용자의 아이디

## 언팔로우 엔드포인트에 전송할 JSON 데이터

```json
{
  "id": 1,
  "unfollow": 2
}
```

- id : 해당 사용자의 아이디
- unfollow : 언팔로우 하고자 하는 사용자의 아이디

## 팔로우 엔드포인트 구현

```python
@app.route("/follow", methods=["POST"])
def follow():
	payload = request.json
	user_id = int(payload["id"])   # 1
	user_id_to_follow = int(payload["follow"])   # 2

	if user_id not in app.users or user_id_to_follow not in app.users:   # 3
		return "사용자가 존재하지 않습니다", 400

	user = app.users[user_id]   # 4
	user.setdefault("follow", set()).add(user_id_to_follow)   # 5

	return jsonify(user)
```

1. HTTP 요청으로 전송된 JSON 데이터에서 해당 사용자의 아이디를 읽어 들임
2. HTTP 요청으로 전송된 JSON 데이터에서 해당 사용자가 팔로우할 사용자의 아이디를 읽어 들임
3. 만일 해당 사용자나 팔로우할 사용자가 존재하지 않는다면 400 Bad Request 응답을 보냄
4. app.users 딕셔너리에서 해당 사용자 아이디를 사용해서 해당 사용자의 데이터를 읽어 들임
5. #4 에서 읽어 들인 사용자의 정보를 담고 있는 딕셔너리가 이미 "follow"라는 필드를 가지고 있다면, 즉 이미 사용자가 다른 사용자를 팔로우한 적이 있다면, 사용자의 "follow" 키와 연결되어 있는 set에 팔로우하고자 하는 사용자 아이디를 추가함.
   - 만일 이번에 처음 다른 사용자를 팔로우하는 것이라면 사용자의 정보를 담고 있는 딕셔너리에 "follow" 라는 키를 empty set과 연결하여 추가함
   - 이렇게 키가 조재하지 않으면 디폴트 값을 저장하고, 만일 키가 이미 존재하면 해당 값을 읽어 들이는 기능을 `setdefault` 를 사용하여 구현함. `setdefault` 는 굉장히 유용한 딕셔너리의 기능임

### SET 사용

팔로우 엔드포인트 구현 시 해당 사용자가 팔로우하는 다른 사용자들의 아이디를 저장하는 자료구조로써 set을 사용함.

list를 사용하지 않고 set을 사용하는 이유는 만일 이미 팔로우하고 있는 사용자를 팔로우하는 요청이 왔을 경우에도 동일한 사용자 아이디가 여러 번 저장되지 않게 해주기 때문. 따라서 팔로우하고자 하는 사용자 아이디를 이미 팔로우하고 있지 않은 지에 대한 확인이 굳이 필요 없음.

중복된 사용자 아이디가 존재할 수 없으므로 언팔로우할 때도 굉장히 편리함

## 실행

```
(api) [api] http -v POST localhost:5000/follow id=1 follow=2

POST /follow HTTP/1.1
Accept: application/json, */*;q=0.5
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 26
Content-Type: application/json
Host: localhost:5000
User-Agent: HTTPie/2.2.0

{
    "follow": "2",
    "id": "1"
}

HTTP/1.0 500 INTERNAL SERVER ERROR
Connection: close
Content-Type: text/html; charset=utf-8
Date: Tue, 20 Oct 2020 14:20:58 GMT
Server: Werkzeug/1.0.1 Python/3.7.9
X-XSS-Protection: 0
...
...
raise TypeError(f'Object of type {o.__class__.__name__} '
TypeError: Object of type set is not JSON serializable
```

팔로우 엔드포인트에 HTTP 요청을 보내면 위와 같은 오류가 발생한다.

팔로우하는 사용자 아이디들을 저장하는 자료구조로 사용하는 set를 파이썬의 json 모듈이 JSON으로 변경하지 못하기 때문임. list는 JSON으로 변경될 수 있지만 set는 변경하지 못함

문제 해결을 위해서는 커스텀 JSON 인코더(custom JSON encoder)를 구현해서 디폴트 JSON 인코더에 덮어 씌워야 함. 직접 커스텀 JSON 인코더를 통해서 set를 list로 변경해 줌으로써 JSON으로 문제 없이 변경될 수 있도록 해줘야 함.

## 커스텀 JSON 인코더 구현

```python
from flask.json import JSONEncoder   # 1

class CustomJSONEncoder(JSONEncoder):   # 2
	def default(self, obj):   # 3
		if isinstance(obj, set):   # 4
			return list(obj)

		return JSONEncoder.default(self, obj)   # 5

app.json_encoder = CustomJSONEncoder   # 6
```

1. flask.json 모듈에서 `JSONEncoder` 클래스를 임포트함
   - `JSONEncoder` 클래스를 확장해서 커스텀 인코더 구현하기 위함
2. `JSONEncoder` 클래스를 부모 클래스로 상속 받는 `CustomJSONENcoder` 클래스 정의
3. `JSONEncoder` 클래스의 `default` 메소드를 확장(over-write)함.
   - `default` 메소드에서 set인 경우 list로 변경해줘야 함
4. JSON으로 변경하고자 하는 객체(obj)가 set인 경우 list로 변경해서 리턴
5. 객체가 set이 아닌 경우는 본래 `JSONEncoder` 클래스의 `default` 메소드 호출해서 리턴
6. `CustomJSONEncoder` 클래스를 Flask의 디폴트 JSON 인코더로 지정
   - 이렇게 하면 `jsonify` 함수가 호출될 때마다 `JSONEncoder`가 아닌 `CustomJSONEncoder` 클래스가 사용됨

위 코드를 추가하고 시스템 재시작한 후 "follow" 엔드포인트를 호출하면 정상적으로 HTTP 응답이 옴

```
(api) [api] http -v POST localhost:5000/follow id=1 follow=2

POST /follow HTTP/1.1
Accept: application/json, */*;q=0.5
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 26
Content-Type: application/json
Host: localhost:5000
User-Agent: HTTPie/2.2.0

{
    "follow": "2",
    "id": "1"
}

HTTP/1.0 200 OK
Content-Length: 130
Content-Type: application/json
Date: Tue, 20 Oct 2020 14:37:43 GMT
Server: Werkzeug/1.0.1 Python/3.7.9

{
    "email": "1234@gmail.com",
    "follow": [
        2
    ],
    "id": 1,
    "name": "박성재",
    "password": "test1234"
}
```

## 언팔로우 엔드포인트 구현

팔로우 엔드포인트 구현과 거의 유사함

차이점은 set에 사용자 아이디를 추가하는 것이 아니라 삭제하는 것임

```python
@app.route("/unfollow", methods=["POST"])
def unfollow():
	payload = request.json
	user_id = int(payload["id"])
	user_id_to_unfollow = int(payload["unfollow"])   # 1

	if user_id not in app.users or user_id_to_unfollow not in app.users:   # 2
		return "사용자가 존재하지 않습니다", 400

	user = app.users[user_id]
	user.setdefault("follow", set()).discard(user_id_to_unfollow)   # 3

	return jsonify(user)
```

1. 언팔로우할 사용자 아이디를 HTTP 요청으로 전송된 데이터에서 읽어 들임
2. 팔로우 엔드포인트와 마찬가지로 해당 사용자 아이디 혹은 언팔로우할 사용자 아이디가 존재하지 않으면 400 Bad Request 응답을 보냄
3. 언팔로우하고자 하는 사용자 아이디를 set에서 삭제함
   - `remove` 메소드를 사용하지 않고 `discard` 메소드를 사용하는 이유는, `remove` 의 경우 만일 없는 값을 삭제하려고 하면 오류를 일으키지만 `discard` 메소드는 삭제하고자 하는 값이 있으면 삭제를 하고 없으면 무시하기 때문
   - 때문에 굳이 삭제하고자 하는 사용자 아이디가 실제로 set에 존재하는지를 확인하는 로직을 구현하지 않아도 됨

## 실행

```
(api) [api] http -v POST localhost:5000/unfollow id=1 unfollow=2

POST /unfollow HTTP/1.1
Accept: application/json, */*;q=0.5
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 28
Content-Type: application/json
Host: localhost:5000
User-Agent: HTTPie/2.2.0

{
    "id": "1",
    "unfollow": "2"
}

HTTP/1.0 200 OK
Content-Length: 121
Content-Type: application/json
Date: Tue, 20 Oct 2020 14:49:58 GMT
Server: Werkzeug/1.0.1 Python/3.7.9

{
    "email": "1234@gmail.com",
    "follow": [],
    "id": 1,
    "name": "박성재",
    "password": "test1234"
}
```

200 OK를 통해 제대로 실행된 것을 확인할 수 있음

리턴된 사용자의 JSON 데이터를 살펴보면 "follow" 필드에 존재하던 사용자 아이디가 삭제된 것을 확인할 수 있음

# 타임라인 엔드포인트

- 해당 사용자의 트윗들, 그리고 팔로우하는 사용자들의 트윗들을 리턴해 주는 엔드포인트
- 데이터의 수정 없이 받아오기만 함 - GET 메소드 사용

## 타임라인 엔드포인트가 리턴하는 JSON 데이터

```json
{
	"user_id" : 1,   # 1
	"timeline" : [   # 2
		{
			"user_id" : 2,   # 3
			"tweet" : "Hello, World!"   # 4
		},
		{
			"user_id" : 1,
			"tweet" : "MY First tweet!!:
		}
	]
}
```

1. 해당 사용자의 아이디
2. 해당 사용자와 사용자가 팔로우하는 사용자들의 트윗 리스트
3. 해당 트윗을 올린 사용자 아이디
4. 트윗 내용

## 타임라인 엔드포인트 구현

- 사용자들의 트윗은 app.tweets 리스트에 저장되어 있음
- app.tweets 리스트에서 해당 사용자와 사용자가 팔로우하는 사용자들의 트윗들을 찾은 후에 전송하면 됨

```python
@app.route("/timeline/<int:user_id>", methods=["GET"])   # 1
def timeline(user_id):   # 2
	if user_id not in app.users:
		return "사용자가 존재하지 않습니다", 400

	follow_list = app.users[user_id].get("follow", set())   # 3
	follow_list.add(user_id)    # 4
	timeline = [tweet for tweet in app.tweets if tweet["user_id"] in follow_list] # 5

	return jsonify({
		"user_id" : user_id,
		"timeline" : timeline
	})   # 6
```

1. `<int:user_id>` 부분은 엔드포인트 주소에 해당 사용자의 아이디를 지정할 수 있게 해줌
   - 예) "/timeline/1" 이 경우 타임라인 엔드포인트에 user_id 인자에 int 값으로 1이 지정되어 엔드포인트를 구현한 함수인 timeilne에 전달됨
2. 타임라인 엔드포인트를 구현하는 함수에서 user_id 를 인자로 받고 있음
   1. # 1 에서 지정된 엔드포인트 주소를 통해서 받는 값이며 해당 사용자의 아이디임
3. 먼저 해당 사용자가 팔로우하는 사용자들 리스트를 읽어 들임.
   - 만일 사용자가 다른 사용자를 팔로우한 적이 없는 경우 follow 필드가 존재하지 않을 수도 있음. 그런 경우에는 empty set을 리턴함
4. 팔로우하는 사용자 리스트에 해당 사용자의 아이디도 추가하여 자신의 트윗도 볼 수 있도록 함
5. 전체 트윗 중 해당 사용자와 사용자가 팔로우하는 사용자들의 트윗들만 읽어 들임
6. 사용자 아이디와 함께 타임라인을 JSON 형태로 리턴

## 실행

```
(api) [api] http -v GET localhost:5000/timeline/1

GET /timeline/1 HTTP/1.1
Accept: */*
Accept-Encoding: gzip, deflate
Connection: keep-alive
Host: localhost:5000
User-Agent: HTTPie/2.2.0

HTTP/1.0 200 OK
Content-Length: 319
Content-Type: application/json
Date: Wed, 21 Oct 2020 04:13:48 GMT
Server: Werkzeug/1.0.1 Python/3.7.9

{
    "timeline": [
        {
            "tweet": "My First Tweet",
            "user_id": 1
        },
        {
            "tweet": "길동이의 첫 트윗",
            "user_id": 2
        },
        {
            "tweet": "실력 있는 개발자가 되자",
            "user_id": 1
        }
    ],
    "user_id": 1
}
```

HTTP 요청을 통해 id가 1인 사용자의 타임라인을 불러와 봤다

주의할 점은, 타임라인을 불러들이기 전 사용자 생성, 사용자 트윗 생성, 사용자 팔로우가 선행되어야 한다는 것

# 전체 코드

지금까지 구현한 엔드포인트들을 합친 코드

책의 깃허브 리포지토리에서도 확인할 수 있음 ([https://github.com/rampart81/python-backend-book/tree/master/chapter5](https://github.com/rampart81/python-backend-book/tree/master/chapter5))

```python
from flask import Flask, jsonify, request
from flask.json import JSONEncoder

'''
Default JSON encoder는 set을 JSON으로 변환 불가
따라서 커스텀 인코더를 작성하여 set을 list로 변환해서
JSON으로 변환 가능하게 해줘야 함.
'''
class CustomJSONEncoder(JSONEncoder):
    def default(self, obj):
        if isinstance(obj, set):
            return list(obj)

        return JSONEncoder.default(self, obj)

app = Flask(__name__)

app.id_count = 1
app.users = {}
app.tweets = []
app.json_encoder = CustomJSONEncoder

@app.route("/ping", methods=["GET"])
def ping():
    return "pong"

@app.route("/sign-up", methods=["POST"])
def sign_up():
    new_user = request.json
    new_user["id"] = app.id_count
    app.users[app.id_count] = new_user
    app.id_count = app.id_count + 1

    return jsonify(new_user)

@app.route("/tweet", methods=["POST"])
def tweet():
    payload = request.json
    user_id = int(payload["id"])
    tweet = payload["tweet"]

    if user_id not in app.users:
        return "사용자가 존재하지 않습니다", 400

    if len(tweet) > 300:
        return "300자를 초과했습니다", 400

    app.tweets.append({
        "user_id" : user_id,
        "tweet" : tweet
        })

    return '', 200

@app.route("/follow", methods=["POST"])
def follow():
    payload = request.json
    user_id = int(payload["id"])
    user_id_to_follow = int(payload["follow"])

    if user_id not in app.users or user_id_to_follow not in app.users:
        return "사용자가 존재하지 않습니다", 400

    user = app.users[user_id]
    user.setdefault("follow", set()).add(user_id_to_follow)

    return jsonify(user)

@ app.route("/unfollow", methods=["POST"])
def unfollow():
    payload = request.json
    user_id = int(payload["id"])
    user_id_to_unfollow = int(payload["unfollow"])

    if user_id not in app.users or user_id_to_unfollow not in app.users:
        return "사용자가 존재하지 않습니다", 400

    user = app.users[user_id]
    user.setdefault("follow", set()).discard(user_id_to_unfollow)

    return jsonify(user)

@app.route("/timeline/<int:user_id>", methods=["GET"])
def timeline(user_id):
    if user_id not in app.users:
        return "사용자가 존재하지 않습니다", 400

    follow_list = app.users[user_id].get("follow", set())
    follow_list.add(user_id)
    timeline = [tweet for tweet in app.tweets if tweet["user_id"] in follow_list]

    return jsonify({
        "user_id" : user_id,
        "timeline" : timeline
        })
```

# 5장 정리

- 데이터를 수정하는 기능의 엔드포인트는 POST 메소드를 사용함
- 데이터를 읽어 들이는 기능의 엔드포인트는 GET 메소드를 사용함
- POST 엔드포인트에 데이터를 전송할 때는 body에 JSON 형식으로 데이터를 전송함
- URL에 인자(parameter)를 전송하고 싶을 때는 <type:value> 형식으로 URL을 구성함
  - 예를 들어, int 값의 사용자 아이디를 URL에 포함시켜 받고 싶을 때는 다음과 같이 주소를 구성하면 됨: /timeline/<int:user_id>
- 중복된 값이 없어야 하는 데이터라면 set을 사용하고 순서나 순차가 중요하다면 list를 사용. 키와 값을 표현해야 하는 데이터의 경우는 딕셔너리를 사용

</details>
<details>
<summary>Chapter 6. 데이터베이스</summary>

# Chapter 6 데이터베이스

앞서 구현한 API 사용 시 불편한 점은 API가 재시작될 때마다 모든 데이터가 없어졌다는 것임

데이터를 영구적으로 보존하기 위해서는 데이터베이스 시스템을 사용해서 저장해야 함

# 데이터베이스 시스템

데이터를 저장 및 보존하는 시스템으로, 데이터 조회, 저장, 업데이트의 기능을 함

데이터베이스의 시스템에는 크게 2가지 종류가 있음

- 관계형 데이터베이스 시스템(RDBMS; Relational Database Management System)
- "NoSQL"로 명칭되는 비관계형(Non-relational) 데이터베이스

## 관계형 데이터베이스

관계형 데이터 모델에 기초를 둔 데이터베이스 시스템. 관계형 데이터란 데이터들이 서로 상호관련성을 가진 형태로 표현된 데이터를 말함

- 대표적인 관계형 데이터베이스 시스템: MySQL, PostgreSQL(줄여서 Postgres)

관계형 데이터베이스에서 모든 데이터들은 2차원 테이블들로 표현됨.

- 각각의 테이블은 칼럼(column)과 로우(row)로 구성됨
- 칼럼(행)은 테이블의 각 항목
- 로우(열)은 각 항목들의 실제 값

각 로우는 저만의 고유 키(primary key)가 있음

- 주로 이 고유 키를 통해서 해당 로우를 찾거나 참조(reference)하게 됨.
- 고유 키 이외에도 다른 값으로 로우를 찾을 수 있음

### 테이블들의 상호 관련성

users 테이블은 사용자 정보를 저장하는 테이블이며 컬럼은 다음과 같음

- id, name, email, phone

tweets 테이블은 사용자들의 트윗들을 저장하는 테이블임.

- id, user_id, tweet

각 테이블에서 id 컬럼은 각 로우를 식별하는 고유 키(primary key)임

users 테이블과 tweets 테이블은 사용자의 id를 기준으로 열결되어 있음. 즉 users 테이블의 id와 tweets 테이블의 user_id가 연결되어 있으며, 두 값이 같은 로우들은 서로 연결되어 있음. 연결되어 있다는 뜻은 tweets 테이블의 user_id 컬럼의 값과 동일한 id 값을 가지는 users 테이블의 사용자가 해당 tweet들의 사용자라는 뜻

한 테이블에서 다른 테이블의 특정 컬럼의 값으로 연결시키는 과정을 외부 키(foreign key)를 통해 연결시킨다고 함. tweets 테이블의 user_id 컬럼이 user 테이블의 id 키에 걸려 있는 외부 키가 됨.

관계형 데이터베이스에서는 일반적으로 외부 키를 사용해서 테이블들을 연결시킴

### 테이블들의 상호 관련성 종류

- one to one
  - 테이블 A의 로우와 테이블 B의 로우가 정확히 일대일 매칭되는 관계
- one to many
  - 테이블 A의 로우가 테이블 B의 여러 로우와 연결되는 관계.
  - 예: 사용자와 트윗의 관계
- many to many
  - 테이블 A의 여러 로우가 테이블 B의 여러 로우와 연결되는 관계
  - 예: 사용자들 사이의 팔로잉과 팔로워 관계

### 정규화

정보를 여러 테이블에 나누어서 저장하는 이유

- 하나의 테이블에서 필요한 모든 정보를 다 넣으면 동일한 정보들이 여러 테이블에 불필요하게 중복되어 저장됨
  - 그러면 불필요하게 더 많은 디스크를 사용하게 됨
  - 반면 외부 키를 사용하여 사용하면 단순 키 값만 저장하면 되므로 디스크 공간을 훨씬 효율적으로 사용할 수 있게 됨
- 관계형식으로 데이터베이스 구조를 잡지 않고 필요한 데이터를 테이블에 저장하게 되면 잘못된 데이터가 저장될 가능성이 높아짐
  - 외부 키를 사용하면 서로 같은 데이터이지만 오타나 스펠링 등의 이유로 부분적으로 오류가 생겨서 틀린 데이터가 생기는 문제가 없어지게 됨

이렇게 중복을 최소화하도록 데이터를 구조화하는 프로세스를 정규화 혹은 노멀리제이션(normalization)이라고 함. 관계형 데이터베이스에서는 정규화가 굉장히 중요한 부분임

### 트랙젝션

관계형 데이터베이스에서 중요한 기능 중 하나.

**트랜젝션**은 일련의 작업들이 마치 하나의 작업처럼 취급되어서 모두 다 성공하거나 아니면 모두 다 실패하는 것을 말함.

1번부터 4번까지의 처리 과정이 있다고 할 때, 1번부터 4번까지 다 제대로 실행되었을 때만 실제 데이터베이스에 영구적으로 반영되고 만일 중간 과정에서 오류가 나거나 실패하는 경우 그 전 상태로 돌아가는 기능임

- 예: 은행 계좌이체, 인터넷 쇼핑 결제

관계형 데이터베이스 시스템은 트랙잭션 기능을 보장하기 위해 ACID 라는 성질을 가지고 있음.

**ACID**는 Atomicity, Consistency, Isolation, Durability 의 약자로 원자성, 일관성, 고립성, 지속성을 의미함.

- **Atomicity(원자성)**: 분해가 불가능한 최소의 단위인 하나의 원자처럼 동작한다는 의미. 트랜잭션 내의 모든 연산들은 반드시 한꺼번에 완전하게 전체가 정상적으로 수행이 완료되거나, 아니면 어떠한 연산도 수행되지 않음.
- **Consistency(일관성)**: 트랜잭션 작업이 시작되기 전에 데이터베이스 상태가 일관된 상태였다면 트랜잭션 작업이 종료된 후에도 일관성 있는 데이터베이스 상태를 유지해야 함
  - 예를 들어 게시물의 글자 제한이 있으면, 트랜잭션이 일어난 후에도 이러한 조건을 만족해야 하는 것. 이를 위반하는 트랜잭션이 있다면 이를 거부해야 함
- **Isolation(고립성)**: 트랜잭션 작업 수행 중에는 다른 트랜잭션에 영향을 주어서도 안 되고, 다른 트랜잭션들에 의해 간섭을 받아서도 안 됨.
  - 다른 트랜잭션의 영향을 받게 되면 영향을 주는 트랜잭션에 의해 자신의 동작이 달라질 수 있기 때문에, 트랜잭션 자신은 고립된 상태에서 수행되어야 함
  - 즉 다수의 트랜잭션이 동시에 수행중인 상황에서 하나의 트랜잭션이 완료될 때까지는 현재 실행 중인 트랜잭션의 중간 수행결과를 다른 트랜잭션에서 보거나 참조할 수 없음
- **Durability(지속성)**: 일련의 데이터 조작(트랜잭션 조작)을 완료하고 사용자가 완료 통지를 받는 시점에서 그 조작이 영구적이게 되어 그 결과를 잃지 않는 것을 나타냄.

  - 시스템이 정상일 때 뿐만 아니라, 데이터베이스나 OS의 이상 종료, 즉 시스템 장애도 견딜 수 있다는 것을 말함.
  - MySQL을 포함해 많은 데이터베이스의 구현에는 트랜잭션 조작을 하드 디스크에 로그로 기록하고, 시스템에 이상이 발생하면 그 로그를 사용해 이상 발생 전까지 복원하는 것으로 지속성을 실현하고 있음

  트랜잭션이라는 것은 데이터베이스 내에서 하나의 논리적 기능을 수행하기 위해 행해지는 한 번에 사용되는 하나 이상의 쿼리를 모아 놓은 쪼갤 수 없는 작업의 논리적인 단위임. ACID는 데이터베이스 트랜잭션이 안전하게 수행되는 것을 보장하기 위한 성질임.

[ACID 개념 참고 블로그](https://covenant.tistory.com/85)

## 비관계형 데이터베이스

NoSQL 데이터베이스라고도 불리며, 비관계형 타입의 데이터를 저장할 때 주로 사용되는 데이터베이스 시스템임

관계형 데이터베이스와 다르게 비관계형이므로 데이터들을 저장하기 전에 정의할 필요가 없음. 즉, 관계형 데이터베이스처럼 테이블들의 스키마(schema)와 테이블들의 관계를 미리 구현해야 하는 필요가 없이 데이터가 들어오는 그대로 저장하면 됨.

가장 대표적인 NoSQL DBMS에는 MongoDB, Redis, Cassandra 등이 있음

# 관계형 DBMS vs 비관계형 DBMS

### 관계형 DB 장점

- 데이터를 더 효율적이고 체계적으로 저장하고 관리할 수 있음
- 저장할 데이터들의 구조(테이블 스키마)를 미리 정의함으로써 데이터의 완전성이 확보됨
- 트랜잭션(transaction) 기능을 제공함

### 관계형 DB 단점

- 테이블을 미리 정의해야 하므로 테이블 구조 변화 등에 덜 유연함
- 확장이 쉽지 않음.
  - 테이블 구조가 미리 정의되어야 하고 ACID를 보장해야 하다 보니 단순히 서버를 늘리는 것만으로 확장하기가 쉽지 않고 서버의 성능 자체도 높여야 함
- 서버를 늘려서 분산 저장하는 것도 쉽지 않음
  - 주로 스케일 아웃(scale out, 서버 수를 늘려서 확장하는 것)보다는 스케일 업(scale up, 서버의 성능을 높이는 것)으로 확장해야 함.

### 비관계형 DB 장점

- 데이터 구조를 미리 정의하지 않아도 되므로 저장하는 데이터의 구조 변화에 유연함
- 데이터베이스 시스템 확장이 비교적 용이.
  - 스케일 아웃, 즉 서버 수를 늘리는 방식으로 시스템 확장이 가능함
- 확장하기가 쉽고 데이터의 구조도 유연하다 보니 방대한 양의 데이터를 저장하는 데 유리함.

### 비관계형 DB 단점

- 데이터의 완전성이 덜 보장됨
- 트랜잭션이 안 되거나, 되더라도 비교적 불안정함

### 각각의 쓰임새

관계형 데이터베이스 시스템은 주로 정형화된 데이터들, 그리고 데이터의 완전성이 중요한 데이터를 저장하는 데 유리함.

- 전자상거래 정보, 은행 계좌 정보, 거래 정보 등을 저장하고 관리하는 데 사용됨

비관계형 데이터베이스 시스템은 주로 비정형화 데이터, 그리고 완전성이 상대적으로 덜 중요한 데이터를 저장하는 데에 유리함.

- 로그 데이터 등

미니터 API 시스템은 관계형 데이터베이스를 사용해 구현할 것임

# SQL

SQL(Structured Query Language)은 MySQL 같은 관계형 데이터베이스에서 데이터를 읽거나 생성 및 수정하기 위해서 사용하는 언어임.

기본적으로 CRUD라고 하여, 데이터를 Create(생성), Read(읽기), Update(수정), Delete(삭제)하는 기능을 제공하는 관계형 데이터베이스 시스템 전용 언어임.

SQL에는 여러 구문이 있지만, 그 중에서도 기본적으로 `SELECT`, `INSERT`, `UPDATE`, `DELETE`, 그리고 `JOIN` 은 필수적으로 이해해야 함.

(SQL 기본 구문은 따로 공부하고 정리한 TIL이 있으므로 생략)

### 참고

INSERT INTO 테이블명 (컬럼명1, 컬럼명2)... VALUES (값1, 값2) 구문 사용시 VALUES 뒤에 여러 개의 괄호와 쉼표를 사용해서 한 번에 여러 로우를 추가해줄 수 있음.

JOIN의 디폴트 행위는 INNER JOIN임

# API에 데이터베이스 연결하기

## 미니터 API의 DB 스키마

### users 테이블

- id
- name
- email
- profile
- hashed_password (암호화된 비밀번호)

### user_follow_list 테이블

사용자들이 다른 사용자들을 팔로우하는 리스트 저장. many to many 관계, users 테이블에 id를 통해 외부 키로 연결

- user_id
- follow_user_id

### tweets 테이블

사용자들의 트윗들을 저장한 테이블. users 테이블과 one to many 관계(한 사용자가 여러 트윗 가능). users 테이블에 id를 통해 외부 키로 연결

- id
- user_id
- tweets

## MySQL 실행

```bash
mysql.server start # MySQL 실행

mysql.server status # 현재 실행 여부 확인

mysql.server stop # 실행 정지
```

## MySQL 사용

```bash
mysql -u root -p
```

- -u 옵션: MySQL에 접속할 사용자의 아이디를 명시하는 옵션
- -p 옵션: 비밀번호를 직접 입력하겠다고 명시하는 옵션

## 데이터베이스 생성

```sql
CREATE DATABASE miniter; # 미니터 데이터베이스 생성

USE miniter; # 미니터 데이터베이스 사용 선언
```

## 테이블 생성

```sql
	CREATE TABLE users(
	id INT NOT NULL AUTO_INCREMENT,   # 1
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL,
    hashed_password VARCHAR(255) NOT NULL,
    profile VARCHAR(255) NOT NULL,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,   # 2
    updated_at TIMESTAMP NULL DEFAULT NULL ON UPDATE CURRENT_TIMESTAMP,   # 3
    PRIMARY KEY(id),   # 4
    UNIQUE KEY email (email)   # 5
);

CREATE TABLE users_follow_list(
	user_id INT NOT NULL,
    follow_user_id INT NOT NULL,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY(user_id, follow_user_id),
    CONSTRAINT users_follow_list_user_id_fkey FOREIGN KEY (user_id)
    REFERENCES users(id),   # 6
    CONSTRAINT users_follow_list_follow_user_id_fkey FOREIGN KEY (follow_user_id)
    REFERENCES users(id)
);

CREATE TABLE tweets(
	id INT NOT NULL AUTO_INCREMENT,
    user_id INT NOT NULL,
    tweet VARCHAR(300) NOT NULL,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY(id),
    CONSTRAINT tweets_user_id_fkey FOREIGN KEY (user_id)
    REFERENCES users(id)
);
```

1. `NOT NULL`, `AUTO_INCREMENT`
   1. `NOT NULL`의 뜻은 해당 컬럼은 null 값이 될 수 없다는 뜻. 해당 컬럼은 항상 값이 있어야 함.
   2. `AUTO_INCREMENT` 를 명시해 주면 해당 컬럼의 값이 자동으로 1씩 증가됨. 주로 id 값을 자동 생성하기 위해서 사용됨
2. `DEFAULT CURRENT_TIESTAMP` 의 뜻은 만일 해당 컬럼의 값이 없으면 디폴트 값으로 현재 시간(timestamp) 값을 사용하라는 뜻임.
   - 주로 created_at 처럼 해당 값이 생성된 시점을 기록하는 컬럼에 사용됨. 일일이 created_at 값을 지정해주지 않아도 데이터베이스가 자동으로 생성해 주므로 편리함
3. `ON UPDATE CURRENT TIEMSTAMP`의 뜻은 만일 해당 로우의 값이 수정되면 해당 컬럼의 값을 수정이 이루어진 시간의 값으로 자동 생성해 준다는 뜻임. 로우가 언제 업데이트 되었는지 자동으로 기록되므로 편리함
4. `PRIMARY KEY` 구문을 통해 고유 키로 사용될 컬럼을 정해 줌.
   - 고유 키는 한 개의 컬럼으로 정할 수 도 있지만 여러 컬럼을 정할 수도 있음.
   - 여러 컬럼을 고유 키로 정해주면 해당 컬럼 값들을 합한 값이 고유 키가 됨.
5. `UNIQUE KEY`의 뜻은 해당 컬럼의 값이 중복되는 로우가 없어야 한다는 뜻
   - 이메일의 경우 이미 등록된 이메일로 중복된 등록이 되면 안 되기 때문에 `UNIQUE KEY` 구문을 사용해 시스템적으로 방지해 둘 수 있어서 편리하고 안전함
6. `CONTRAINT ... FOREIGN KEY ... REFERENCES ...` 구문을 통해 외부 키를 설정할 수 있음
   - user_follow_list 테이블과 tweets 테이블 둘 다 users 테이블에 외부 키를 통해 연결됨.

### `SHOW TABLES` 명령어를 통해 테이블 생성 확인

```bash
mysql> SHOW TABLES;
+-------------------+
| Tables_in_miniter |
+-------------------+
| tweets            |
| users             |
| users_follow_list |
+-------------------+
3 rows in set (0.00 sec)
```

### `EXPLAIN 테이블명` 명령어를 통해 더 자세한 내용 확인 가능

```bash
mysql> EXPLAIN tweets;
+------------+--------------+------+-----+-------------------+-------------------+
| Field      | Type         | Null | Key | Default           | Extra             |
+------------+--------------+------+-----+-------------------+-------------------+
| id         | int          | NO   | PRI | NULL              | auto_increment    |
| user_id    | int          | NO   | MUL | NULL              |                   |
| tweet      | varchar(300) | NO   |     | NULL              |                   |
| created_at | timestamp    | NO   |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED |
+------------+--------------+------+-----+-------------------+-------------------+
```

### MySQL 종료

`exit` 을 치면 MySQL을 종료하고 터미널로 돌아갈 수 있음.

## SQLAlchemy

파이썬 코드에서 DB와 연결하기 위해서 사용할 수 있는 다양한 라이브러리가 있는데 그 중 SQLAlchemy 라는 라이브러리가 파이썬에서 가장 널리 쓰이는 라이브러리 중 하나임. 이를 통해 파이썬 코드에서 데이터베이스에 연결해서 SQL을 실행시킬 수 있음

SQLAlchemy는 ORM(Object Relational Mapper)임.

- ORM이란 관계형 데이터베이스의 테이블들을 프로그래밍 언어의 클래스로 표현할 수 있게 해주는 것을 말함.
- 즉, 클래스를 사용해서 테이블들을 표현하고 데이터를 저장, 읽기, 업데이트 등을 할 수 있게 해줌

### SQLAlchemy 설치

```bash
pip install sqlalchemy
```

SQLAlchemy에서 MySQL을 사용하기 위해서는 MySQL용 DBAPI 또한 설치해야 함. DBAPI는 DB를 사용하기 위한 API임.

MySQL용 DBAPI는 여러 가지가 있는데, 그 중 MySQL의 공식 파이썬 DBAPI인 MySQL-Connector 설치

```bash
pip install mysql-connector-python
```

### SQLAlchemy 사용 예시

```python
from sqlalchemy import create_engiene, text # 1

db = {
	'user' : 'root',
	'password' : 'test1234',
	'host' : 'localhost',
	'port' : '3306',
	'database' : 'miniter'
} # 2

db_url = f"mysql+mysqlconnector://{db['user']}:{db['password']}@{db['host']}:{db['port']}/{db['database']}?charset=utf8" # 3
db = create_engiene(db_url, encoding = 'utf-8', max_overflow = 0) # 4

params = {'name' : '박성재'}
rows = db.execute(text("SELECT * FROM users WHERE name = :name"), params).fetchall() # 5

for row in rows: # 6
	print(f"name : {row['name']}")
	print(f"email : {row['email']}")
```

1. sqlalchemy 모듈에서 필요한 함수 임포트
   - `create_engine`: 데이터베이스에 연결
   - `text`: 실행할 SQL을 만듦
2. 데이터베이스에 연결하기 위한 접속 정보
   - 데이터베이스에 접속할 사용자 아이디, 비밀번호, 접속할 데이터베이스 시스템의 주소, 그리고 DB명 등이 필요함
3. 데이터베이스 접속 정보를 사용해 DB URL을 구성함.
   - DB URL을 사용해서 실제 데이터베이스에 접속할 수 있음
   - 마치 URL을 사용해 웹사이트에 접속하는 것과 같은 개념
4. sqlalchemy의 `create_engiene` 함수를 통해서 db_url에 명시된 데이터베이스에 접속
   - `create_engiene` 함수는 Engine 객체를 리턴함. 연결된 데이터베이스의 SQL 실행을 Engine 객체를 사용해서 할 수 있음.
   - 여기서는 Engine 객체를 db 변수에 저장했음.
5. Engine의 `execute` 메소드를 통해 SQL을 데이터베이스에 전송해 실행함.
   - 여기서는 users 테이블에서 이름이 "박성재"인 사용자의 데이터를 읽어 들이는 SQL 구문 실행
   - `execute` 메소드는 크게 2가지 parameter를 받음: SQL 구문, SQL 구문에 필요한 인자들의 값
     - SQL 구문에 필요한 인자들은 딕셔너리 형태로 보내야 함.
     - `text` 함수에 넘겨진 sQL에 만일 `:` 이 포함되어 있으면 `:` 다음에 오는 단어와 동일한 키를 사용해 딕셔너리에서 읽어 들여 치환함.
     - 여기서 `SELECT * FROM users WHERE name = :name` 이 `SELECT * FROM users WHERE name = '박성재'` 로 변경되는 것임
   - `execute` 메소드는 ResultProxy 객체를 리턴하는데 ResultProxy의 `fetchall` 메소드를 사용해 실제 데이터들을 리스트의 형태로 리턴함
6. 위에서 읽어들인 데이터들을 for loop를 사용해 각 로우를 읽어 들여 원하는 컬럼의 값을 출력함.
   - 각 로우는 딕셔너리처럼 사용할 수 있으며(실제로 딕셔너리는 아님), 컬럼 이름이 키 값으로 사용됨.

# SQLAlchemy를 사용하여 API와 데이터베이스 연결하기

## 데이터베이스의 연결 정보를 저장할 파일 만들기 (설정 파일)

config.py

```python
db = {
    'user' : 'root', # 1
    'password' : 'test1234', # 2
    'host' : 'localhost', # 3
    'port' : '3306', # 4
    'database' : 'miniter' # 5
}
DB_URL = f"mysql+mysqlconnector://{db['user']}:{db['password']}@{db['host']}:{db['port']}/{db['database']}?charset=utf8"
```

1. 데이터베이스에 접속할 사용자 아이디
2. 사용자의 비밀번호
3. 접속할 데이터베이스의 주소
   - 지금은 같은 컴퓨터에 설치되어 있는 데이터베이스에 접속하므로 localhost로 지정.
   - 만일 외부 서버에 설치되어 있는 데이터베이스에 접속해야 한다면 해당 서버의 주소를 지정해 주어야 함
4. 접속한 데이터베이스의 포트 넘버
   - 관계형 데이터베이스는 주로 3306 포트를 통해 연결됨
   - API나 사이트와 마찬가지로 데이터베이스도 네트워크를 통해 연결되는 시스템이므로 당연히 포트 정보가 필요함
5. 실제 사용할 데이터베이스 이름

### 설정 파일을 따로 만드는 이유

1. 설정 정보를 따로 관리함으로써 민감한 개인 접속 정보를 노출하지 않아도 됨
   - .gitignore 파일에 [config.py](http://config.py) 파일을 지정해 놓음으로써 이 파일이 git 리포지토리에 포함되지 않게 함으로써 개인정보 노출을 막음
2. 각 환경과 설정에 맞는 설정 파일을 적용할 수 있게 됨.
   - 각 개발 호스트 혹은 서버에 맞는 config.py를 설정하게 함으로써 각 환경에 적합한 설정을 적용하도록 함

## 데이터베이스 설정 정보 읽어들이기

[app.py](http://app.py) 파일을 수정하여 [config.py](http://config.py) 파일에서 DB 설정 정보를 읽어들여 데이터베이스와 연결.

```python
from sqlalchemy import create_engine, text

def create_app(test_config = None): # 1
    app = Flask(__name__)

    if test_config is None: # 2
        app.config.from_pyfile('config.py')
    else:
        app.config.update(test_config)

    database = create_engine(app.config['DB_URL'], encoding = utf-8, max_overflow = 0) # 3
    app.database = database # 4

		return app # 5
```

1. `create_app` 함수 정의
   - Flask가 `create_app` 이라는 이름의 함수를 자동으로 팩토리(factory) 함수로 인식해서 해당 함수를 통해서 Flask를 실행시킴.
   - `create_app` 함수는 `test_config` 를 인자로 받는데, 이는 단위 테스트(unit test)를 실행시킬 때 테스트용 데이터베이스 등의 테스트 설정 정보를 적용하기 위함임.
2. 만일 `test_config` 인자가 None 이면 [config.py](http://config.py) 파일에서 설정을 읽어 들임
   - 만일 `test_confing` 인자가 None이 아니라면, 즉 `test_config` 의 값이 설정되어 들어왔다면 `test_config` 의 설정을 적용시킴
3. sqlalchemy의 `create_engine` 함수를 사용해 데이터베이스와 연결함
4. `create_engine` 함수를 통해 생성한 Engine 객체를 Flask 객체에 저장함으로써 `create_app` 함수 외부에서 도 데이터베이스를 사용할 수 있게 함
5. Flask 객체를 리턴함.
   - `create_app` 이라는 함수는 Flask가 자동인지해서 Flask 객체를 찾아서 실행할 수 있게 함

이제는 `create_app` 함수 안에서 엔드포인트들을 구현할 것임. 엔드포인트 구현 시 sqlalchemy를 사용해서 MySQL DB에 연결하여 데이터를 DB에 저장 및 읽어들이도록 할 것임.

## 회원가입 엔드포인트

```python
@app.route('/sign-up', methods=['POST'])
def sign_up():
    new_user = request.json
    new_user_id = app.database.execute(text(""" # 1
        INSERT INTO users (
            name,
            email,
            profile,
            hashed_password
        ) VALUES (
            :name,
            :email,
            :profile,
            :password
        )
    """), new_user).lastrowid # 2

    row = app.database.execute(text(""" # 3
        SELECT
            id,
            name,
            email,
            profile
        FROM users
        WHERE id = :user_id
    """), {
        'user_id' :new_user_id
    }).fetchone()

    created_user = { # 4
        'id' : row['id'],
        'name' : row['name'],
        'email' : row['email'],
        'profile' : row['profile']
    } if row else None

    return jsonify(created_user)
```

1. HTTP 요청을 통해 전달받은 회원 가입 정보를 DB에 저장
   - `app.database`는 SQLAlchemy를 통해 MySQL DB에 연결된 객체임. `app.database` 를 통해 원하는 SQL 구문을 해당 DB에 실행하게 됨.
2. SQL 구문에 사용될 실제 데이터들은 HTTP 요청(request)에서 읽어 들인 데이터를 그대로 사용함
   - HTTP 요청을 통해 전송된 JSON 데이터의 구조가 # 1 의 SQL에서 필요한 필드를 모두 포함하고 이씨 때문임.
   - 만일 필드 이름이 다르거나 필드가 부재인 경우 오류가 나게 됨.
   - 새로 사용자가 생성되면, 새로 생성된 사용자의 id를 `lastrowid` 를 통해 읽어 들임
3. 새로 생성한 사용자의 정보를 DB에서 읽어 들임
4. 읽어 들인 새 사용자의 정보를 딕셔너리로 변환해서 결국에 JSON 형식으로 HTTP 응답으로 보낼 수 있도록 함.

## tweet 엔드포인트

저장해야 하는 데이터를 HTTP 요청을 통해서 받아서 DB에 저장하면 됨

```python
@app.route('/tweet', methods=['POST'])
def tweet():
		user_tweet = request.json
    tweet = user_tweet['tweet']

    if len(tweet) > 300:
        return '300자를 초과했습니다', 400

    app.database.execute(text(""" #1
        INSERT INTO tweets (
            user_id,
            tweet
        ) VALUES (
            :id,
            :tweet
        )
    """), user_tweet) #2

    return '', 200
```

1. HTTP 요청을 통해 전달받은 트윗 데이터를 DB에 저장함
2. SQL 구문을 통해 `INSERT` 될 트윗 데이터는 HTTP 요청을 통해 전송된 JSON을 그대로 사용함

## follow 엔드포인트 직접 구현해보기

```python
@app.route('/follow', methods=['POST'])
def follow():
    user_follow = request.json

    app.database.execute(text("""
        INSERT INTO users_follow_list (
            user_id,
            follow_user_id
        ) VALUES (
            :id,
            :follow
        )
    """), user_follow)

    return '', 200
```

## timeline 엔드포인트

timeline 엔드포인트는 `SELECT` 구문을 사용함.

이번에는 데이터를 저장하는 것이 아니라 DB에 있는 데이터들을 읽어 들여 JSON 형태로 변환하여 HTTP 응답으로 보냄.

```python
@app.route('/timeline/<int:user_id>', methods=['GET'])
def timeline(user_id):
    rows = app.database.execute(text(""" #1
        SELECT
            t.user_id,
            t.tweet
        FROM tweets AS t
        LEFT OUTER JOIN users_follow_list AS ufl
        ON ufl.user_id = :user_id
        WHERE (t.user_id = :user_id)
            OR (t.user_id = ufl.follow_user_id)
    """), {
        'user_id' : user_id
    }).fetchall()

    timeline = [{ #2
        'user_id' : row['user_id'],
        'tweet' : row['tweet']
    } for row in rows]

    return jsonify({ #3
        'user_id' : user_id,
        'timeline' : timeline
    })
```

1. `SELECT` 구문과 `JOIN` 구문을 사용해서 해당 사용자의 트윗들과 해당 사용자가 팔로우하는 사용자들의 트윗들을 DB에서 읽어 들임
   - 여기서 `LEFT OUTER JOIN` 을 활용해서 혹시라도 해당 사용자가 팔로우하는 사용자가 없더라도 해당 사용자의 트윗만이라도 읽어들일 수 있게 함.
   - 읽어 들이는 로우의 수가 여럿일 것이므로 `fetchall` 메소드를 사용해서 전부 다 읽어 들임
2. 읽어 들인 트윗 리스트를 딕셔너리들을 품은 리스트 형태로 변환
   - 즉 하나 하나의 로우를 딕셔너리로 변환하여 전체를 리스트에 담는 것
3. 변환한 딕셔너리 리스트를 JSON 형태로 HTTP 응답으로 보냄

막상 이렇게 엔드포인트 구현을 하니 두 테이블이 조인되는 과정에서 해당 사용자가 팔로우하는 대상이 여럿일 경우 해당 **사용자 자신의 트윗이 중복**하여 나타났다.

이를 방지하기 위해 다음과 같이 **서브쿼리**와 **병합 연산**을 이용하여 다시 코드를 짜봤다.

그리고, tweets 테이블의 creaetd_at 컬럼을 이용하여 트윗이 생성된 시간순으로 정렬해 타임라인에 생성 시간이 더 빠른 트윗 순으로 나타나도록 해 보았다.

```python

@app.route('/timeline/<int:user_id>', methods=['GET'])
def timeline(user_id):
    rows = app.database.execute(text("""
        SELECT
            t.user_id,
            t.tweet,
						t.created_at
        FROM tweets AS t
        LEFT OUTER JOIN users_follow_list AS ufl
        ON ufl.user_id = :user_id
        WHERE t.user_id = ufl.follow_user_id
				UNION
				(
				SELECT
					t.user_id,
					t.tweet,
					t.created_at
				FROM tweets AS t
				WHERE t.user_id = :user_id
				)
				ORDER BY created_at ASC
    """), {
        'user_id' : user_id
    }).fetchall()

    timeline = [{
        'user_id' : row['user_id'],
        'tweet' : row['tweet']
    } for row in rows]

    return jsonify({
        'user_id' : user_id,
        'timeline' : timeline
    })
```

이후 실행시켜 확인해 보니, 더 이상 자기 자신의 트윗이 중복되어 나타나지 않았다.

이를 통해 서브쿼리와 병합 연산을 다시 한 번 연습해볼 수 있었다.

다만, 이 경우 데이터 조회에 걸리는 시간이 추가될 수 있다는 점을 고려하고, 이 SQL 문이 목적 달성을 위한 최선인지 앞으로 SQL 구문을 더 사용해 보고 자료를 찾아보며 고민해 봐야할 것 같다.

## unfollow 엔드포인트 직접 구현해보기

```python
@app.route('/unfollow', methods=['POST'])
def unfollow():
    user_unfollow = request.json

    app.database.execute(text("""
        DELETE FROM users_follow_list
            WHERE (user_id = :id)
                AND (follow_user_id = :unfollow)
    """), user_unfollow)

    return '', 200
```

## 전체 코드

DB에 SQL을 실행하는 로직들을 따로 함수로 만들고 각 엔드포인트에서 필요한 함수들을 호출하는 형태로 변환.%

SQL을 실행하는 함수들에서 `current_app` 이 사용되는데, 이는 `create_app` 함수에서 생성된 app 변수를 `create_app` 함수 외부에서도 사용할 수 있게 해줌

```python
from flask import Flask, jsonify, request, current_app
from sqlalchemy import create_engine, text

def insert_user(user):
    return current_app.database.execute(text("""
        INSERT INTO users (
            name,
            email,
            profile,
            hashed_password
        ) VALUES (
            :name,
            :email,
            :profile,
            :password
        )
    """), user).lastrowid

def get_user(user_id):
    user = current_app.database.execute(text("""
        SELECT
            id,
            name,
            email,
            profile
        FROM users
        WHERE id = :user_id
    """), {
        'user_id' : user_id
    }).fetchone()

    return {
        'id' : user['id'],
        'name' : user['name'],
        'email' : user['email'],
        'profile' : user['profile']
    } if user else None

def insert_tweet(user_tweet):
    current_app.database.execute(text("""
        INSERT INTO tweets (
            user_id,
            tweet
        ) VALUES (
            :id,
            :tweet
        )
    """), user_tweet)

def insert_follow(user_follow):
    current_app.database.execute(text("""
        INSERT INTO users_follow_list (
            user_id,
            follow_user_id
        ) VALUES (
            :id,
            :follow
        )
    """), user_follow)

def insert_unfollow(user_unfollow):
    current_app.database.execute(text("""
        DELETE FROM users_follow_list
        WHERE ufl.user_id = :id
            AND follow_user_id = :unfollow
    """), user_unfollow)

def get_timeline(user_id):
    timeline = current_app.database.execute(text("""
        SELECT
            t.user_id,
            t.tweet,
            t.created_at
        FROM tweets AS t
        LEFT OUTER JOIN users_follow_list AS ufl
        ON ufl.user_id = :user_id
        WHERE t.user_id = ufl.follow_user_id
        UNION
        SELECT
            t.user_id,
            t.tweet,
            t.created_at
        FROM tweets AS t
        WHERE t.user_id = :user_id
        ORDER BY created_at
    """), {
        'user_id' : user_id
    }).fetchall()

    return [{
        'user_id' : tweet['user_id'],
        'tweet' : tweet['tweet']
    } for tweet in timeline]

def create_app(test_config = None):
    app = Flask(__name__)

    if test_config is None:
        app.config.from_pyfile("config.py")
    else:
        app.config.update(test_config)

    database = create_engine(app.config['DB_URL'], encoding = 'utf-8', max_overflow = 0)
    app.database = database

    @app.route('/ping', methods=['GET'])
    def ping():
        return 'pong'

    @app.route('/sign-up', methods=['POST'])
    def sign_up():
        new_user = request.json
        new_user_id = insert_user(new_user)
        created_user = get_user(new_user_id)

        return jsonify(created_user)

    @app.route('/tweet', methods=['POST'])
    def tweet():
        user_tweet = request.json
        tweet = user_tweet['tweet']

        if len(tweet) > 300:
            return '300자를 초과했습니다', 400

        insert_tweet(user_tweet)

        return '', 200

    @app.route('/follow', methods=['POST'])
    def follow():
        user_follow = request.json
        insert_follow(user_follow)

        return '', 200

    @app.route('/unfollow', methods=['POST'])
    def unfollow():
        user_unfollow = request.json
        insert_unfollow(user_unfollow)

        return '', 200

    @app.route('/timeline/<int:user_id>', methods=['GET'])
    def timeline(user_id):

        return jsonify({
            'user_id' : user_id,
            'timeline' : get_timeline(user_id)
        })

    return app
```

# 6장 정리

- 데이터베이스 시스템은 데이터를 저장 및 보존하는 시스템임. DB에 저장되어 있는 데이터를 조회할 수 있고, 새로운 데이터를 저장할 수도 있고, 기존의 데이터를 업데이트할 수 도 있음
- DB 시스템은 크게 2종류로 분류된다. 관계형 DB 시스템 (RDBMS), 그리고 "NoSQL"로 불리우는 비관계형(Non-relational) DBMS다.
- 관계형 DB에서 테이블들의 상호 관련성
  - one to one
  - one to many
  - many to many
- 관계형 DB에서 외래 키(foreign key)를 사용해서 테이블들을 연결하여 데이터 값의 중복을 최소화하게 데이터를 구조화하는 프로세스를 정규화라고 함
- 관계형 DB에서 트랜잭션은 일련의 작업들이 마치 하나의 작업처럼 취급되어서 모두 다 성공하거나 아니면 모두 다 실패하는 것을 말함
- SQL은 MySQL 같은 관계형 DB에서 데이터를 읽거나 생성 및 수정하기 위해 사용하는 언어임
- sqlalchemy 라이브러리를 사용해서 파이썬 코드에서 DB에 연결하여 SQL을 실행시킬 수 있음
- Flask는 `create_app` 이라는 이름의 함수를 자동으로 팩토리 함수로 인식해서 해당 함수를 통해 Flask를 실행시킴

</details>

<details>
  <summary>Chatper 7. 인증</summary>

# Chapter 7 인증

## 인증이 필요한 이유

### private API

사용할 수 있는 사용자 혹은 클라이언트를 제한해야 하므로 당연히 인증 엔드포인트를 구현해야 함

### public API

사용 횟수 제한, 남용 방지, 사용자 통계 등의 이유로 인증 엔드포인트를 대부분 필요로 함

## 인증 절차

1. 사용자 가입 절차를 통해 아이디와 비밀번호 생성
2. 가입한 사용자의 아이디와 비밀번호를 DB에 저장. 비밀번호는 암호화해서 저장
3. 사용자가 본인의 아이디와 비밀번호 입력 (로그인)
4. 사용자가 입력한 비밀번호를 암호화한 후, 그 값을 이미 암호화 되어서 DB에 저장된 비밀번호와 비교
5. 비밀번호가 일치하면 로그인 성공
6. 로그인에 성공하면 백엔드 API 서버는 access token을 프론트엔드 혹은 클라이언트에게 전송
7. 프론트엔드 서버는 로그인 성공 후 다음부터는 해당 사용자의 access token을 첨부해서 request를 서버에 전송함으로써 매번 로그인하지 않아도 되도록 함

## 사용자 비밀번호 암호화

### 암호화의 이유

사용자의 비밀번호는 절대 본래의 비밀번호 값 그대로 DB에 저장하지 않음!

그 이유는 외부 해킹 또는 내부 인력에 의해 DB에 노출되었을 경우에 사용자의 정보가 노출되는 것을 막기 위해서임

### 암호화 방식

일반적으로 단방향 해시 함수(one-way hash function)가 쓰임

- 이름에서 알 수 있듯이 복호화(decryption) 할 수 없는 암호화 알고리즘임
- 사용자의 비밀번호를 DB에 저장할 때는 복호화할 목적으로 저장하지 않고, 온전히 본래의 비밀번호 값을 알지 못하도록 방지하는 데에 목적이 있는 것

password 와 password2 와 같이 비슷한 비밀번호를 암호화하게 되면 원본의 비밀번호 값은 굉장히 비슷하지만, 암호화된 해시 함수 값은 완전히 다르게 되는데, 이러한 효과를 **애벌런시 효과**(avalanche effect)라고 함. 원본 값과 해시 값 사이에 직접적인 연관성이나 패턴이 없도록 하여 원본 값을 추론하는 것을 어렵게 만들도록 함

### `hashlib` 모듈

파이썬에서는 `hashlib` 모듈을 사용해서 단방향 해시 함수를 통해 값들을 암호화할 수 있음

```python
import hashlib # 1
m = hashlib.sha256() # 2
m.update(b"test password") # 3
m.hexdigest() # 4
# 0b47c69b1033498d5f33f5f7d97bb6a3126134751629f4d0185c115db44c094e
```

1. `hashlib` 모듈 임포트.
2. `sha256` 암호 알고리즘 선택
3. 암호화하고자 하는 값을 인자로 설정해서 `update` 메소드 호출
   - `update` 메소드는 바이트 값을 받으므로 b prefix를 스트링 앞에 붙여서 바이트로 변환해 줌
4. 암호화된 값을 hex(16진수) 값으로 읽어 들임

## bcrypt 암호 알고리즘

단방향 해시 알고리즘도 취약점이 있고, 충분히 해킹 가능하다.

가장 널리 사용되는 단방향 해시 암호 알고리즘 해킹 방법은 **rainbow attack**

- 미리 임의의 문자열들의 해시 값들을 계산해 놓은 테이블은 rainbow table 이라는 테이블을 먼저 생성해 놓은 후 해시 값을 역추적해서 본래 값을 찾아내는 해킹 방법.
- 해시함수의 실행 속도가 굉장히 빠르므로 충분히 구현 가능한 방법
  - 해시 함수는 본래 패스워드를 저장하기 위한 것이 아니라, 짧은 시간에 데이터를 검색하기 위해 설계된 것이기 때문. (딕셔너리나 세트 자료구조에 해시가 쓰임)

### salting

요리에서 음식에 간을 맞추기 위해 소금을 더하듯이, 실제 비밀번호 이외에 추가적으로 랜덤 데이터를 더해서 해시 값을 계산하는 방법.

해커가 실제 어느 부분이 비밀번호 값이고, 어느 부분이 랜덤 값인지 알 수가 없게 됨. 따라서 rainbow attack 처럼 미리 해시 값들을 계싼해서 해킹하는 공격들을 무효화시킬 수 있음

### 키 스트레칭

기존의 단방향 해시 알고리즘들의 실행 속도가 너무 빠르다는 취약점을 보완하기 위한 방법

단방향 해시 값을 계산한 후 그 해시 값을 또 해시하고, 이를 여러 번 반복하는 방법

일반적인 장비로 1초에 50억 개 이상의 해시 함수를 실행시킬 수 있다고 하면, 이 방법을 적용하면 동일한 장비에서 1초에 5번 정도만 가능하다고 함. GPU를 사용하더라도 수백에서 수천 번 정도만 실행 가능

### bcrypt

salting과 키 스트레칭을 구현한 해시 함수 중 가장 널리 사용되는 것이 bcrypt

bcrypt는 처음부터 비밀번호를 단방향 암호화하기 위해 만들어짐 해시 함수임

외부 라이브러리 설치: `pip install bcrypt`

**bcrypt 사용**

```python
import bcrypt # 1
bcrypt.hashpw(b'secret password', bcrypt.gensalt()) # 2
# b'$2b$12$ViZ0qxKGtPsdjuP5QelQW.1QLikHfLd7QozBnx8CVLECZPUx9qf3m'
bcrypt.hashpw(b'secret password, bcrypt.gensalt()).hex() # 3
# '24326224313224455352587837364c5730534e36586d53463271384b4f72334364716634687976506b497a476561774444665a2f7745494f42777971'
```

1. bcrypt 라이브러리 임포트
2. bcrypt 라이브러리의 `hashpw` 메소드를 호출하여 해시화 수행.
   - `hashpw` 메소드는 2개의 인자를 받음
   - 하나는 해시화 하고자 하는 값(byte 타입)
   - 나머지 하나는 salt 값. `gensalt` 메소드를 통해 salt 값 생성. 개발자조차 어떤 salt 값이 쓰였는지 알지 못하도록 함
3. 2와 동일하나, 결괏값을 바이트가 아니라 hex(16진수) 값으로 생성

## access token

사용자가 로그인에 성공하면 백엔드 API 서버는 access token 이라고 하는 데이터를 프론트엔드에 전송한다.

그리고 프론트 엔드에서는 해당 사용자의 access token을 HTTP에 첨부해서 서버에 전송한다.

### access token을 사용하는 이유

HTTP는 stateless 이기 때문에 각각의 HTTP 통신은 독립적이어서 이전에 어떤 HTTP 통신들이 실행됐는지 모른다. 때문에 로그인 정보를 HTTP 요청에 첨부해서 보내야 API 서버에서 해당 사용자가 이미 로그인 된 상태라는 것을 알 수 있다.

access token 은 바로 이 로그인 정보를 담고 있는 것이다.

## JWT

access token 을 생성하는 여러 가지 방법이 있는데, 가장 널리 사용되는 것 중 하나가 JWT(JSON Web Token). 이름 그대로 JSON 데이터를 token으로 변환하는 방식임

백엔드 API 서버는 전송받은 사용자 아이디와 비밀번호를 확인하는 절차를 거친 후 인증이 되면 해당 사용자의 아이디를 다음과 같은 JSON 형태로 생성함

```json
{
	user_id = 1
}
```

로그인한 사용자 아이디를 JSON 형태로 저장함으로써 어느 사용자가 이미 로그인한 상태인 지를 알 수 있도록 하는 것임

하지만 이 정보를 HTTP로 네트워크상에서 주고받아야 하므로 JSON 데이터를 token 데이터로 변환시켜서 HTTP 응답을 보냄

access token을 받은 프론트엔드는 쿠키 등에 access token을 저장하고 있다가 해당 사용자를 위한 HTTP 요청을 백엔드 서버 API에 보낼 때 access token을 첨부해서 보냄. 그러면 백엔드에서는 프론트엔드로부터 받은 access token을 복호화해서 JSON 데이터를 얻어서 로그인한 사용자의 아이디를 읽어 들임으로써 해당 사용자가 이미 로그인한 상태임을 확인

### 왜 JSON 데이터를 토큰화 시켜서 사용해야 하는가?

단순 JSON 데이터를 사용하면 해킹에 취약함

누구나 JSON 데이터를 HTTP 요청에 첨부해서 전송할 수 있기 때문에 해당 사용자가 아니어도 해당 사용자로 인식될 수 있기 때문임

JWT는 단순 데이터 전송 기능 이외에도 검증의 기능도 가지고 있음

만약 누가 해킹 목적으로 가짜 JWT를 전송해도 백엔드 API 서버에서 자신이 생성한 JWT인지 아닌지를 확인할 수 있는 기능도 제공함

## JWT 구조

- header
- payload
- signature

JWT의 일반적인 형태는 다음과 같음

`xxxxx.yyyyy.zzzzz`

x 부분은 헤더이고 y 부분은 payload이며, z 부분은 signature 임. 각 부분은 `.` 으로 분리되어 있음

### header

해더는 두 부분으로 되어 있으며, 사용되는 해시 알고리즘(hashing algorithm)와 토큰 타입(JWT)를 지정함

```json
{
  "alg": "HS256",
  "typ": "JWT"
}
```

헤더를 [Base64URL](https://ko.wikipedia.org/wiki/베이스64) 방식으로 코드화해서 JWT의 첫 부분을 구성함

### payload

payload 는 JWT를 통해 실제로 서버 간에 전송하고자 하는 데이터 부분임. HTTP 메시지의 body 부분과 비슷함

```json
{
  "user_id": 2,
  "exp": 1539517391
}
```

payload도 Base64URL 코드화 되어서 JWT의 두 번째 부분을 구성함

Base64URL은 코드화(encoding) 시키는 것이지 암호화(encryption)가 아니기에 누구나 복원 가능함

그러므로 민감한 정보는 넣지 않는 것이 좋음

### signature

JWT가 원본 그대로라는 것을 확인할 때 사용되는 부분임

signature는 Base64URL 코드화된 header와 payload, 그리고 JWT secret을 헤더에 지정된 암호 알고리즘으로 암호화하여 전송함(복호화 가능).

프론트엔드가 JWT를 백엔드 API 서버로 전송하면 서버에서는 전송받은 JWT의 signature 부분을 복호화하여 서버에서 생성한 JWT가 맞는지를 확인함. (싸인과도 같은 것)

이 signature 부분이 잘못되어 있으면 JWT를 누군가 임의적으로 바꾸거나 해킹의 목적으로 임의로 생성한 것이라고 간주

JWT 사용시 조심해야 할 점은 signature 부분 외에 다른 부분들은 암호화가 아닌 Base64URL 코드화되어 있다는 것임. 누구나 원본 데이터를 볼 수 있는 부분이므로 민감한 데이터는 저장하지 않도록 해야 함

## PyJWT

파이썬에서 JWT를 생성하고 복호화할 수 있게 해주는 라이브러리

설치: `pip install PyJWT`

**기본 사용법**

```python
import jwt # 1
data_to_encode = {'some': 'payload'} # 2
encryption_secret = 'secrete' # 3
algorithm = 'HS256' # 4
encoded = jwt.encode(data_to_encode, encryption_secret, algorithm=algorithm) # 5
# b'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzb21lIjoicGF5bG9hZCJ9.j4hydZvraNFUqUHpXw0hYBN9qTRzbm9-yS9h5skNht0'
jwt.decode(encoded, encryption_secret, algorithms=[algorithm]) # 6
# {'some': 'payload'}
```

1. PyJWT 라이브러리의 jwt 모듈 임포트
2. JWT의 payload 부분에 들어갈 JSON 데이터
3. JWT의 signature 부분을 암호화할 때 사용할 비밀 키(secret key) 지정.
   - 여기서는 아주 간단한 키를 사용했지만, 실제 시스템에서는 훨씬 복잡한 값을 사용하는 것이 권장됨
4. JWT의 signature 부분을 암호화할 때 사용할 암호 알고리즘을 지정함
5. JWT를 생성함
6. 5에서 만들었던 JWT를 복호화하여 원본 payload 데이터를 읽어 들임

# 인증 엔드포인트 구현하기

## sign-up 엔드포인트 수정

sign-up 엔드포인트를 수정해서 사용자의 비밀번호를 bcrypt 알고리즘을 사용해서 암호화해서 저장하도록 함

```python
import bcrypt # 1

@app.route('/sign-up', methods=['POST'])
def sign_up():
	new_user = request.json
	new_user['password'] = bcrypt.hashpw(new_user['password'].encode('UTF-8'), bcrypt.gensalt()) # 2

	#생략
```

1. bcrypt 모듈 임포트
2. bcrypt 모듈을 사용해서 사용자의 비밀번호를 암호화 함
   - bcrypt 모듈의 `hashpw` 함수는 스트링 값이 아닌 byte 값을 받으므로 사용자의 비밀번호를 UTF-8 인코딩으로 byte 변환해서 `hashpw` 함수에 넘겨주어 호출함

## 인증 엔드포인트 생성

인증 엔드포이트에서는 HTTP POST request에 JSON 데이터로 해당 사용자의 아이디(혹은 이메일)와 비밀번호를 전송받아서 데이터베이스에 저장되어 있는 해당 사용자의 비밀번호와 동일한지 확인하면 됨.

동일하면 JWT access token을 생성해서 보내면 됨

```python
from datetime import datetime, timedelta
import bcrypt
import jwt # 1

@app.route('/login', methods=['POST'])
def login():
	credential = request.json
	email = credential['email'] # 2
	password = credential['password'] # 3

	row = database.execute(text("""
		SELECT
			id,
			hashed_password
		FROM users
		WHERE email = :email
	"""), {'email' : email}).fetchone() # 4

	if row and bcrypt.checkpw(password.encode('UTF-8'), row['hashed_password'].encode('UTF-8')): # 5
		user_id = row['id']
		payload = {
			'user_id' : user_id
			'exp' : datetime.utcnow() + timedelta(seconds = 60 * 60 * 24)
		} # 6
		token = jwt.encode(payload, app.config['JWT_SECRET_KEY'], 'HS256') # 7

		return jsonify({
			'access_token' : token.decode('UTF-8')
		}) # 8
	else:
		return '', 401  # 9
```

1. jwt 모듈 임포트
2. HTTP 요청으로 전송된 JSON body에서 사용자의 이메일을 읽어 들임
3. HTTP 요청으로 전송된 JSON body에서 사용자의 비밀번호를 읽어 들임
4. 2에서 읽어 들인 사용자의 이메일을 사용하여 DB에서 해당 사용자의 암호화된 비밀번호를 읽어 들임
5. 4에서 읽어 들인 사용자의 암호화된 비밀번호와 2에서 읽어 들인 사용자의 비밀번호가 일치하는 지 확인하는 부분
   - 먼저, row가 None이면 해당 사용자가 존재하지 않는다는 뜻이므로 인증 허가를 안 해주면 됨
   - 만일 사용자가 존재한다면 해당 사용자의 암호화된 비밀번호와 사용자가 전송한 비밀번호를 bcrypt 모듈의 `checkpw` 함수를 사용해서 동일한지 확인.
   - `checkpw` 함수가 사용자의 비밀번호를 동일한 방식으로 암호화해서 이미 암호화되어 있는 비밀번호와 동일한 지를 확인해 줌
6. 사용자의 비밀번호가 확인 되었으면 이제 JWT를 생성할 차례임
   - 해당 사용자의 DB 상의 아이디에 해당하는 user_id, 그리고 해당 JWT의 유효기간 부분인 exp를 설정해 줌.
   - 여기서는 JWT의 유효기간을 하루로 설정하였음
   - JWT의 유효기간이 지나면 해당 JWT를 무효화가 되므로 새로 인증을 받아야 함
7. 6에서 생성한 payload JSON 데이터를 JWT로 생성함
8. 7에서 생성한 JWT를 HTTP 응답으로 전송함
9. 만일 5에서 사용자가 존재하지 않거나 사용자의 비밀번호가 틀리면, Unauthorized 401 status의 HTTP 응답을 보냄.

# 인증 절차를 다른 엔드포인트에 적용하기

인증을 통해 생성된 access token을 통해서 인증된 사용자만 사용 가능하도록 다른 엔드포인트들에 적용하기

미니터 API에서 인증 절차가 필요한 엔드포인트들을 tweet, follow, unfollow

일반적으로 인증 절차는 여러 엔드포인트에서 공통적으로 필요한 경우가 대부분임

이렇게 여러 함수(엔드포인트도 함수로 구현되므로)에서 공통적인 기능을 필요로 하는 경우에 자주 사용되는 구현 방법은 파이썬의 decorator를 사용하는 것임

**decorator**는 어떤 함수를 다른 함수가 실행되기 전에 자동으로 먼저 실행될 수 있도록 도와줌. 이름 그대로 다른 함수에 장식처럼 첨부. 주로 공통적으로 항상 먼저 실행되어야 하는 코드가 있을 때 사용하게 됨

decorator로 사용되는 함수는 함수 이름 앞에 @를 붙여서 적용하고자 하는 함수의 정의 부분 위에 지정해 줌

```python
@run_this_first # 1
def and_then_rutn_this(): # 2
	print("RUnning the second method")
```

1. @ + 함수 이름의 형태로 decorator를 적용해 줌
2. 이 함수가 실행되면 해당 함수가 실행되기 전에 1의 `run_this_first` 함수가 먼저 실행 됨

## decorator 함수

decorator 함수는 함수를 리턴하는 함수임

파이썬에서는 functools 모듈의 wraps decorator 함수를 사용해서 decorator 함수를 만들 수 있음

```python
from functools import wraps # 1

def test_decorator(f): # 2
	@wraps(f) # 3
	def decorated_function(*args, **kwargs): # 4
		print("Decorated Function")
		return f(*args, **kwargs) # 5

	return decorated_function # 6

@test_decorator # 7
def func(): # 8
	print("Calling func function")
```

1. functools 모듈의 `wraps` decorator 함수 임포트
2. decorator 함수 정의
   - decorator 함수는 함수를 인자로 받아서 함수를 리턴하는 함수임
   - 여기서는 `f` 라고 이름 지어진 함수를 인자로 받음
   - 이 `f` 함수는 바로 해당 decorator 함수가 적용되는 함수가 됨
3. `wraps` decorator 함수를 적용함
   - `wraps` decorator 함수를 꼭 적용해야만 decorator 함수를 만들 수 있는 것은 아님
   - 하지만 `wraps` decorator 함수를 적용하면 부차적으로 생기는 이슈들을 해결해 줌(공식문서 참조)
4. decorator 함수
   - decorator 함수를 리턴해 줘야 하므로 nested 함수로 지정해 줌
   - 함수의 인자가 \*args 와 \*\*kwargs 로 되어 있음!
   - decorator 함수는 여러 다양한 함수에 적용될 수 있으므로 모든 형태의 인자들을 받을 수 있어야 함. 그러므로 \*args 와 \*\*kwargs 를 인자로 지정해 줘서 모든 형태의 인자를 받을 수 있도록 함
5. `f` 함수를 실행시켜 리턴해 줌.
   - 즉, 해당 decorator 함수가 실행되고 난 후에 decorator가 적용된 함수를 호출해 주는 것
6. decorator 함수를 리턴해 줌
7. 2에서 만든 decorator 함수를 8의 함수에 적용해 줌
8. 2에서 만든 decorator 함수가 적용되는 함수

### 함수 호출

위에서 만든 `func()` 함수를 호출하면 다음과 같은 결과가 나옴

```python
func()
# Decorated Function
# Calling func function
```

decorator 함수의 출력물이 먼저 출력되고, 그 다음에 `func` 함수의 `print` 문이 실행되는 것을 볼 수 있음

## 인증 decorator 함수

1. 인증 엔드포인트를 통해 생성된 JWT access token
2. 프론트엔드는 JWT access token을 HTTP 요청에서 "Authorization" 헤더에 포함시켜 보냄
3. 인증 decorator 함수는 전송된 HTTP 요청에서 "Authorization" 헤더 값을 읽어 들여서 JWT access token을 읽어 들임
4. 인증 decorator 함수는 읽어 들인 JWT access token을 복호화해서 사용자 아이디를 읽어 들임으로써 해당 사용자의 로그인 여부를 결정함

```python
import jwt
from functools import wraps
from flask import request, Response, current_app

def login_required(f): # 1
	@wraps(f) # 2
	def decorated_function(*args, **kwargs):
		access_token = request.headers.get('Authorization') # 3
		if access_token is not None: # 4
			try:
				payload = jwt.decode(access_token, current_app.config['JWT_SECRET_KEY'], 'HS256') # 5
			except jwt.InvalidTokenError:
				payload = None # 6

			if payload is None: return Response(status=401) # 7

			user_id = payload['user_id'] # 8
			g.user_id = user_id
			g.user = get_user_info(user_id) if user_id else None

		else:
			return Response(status = 401) # 9

		return f(*args, **kwargs)
	return decorated_function

```

1. `login_required` decorator 함수를 지정함
   - `login_decorator` 함수가 적용된 함수는 해당 사용자가 로그인을 이미 한 상태에서만 실행될 수 있음
2. functools 라이브러리의 `wraps` decorator 함수를 적용해서 decorator 함수를 구현함
3. 전송된 HTTP 요청에서 "Authorization" 헤더 값을 읽어 들여 access token을 얻음
4. authorization 헤더가 전송되었다면 access token을 복호화해서 payload JSON을 읽어 들이도록 함.
   - 만일 access_token이 None이라면 authorization 헤더가 전송되지 않았다는 뜻이므로 인증 허가를 하지 않도록 함
5. access token을 복호화 해서 payload JSON을 읽어 들임.
   - jwt 모듈의 `decode` 함수는 JWT access token을 복호화할 뿐만 아니라, 토큰이 해당 백엔드 API 서버에서 생성된 토큰이 맞는지 확인하는 절차도 실행함.
   - 이런 절차를 실행하기 위해서는 해당 JWT의 signature 부분을 암호화할 때 사용한 secret key가 필요함
   - 여기서는 config에서 JWT_SECRET_KEY 필드 값을 읽어 들여 secret key를 읽어 들임 (login 엔드포인트에서 JWT 토큰을 생성할 때 사용한 동일한 secret key)
6. 만일 exception이 일어나면 JWT를 복호화하는 데 문제가 있었다는 뜻임
7. payload가 None이라는 것은 문제가 있다는 뜻이므로 Unauthorized 401 응답을 보냄
8. JWT에서 복호화한 payload JSON에서 user_id를 읽어 들임.
   - 그리고 해동 사용자 아이디를 사용해서 DB에서 사용자 정보도 읽어 들임
   - `get_user_info` 함수는 주어진 사용자 아이디를 바탕으로 DB에서 사용자 정보를 읽어 들이는 함수
   - 참고: Flask의 g 객체는 스레드와 각각의 request 내에서만 값이 유효한 스레드 로컬 변수임. 사용자의 요청이 들어오더라도 각각의 request 내에서만 g 객체가 유효하기 때문에 사용자 ID를 저장해도 문제가 없음. `from flask import g` 필요
9. 4에서 authorization 헤더가 전송되지 않은 경우 Unauthorized 401 응답을 보냄.

## 인증 decorator 적용하기

미니터 API에서 로그인을 해야만 사용할 수 있는 엔드포인트는 tweet, follow, 그리고 unfollow 엔드포인트임

다음과 같이 적용하기를 원하는 함수의 정의 부분 위에 명시해주면 됨

```python
@app.route('/tweet', methods=['POST']) # 1
@login_required #2
def tweet():
	user_tweet = request.json
	user_tweet['id'] = g.user_id # 인증 데코레이터에서 읽어 들인 사용자 아이디
	tweet = user_tweet['tweet']

	if len(tweet) > 300:
		return '300자를 초과했습니다', 400

	insert_tweet(user_tweet)

	return '', 200

@app.route('/follow', methods=['POST'])
@login_required
def follow():
	#생략

@app.route('/unfollow', methods=['POST'])
@login_required
def unfollow():
	#생략
```

1. `route` decorator를 먼저 적용시킴
   - `route` 는 적용된 함수를 Flask 엔드포인트로 변경시켜 주는 decorator 함수이기 때문에 이 경우 `route` decorator 함수와 `login_required` decorator 함수까지 2 개의 decorator를 적용해야 함
   - 이렇게 하나 이상의 decorator를 저굥시킬 때에는 순서가 중요한데, 먼저 적용하는 decorator가 먼저 실행되기 때문임
   - 그러므로 이 경우 `route` decorator를 먼저 적용해서 해당 함수가 엔드포인트로 지정되도록 해주는 게 중요함
2. `route` decorator를 먼저 적용시킨 후 `login_required` decorator를 적용시켜 줌

이제 tweet, follow, unfollow 엔드포인트에 `login_required` decorator를 적용시켰으니 해당 엔드포인트들을 실행시키기 위해서는 먼저 로그인을 해야 함. 그렇지 않으면 다음과 같이 Unauthorized 401 응답이 리턴 됨

```python
(api) [api] http -v POST localhost:5000/tweet id=7 tweet="안녕하세요 저는 서버 개발자 김서버입니다"

POST /tweet HTTP/1.1
Accept: application/json, */*;q=0.5
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 136
Content-Type: application/json
Host: localhost:5000
User-Agent: HTTPie/2.2.0

{
    "id": "7",
    "tweet": "안녕하세요 저는 서버 개발자 김서버입니다"
}

HTTP/1.0 401 UNAUTHORIZED
Content-Length: 0
Content-Type: text/html; charset=utf-8
Date: Wed, 28 Oct 2020 03:29:53 GMT
Server: Werkzeug/1.0.1 Python/3.7.9
```

따라서 먼저 로그인 엔드포인트를 호출해서 인증 절차를 거친 후 access token을 생성해야 함

```python
(api) [api] http -v POST localhost:5000/login email=serverk@gmail.com password=serverk1234

POST /login HTTP/1.1
Accept: application/json, */*;q=0.5
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 57
Content-Type: application/json
Host: localhost:5000
User-Agent: HTTPie/2.2.0

{
    "email": "serverk@gmail.com",
    "password": "serverk1234"
}

HTTP/1.0 200 OK
Content-Length: 146
Content-Type: application/json
Date: Wed, 28 Oct 2020 03:32:43 GMT
Server: Werkzeug/1.0.1 Python/3.7.9

{
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjo3LCJleHAiOjE2MDM5NDIzNjN9.WnxVef_YyrO0S6AV_Y5rMZiDCjJcnPeg7pJTFgJZ4Cw"
}
```

로그인 엔드포인트를 사용해서 인가 절차를 거친 후 생성된 access token을 HTTP 요청의 authorization 헤더 값으로 지정해서 HTTP 요청을 전송해야 엔드포인트가 실행됨

```python
(api) [api] http -v POST localhost:5000/tweet tweet="안녕하세요 저는 서버 개발자 김서버입니다" "Authorization: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjo3LCJleHAiOjE2MDM5NDIzNjN9.WnxVef_YyrO0S6AV_Y5rMZiDCjJcnPeg7pJTFgJZ4Cw"

POST /tweet HTTP/1.1
Accept: application/json, */*;q=0.5
Accept-Encoding: gzip, deflate
Authorization: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjo3LCJleHAiOjE2MDM5NDIzNjN9.WnxVef_YyrO0S6AV_Y5rMZiDCjJcnPeg7pJTFgJZ4Cw
Connection: keep-alive
Content-Length: 125
Content-Type: application/json
Host: localhost:5000
User-Agent: HTTPie/2.2.0

{
    "tweet": "안녕하세요 저는 서버 개발자 김서버입니다"
}

HTTP/1.0 200 OK
Content-Length: 0
Content-Type: text/html; charset=utf-8
Date: Wed, 28 Oct 2020 03:45:39 GMT
Server: Werkzeug/1.0.1 Python/3.7.9
```

더 이상은 /tweet 엔드포인트를 호출할 때 사용자 아이디를 지정해 주지 않아도 된다

이는 `login_required` decorator 에서 이미 해당 사용자의 인증 절차를 거치면서 사용자 아이디를 읽어 들였고, /tweet 엔드포인트에서 그 정보를 g 객체를 통해 읽어들이는 부분을 추가했기 때문이다.

이렇게 인증 절차를 통해서 해당 사용자의 정보를 얻는 것이 보안적으로 훨씬 더 안전하다. 이전의 트윗 엔드포인트에서는 누구나 사용자 id 부분을 임의로 정해서 트윗을 보낼 수 있었다면, 이제는 인증된 사용자만 본인의 계정으로 트윗을 보낼 수 있다.

```python
@app.route('/tweet', methods=['POST'])
@login_required
def tweet():
	user_tweet = request.json
	user_tweet['id'] = g.user_id # 1
	tweet = user_tweet['tweet']

	if len(tweet) > 300:
		return '300자를 초과했습니다', 400

	insert_tweet(user_tweet)

	return '', 200
```

# 샘플 프론트엔드 시스템

다음의 깃허브 리포지토리에서 샘플 프론트엔드 시스템 코드를 내려받자

```
https://github.com/Yeri-Kim/python-tutorial-frontend
```

다운받은 해당 디렉토리로 가서 다음의 파이썬 명령어를 실행하면 샘플 프론트엔드가 실행된다

```bash
python -m http.server
```

샘플 프론트엔드 시스템에서는 미니터 API가 로컬 호스트 5000번 포트에서 실행되고 있다고 가정함. API를 실행해 놓아야 함.

샘플 프론트엔드와 연결시키기 위해서는 API에 몇 가지 추가할 것이 있음

우선 API URL 도메인 주소와 프론트엔드 URL 도메인 주소가 달라서 생기는 문제인 CORS 문제를 해결해 줘야 함

```bash
pip install flask-cors
```

라이브러리를 설치하고, API에 다음과 같은 코드를 추가해야 함

```bash
from flask_cors import CORS # 임포트

def create_app(test_config=None):
	app = Flask(__name__)

	CORS(app) # 추가한 부분
```

다음의 엔드포인트도 추가

```bash
@app.route('/timeline', methods['GET'])
@login_required
def user_timeline():
	user_id = g.user_id

	return jsonify({
		'user_id': user_id,
		'timeline': get_timeline(user_id)
	})
```

이제 샘플 프론트엔드와 API를 모두 실행하고, 웹 브라우저 주소창에 [http://localhost:8000/sign-up.html](http://localhost:8000/sign-up.html) 주소로 접속하면 된다.

그리고 다운 받은 프론트엔드를 실행할 때나 로그인할 때 오류가 나서 살펴보니, 파일명 signup.html 을 sign-up.html로 바꿔주고(혹은 주소창을 signup.html로)

`login` 함수의 JSON 반환 부분에 user_id를 추가해주면 되더라

```python
return jsonify({
	'user_id': user_id, # 추가한 부분
	'access_token': token.decode('UTF-8')
})
```

## 7장 정리

7장에서 알아본 것:

- 인증 절차는 대부분의 API들일 필요로 함
- 사용자 비밀번호는 꼭 단방향 해시 암호화 해서 저장해야 함. 그리고 bcrypt와 같이 rainbow attack을 막아 주는 단방향 암호 알고리즘을 사용하는 것이 더욱 안전
- HTTP 통신은 stateless이므로 해당 통신 전에 인증 절차를 거치는 통신이 있었는지에 대해 알 수 없음. 따라서 모든 HTTP 통신에 인증 여부 정보를 첨부해야 함. 이걸 가능케 해주는 것이 access_token
- access token은 JWT(JSON Web Token)을 사용해서 생성. JWT를 생성할 때 조심해야 할 점은 민감한 사용자의 개인정보는 포함시키지 말아야 한다는 것!
- 인증 절차를 엔드포인트에 적용시키기 위해서 decorator를 사용할 수 있음

</details>
<details>
<summary>Chapter 8. unit test</summary>

# Chapter 8 unit test

# 테스트 자동화의 중요성

시스템 테스트에서 가장 중요한 것은 테스트의 자동화임

매뉴얼 테스트는 테스트 실행 속도도 느리고, 자주 실행하기 힘들고, 부정확할 확률이 높다.

테스트를 최대한 자동화해서 테스트가 반복적으로, 자주 실행될 수 있도록 해야하고, 항상 정확하게 빠지는 부분이 없도록 테스트가 실행되도록 해야 한다.

시스템 테스트 방법은 크게 3가지로 나눌 수 있음

- UI test / End-To-End test
- integration test
- unit test

# UI test / End-To-End test

UI test는 시스템의 UI(User Interface)를 통해서 하는 테스트다.

- ex) 웹 브라우저를 통해 웹사이트를 실제로 접속하고 UI에 직접 입력하고 클릭

장점

- 사용자가 실제로 시스템을 사용하는 방식과 가장 동일하게 테스트.

단점

- 시간이 가장 많이 소요되는 테스트임
- 프론트엔드부터 백엔드까지 모든 시스템을 실행시키고 연결해야 할 수 있음
- 자동화하기가 가장 까다로움

UI test는 사용자가 사용하는 것과 동일한 방식으로 테스트 한다는 점 때문에 꼭 필요한 테스트지만, 단점들 때문에 다른 테스트 방식에 비해 비중을 가장 적게 두어야 하는 테스트 방식임. (대략 10% 정도)

# integration test

integration test는 테스트하고자 하는 서버를 실제로 실행시키고, 해당 서버를 작동시킬 수 있는 요청(eg., HTTP 요청)이나 명령어를 실행해서 테스트해 보는 방식이다.

실제 시스템을 실행시켜서 진행하는 점에서 UI test와 비슷한 면이 있으나, 모든 시스템이 아니라 테스트하고자 하는 해당 시스템만 실행시켜 테스트한다는 점에서 다르다.

장점

- 하나의 시스템만 실행해서 테스트하므로 UI test에 비해 테스트 설정이나 실행 시간이 더 짧고 간단함
- 대부분이 백엔드 API 시스템처럼 UI적인 요소가 없는 백엔드 시스템에 실행하기 때문에 자동화하기도 UI test보다 더 용이함

단점

- 실제로 시스템을 실행해서 테스트를 실행해야 하므로 여전히 까다로운 부분이 존재
- unit test에 비해 자동화에 걸리는 공수가 더 크고 실행 속도도 더 느림

전체 테스트 중 대략 20% 정도 할당

# unit test

unit test는 시스템을 테스트한다는 개념보다는, 코드를 직접 테스트하는 개념이다. 즉, 코드로 코드를 테스트하는 것임

## 예시

`multiply_by_two`

```python
def multiply_by_two(x):
	return x * 2
```

위 함수를 테스트 하는 방법

: 함수를 호출한 후 결괏값이 예상하는 값과 동일한지 확인하는 코드를 구현해서 실행

```python
assert multiply_by_two(2) == 4  # 1
```

1. `assert` 는 그 다음에 오는 표현이 False일 경우 AssertionError 익셉션(exception)을 던짐.

방금 구현한 코드가 바로 unit test다. 이런 방식으로 모든 함수 또는 메소드를 테스트하는 것이다.

unit test는 테스트가 가능한 코드의 unit(단위)들을 테스트한다는 의미다. 테스트 가능한 코드 unit들은 일반적으로 함수(메소드)다. 따라서 함수나 메소드를 호출한 후 결괏값을 확인하는 코드를 실행함으로써 unit test를 실행하는 것이다.

장점

- 실행하기 쉽고, 실행 속도가 빠름
- 디버깅이 비교적 쉬움 (함수 단위로 테스트하기 때문)

단점

- 전체적인 부분을 테스트하기에는 제한적(함수 단위로 테스트하기 때문)
- 모든 함수가 제대로 작동하는 것을 테스트했다고 할지라도, 전체적인 하나의 서비스로 연결되었을 때에도 정상적으로 작동하는 지 확신하기 힘듦

unit test의 단점을 UI test와 integration 테스트로 보완해야 함.

unit test 70%, integration test 20%, UI test 10% 할당

# pytest

외부 라이브러리 pyteset 설치

```
pip install pytest
```

pytest는 파일 이름의 앞부분에 test\_ 라고 되어 있는 파일들만 테스트 파일로 인식하고 실행한다

- test_example.py (O)
- [example.py](http://example.py) (X)

함수도 마찬가지로 함수 이름 앞부분에 test\_ 라고 되어 있는 함수들만 실제 unit test 함수로 인식하고 실행시킨다

test_multiply_by_two.py

```python
def multiply_by_two(x):
	return x * 2

def test_multiply_by_two():   # 1
	assert multiply_by_two(4) == 7   # 2
```

1. `multiply_by_two` 함수를 테스트하는 unit test 함수.
2. `multiply_by_two(4)` 가 7을 리턴하는지 테스트함. 8을 리턴해야 정상이므로 실행하면 AssertionError 발생

위와 같이 test_multiply_by_two.py 파일을 만들고 터미널에서 해당 디렉토리에서 pytest를 실행하면 오류가 난다. 어느 부분에 문제가 있는지 자세한 내용이 같이 나와 디버깅하기 수월하다.

파일에서 문제가 되는 부분을 수정한 후 다시 pytest를 실행하면 unit test가 성공했다는 메시지가 나온다.

# 미니터 API unit test

unit test는 일반적으로 함수를 테스트하는 코드인데, Flask에서는 엔드포인트들이 함수로 구현되어 있기 때문에 unit test로 엔드포인트를 직접 테스트할 수 있다는 장점이 있다.

unit test를 하기 위해 test_endpoints.py 라는 이름의 파일을 만들어서 unit test 코드를 구현하고, 테스트용 DB를 만들어 본다

그리고 [config.py](http://config.py) 파일에 다음과 같은 내용 추가

config.py

```python
test_db = {     # 1
		'user' : 'test', # mysql 아이디
		'password' : 'password',
		'host' : 'localhost',
		'port' : 3306,
		'database' : 'test_db'
}

test_config = {   # 2
		'DB_URL' : f"mysql+mysqlconnector://{test_db['user']}:{test_db['password']}@{test_db['host']}:{test_db['port']}/{test_db['database']}?charset=utf8"
}
```

1. test 데이터베이스 접속 설정 지정
2. 1의 지정해 준 test 데이터베이스 접속 설정을 기반으로 test 데이터베이스 접속 URL을 test_config 라는 딕셔너리에 지정

이제 test_endpoints.py 에서 앞서 지정한 테스트 설정들을 읽어 들여 test 데이터베이스에 접속

test_endpoints.py

```python
import config # 1

from sqlalchemy import create_engine, text

# 2
database = create_engine(config.test_config['DB_URL'], encoding='utf-8', max_overflow=0)

```

1. config 파일을 임포트하여 테스트 설정 읽어 들이기
2. 테스트 설정을 읽어 들여서 test DB에 접속

이제 가장 간단한 엔드포인트인 ping 엔드포인트틀 테스트해봐야 하는데,

ping 함수는 단순히 호출하는 것은 의미가 없고, ping 엔드포인트에 GET 요청을 보내야 의미 있는 실행이다.

unit test 코드를 실행시키는 것이기 때문에 실제로 API 서버가 실행되지는 않는데, Flask에서는 unit test에서 엔드포인트를 테스트할 수 있는 기능을 제공한다.

Flask에서 제공하는 `test_client` 함수를 사용해서 엔드포인트들을 그들의 URI를 통해 호출하고, 데이터도 전송할 수 있다.

실제로 HTTP 전송을 하는 듯한 효과를 볼 수 있는데, 실제로 네트워크롤 통한 HTTP 전송을 하는 것은 아니고, 코드상에서(메모리에서만) 실행되는 것이다.

`test_client` 메소드를 사용하기 위해서는 먼저 테스트할 flask application을 생성해야 한다.

이미 구현한 미니터 API 코드로부터 `create_app` 함수를 임포트하면 된다.

test_endpoints.py

```python
from app import create_app   # 1
import pytest

@pytest.fixture # 2
def api(): # 3
	app = create_app(config.test_config) # 4
	app.config['TEST'] = True # 5
	api = app.test_client() #  6

	return api # 7
```

1. 미니터 API 소스 코드 파일인 [app.py](http://app.py) 파일에서 `create_app` 함수를 임포트
2. pytest.fixture 데코레이터를 적용.
   - 이 데코레이터가 중요하다.
   - 이 데코레이터가 적용된 함수와 같은 이름의 인자(parameter)가 다른 test 함수에 지정되어 있으면 pytest가 알아서 같은 이름의 함수의 리턴 값을 해당 인자에 넣어 준다.
3. fixture 함수 이름
   - 함수의 이름이 중요
   - 동일한 이름의 인자를 해당함수의 리턴 값으로 적용시켜 줌
4. 1에서 임포트한 `create_app` 함수를 사용해서 테스트할 미니터 API 애플리케이션을 생성한다.
   - 이때 설정을 test_config를 `create_app` 함수에 인자로 넘겨줌으로써 DB 등의 설정이 모두 테스트 설정이 적용되도록 함
5. TEST 옵션을 `True` 로 설정해 줌으로써 Flask가 에러가 났을 경우 HTTP 요청 오류 부분은 핸들링하지 않음으로써 불필요한 오류 메시지는 출력되지 않게 함
6. `test_client` 함수를 호출해서 테스트용 클라이언트를 생성함
   - 테스트용 클라이언트를 사용해서 URI 기반으로 원하는 엔드포인트들을 호출할 수 있게 됨
7. 6에서 호출한 test client를 리턴해 줌

이제 생성된 test_client를 이용해서 /ping 엔드포인트를 테스트하는 코드를 구현한다.

test_client를 통해서 GET 요청을 /ping URI에 보내면 된다.

```python
def test_ping(api):    # 1
	resp = api.get('/ping')   # 2
	assert b'pong' in resp.data   # 3
```

1. ping 엔드포인트를 테스트하는 함수.
   - 여기서 중요한 것은 api 인자!
   - pytest 커맨드를 실행해서 테스트들을 실행하기 때문에 test 함수들에 인자를 넘겨주어 실행할 수 없다.
   - 하지만, pytest 함수가 동일한 이름을 가지고 있고, pytest fixture 데코레이터가 적용되어 있는 함수를 찾아서 해당 함수의 리턴 값을 인자에 적용시켜 주기 때문이다.
   - 따라서 여기에서는 앞서 구현된 api 함수의 리턴 값, 즉 test client가 자동으로 적용되는 것이다.
2. test client의 get 메소드를 통해서 가상의 GET 요청을 /ping URI와 연결되어 있는 엔드포인트에 보낸다.
3. 2를 실행 후 리턴받은 응답(response)의 body에 "pong"이라는 텍스트가 포함되어 있는지 확인한다.
   - 포함되어 있으면 정상적으로 작동한 것으로 간주하여 테스트 성공이고, 그렇지 않으면 실패한 것으로 간주도니다.
   - 여기에 "pong"이라는 스트링 앞에 붙은 b는 해당 스트링을 _byte로 변환_ 해서 비교하는 것이다.

이제 터미널에서 `pytest test_endpoints.py` 명령어를 실행하면 테스트가 성공하는 것을 확인할 수 있다.

다음은 좀 더 복잡하고 POST 요청을 보내야 하는 /tweet 엔드포인트다.

/tweet 엔드포인트를 통해 tweet을 생성하기 위해서는

- 먼저, 사용자가 있어야 하고
- 해당 사용자로 인증 절차를 걸친 후 access token을 받고
- tweet 엔드포인트를 호출해야 한다

test_tweet 함수 구현

```python
def test_tweet(api):
    ## Create new test user   #1
    new_user = {
            'email' : 'test1234@gmail.com',
            'password' : 'test password',
            'name' : '시험용',
            'profile' : 'test profile'
            }

    resp = api.post(
            '/sign-up',
            data = json.dumps(new_user),
            content_type ='application/json'
    )
    assert resp.status_code == 200

    ## Get the id of the new user    #2
    resp_json = json.loads(resp.data.decode('utf-8'))
    new_user_id = resp_json['id']

    ## login   #3
    resp = api.post(
        '/login',
        data = json.dumps({'email' : 'test1234@gmail.com',
            'password' : 'test password'}),
        content_type = 'application/json'
    )
    resp_json = json.loads(resp.data.decode('utf-8'))
    access_token = resp_json['access_token']

    ## tweet   #4
    resp = api.post(
        '/tweet',
        data = json.dumps({'tweet' : "Hello World!"}),
        content_type = 'application/json',
        headers = {'Authorization' : access_token}
    )
    assert resp.status_code == 200

    ## tweet 확인   #5
    resp = api.get(f'/timeline/{new_user_id}')
    tweets = json.loads(resp.data.decode('utf-8'))

    assert resp.status_code == 200
    assert tweet == {
        'user_id' : 1,
        'timeline' : [
            {
                'user_id' : 1,
                'tweet' : "Hellow World!"
            }
        ]
    }
```

1. tweet을 보낼 테스트 사용자를 먼저 생성한다. sign-up 엔드포인트를 호출해서 생성하며, 호출 후 응답(response)의 status code가 OK 200인지 확인한다
2. 1에서 새로 생성한 사용자의 아이디를 1에서 받은 JSON 응답(response)에서 읽어 들인다. 나중에 /timeline 엔드포인트를 호출할 때 사용자 아이디가 필요하다
3. /tweet 엔드포인트에 HTTP 요청을 전송하려면 access token이 필요하므로 /login 엔드포인트를 먼저 호출해서 access token을 읽어 들인다.
   - 주의!!: 계속 에러가 떠서 확인해 보니, [config.py](http://config.py)의 test_config 부분에 JWT_SECRET_KEY를 추가해 줘야 한다. 이는 테스트 api를 생성할 때에는 config 방식이 달라지기 때문이다 (app.py 참고)
4. /tweet 엔드포인트를 호출해 tweet을 생성한다. 3에서 생성한 access code를 "Authorization" 헤더에 첨부해서 request를 보낸다.
5. 4에서 생성한 tweet이 정상적으로 생성되었는지를 확인하기 위해 timeline 엔드포인트를 호출해서 응답(response)을 확인한다. timeline 엔드포인트를 호출할 때 2에서 읽어 들인 사용자 아이디를 사용한다.
   - 주의!!: 테스트 시 tweets = json.loads(resp.data.decode('utf-8')) 부분에서 계속 오류가 뜬다 json.decoder.JSONDecodeError: Expecting value: line 1 column 1 (char 0)

</details>
