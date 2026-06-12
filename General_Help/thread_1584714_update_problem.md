---
title: "update problem"
date: 2010-09-29
forum: General Help
---

### Post by gmaier on 2010-09-29
Hi.
I don't speak english but i'll do my best.
I have 2 laptops (dell inspiron 1525 and dell mini 12 (gma 500)) with a dual boot (win vista/ ubuntu 10.04).
Ubuntu was installed using wubi without any problem. Actually i have been using  ubuntu since 6 moths ago as my only OS.
Today I made an update --not an upgrade-- on both laptops and I lost the grub (on both).
Now, on the inspiron 1215 if i choose "ubuntu" nothing happen. The menu ask me again if i want "ubuntu" or "vista". And so.
On the mini 12 is different. If I choose "ubuntu" following message apears on the screen:
Error: unkown command 'loadfont'
Error: File not found
And then the computer is dead. I mean, i can't write o restart the machine. 
Any ideas?
Thanks a lot!
g.

---

### Post by bcbc on 2010-09-29
I saw this issue a while ago. Try this for a fix: [http://ubuntuforums.org/showpost.php?p=9640093&postcount=30](http://ubuntuforums.org/showpost.php?p=9640093&postcount=30)


You'll have to figure out what partition your root disk is on and change it within the instructions if required (where /dev/sda2 is referenced)

---

### Post by olivaw_daneel on 2010-09-29
I've got the same problem as the OP except I'm using a desktop (Dell Inspiron 530).

I updated Ubuntu using the update manager about 1 hour ago on 29th September 2010. After the update had finished it said I needed to restart my computer to complete the update so I did. However, now whenever I select to start Ubuntu from the boot-up screen all that happens is my computer restarts again. Ubuntu doesn't load up at all.

I looked at the post you linked to bcbc but it's talking about booting from a live CD. Both the OP and I used wubi to install ubuntu originally so we don't have a live CD.

---

### Post by bcbc on 2010-09-29
> **olivaw_daneel said:**
> I've got the same problem as the OP except I'm using a desktop (Dell Inspiron 530).

I updated Ubuntu using the update manager about 1 hour ago on 29th September 2010. After the update had finished it said I needed to restart my computer to complete the update so I did. However, now whenever I select to start Ubuntu from the boot-up screen all that happens is my computer restarts again. Ubuntu doesn't load up at all.

I looked at the post you linked to bcbc but it's talking about booting from a live CD. Both the OP and I used wubi to install ubuntu originally so we don't have a live CD.

I understand - that's one of the selling points of Wubi - that you don't need a live CD. But in practice it's always handy to have one. This is one of those times when you do. Unfortunately grub-pc has undergone many changes since it was released and wubi is dependent on it. As long as you update it you run the risk of breaking wubi installs.

Go to [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) and it will give you a link as well as instructions on how to create burn the image to CD.

---

### Post by gmaier on 2010-09-30
thanks!
now i'm installing ubuntu from a cd.
maybe is the best solution.
best,
g.

---

### Post by bcbc on 2010-09-30
> **gmaier said:**
> thanks!
now i'm installing ubuntu from a cd.
maybe is the best solution.
best,
g.

Maybe :)

You know that you can recover all your data off the wubi install (if you haven't already uninstalled it right?). It doesn't matter if you've just started using wubi but if you have spent a lot of time on it, it's a pain to have to redo everything.

In fact, if you don't mind entering a bunch of commands you can even migrate a wubi from the root.disk to a partition using a live CD. I only mention this since you said you have been using wubi for 6 months as your sole OS and it'd be a pity to lose that.

---

### Post by edgeofwrath on 2010-11-25
I booted off a USB drive, mounted the windows partition, edited the grub.cfg file, went to reboot, and while at first I was getting Unknown command "frontloader" then error: file not found, now it only does error: file not found, but the front loader line isn't there anymore. Still wont boot into Linux, and I have homework due by Saturday. Any additional help would be amazing. Running desktop 10.04.1 on an Acer Aspire One A075h wubi install through windows xp.

UPDATE: I cant get it to load, so I'm just going to re-install THE RIGHT WAY with a USB key. But, this solution helped me get my files off the system so I didn't loose all my precious school work. 
[http://ubuntuforums.org/showthread.php?t=1007816](http://ubuntuforums.org/showthread.php?t=1007816)

---

### Post by phflupp on 2010-11-28
> **bcbc said:**
> ...Unfortunately grub-pc has undergone many changes since it was released and wubi is dependent on it. As long as you update it you run the risk of breaking wubi installs.


This is a sad comment on the state of Ubuntu's grub & wubi folks not working together. One expects such disconnections with proprietary systems, but I would have hoped that these two sub-communities would learn to work together to maintain a high overall user experience. Without that coordination Ubuntu is thrown into the dark ages of Linux where everyone had to be a sys admin in order to use the OS.

Very sad.
-P.

---

