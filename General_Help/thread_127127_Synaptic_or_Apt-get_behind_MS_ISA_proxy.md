---
title: "Synaptic or Apt-get behind MS ISA proxy"
date: 2006-02-08
forum: General Help
---

### Post by Juanra on 2006-02-08
Good Moring to all of you.

I'm mounting a [COLOR="Red"]LAMP web server[/COLOR] in my office, but I'm behind a [COLOR="Red"]MS ISA proxy[/COLOR].  I read a lot of threads about this and try different ways to let [COLOR="Red"]apt-get or synaptic[/COLOR] pass through the proxy but it doesn't work.

Any of you [COLOR="Red"]please[/COLOR], know **how to config apt-get or synaptic to download packages through MS ISA proxy?**

Thanks a lot for the time taken to read this,

---

### Post by Juanra on 2006-02-08
I found the answer. Thanks a lot anyway.

---

### Post by Juanra on 2006-02-09
Hello everyone, **new21nx** ask me about the solution, so **if any of you need help with this just follow the next steps:**

   1. Open Synaptic
   2. Go Settings -> Preferences -> Network tab
   3. Enter in the first field of HTTP:
          [COLOR="Red"]*** <<user>>:<<password>>@<<proxyaddress>>**[/COLOR]
   4. Enter in the second field of HTTP the port number.
   5. Same with FTP

[COLOR="Blue"]**Example:**[/COLOR]

[COLOR="Wheat"]................................[/COLOR]Address[COLOR="Wheat"].............................[/COLOR]Port
[COLOR="Wheat"].................[/COLOR]________________________________             _____
HTTP:[COLOR="Wheat"]........[/COLOR]|[COLOR="Red"]new21nx:pa$$word@proxy.ihate.com[/COLOR]|            |[COLOR="Red"]8080[/COLOR]|
[COLOR="Wheat"].................[/COLOR]________________________________             _____
FTP:[COLOR="Wheat"]..........[/COLOR]|[COLOR="Red"]new21nx:pa$$word@proxy.ihate.com[/COLOR]|            |[COLOR="Red"]8080[/COLOR]|


Well, good luck!
Anything, anytime...


Juanra

---

### Post by depele on 2006-02-09
which command do we need  to fix this in terminal?

grtz....

---

### Post by sunny_nwho on 2006-02-09
to run the apt-get from the terminal u might want to create a file called apt.conf under /etc/apt/ for creating the file follow the following steps

$ sudo nano /etc/apt/apt.conf

after creating the file enter the following 

ACQUIRE
{
          http_proxy="http://username:password@proxyname:port"
}

and test it using sudo apt-get update

hope this works

---

### Post by Juanra on 2006-02-09
When creating the apt.conf file change this...
```
ACQUIRE
{
          [COLOR="Red"]**http_proxy**[/COLOR]="http://username:password@proxyname:port"
}
```

**with this...**
```
ACQUIRE
{
          [COLOR="Red"]**http::proxy "**[/COLOR]http://username:password@proxyname:port"
}
```

and test it with...

```
$ sudo apt-get update
```

**Important: If you don't change the [COLOR="Red"]"_"[/COLOR] with the [COLOR="Red"]"::"[/COLOR] it'll may not work.**

Anything, anytime,

Juanra

---

