---
title: "Ubuntu Terminal Spelling Mistake?"
date: 2010-10-19
forum: General Help
---

### Post by [::AP::] on 2010-10-19
Greetings - 

This has no impact on performance what-so-ever... It is really no big deal, I was just wondering. 

My terminal spells Ubuntu "Ububtu"...

Either I am seeing double, am completely nuts, a package is broken (?), or I am missing some sort of technological info/explination...

Instead of "username@ubuntu:~$", it comes out as "andrew@ububtu". 

[[IMG]http://img638.imageshack.us/img638/2641/screenshotftv.png[/IMG]](http://img638.imageshack.us/i/screenshotftv.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

This was a screenshot I took on August 21st, 2010, after I upgraded to 10.04 LTS (I was excited). 

[[IMG]http://img823.imageshack.us/img823/2198/screenshot1vp.png[/IMG]](http://img823.imageshack.us/i/screenshot1vp.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

So obviously it has been like this for a very long time - and I just noticed. 

A google search of "Ububtu" does the "showing results for ***_[COLOR="Navy"]Ubuntu[/COLOR]_***" thing. 
When adding the tag for this post, there were a fair amount of Ububtu suggestions. 

Any explanation? :confused: I really don't care - if there is a simple way to fix I will, other than that, I was just wondering...:)

Thanks, 

[::AP::]

---

### Post by wojox on 2010-10-19
You spelled Ubuntu wrong. That part after @ is your local host. :P

---

### Post by sisco311 on 2010-10-19
By default, the prompt is:
```
username@hostname:path/to/current/directory
```

So, you most likely misspelled the hostname at installation time. 

In order to change it, open the /etc/hosts file:
```
gksu gedit /etc/hosts
```
and edit the line: 
```
127.1.0.1               **Ububtu**
```


You may have to edit /etc/hostname too, if it exists.

Then run:
```
sudo hostname **Ubuntu**
```
replace **Ubuntu** with the desired hostname and start a new terminal.

---

### Post by [::AP::] on 2010-10-19
#-o Ahh...lol...I feel ridiculous.

Absoulutely ridiculous. 

Please excuse that really dumb error. :P

Thanks. 

[::AP::]

---

