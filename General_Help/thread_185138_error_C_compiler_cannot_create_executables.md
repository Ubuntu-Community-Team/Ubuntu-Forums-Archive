---
title: "error: C compiler cannot create executables"
date: 2006-05-31
forum: General Help
---

### Post by Ch41r on 2006-05-31
When trying to install Apache Webserver running ./configure I get,  	
error: C compiler cannot create executables

I've google'ed around found out about and old binutils update 2.15-5ubuntu2.2?

I'm quite the noobie when it comes to using Linux so any help is appriciated :D

---

### Post by bruce89 on 2006-05-31
Why don't you just install apache from the repositories? ```
sudo apt-get install apache2
```

---

### Post by Ch41r on 2006-05-31
Yea guess I could do that.. (probably gonna have to in the end :)) 

It's just that with Linux I was hoping to actually solve the problem instead of working around it like when using Windows.. I mean... again in like a couple of days when I can't find 'that' exact program on any of the repos, I'm still sitting with the C compiler error... ](*,) 

Thnx for taking time to help out though :)

---

### Post by bruce89 on 2006-05-31
Have you got build-essential installed?  If not, ```
sudo apt-get install build-essential
```
You might like to know the next version of Ubuntu is out in 7 hours.

---

### Post by Zdravko on 2006-05-31
I might like to know whether the GNU compiler collection is included in the new version... finally?

---

### Post by bruce89 on 2006-05-31
[QUOTE=Zdravko]I might like to know whether the GNU compiler collection is included in the new version... finally?[/QUOTE]
Not installed by default on Dapper.

---

### Post by PriceChild on 2006-05-31
[quote=Ch41r]I was hoping to actually solve the problem instead of working around it[/quote]

Well i don't really think using apt is working around it :S

That *should* be the standard way to do things in ubuntu. Its the simplest, and easiest to undo.

I haven't had to compile anything manually so far :D Though i will do one day soon maybe :)

Pricey

---

### Post by n2diy on 2006-05-31
[QUOTE=Ch41r]Yea guess I could do that.. (probably gonna have to in the end :)) 

It's just that with Linux I was hoping to actually solve the problem instead of working around it like when using Windows.. I mean... again in like a couple of days when I can't find 'that' exact program on any of the repos, I'm still sitting with the C compiler error... ](*,) 

Thnx for taking time to help out though :)[/QUOTE]

I'm having the same problem with Evolution 2.6.2, hopefully apt-get build essentials will fix it.

I agree with you about still having a compiler problem. Someday your going to find something that you have to compile, so you will want a working compiler.

Darryl N2DIY

---

### Post by Ch41r on 2006-06-02
/bruce89,
/Have you got build-essential installed? If not,

It seemed to solve the problem..

thnx dude.. :D

---

