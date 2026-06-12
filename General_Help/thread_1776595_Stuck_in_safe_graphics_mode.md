---
title: "Stuck in safe graphics mode"
date: 2011-06-06
forum: General Help
---

### Post by XFTOX on 2011-06-06
Hi guys Ill try keep this simple. I'm kind of new to Ubuntu. Anyways did a fresh install over windows, would crash with this pixilated purple screen. So I tried "safe graphics mode" and it worked. But now that it is installed, how do I get out of it and have it run normally?

Please help, thnx.


Edit: tried to manually install the nvidia drivers, restarted comp and now it wont boot in. Stuck on a black screen and it says "gpu lockup - switching to software fbcon". Great

---

### Post by seawolf167 on 2011-06-06
Welcome to the forums!

When you say you manually installed the graphics drivers - what specifically did you do? Did you see if there were any drivers available in System -> Administration -> Hardware Drivers before you attempted the manual installation?

Can you boot at all now? Even into failsafe graphics mode?

If you can boot, what is the output of

```
sudo lspci | grep -i vga
```

---

### Post by XFTOX on 2011-06-06
Well graphic drivers showed that they were installed, however it said they werent being used. So for some reason I figured Id download the official ones from the nvidia site.   Then got a .run file (Im new to this whole linux thing) and lookined up how to install it.  Then found out there was some command like +e or plus something then the file. Then it said it installed. Then asked to restart so I did.    If I try to install again it just crashees. I boot from disk, ubunto loads up, purpple background, has the version number 11.04.   THen has this white text that starts turning rud and has a bunch of &quot;[OK]&quot; things on the right.  Then the screen gets this crash and there are staticky green and purple square covering the screen, then nothing happens.

---

### Post by seawolf167 on 2011-06-06
We could maybe walk through and fix this - but I think it would be easiest to simply reinstall Ubuntu unfortunately. Someone else may chime in with a different method if you wait though. You can save all your files and settings very easily if you decide to reinstall.

The first step would be firing up a LiveCD and booting into the live environment. Once there, you can simply copy your /home folder to an external hard drive (ensure it is formatted in ext3 or ext4 if you want to save your settings).

After you have your /home folder copied, you can reinstall Ubuntu. When you set it up this time I suggest a separate /home partition. The basic setup would be:

/ (root)   mount point: /   size: 20GB
swap   mount point: swap   size: 2-4 GB (more if you have less RAM)
/home   mount point: /home   size: remainder of the space

Once the installation completes, you can easily copy your /home folder over to your new installation. 

The preferred way to install the graphics drivers would then be to check under Hardware Drivers to see if you have open source drivers available.

---

### Post by XFTOX on 2011-06-07
Lol well like I said Ive put windows back on. Stayed up till 7am doing all this :)  Anyways, I really enjoyed Ubuntu, because my friend has it. But only one thing is that the gaming side. I game, not alot, but i do game. Mainly atm its battlefield 2 on Steam. Ive got steam to work at my friends place, but i dunno.   Dunno if i should risk trying Ubuntu again, I think the same thing will just happen. Plus im not too experianced with this whole /root sudo stuff.

---

