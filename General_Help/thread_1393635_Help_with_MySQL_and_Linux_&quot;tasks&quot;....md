---
title: "Help with MySQL and Linux &quot;tasks&quot;..."
date: 2010-01-29
forum: General Help
---

### Post by sakko on 2010-01-29
I am saying this wrong in the subject and I apologize ahead of time.

BACKGROUND
I am learning Databases and want to use my Ubuntu Server MySQL installation to tinker and "make things" for practice etc.

PROBLEM
There is a command in Linux that lets you see some information like CPU temp, etc. I have it archived somewhere. What I'd like to do is get Ubuntu to read this value every once in a while and shove it in a database, then have a webpage read that set of saved values over time and make a nifty graphical display of the CPU temp over a period of time.

I know for the web end of things I am using PHP and MySQL, I am comfortable looking all that up. What I do not know how to do is to get Ubuntu to "do things" at specified intervals and store results in the local MySQL database automatically.

Can someone give me a command name or technology or example in which I can look this up? I do not need it to be terribly descriptive, I just need to be pointed in the right direction.

Is it that "cron" thing? I've been meaning to figure out what the heck that is exactly.

If you are not terribly bored or disinterested in this post yet, I'd like to use google charts for the "fancy chart" part, which if you are not familiar with, is worth checking out.

This is a learning experience, likely been done before, but it is an exercise I want to get in to! Thank you in advance for any direction-pointing :)

---

### Post by whiskeylover on 2010-01-29
Yes, use cron.

Its simple to use. YOu specify what you want to run when, and it does it for you repeatedly. 

[http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)

---

