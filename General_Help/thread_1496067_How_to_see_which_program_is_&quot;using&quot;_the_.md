---
title: "How to see which program is &quot;using&quot; the localhost?"
date: 2010-05-28
forum: General Help
---

### Post by ZequeZ on 2010-05-28
Well, I have LAMPP installed, It was working fine, until I installed something that is running a web server right now and it replace the LAMPP server port I guess.

And BTW, how can I see the system services so can I disable some of them and see what is starting with my OS? -.- (I remember a console app for that, but I cannot remember the name ](*,)

---

### Post by WorMzy on 2010-05-28
What page do you see when you go to [http://localhost](http://localhost)?

---

### Post by vandorjw on 2010-05-28
do you mean "top"

open up a shell and "top" without the quotes will tell you what is running.

maybe this is not what you meant.

------------------------------------------
Apache "broadcasts" for lack of vocabulary on port 80 by default. You can change this port in the httpd.conf file found in....
/etc/apache2/ (i think)

So,when you change this, you can go to [http://localhost:NUMBER_YOU_CHANGED_TO](http://localhost:NUMBER_YOU_CHANGED_TO)

example you changed to port 81 instead
[http://127.0.0.1:81](http://127.0.0.1:81)

to check is apache is still running. type this into a shell/terminal
```

/etc/rc5.d/S91apache2 status

```

you should get something back like this
> 
Apache is running (pid 1255).


Hope that helps

---

### Post by jobix on 2010-05-28
If you know the port number, you can use the "netstat" command to figure out what's using it. Even if you don't, netstat can give you a lot of info.

---

### Post by mpetrovic on 2010-05-28
```
lsof -i:80
```
will show you what's on port 80 (if apache was supposed to work on port 80)

---

