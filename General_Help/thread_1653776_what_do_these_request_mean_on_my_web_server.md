---
title: "what do these request mean on my web server?"
date: 2010-12-27
forum: General Help
---

### Post by 0949er on 2010-12-27
Hey guys, quick question. I run a Apache web server on my computer, and I am noticing a lot of weird "GET" request. A lot of random IP's will have the following random request: 


```

[26/Dec/2010:12:33:30 -0500] 58.218.204.110 - "GET http://www.racross.com/proxyheader.php HTTP/1.1" 294 404 T:0 "-"

```-or-
```

[26/Dec/2010:08:29:22 -0500] 58.218.204.110 - "GET http://www.foodnese.com/indux.php HTTP/1.1" 289 404 T:0 "-"

```-or-
```

[27/Dec/2010:09:36:14 -0500] 58.218.204.110 - "GET http://www.mtajp.com/proxyheader.php HTTP/1.1" 292 404 T:0 "-"

```Are they using my web server to connect to the addresses after the "GET" command? What exactly is going on in these request? I actually just noticed that these three incidents are from the same IP address. However, other random IP's will have the same request for a random website. Can anybody shed some light on what is going on with this? Thank you.

log info from apache.conf:

```

LogLevel warn

    LogFormat "%t %h %u \"%r\" %b %>s T:%T \"%{Referer}i\"" custom
    SetEnvIf Remote_Addr "127\.0\.0\.1" dontlog
    CustomLog /xxx/xxx/xxx/access_log custom env=!dontlog 


    CustomLog ${APACHE_LOG_DIR}/access.log combined

```

---

### Post by efflandt on 2010-12-27
They are bots or script kiddies trying to see if your apache server is an open proxy that they can be used for questionable purposes like worms or attacks.  But the 404 in the logs means that it did NOT work.

[http://en.wikipedia.org/wiki/List_of_HTTP_status_codes](http://en.wikipedia.org/wiki/List_of_HTTP_status_codes)

So you are safe from that as long as you do not use mod_proxy or ProxyPass (improperly) which could leave your apache wide open for use as an anonymous proxy.

---

### Post by 0949er on 2010-12-27
thanks a lot man.

---

