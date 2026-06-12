---
title: "Problem with Ubuntu"
date: 2011-12-03
forum: General Help
---

### Post by Chelidze on 2011-12-03
I finally decided to install ubuntu and did so i installed 11.10 x64 version every thing want well in the beginning but after that a run into some problems,  i do not know how to fix them and can you help me out 
1) **swap and ram** this thing is a mess for me swap is rarely used and ram does not get cleaned up ,, there was four skype app running in the ram even though i quite all of them" ubuntu just does not cleans up ram 
2) I have problems with **npviwer.bin** it takes half of cpu performance even after i exit browser programs ,,I uninstalled flash player from the system and managed to install x64 flash with terminal, for now flash performance is ok, but now i do not know, will flash get updated or how to uninstall it, ubuntu software center tells me that flash player is not installed 
3) **software architecture  ** I have no idea are my software x32 or x64 architecture i am pretty sure software center only has x32 apps. maybe i am wrong but there is no indicator to tell me what am i using
4)this is a small problem and easy to solve i was uploading images and i could not change view mode to thumbnails all i got was this view that was really unpractical
[http://i.imgur.com/bo3h0.png](http://i.imgur.com/bo3h0.png)
5) having serious problems with flash while running windows i can watch this video with no problems but under ubuntu it is just unwatchable
 [Video 4K]("http://www.youtube.com/watch?v=JYJ19HWMY4Y")

 Sorry for my horrible English and thank you for your time

---

### Post by oldtimer7777 on 2011-12-03
A good idea would be to run 

sudo apt-get install bleachbit
sudo bleachbit

In your terminal.. to clean out your caches, since it sounds like you are getting swampt.

You can configure bleachbit to run at shutdown, which is what I do to resolve this kind of issue..

Becareful with bleachbit that it doesn't delete your passwords or bookmarks.

BTW your english is great.  No worries.   

As for the difference between 32-bit and 64-bit maybe someone can point you to a educational tutorial about the difference.

> **Chelidze said:**
> I finally decided to install ubuntu and did so i installed 11.10 x64 version every thing want well in the beginning but after that a run into some problems,  i do not know how to fix them and can you help me out 
1) **swap and ram** this thing is a mess for me swap is rarely used and ram does not get cleaned up ,, there was four skype app running in the ram even though i quite all of them" ubuntu just does not cleans up ram 
2) I have problems with **npviwer.bin** it takes half of cpu performance even after i exit browser programs ,,I uninstalled flash player from the system and managed to install x64 flash with terminal, for now flash performance is ok, but now i do not know, will flash get updated or how to uninstall it, ubuntu software center tells me that flash player is not installed 
3) **software architecture  ** I have no idea are my software x32 or x64 architecture i am pretty sure software center only has x32 apps. maybe i am wrong but there is no indicator to tell me what am i using
4)this is a small problem and easy to solve i was uploading images and i could not change view mode to thumbnails all i got was this view that was really unpractical
[http://i.imgur.com/bo3h0.png](http://i.imgur.com/bo3h0.png)


 Sorry for my horrible English and thank you for your time

---

### Post by Chelidze on 2011-12-03
> **oldtimer7777 said:**
> A good idea would be to run 

sudo apt-get install bleachbit
sudo bleachbit

In your terminal.. to clean out your caches, since it sounds like you are getting swampt.

You can configure bleachbit to run at shutdown, which is what I do to resolve this kind of issue..

Becareful with bleachbit that it doesn't delete your passwords or bookmarks.

BTW your english is great.  No worries.   

As for the difference between 32-bit and 64-bit maybe someone can point you to a educational tutorial about the difference.



I will give it a shot but still have problems with other things

---

### Post by oldtimer7777 on 2011-12-03
> **Chelidze said:**
> I will give it a shot but still have problems with other things

see if that helped for now, and keep asking questions..

---

### Post by Chelidze on 2011-12-03
> **oldtimer7777 said:**
> see if that helped for now, and keep asking questions..

thanks you are very kind

 I mostly know the difference between x32 and X64 :) i just do not know which version of software  am i getting and about the thumbnails is there a way to show thumbnails

---

### Post by ~Hinterland on 2011-12-03
You can tell if you are using 32bit or 64bit by typing the following into a terminal:

uname -m

x86_64 = 64bit
i686 = 32bit

---

### Post by Chelidze on 2011-12-03
> **~Hinterland said:**
> You can tell if you are using 32bit or 64bit by typing the following into a terminal:

uname -m

x86_64 = 64bit
i686 = 32bit

I am interested in software architecture for exampled what version vlc am i ruining x32 or x64

---

### Post by MG&amp;TL on 2011-12-03
Unused RAM is wasted RAM, according to the linux kernel. Applications can immediately claim RAM back when they need. See [this article]("http://www.linuxatemyram.com/") :D


You can tell what architecture a program is (typically 64-bit on 64-bit machine, but that might change soon) by:

1. Opening a terminal

2. Typing:

```
which vlc (or other program)
(the shell says:) /usr/bin/vlc

file /usr/bin/vlc
(the shell says:) /usr/bin/vlc: ELF [COLOR="Red"]64-bit[/COLOR] LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped (for instance)
 
```

---

### Post by Chelidze on 2011-12-03
> **MG&TL said:**
> Unused RAM is wasted RAM, according to the linux kernel. Applications can immediately claim RAM back when they need. See [this article]("http://www.linuxatemyram.com/") :D


You can tell what architecture a program is (typically 64-bit on 64-bit machine, but that might change soon) by:

1. Opening a terminal

2. Typing:

```
which vlc (or other program)
(the shell says:) /usr/bin/vlc

file /usr/bin/vlc
(the shell says:) /usr/bin/vlc: ELF [COLOR="Red"]64-bit[/COLOR] LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped (for instance)
 
```

Thank you very much your post has been really helpful

---

### Post by MG&amp;TL on 2011-12-03
Thank you! Always happy to help. :)

Regarding flash and other similiar codec and web related issues-I have never had any trouble with these if I:

```
sudo apt-get install ubuntu-restricted-extras
```

Reading your original post; you don't need to worry about the architecture of programs you get from the software centre or apt-get (terminal version) (unless you are a developer or computer scientist and need to modify or something) apt will decide what architecture you are running and try and fetch the appropriate package for you.

---

### Post by oldtimer7777 on 2011-12-03
> **MG&TL said:**
> Thank you! Always happy to help. :)

Regarding flash and other similiar codec and web related issues-I have never had any trouble with these if I:

```
sudo apt-get install ubuntu-restricted-extras
```

If you still have problems after that, try using Flash Aid plugin for Firefox.

---

### Post by Chelidze on 2011-12-03
Thank you for your help :) Canonical should be really delighted to have community like this 
 Thank you again and i wish you the best of luck

---

### Post by oldtimer7777 on 2011-12-03
> **Chelidze said:**
> Thank you for your help :) Canonical should be really delighted to have community like this 
 Thank you again and i wish you the best of luck

Okay, don't forget to close this thread when you are done.

---

