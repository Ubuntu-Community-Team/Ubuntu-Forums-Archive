---
title: "Alien .rpm to .deb not working"
date: 2009-11-23
forum: General Help
---

### Post by The Grey Wizard on 2009-11-23
So I tried to convert a .rpm to .deb and it told me to log into root so I logged fakeroot and finally got it to convert but now it won't unpack the .deb, all I get is this.

[http://img412.imageshack.us/img412/7199/bullshitx.png](http://img412.imageshack.us/img412/7199/bullshitx.png)

---

### Post by Bluppie on 2009-11-23
Look at [http://linux.die.net/man/1/alien]("http://linux.die.net/man/1/alien") Maybe this is the answer.

---

### Post by The Grey Wizard on 2009-11-23
Not much helped there. :(

---

### Post by The Grey Wizard on 2009-11-30
bump

---

### Post by raktarok on 2009-12-01
I don't think I will be much of a help, but can you install other .deb files via dpkg? and what are the permissions for the file /var/log/dpkg.log?
Please post the output of this:
```
sudo ls -l  /var/lib/dpkg.log
```
If you can't install the deb, what you can probably do is just extract the files from the archive, place it in their appropriate locations and then pray that the program works. :)

---

### Post by The Grey Wizard on 2009-12-01
Now I had thought of that, but I don't have permissions to place the files in the usr folder. I'll try that terminal command real quick though and see what I get.

Edit: Here it is: [http://img339.imageshack.us/img339/9662/screenshot4z.png](http://img339.imageshack.us/img339/9662/screenshot4z.png)

---

### Post by raktarok on 2009-12-01
oops..sorry. that was meant to be:
sudo ls -l  /var/log/dpkg.log

and you can do **gksudo nautilus ** to open nautilus as root. Then you can extract the deb and place its files in the appropriate folders.

---

### Post by The Grey Wizard on 2009-12-01
Yeah, I reckon I could log in as the root, but I've always tried to steer clear of logging in as root. I've been told messing around in root can crash your system.

Edit: Here's my terminal: [http://img163.imageshack.us/img163/421/screenshot5b.png](http://img163.imageshack.us/img163/421/screenshot5b.png)

---

### Post by raktarok on 2009-12-01
That's true, but you are only using root privileges here, you are not actually logging in as root. Of course, you need to be careful, and as long as you don't randomly delete files inside the root nautilus, it will be safe. Give it a try, and see if it works. 

And when you try installing other deb files, do you get the same error?

Edit:
Hmm..the permissions of the file dpkg.log seem to be all right.And the superuser should be able to write to the file. Try this and see if you can install the deb:
```
sudo touch /var/log/dpkg.log
```

---

### Post by The Grey Wizard on 2009-12-01
Oh boy, now I've got a big problem. I put that terminal command, then tried to log out of my user account to switch to root. When I logged out my screen no longer had a vga signal and now when I try to boot Ubuntu it tells me root cannot be mounted!

---

### Post by raktarok on 2009-12-01
That command should have been harmless....
Your new problem is probably due to some other issue. Did you make any other changes? and what exactly is the error, can you give the full description? Do you get the error in a black console screen? Are you dropped to a shell i.e. can you type commands?
I don't think the problem is due to the commands I gave, but if they are linked in any way, I am truly, truly sorry. I will try to solve your problem, so please post more details.

---

### Post by The Grey Wizard on 2009-12-01
Don't worry, Ubuntu 9.10 just needs some more attention, I've had this problem with it before. Seeing as how Ubuntu doesn't really need to be shut down periodically like Windows, I haven't shut it down for probably over a week, so pinpointing the culprit might be hard. Now I have a dual partition with Windows XP(what I'm on right now) and Ubuntu on D:\ I go to select Ubuntu from the boot menu and it takes me to the grub menu where you can select; Ubuntu, Ubuntu Recovery, Windows XP. I select Ubuntu and it gives me an error. I can't type anything and I have to restart my computer. I'll get the exact code here in a minute. Thanks for the quick reply, I about had a hard attack.

Edit:
```
[Linus-bzImage, setup=0x3400, size=0x3bf0c0]
[Initrd, addr=0x37763000, size=0x83c819]
[   0.689464] Kernel Panic-not syncing:VFS: Unable to mount root on fs on unkno
wn-block(8.5)
```

---

### Post by The Grey Wizard on 2009-12-01
Bump

Ok, it was a graphics driver that was causing me so much grief! I can't believe that, if I had known that I would have all my old 3d models from the last time this happened. I officially declare war on ATI for not supporting the x850 on linux. However, my original problem is still unsolved. Funny how that works.

---

### Post by 3rdalbum on 2009-12-01
Elevate to root using "sudo" whenever necessary. Just don't actually log in every day as root (you can't log in as root on Ubuntu unless you actually set this up yourself).

The 'alien' command needs to be run as root, I believe.

---

### Post by The Grey Wizard on 2009-12-01
It doesn't matter, I went to install the 3d drivers for the other video card and I'm **[[COLOR="Blue"]back at square one[/COLOR]](http://img525.imageshack.us/img525/1017/linuxsucks.png)**

I'll just use windows to 3d model, I guess I'll have to wait until Ubuntu has better 3d graphics support.

---

