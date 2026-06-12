---
title: "What is dnsmasq??"
date: 2010-04-04
forum: General Help
---

### Post by kumaraSrlk on 2010-04-04
What does it do?? Can i remove it??

i tried apt-get remove dnsmasq. it didn't work.

thnks

---

### Post by capscrew on 2010-04-04
> **kumaraSrlk said:**
> What does it do?? Can i remove it??

i tried apt-get remove dnsmasq. it didn't work.

thnks

It's a lightweight DNS and DHCP server.  See [**_here_**]("http://thekelleys.org.uk/dnsmasq/doc.html").  

Are you sure it is installed?  Did you install it?

---

### Post by kumaraSrlk on 2010-04-04
> **capscrew said:**
> It's a lightweight DNS and DHCP server.  See [**_here_**]("http://thekelleys.org.uk/dnsmasq/doc.html").  

Are you sure it is installed?  Did you install it?


I didn't install it, but when i type dnsmasq at konsole, it says nothing, if its not installed, it should display "command not found" or something, right?

---

### Post by capscrew on 2010-04-05
> **kumaraSrlk said:**
> I didn't install it, but when i type dnsmasq at konsole, it says nothing, if its not installed, it should display "command not found" or something, right?

That's no test.  

You can see if it is running by running:```
ps -ef|grep dnsmasq
```  You could also try: ```
where dnsmasq
```

What prompted you to try the command "dnsmasq" in the first place?

---

### Post by ryanfx on 2010-04-05
> **kumaraSrlk said:**
> I didn't install it, but when i type dnsmasq at konsole, it says nothing, if its not installed, it should display "command not found" or something, right?

it says nothing because it simply started a running daemon.  There isn't supposed to be output or input.... it's a dhcp / dns server.

---

### Post by capscrew on 2010-04-05
> **ryanfx said:**
> ...it's a dhcp / dns server.

As was stated in post #2 yesterday.

---

### Post by kumaraSrlk on 2010-04-05
> **capscrew said:**
> That's no test.  

You can see if it is running by running:```
ps -ef|grep dnsmasq
```  You could also try: ```
where dnsmasq
```

What prompted you to try the command "dnsmasq" in the first place?

thanks for reply.

```
ps -ef|grep dnsmasq 
```results in:

```
root 3049 3037 0 12:05 pts/1 00:00:00 grep dnsmasq
```

I don't get what is means and i just don't want a dns server on my vm. I just want to remove it!

```
where dnsmasq
``` doesn't work.
And ```
which dnsmasq
``` resuls in:

```
/usr/sbin/dnsmasq
```

---

### Post by me13221 on 2010-04-05
If dnsmasq is installed, 'sudo apt-get remove dnsmasq' should get rid of it.

When you say it "doesn't work" you aren't saying anything.  what happens?

---

### Post by capscrew on 2010-04-05
> **kumaraSrlk said:**
> thanks for reply.

```
ps -ef|grep dnsmasq 
```results in:

```
root 3049 3037 0 12:05 pts/1 00:00:00 grep dnsmasq
```

I don't get what is means and i just don't want a dns server on my vm. I just want to remove it!

```
where dnsmasq
``` doesn't work.
And ```
which dnsmasq
``` resuls in:

```
/usr/sbin/dnsmasq
```

It appears that dnsmasq is indeed installed.  Or at least part of it is installed.  It appears you only have the dnsmasq-base package installed.  Try removing the base package like this:```
sudu apt-get remove dnsmasq-base
```

---

### Post by ryanfx on 2010-04-05
> **capscrew said:**
> As was stated in post #2 yesterday.


Perhaps you didn't read past post #2.  I was responding to post #3.

---

### Post by kumaraSrlk on 2010-04-05
> **me13221 said:**
> If dnsmasq is installed, 'sudo apt-get remove dnsmasq' should get rid of it.

When you say it "doesn't work" you aren't saying anything.  what happens?

i meant "where dnsmasq" doesn't work 'cos "where" is not recognized as a command.

---

### Post by kumaraSrlk on 2010-04-05
> **capscrew said:**
> It appears that dnsmasq is indeed installed.  Or at least part of it is installed.  It appears you only have the dnsmasq-base package installed.  Try removing the base package like this:```
sudu apt-get remove dnsmasq-base
```

it doesn't work, it says "dnsmasq-base" is not installed

---

### Post by kumaraSrlk on 2010-04-06
OK, i found a script file /etc/init.d/dnsmasq, it contains a lot of things i don't understand!. i also tried,
```
/etc/init.d/dnsmasq stop
``` and even after that ```
ps -ef|grep dnsmasq
``` gives ```
root 3634 2904 0 09:52 pts/1 00:00:00 grep dnsmasq
``` No ESCAPE:icon_frown:

after few minutes,```
which dnsmasq
``` gives no reply!, and ```
dnsmasq
``` gives,```
The program 'dnsmasq' is currently not installed. You can instal it by............ bla bla bla....
``` But still "ps" shows "dnsmasq" as a running program/daemon. I think the problem is with "/etc/init.d/dnsmasq" file. Do u guys think i should delete it??

---

### Post by capscrew on 2010-04-06
> **kumaraSrlk said:**
> OK, i found a script file /etc/init.d/dnsmasq, it contains a lot of things i don't understand!. i also tried,
```
/etc/init.d/dnsmasq stop
``` and even after that ```
ps -ef|grep dnsmasq
``` gives ```
root 3634 2904 0 09:52 pts/1 00:00:00 grep dnsmasq
``` No ESCAPE:icon_frown:

I think you are misinterpreting the **ps **command.  The response returned shows that you have NO DNSMASQ running.  The line you do see is the grep command asking for a return of the term dnsmasq.  Of which there is none.  If dnsmasq was running you would get somthing like this 
```

root 2515 2515 0 09:25 pts/1 00:00:00 dnsmasq 
root 3634 2904 0 09:52 pts/1 00:00:00 grep dnsmasq [COLOR="Blue"]<--This is grep[/COLOR]


```

---

### Post by kumaraSrlk on 2010-04-06
OMG! Thanks a lot!!!!!!!!!! u saved me.
i think i should learn something deep abt linux. Anyway, what about /etc/init.d/dnsmasq file?? Should i leave it?

---

### Post by capscrew on 2010-04-06
> **kumaraSrlk said:**
> OMG! Thanks a lot!!!!!!!!!! u saved me.

No way!  You did it all by yourself.  With a little help from friends.  :D

---

