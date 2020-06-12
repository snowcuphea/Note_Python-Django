

# Django



## 프로젝트 생성

* 현재 내가 위치한 곳에서 project를 만든다. (뒤에 .을 붙여주지 않으면, 폴더 안에 폴더 형식으로 생성된다.)

  ```bash
  django-admin startproject mysite .
  ```

* startapp pages 해주고 `settings.py` 에서 pages 앱 추가 해준다.

  ```bash
  django-admin startproject mysite .
  ```

  ![image-20200610134747551](images/image-20200610134747551.png)



* 서버를 켠다. 서버를 켜고, 다른 bash창을 이용해서 작업한다. 

```bash
python manage.py runserver
```

![image-20200610093310201](images/image-20200610093310201.png)







## 프로젝트 구성

* 세팅을 마친 후, url을 정의하여 경로를 지정한다. 

### urls.py

![image-20200610093733493](images/image-20200610093733493.png)

* 문자열로 path를 정의해준다.
* views.py에 있는 함수를 불러온다는 뜻이다. 그런데, 함수명 뒤에 괄호가 없다. 함수명만 넘겨줘야 하기 때문에 괄호가 없다 (괄호가 있으면 실행한다는 뜻이므로)



### views.py

* 요청을 처리하기 위한 함수를 정의한다. 

![image-20200610093505708](images/image-20200610093505708.png)



* mysite 안의 pages에 templates라는 폴더를 만들어준다. 

![image-20200610093436216](images/image-20200610093436216.png)

![image-20200610093632125](images/image-20200610093632125.png)





![image-20200610093912950](images/image-20200610093912950.png)

이번엔 hello라는 함수를 정의한다. 먼저 url부터 정의한다.



그 다음은 hello 함수를 만든다.

* 딕셔너리 형태로 보내면, key값에 대한 value를 html에서 받을 수 있다. 

![image-20200610094923869](images/image-20200610094923869.png)

![image-20200610101106268](images/image-20200610101106268.png)



* 변수에 담아서 보낼 수 있다.

![image-20200610101222268](images/image-20200610101222268.png)

![image-20200610101244408](images/image-20200610101244408.png)

![image-20200610101256997](images/image-20200610101256997.png)



* 여러 값을 보내야 할 때는 딕셔너리 형태로 만든다.

  ![image-20200610102741153](images/image-20200610102741153.png)

  ![image-20200610102828846](images/image-20200610102828846.png)

* 딕셔너리의 key값을 적어주면 value를 출력할 수 있다. (단, 딕셔너리 변수명 그대로는 접근할 수 없다. )

  ![image-20200610102915251](images/image-20200610102915251.png)





* 넘겨주는 변수 개수 상관없이 딕셔너리 형태로 보내면 나중에 편리하다.
* 딕셔너리명도 웬만하면 context로 통일해서 사용 

![image-20200610105124077](images/image-20200610105124077.png)

![image-20200610105136531](images/image-20200610105136531.png)



### request 랑 같이 넘겨주기

![image-20200610111307627](images/image-20200610111307627.png)

![image-20200610111335455](images/image-20200610111335455.png)

![image-20200610111434281](images/image-20200610111434281.png)

![image-20200610111420213](images/image-20200610111420213.png)







### 변수를 주소창으로 여러 개 넣어서 보내기

![image-20200610113038701](images/image-20200610113038701.png)

* path를 정해줄 때는 tring은 `<str:변수명>` 으로, int는 `<int:변수명>` 으로 구분해준다. 



![image-20200610113303467](images/image-20200610113303467.png)



![image-20200610113341002](images/image-20200610113341002.png)

![image-20200610113321349](images/image-20200610113321349.png)





![image-20200610113357894](images/image-20200610113357894.png)



* DTL을 사용하여 html내에서 for문을 사용할 수 있다. 중괄호 안에 %를 적는다. 

  ![image-20200610132109329](images/image-20200610132109329.png)

* 렌더링한 html안에서 주석을 쓰면, 오류가 난다. 웬만하면 주석은 사용하지 않는다. 



