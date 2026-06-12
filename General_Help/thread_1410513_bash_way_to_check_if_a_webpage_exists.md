---
title: "bash way to check if a webpage exists?"
date: 2010-02-18
forum: General Help
---

### Post by juicymixx on 2010-02-18
Hey everyone...   I know I can use bash to test if a file exists locally:

```
if [ -f testfile ]
then
echo testfile exists!
fi
```

Is there some bash equivalent way to check to see if a webpage exists somewhere out on the internet?   Also, is there a bash way to test if a url to streaming media points to something real (I mean streaming media and not a 404)?

Thanks.;)

---

### Post by blueridgedog on 2010-02-18
Use wget, then parse the result...here is one not found:

```
:~$ wget www.somesite.org/notthere.html
--2010-02-18 21:16:28--  http://www.somesite.org/notthere.html
Resolving www.somesite.org... xx.xx.xx.xx
Connecting to www.somesite.org|xx.xx.xx.xx|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-02-18 21:16:28 ERROR 404: Not Found.
```

---

### Post by juicymixx on 2010-02-19
okay... I'll try it out :D ...  Are there any other ways to do this besides using wget?   Some kind of ping like tool?

Thanks!

---

### Post by tom.swartz07 on 2010-02-19
> **juicymixx said:**
> okay... I'll try it out :D ...  Are there any other ways to do this besides using wget?   Some kind of ping like tool?

Thanks!

Yepper. its more obvious than you may think!

```
ping -c 3 www.google.com
```
or whatever your site of choice is. -c 3 tells the command to ping the server 3 times and then tell you. if you run it without it, it will do it indefinitely.

---

### Post by KeyserSoze93 on 2010-02-19
> **tom.swartz07 said:**
> Yepper. its more obvious than you may think!

```
ping -c 3 www.google.com
```
or whatever your site of choice is. -c 3 tells the command to ping the server 3 times and then tell you. if you run it without it, it will do it indefinitely.

But that will only check if the site exists, not if a page exists on the site.

I wrote a script which checks all the links on a page to see if any are broken, which may also be of some use:

[http://tpn.lowtech.org/scripts/chklinks.sh]("http://tpn.lowtech.org/scripts/chklinks.sh")

---

### Post by Richard1979 on 2010-02-19
If you just need to check one site:
wget -nv [www.somesite.org/notthere.html](www.somesite.org/notthere.html) -o /tmp/404.txt; grep "404: Not Found" /tmp/404.txt

---

### Post by zerofool2005 on 2010-02-19
Telnet to the server on port 80

do: > GET /PAGENAME HTTP/1.1

If its there the server will reply. 

HTTP/1.1 200 OK

Otherwise a 404 or other error.

---

