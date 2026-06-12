---
title: "Restarting router script"
date: 2010-07-07
forum: General Help
---

### Post by moriturius on 2010-07-07
Hi!

I'm quite close (I think...) for finishing my script to restart my Linksys WAG54G2 router.

First thing was to create a script for JDownloader. It has an option to launch router config page while JDownloader is logging operations and automatically create a script:

```
[[[HSRC]]]
    [[[STEP]]]
        [[[REQUEST]]]
        GET / HTTP/1.1
        Host: %%%routerip%%%
        [[[/REQUEST]]]
    [[[/STEP]]]

    [[[STEP]]]
        [[[REQUEST]]]
        GET / HTTP/1.1
        Host: %%%routerip%%%
        Authorization: Basic %%%basicauth%%%
        [[[/REQUEST]]]
    [[[/STEP]]]

    [[[STEP]]]
        [[[REQUEST]]]
        GET /linux.js HTTP/1.1
        Host: %%%routerip%%%
        Authorization: Basic %%%basicauth%%%
        [[[/REQUEST]]]
    [[[/STEP]]]

    [[[STEP]]]
        [[[REQUEST]]]
        GET /setup.cgi?next_file=Setup.htm HTTP/1.1
        Host: %%%routerip%%%
        Authorization: Basic %%%basicauth%%%
        [[[/REQUEST]]]
    [[[/STEP]]]

    [[[STEP]]]
        [[[REQUEST]]]
        GET /others_po.js HTTP/1.1
        Host: %%%routerip%%%
        Authorization: Basic %%%basicauth%%%
        [[[/REQUEST]]]
    [[[/STEP]]]

    [[[STEP]]]
        [[[REQUEST]]]
        GET /func.js HTTP/1.1
        Host: %%%routerip%%%
        Authorization: Basic %%%basicauth%%%
        [[[/REQUEST]]]
    [[[/STEP]]]

    [[[STEP]]]
        [[[REQUEST]]]
        GET /LANG_PO.js HTTP/1.1
        Host: %%%routerip%%%
        Authorization: Basic %%%basicauth%%%
        [[[/REQUEST]]]
    [[[/STEP]]]

    [[[STEP]]]
        [[[REQUEST]]]
        GET /setup.cgi?next_file=Status.htm HTTP/1.1
        Host: %%%routerip%%%
        Authorization: Basic %%%basicauth%%%
        [[[/REQUEST]]]
    [[[/STEP]]]

    [[[STEP]]]
        [[[REQUEST]]]
        GET /others_po.js HTTP/1.1
        Host: %%%routerip%%%
        Authorization: Basic %%%basicauth%%%
        [[[/REQUEST]]]
    [[[/STEP]]]

    [[[STEP]]]
        [[[REQUEST]]]
        POST /setup.cgi HTTP/1.1
        Host: %%%routerip%%%
        Authorization: Basic %%%basicauth%%%

ctype=pppoa&ifstatus=Up&todo=disconnect&this_file=Status.htm&next_file=Status.htm&message=&SID=1314968760
        [[[/REQUEST]]]
    [[[/STEP]]]

    [[[STEP]]]
        [[[REQUEST]]]
        GET /others_po.js HTTP/1.1
        Host: %%%routerip%%%
        Authorization: Basic %%%basicauth%%%
        [[[/REQUEST]]]
    [[[/STEP]]]

    [[[STEP]]]
        [[[REQUEST]]]
        POST /setup.cgi HTTP/1.1
        Host: %%%routerip%%%
        Authorization: Basic %%%basicauth%%%

ctype=pppoa&ifstatus=Down&todo=connect&this_file=Status.htm&next_file=Status.htm&message=&SID=1314968760
        [[[/REQUEST]]]
    [[[/STEP]]]

    [[[STEP]]]
        [[[REQUEST]]]
        GET /others_po.js HTTP/1.1
        Host: %%%routerip%%%
        Authorization: Basic %%%basicauth%%%
        [[[/REQUEST]]]
    [[[/STEP]]]

[[[/HSRC]]]

```


Then it worked once. I've managed to discover why - it uses session numbers (at the end of the long lines with POST request).

I can get the SID from the router using linux GET command:

```
SID=`GET -C "$USER:$PASS" http://192.168.1.1/setup.cgi?next_file=Status.htm | grep 'name="SID"' | sed 's,^.*value="\([0-9]*\).*,\1,g'`
```

The problem is that i don't know how to use POST command. I have tried something like:

```
DIS_DATA="ctype=pppoa&ifstatus=Up&todo=disconnect&this_file=Status.htm&next_file=Status.htm&message=&SID=$SID"

echo $DIS_DATA | POST -C "$USER:$PASS" http://192.168.1.1/setup.cgi
```

But I get HTTP error 401 - Unauthorized. Anybody knows how to POST something to the router?

---

### Post by moriturius on 2010-07-07
Success!

I used *curl* instead of *POST*:

```

CONN_DATA="ctype=pppoa&ifstatus=Down&todo=connect&this_file=Status.htm&next_file=Status.htm&message=&SID=$SID"
DIS_DATA="ctype=pppoa&ifstatus=Up&todo=disconnect&this_file=Status.htm&next_file=Status.htm&message=&SID=$SID"

curl -u "$USER:$PASS" -d "$DIS_DATA" "http://192.168.1.1/setup.cgi"
curl -u "$USER:$PASS" -d "$CONN_DATA" "http://192.168.1.1/setup.cgi"
```

---

