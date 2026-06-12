---
title: "(initramfs) prompt appears while booting."
date: 2011-03-01
forum: General Help
---

### Post by vat with tux on 2011-03-01
Hello friends'

I'm(was)using ubuntu 10.04. I've installed it inside windows 7 using wubi installer.
Before stating my problem i would like to apologize if you find my English difficult to understand.

I have been using it since last 2 months. But yesterday when i tried to shut down the system it didn't closed properly. Actually it was showing that " Ubuntu " text which appears when system shut down. I waited for around 15 minutes but i didn't shut down. So i used hard ware restart button to restart my system. It wasn't the case that it happened first time. The same thing happened before 4 or 5 times.But this time when i restarted my system after boot i found two dialog box indicating erroneous condition & then it just hanged. So i again restarted my system (of course using hardware restart:|). 
After restart when i choose ubuntu from my boot menu i found console. Indicating something like: 

> Target file system doesn't have /sbin/init.
No init found. Try passing init=bootarg. 

And few more lines indicating busybox version etc...  And a prompt: **(initramfs) ** 

Now i haven't any idea about these things. And i'm having a little bit important data on my ubutnu system .

Is there any way to recover my ubuntu system?If yes then please someone tell me as fast as possible. 
 
I'm having a little technical knowledge about unix system.    

Thanking u in advanced.:)

---

### Post by bcbc on 2011-03-01
[How can I access my Wubi install and repair my install if it won't boot?]("https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?")
I'd start off by backing up the \ubuntu\disks\root.disk (straight copy). Then run fsck on it, then try and mount it and copy off data.

You want to avoid hard resets. Instead you [Alt+SysRq r-e-i-s-u-b]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.22Raising_Elephants.22_mnemonic_device")

---

### Post by vat with tux on 2011-03-05
It worked perfectly for me.:) :guitar:   Thanks a lot dude.:D

---

