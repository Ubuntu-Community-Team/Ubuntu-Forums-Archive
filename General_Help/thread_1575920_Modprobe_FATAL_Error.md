---
title: "Modprobe FATAL Error"
date: 2010-09-16
forum: General Help
---

### Post by gameplay on 2010-09-16
Tried updating today from Ubuntu 10.04 to 10.10.  Seemed to go ok, but on reboot I got the message 

Error Modprobe FATAL  Could not load /lib/modules/ 2.6.35-21-generic/modules.dep   no such file or module

Havn't got a clue what to do.  HELP!!!

---

### Post by gameplay on 2010-09-19
I can only get a command prompt with which I can log in to my account, but I don't know what to do with the command line to get back a working system.  Any help appreciated.

---

### Post by gameplay on 2010-09-20
I managed to use a live disk to see that there is file with that name but have no idea what is going on - any help appreciated.

---

### Post by rasmus91 on 2010-09-22
I have the exactly same problem. But my computer boots up fine otherwise. i hope this is a beta thing ;)

---

### Post by gameplay on 2010-09-23
Unfortunately it doesn't boot up for me.  Googling round there is not much on this problem, at least that I can understand - hence my request for help.

---

### Post by gameplay on 2010-09-23
OK - after logging in at the command prompt tried 

sudo apt-get update     and then 
sudo apt-get upgrade

Didn't work, but then tried the 'recovery' option on the boot screen which seemed to rebuild the system and put in missing packages.

Tried rebooting and still got the 'FATAL' error as before, but then it went through and came up as if nothing was wrong and the system now seems fine.  Don't know what is wrong but this is a big step in the right direction as I can get in the system now.

---

### Post by atari130xe on 2010-09-24
I have the same problem, but my system boots up ok and I can use Ubuntu 10.10 Beta I have upgraded from 10.04 to 10.10 beta and got the same results, I think its a bug or something.

---

### Post by treschny on 2010-10-02
same thing happening to me - upgraded 10.04 to 10.10 beta and got the same message.  It continues to boot but just takes a bit longer while it shows that message and hangs for a few seconds...  System is otherwise seeming normal.  Nice new font!

---

### Post by gameplay on 2010-10-08
Still getting the error message but it does boot through.  This is getting annoying, as the updates don't resolve the problem.  Anybody got any ideas on how to start diagnosing this?

---

### Post by Ayuthia on 2010-10-08
Does
```

sudo depmod -a

```
help?

It is supposed to rebuild the modules.dep file.

---

### Post by gameplay on 2010-10-09
Thanks for the reply - tried this but did not resolve the problem.  Have tried turning on the text during boot up but it goes so fast that I can't see it all.  Is there some way of capturing this to a file so I can look at it?

---

### Post by Meandlinux on 2010-10-11
I had the same error. I downloaded the iso again. Burned it at 8x speed and reinstalled. It fixed it.

---

### Post by gameplay on 2010-10-16
Ant way of capturing the boot up text as asked in my previous post?

---

### Post by sffvba[e0rt on 2011-02-12
MAJOR BUMP for unresolved issue...

I am now too getting a similar error message at boot time, at least my system continues to boot successfully and this is just an annoying message to see at boot-time...

Any ideas how to resolve this issue, it seems to be trying to load something on an old kernel and I suspect it happens after upgrading of the kernel...



Thanks
404

---

### Post by AuditoryEden on 2011-02-12
I also have a similar problem. I just switched to Ubuntu from Windows XP, so I have no idea what to do about it, although I probably could have fixed this sort of thing in my old OS. 
My computer tells me it has had a Fatal Error, then boots through like normal, though I've had some worrying glitches. I run Maverick on an Acer Aspire One.

---

### Post by sffvba[e0rt on 2011-02-14
I come bearing a SOLUTION :)

Check out this link: [http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=auto&tl=en&u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fid%3D420686](http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=auto&tl=en&u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fid%3D420686)

Post number 8 will do the trick for you (worked for me) :)

Thanks to JoeMaverickSett at #ubuntu-beginners for hooking me up with the link...


404

---