* 주석을 표현하려면,

  1) 파이썬의 주석처럼 `{#    #}` 로 표현한다. 

  * 개발자 도구에서 해당 주석이 나온다.

    

  2) `comment`

  * 개발자 도구에서 해당 주석이 나오지 않는다. 

```html
{% comment %}
	여기는 전부
	출력이 안됨
{% endcomment %}
```







### DTL : Django Template Language

![image-20200610132606645](images/image-20200610132606645.png)





* `forloop counter` : 내가 지금 몇번째 반복문을 하고 있는지 알려준다.

  '몇 번째' 인지 알려주는 거라서 index값 시작인 0이 아니라 1부터 시작된다. 

![image-20200610133232795](images/image-20200610133232795.png)

![image-20200610133244040](images/image-20200610133244040.png)



#### if문

![image-20200610133952994](images/image-20200610133952994.png)







* forloop.first, forloop.last

![image-20200610133801872](images/image-20200610133801872.png)

![image-20200610133827055](images/image-20200610133827055.png)



#### {% empty %}

![image-20200610134043258](images/image-20200610134043258.png)

![image-20200610134105792](images/image-20200610134105792.png)



*** 주의사항 ***

* 조건 걸 때, 변수와 `==` 을 붙여쓰면 오류가 난다. 무조건 변수와 `==`  사이에 공백을 줘야 한다. 

![image-20200610134321249](images/image-20200610134321249.png)



#### Filter

* 파이프라인 (shift + `\`) 를 활용한다.

![image-20200610141334268](images/image-20200610141334268.png)

![image-20200610141424813](images/image-20200610141424813.png)



* truncate 는 자르는 기능을 한다.
  * `truncatewords:단어수지정` : n단어 까지만 나오고, 나머지는 `...` 으로 출력된다.
  * `truncatechars:글자수지정` : `...`을 포함해 총 n글자가 나오게 한다.

![image-20200610141629355](images/image-20200610141629355.png)



#### lorem

* 의미없는 글을 채워넣을 수 있다.

![image-20200610142111448](images/image-20200610142111448.png)

![image-20200610142214721](images/image-20200610142214721.png)





## 예제



<h3>1. 간단한 반복문으로 리스트 각 요소들을 출력</h3>

```html
{% for item in my_list%}
    <p>{{item}}</p>
{%endfor%}
```

![image-20200610150837168](images/image-20200610150837168.png)



<h3>2.if, else 활용해서 문자열 비교</h3>

```html
{% if data_a == data_b %}
    <p>{{data_a}}와 {{data_b}}의 문자열이 같다.</p>
{% else %}
    <p>{{data_a}}와 {{data_b}}의 문자열은 다르다. </p>
{% endif %}

```





<h3>2-1. 내가 넘긴 문자열과 특정한 문자열 비교</h3>

```html
{% if thing == "admin" %}
    <p>admin입니다.</p>
{% else %}
    <p>일반회원입니다. </p>
{% endif %}

```



<h3>3. if, elif, else 사용해보기 : 문자열의 길이가 5이하면 short,문자열의 길이가 10이상이면 long,모두 아니면 적당 출력 </h3>

```html
{% if thing|length <= 6 %}
    <p>{{thing}}의 길이는 {{thing|length}} : short</p>
{% elif thing|length >= 10 %}
    <p>{{thing}}의 길이는 {{thing|length}} : long</p>
{% else %}
    <p>{{thing}}의 길이는 {{thing|length}} : 적당합니다. </p>
{% endif %}
```

![image-20200610150900802](images/image-20200610150900802.png)

<h3>4. 반복문으로 리스트 각 요소들을 출력해서 A:90이상, B:50이상, C:그외 출력</h3>

```html
{% for item in my_list%}
    {%if item >= 90 %}
        <p>점수:{{item}} => A</p>
    {%elif item >= 50 %}
        <p>점수:{{item}} => B</p>
    {%else %}
        <p>점수:{{item}} => C</p>
    {%endif%}
{%endfor%}
```

![image-20200610150911492](images/image-20200610150911492.png)