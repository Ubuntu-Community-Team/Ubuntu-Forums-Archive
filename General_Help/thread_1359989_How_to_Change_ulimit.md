---
title: "How to Change ulimit?"
date: 2009-12-20
forum: General Help
---

### Post by antdgar on 2009-12-20
ulimit -n gives me 1024

I have to change this limit to 8000~ for utorrent to be able to handle many open torrents (or so a mod at utorrent forums told me)

How can I change the ulimit for utorrent?

I have searched around but could not find a simple explanation

---

### Post by pbrane on 2009-12-20
Have a look at this

[http://linux.die.net/man/1/ulimit]("http://linux.die.net/man/1/ulimit")

I did this:
```

sudo -i

```
once you give your password you are root, be careful!
```

ulimit -n <number of file descriptors you want>

```

I'm not sure if those changes are permanent or even for other shells though. That only seems to work for the current shell. Are you actually having an issue with utorrent?

---

### Post by john newbuntu on 2009-12-21
Here is a link that might help you.  Right at the bottom, it mentions modifying the /etc/security/limits.conf file for a permanent per-login change.
[http://www.techiesabode.com/article/read_article_w.php?article_id=2](http://www.techiesabode.com/article/read_article_w.php?article_id=2)

---

### Post by antdgar on 2009-12-21
> **pbrane said:**
> Have a look at this

[http://linux.die.net/man/1/ulimit](http://linux.die.net/man/1/ulimit)

I did this:
```

sudo -i

```once you give your password you are root, be careful!
```

ulimit -n <number of file descriptors you want>

```I'm not sure if those changes are permanent or even for other shells though. That only seems to work for the current shell. Are you actually having an issue with utorrent?
Yes I am having major issues with utorrent.

I did what you said as root, but then when i typed 'ulimit -n' it says the original 1024.
I tried to change it to 8024

any ideas why it is not changing?

[IMG]http://i187.photobucket.com/albums/x268/antdgar/Picture24.png[/IMG]
 Still ulimit -n says 1024 (I rebooted)

---

### Post by pbrane on 2009-12-21
In my first post I pointed out that doing what I said seems to only affect the current shell. Have a look at this:
[http://forum.utorrent.com/viewtopic.php?id=16707]("http://forum.utorrent.com/viewtopic.php?id=16707")
Specifically post #6.

I think that is the way to do what you want. This technique was also pointed out by *john newbuntu* in his post.

How are you running utorrent? In wine?

If you haven't alreadyseen this, here is the utorrent FAQ:
[http://www.utorrent.com/faq#faq32]("http://www.utorrent.com/faq#faq32")

---

### Post by antdgar on 2009-12-21
> **pbrane said:**
> In my first post I pointed out that doing what I said seems to only affect the current shell. Have a look at this:
[http://forum.utorrent.com/viewtopic.php?id=16707](http://forum.utorrent.com/viewtopic.php?id=16707)
Specifically post #6.
My screenshot shows I did that? It still says 1024 though =/

I'm running utorrent in WINE

---

### Post by pbrane on 2009-12-22
I'm not sure that when you run an app in wine that you are executing it under your user name. You added the ulimit line to /etc/security/limits.conf under your username. Somehow you need to execute *wine utorrent.exe* under your username I think.

```

xhost + 
su 
ulimit -n 4096
su <your username>
wine utorrent.exe

```

but using xhost is supposed to be a security risk.

---

### Post by abdusamed on 2010-10-16
still having issues on ubuntu 10.04.1. The adding the line in the file doesn't seem to work! Reboot, still stays 1024!!

---

### Post by abdusamed on 2010-10-23
How do I find the name of the account because I'm getting confused with whether the name I login with is a group name or account name. Cuz memenu name != account login name...

---

### Post by kashif_max on 2012-03-24
You also need to edit this file (/etc/pam.d/common-session) and add the following line.
session required pam_limits.so :KS

---

