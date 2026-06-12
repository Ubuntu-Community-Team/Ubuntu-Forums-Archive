---
title: "Grub not initializing menu"
date: 2010-01-20
forum: General Help
---

### Post by HeretikSaint on 2010-01-20
I need some help.  I'm not exactly new to linux but I'm not an expert either.  I decided to try and play around with GRUB and see if I could get the GRUB gui and themes working.  Apparently I did something and now, when I start up my computer, all I get is:
```

Grub Loading.
Welcome to Grub!

error: file not found
error: file not found
error: file not found
error: file not found
error: file not found
error: file not found
error: file not found
error: file not found
error: file not found
error: file not found
error: file not found
Entering rescue mode... 
error: menu not initialized 
grub rescue>

```

I know little to nothing about grub.  I will welcome any and all help or advice with this.  Let me know if you need any other information and I will try to post it.  Also, I have no idea whether I am running legacy or 2.  It originally told me I was running legacy and I attempted to upgrade to 2 but I have no idea if it actually upgraded.  Thank you in advance.

---

### Post by rnerwein on 2010-01-20
hi
try # grub-install -v    (that gives you the version you are running)

---

### Post by HeretikSaint on 2010-01-20
I'm getting:
```

error: unknown command 'grub-install'

```
I wasn't sure if the '#' was part of the command so I tried that as well and it didn't help.  I can't get into either of my OSes.  I'm stuck inside grub with a command prompt that says "grub rescue>'.

---

### Post by rnerwein on 2010-01-20
hi 
sorry excuse me this command isn't available in rescue mode but try this:
1 ls
2 set prefix=(hdX,Y)/boot/grub
3 set root=(hdX,Y)
4 set
5 ls /boot
6 insmod /boot/grub/linux.mod
7 linux /vmlinuz root=/dev/sdXY ro
8 initrd /initrd.img
9 boot

i got this from the manual pages.
hope it helps
ciao

---

### Post by HeretikSaint on 2010-01-20
I actually figured out what I did.  When I did:
```
 sudo update-grub-from-legacy
```
It asked me which partitions to add.  I hit enter instead of space bar so it selected no partitions to load.  I went and reinstalled grub2 by loading a live version of ubuntu.  Thanks for the replies.

---

