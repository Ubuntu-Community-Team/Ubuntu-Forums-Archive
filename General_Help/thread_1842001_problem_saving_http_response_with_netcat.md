---
title: "problem saving http response with netcat"
date: 2011-09-10
forum: General Help
---

### Post by carel.jonkhout on 2011-09-10
I am trying to use netcat to send http requests and save the http responses. I can't get netcat to print the http response:

echo -e "GET [http://google.com/index.html](http://google.com/index.html) HTTP/1.0\n\n" | nc -v [www.google.com](www.google.com) 80

will just say:

Connection to [www.google.com](www.google.com) 80 port [tcp/www] succeeded!

I used wireshark to see what is going on. I am definitely recieving a response. in this case:

HTTP/1.0 301 Moved Permanently
Location: [http://www.google.com/index.html](http://www.google.com/index.html)
Content-Type: text/html; charset=UTF-8
Date: Sat, 10 Sep 2011 17:36:13 GMT
Expires: Mon, 10 Oct 2011 17:36:13 GMT
Cache-Control: public, max-age=2592000
Server: gws
Content-Length: 229
X-XSS-Protection: 1; mode=block

<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>301 Moved</TITLE></HEAD><BODY>
<H1>301 Moved</H1>
The document has moved
<A HREF="http://www.google.com/index.html">here</A>.
</BODY></HTML>

---

### Post by Dangertux on 2011-09-10
> **carel.jonkhout said:**
> I am trying to use netcat to send http requests and save the http responses. I can't get netcat to print the http response:

echo -e "GET [http://google.com/index.html](http://google.com/index.html) HTTP/1.0\n\n" | nc -v [www.google.com]("http://www.google.com") 80

will just say:

Connection to [www.google.com]("http://www.google.com") 80 port [tcp/www] succeeded!

I used wireshark to see what is going on. I am definitely recieving a response. in this case:

HTTP/1.0 301 Moved Permanently
Location: [http://www.google.com/index.html](http://www.google.com/index.html)
Content-Type: text/html; charset=UTF-8
Date: Sat, 10 Sep 2011 17:36:13 GMT
Expires: Mon, 10 Oct 2011 17:36:13 GMT
Cache-Control: public, max-age=2592000
Server: gws
Content-Length: 229
X-XSS-Protection: 1; mode=block

<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>301 Moved</TITLE></HEAD><BODY>
<H1>301 Moved</H1>
The document has moved
<A HREF="http://www.google.com/index.html">here</A>.
</BODY></HTML>

Try something like this

```

echo -e "GET http://google.com/index.html HTTP/1.0\n\n" | nc -v www.google.com 80 > response

```

That should save the output to the file response.

For me the output of cat response is as follows
```

HTTP/1.0 301 Moved Permanently
Location: http://www.google.com/index.html
Content-Type: text/html; charset=UTF-8
Date: Sat, 10 Sep 2011 18:00:36 GMT
Expires: Mon, 10 Oct 2011 18:00:36 GMT
Cache-Control: public, max-age=2592000
Server: gws
Content-Length: 229
X-XSS-Protection: 1; mode=block

<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>301 Moved</TITLE></HEAD><BODY>
<H1>301 Moved</H1>
The document has moved
<A HREF="http://www.google.com/index.html">here</A>.
</BODY></HTML>

```

Hope that helps.

---

