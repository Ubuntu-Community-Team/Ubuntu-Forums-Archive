---
title: "windows me and linux"
date: 2010-11-15
forum: General Help
---

### Post by Galva1 on 2010-11-15
Hello!

I am a beginer of using computers and I just need some help.

My other computer is running Windows Millennium Edition.
I want to make that computer so it has Windows and Linux. Like two at the same time. I know about Wubi but the thing is that Wubi doesn't support Windows Millenium and the computer also is not connected to internet.
 
:(

Could you kind people give me some instructions?

---

### Post by jroa on 2010-11-15
Just boot the computer from an Ubuntu CD.  Click the icon on the desktop to start the install.  

Are you able to set the boot order in the BIOS?

---

### Post by sanderd17 on 2010-11-15
wait a minute. If your computer came with millenium, you probably don't have enough RAM. You should have 512 MB to have a good experience. If you have less, I wouldn't advise to install ubuntu. Try something lighter like Lubuntu.

When you have your CD. put the CD into your computer and boot. If you have space enough on your hard disk, (L)Ubuntu will propose to install itself next to millenium. Please backup all important files before you do this.

It would be better to test ubuntu before you install it.
Just do the same: put in the CD and boot, but choose to "test ubuntu" instead of "install ubuntu". If ubuntu works for you, you can go ahead and install it.

---

### Post by Galva1 on 2010-11-15
I tried the Ubuntu Live CD. Everything works great. But if I install it  Windows seems to be gone. It has to do something with the partitioning which I don't know how to make.

---

### Post by jroa on 2010-11-15
When you install, you should be given an option to dual boot.  I can't remember exactly how it is worded, but it should say something like "Create a new partition for dual boot" or "Install next to an existing OS" or something like that.

---

### Post by sanderd17 on 2010-11-15
so now you have a computer with only ubuntu on it?

Well, then you'll first have to reinstall millenium. Millenium will certainly wipe ubuntu out.

How big is your hard disk? I guess you need about 20 GB for both ubuntu and millenium (including your data and installed programs).

If millenium is on your computer and ubuntu not, can you execute
```

sudo parted -l

```
in the terminal? so we can see what your current configuration is and how you can do it manually.

---

### Post by Galva1 on 2010-11-15
Yes I have Millenium back and Ubuntu is gone.

---

### Post by sanderd17 on 2010-11-15
then boot the live cd, try ubuntu and execute the command.

---

### Post by Galva1 on 2010-11-15
Got no idea how to do that

---

### Post by sanderd17 on 2010-11-15
it should be somewhere in your menu's, but I don't know where because I don't have the standard menu's anymore.

But you can always start the terminal with pressing ALT+F2 and then typing
```

gnome-terminal

```

once you have the terminal, type
```

sudo parted -l

```
and post the output.

you can copy-paste by selecting the text and middle-clicking where it need to come. You can also use CTRL+SHIFT+C to copy. CTRL+C won't work.

---

### Post by Galva1 on 2010-11-15
What will that command do?

---

### Post by sanderd17 on 2010-11-15
it will show how big your hdd is and how the current partitions are. It would be the same like you launched gparted and took a screenshot. But screenshots are big and unreadable.

---

### Post by mastablasta on 2010-11-15
You can get a bit info if you have latest edition here:
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
 
Otherwise (if you downloaded the Long term Support version = 10.04) then you should read the Ubuntu manual (see my signature).
 
Go through it, read it a bit and see the pictures. At least the part about installation.
 
if live CD works you are in luck and there might be no point in having the Windows Millenium arround, as ubuntu has much more advance programmes available. then again it's your choice.

---

