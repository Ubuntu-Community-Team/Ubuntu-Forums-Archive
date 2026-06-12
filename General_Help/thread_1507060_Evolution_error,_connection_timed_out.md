---
title: "Evolution error, connection timed out"
date: 2010-06-11
forum: General Help
---

### Post by 1cookie on 2010-06-11
hi

Trying to get evolution working in Lucid Lynx. Ive done all the dumb stuff:

set

SMTP.virginmedia.com
POP3.virginmedia.com
username: *********


but am getting the following: [http://webtechnologies.me.uk/img/Screenshot.png](http://webtechnologies.me.uk/img/Screenshot.png) error?

Any ideas? ;)

help

---

### Post by plucky on 2010-06-11
> **1cookie said:**
> hi

Trying to get evolution working in Lucid Lynx. Ive done all the dumb stuff:

set

SMTP.virginmedia.com
POP3.virginmedia.com
username: andycookson


but am getting the following: [http://webtechnologies.me.uk/img/Screenshot.png](http://webtechnologies.me.uk/img/Screenshot.png) error?

Any ideas? ;)

help

You have to enter the port numbers ```
smtp.virginmedia.com:465
pop3.virginmedia.com:995
``` and enable SSL encryption.

Please edit your post and remove your username so the spammers don't get you.

Good Luck

p.s this is the requirement for the UK.Use whatever port is required in your location.

---

### Post by 1cookie on 2010-06-11
> **plucky said:**
> 
p.s this is the requirement for the UK.Use whatever port is required in your location.

hi

So am i best contacting virgin media UK, for the specific port numbers, or are the ones you provide generic ones? :)

---

### Post by plucky on 2010-06-11
> **1cookie said:**
> hi

So am i best contacting virgin media UK, for the specific port numbers, or are the ones you provide generic ones? :)

They were the ones from the UK virginmedia help page.If you live in the UK then they are the ones to use.

Good Luck

---

### Post by 1cookie on 2010-06-11
> **plucky said:**
> They were the ones from the UK virginmedia help page.If you live in the UK then they are the ones to use.

Good Luck

hi

The client promts me for a pop3 password so i use my web mail details that i have configured on my account. Now evolution says: 

```
Unable to connect to POP server pop3.virginmedia.com error sending password, username and password not accepted.
```

whut? :)

---

### Post by dcstar on 2010-06-11
> **1cookie said:**
> hi

The client promts me for a pop3 password so i use my web mail details that i have configured on my account. Now evolution says: 

```
Unable to connect to POP server pop3.virginmedia.com error sending password, username and password not accepted.
```

whut? :)

It is saying that you are not giving the server the right information.

Check with that provider as to what you should be doing.

---

### Post by 1cookie on 2010-06-11
> **dcstar said:**
> It is saying that you are not giving the server the right information.

Check with that provider as to what you should be doing.


hi

Well after checking with my provider all my settings (inc above) seem to be correct, only still evolution wont play: [http://webtechnologies.me.uk/img/Screenshot-1.png](http://webtechnologies.me.uk/img/Screenshot-1.png)

Im now thinking of just sticking to webmail, it's a lot less headache..:)

---

### Post by dcstar on 2010-06-12
> **1cookie said:**
> hi

Well after checking with my provider all my settings (inc above) seem to be correct, only still evolution wont play: [http://webtechnologies.me.uk/img/Screenshot-1.png](http://webtechnologies.me.uk/img/Screenshot-1.png)

Im now thinking of just sticking to webmail, it's a lot less headache..:)

Did you enable the required encryption as instructed in a previous post?

---

### Post by Soul-Sing on 2010-06-12
maybe disable IPv6 would do.

---

