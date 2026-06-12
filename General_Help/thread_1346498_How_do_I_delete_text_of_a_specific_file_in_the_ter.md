---
title: "How do I delete text of a specific file in the terminal? Help please"
date: 2009-12-05
forum: General Help
---

### Post by gordong11 on 2009-12-05
I want to delete the text with a log file, but not the log file itself.

Example:

What would be the terminal command to delete the all the data/text inside /var/log/kern.log but keep the kern.log file itself?

Thank you :)

---

### Post by SecretCode on 2009-12-05
Essentially you want to rewrite the file contents with nothing ... truncate it to zero length ... 

The following should do it:

```
cat /dev/null > /var/log/kern.log
```


But if you want to do this regularly, read up on [FONT="Courier New"]logrotate[/FONT]

---

### Post by Rinzwind on 2009-12-05
```

 > /var/adm/sylog

```
will clear syslog

You need to do a
```
sudo su
```
first btw.

---

### Post by alienclone on 2009-12-05
maybe delete the file then create a new blank one with the same name?

---

### Post by SecretCode on 2009-12-05
> **alienclone said:**
> maybe delete the file then create a new blank one with the same name?

A possible problem with that would be making sure all the permissions were preserved.

---

### Post by Rinzwind on 2009-12-05
> **alienclone said:**
> maybe delete the file then create a new blank one with the same name?

Well 
... the file might be in use by some program that could crash.
... permissions need to be set. 
... owner and group need to be set.

My 1st post is a lot easier, isn't it? ;)

---

### Post by amauk on 2009-12-05
> **SecretCode said:**
> A possible problem with that would be making sure all the permissions were preserved.Also, if it's a symlink you'll just delete the link and create a file

Overwriting the contents of the file with nothing is the best way to go (as post #2)

---

### Post by gordong11 on 2009-12-05
thanks,

i did cat /dev/null > /var/log/kern.log and kern.1.log


This cleared up 17GB of space on my hard drive!!!!

---

### Post by Rinzwind on 2009-12-05
> **gordong11 said:**
> thanks,

i did cat /dev/null > /var/log/kern.log and kern.1.log


This cleared up 17GB of space on my hard drive!!!!


That's a lot :D

I just removed all the backups (rm *[0-9] *gz) and had a 2 Gb clean up :D and was like: wow. 
But 17 is ALOT. 

Oh and you can remove all the logs that end on digits and end on gz. Both are backups and are created when a log gets over a certain file size!

How old is that system? :D If it is not old you might want to investigate what is making those logs ...

---

### Post by gordong11 on 2009-12-05
It a brand new install 3 weeks ago

The problem was i had just OC my pc barely within cpu temp specification tolerance, but the log was posting temperature warnings to the tune of 50,000+ plus a day.

I removed the overclock, so it should correct the problem.

---

### Post by amauk on 2009-12-05
you might want to keep an eye in kern.log
that much being logged may indicate a problem with your system

---

### Post by alienclone on 2009-12-05
> **Rinzwind said:**
> Well 
... the file might be in use by some program that could crash.
... permissions need to be set. 
... owner and group need to be set.

My 1st post is a lot easier, isn't it? ;)

yes your 1st post is a lot easier, but it was not visible to me at the time of my reading the OP and replying.

---

### Post by Rinzwind on 2009-12-05
> **alienclone said:**
> yes your 1st post is a lot easier, but it was not visible to me at the time of my reading the OP and replying.
I forgive you ;)



gordong11 good. Been there done that :D 
I've seen it happen with a mailformed mail no-one bothered to fix. Took a few weeks but it crashed the system at some point due to lack of space ;)
n
Lots of people have cups but remove the 'remove log file after print is done' and end up with /var/log/ eating all the space :D

---

### Post by gordong11 on 2009-12-05
I totally forgot i had OC just before karmic install. Plus with a stock cooler on a celeron cpu, I was only able to move it to 2.2Ghz from 2.0Ghz. There is not much difference, so I just removed the OC all together. not worth it!! ;)

---

