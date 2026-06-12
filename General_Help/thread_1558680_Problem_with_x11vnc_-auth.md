---
title: "Problem with x11vnc -auth"
date: 2010-08-22
forum: General Help
---

### Post by mahmoodn on 2010-08-22
Dear all,
I want to run x11vnc but receive this error:
```
22/08/2010 23:53:02 x11vnc version: 0.9.9 lastmod: 2009-12-21  pid: 2659
22/08/2010 23:53:05 XOpenDisplay(":10.0") failed.
22/08/2010 23:53:05 Trying again with XAUTHLOCALHOSTNAME=localhost ...

22/08/2010 23:53:07 ***************************************
22/08/2010 23:53:07 *** XOpenDisplay failed (:10.0)
```

It seems that no X server is running. I then searched and found that I have to use -auth option. Here is the output of ps wwaux | grep auth:
```
mahmood@localhost:~$ ps wwaux | grep auth
root       869  0.0  1.6  42788 33424 tty7     Ss+  18:13   0:03 /usr/bin/X :0 vt7 -nr -nolisten tcp -auth /var/run/xauth/A:0-VBgiQb
mahmood   2000  0.0  0.0   1856   600 pts/0    S+   19:48   0:00 grep --color=auto auth
```

Then I ran
```
mahmood@localhost:~$ sudo x11vnc -auth /var/run/xauth/A:0-VBgiQb 
```
But I see this:
```
22/08/2010 19:49:54 x11vnc version: 0.9.9 lastmod: 2009-12-21  pid: 2003
PuTTY X11 proxy: MIT-MAGIC-COOKIE-1 data did not match22/08/2010 19:49:54 XOpenDisplay(":10.0") failed.
22/08/2010 19:49:54 Trying again with XAUTHLOCALHOSTNAME=localhost ...
PuTTY X11 proxy: MIT-MAGIC-COOKIE-1 data did not match
22/08/2010 19:49:54 ***************************************
22/08/2010 19:49:54 *** XOpenDisplay failed (:10.0)
```
Any idea? Thanks

---

### Post by krunge on 2010-08-22
Why not add '-display :0' to the x11vnc command line so it knows which X server you want to attach to?

I guess the :10 in your $DISPLAY environment variable (the default display x11vnc tries) is for a ssh X tunnelling or something like that...

---

### Post by mahmoodn on 2010-08-23
Yes, 
```
sudo x11vnc -auth /var/run/xauth/A:0-6IOZza -display :0
```
Works fine.

The only problem is a random string **A:0-6IOZza **which change every time. Is there any solution for that?

---

### Post by mahmoodn on 2010-08-23
Does anybody know? How to do an auto login from remote?:confused::confused:

---

### Post by krunge on 2010-08-23
> 
The only problem is a random string **A:0-6IOZza **which change every time. Is there any solution for that?
x11vnc 0.9.9 and later has the '-auth guess' mode that applies heuristics to try to guess the auth file.  You may have some trouble running it as root, read the -findauth documentation.

Here are some other ways to automate this:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-service](http://www.karlrunge.com/x11vnc/faq.html#faq-service)[/INDENT]

(e.g. use the "Continously" section in the first link.)

---

### Post by mahmoodn on 2010-08-24
Thanks I got it.

---

### Post by mahmoodn on 2010-08-27
I think [http://foo-gr.blogspot.com/2009/05/remote-login-using-x11vnc-for-jaunty.html](http://foo-gr.blogspot.com/2009/05/remote-login-using-x11vnc-for-jaunty.html) describes better than the x11vnc FAQ !

---

### Post by gradinaruvasile on 2010-08-27
I use this (root rights):

x11vnc -localhost -display :0 -auth /var/lib/gdm/:0.Xauth  -xkb -rfbport 25500 -forever

works well,  i can even log in GDM with it.
I use 25500 port, localhost binding - the connection is open only for localhost (from inside).
I connect to my comp through ssh tunnel and connect to localhost:25500, so i have an encrypted connection.
I use Remmina for client, it can do ssh tunneling.

So, use 

-auth /var/lib/gdm/:0.Xauth

It works for me on Debian wery well. Also use Remmina, it is faster and has many handy features than any other client out there, even file transfer if tunneled through ssh.

---

