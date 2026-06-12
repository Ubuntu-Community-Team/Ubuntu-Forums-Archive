---
title: "Ubuntu not working - mount /dev on /root/dev failed : no such file or directory"
date: 2010-08-08
forum: General Help
---

### Post by apoorvumang on 2010-08-08
Ubuntu(10.04)  was working fine, then some program crashed or something, and I just  switched off (power offed) the computer (sorry, shouldn't have). When I  restarted it, this sort of stuff comes:
  ```

mount /dev on /root/dev failed : No such file or directory 

```
and some more lines like that, and then 'Busybox' starts with  [intramfs].
I booted Ubuntu from a pen drive and ran fsck on the main partition. I  just pressed 'y' for a long time (it asks stuff like should it continue  repairing or something), and then it was done. I restarted the pc and it  booted normally - it looked as if everything was fine.

I started google chrome, and it said it couldn't find a personal config  file .. ok. Then I tried opening a folder - nothing happens. The system  monitor doesn't open, and windows that do open eventually are completely  blank. I restarted the pc (this time by doing the normal restart), and  it gave me the same 'Busybox' thing.

I did the same procedure again, and got the same results. (ubuntu boots,  programs dont work, then I restart and the Busybox thing comes again)
Why is this happening?
Please help!!

One More Thing :  The Ubuntu installed on the hard disk had all the  recent updates (including the latest linux kernel) while the pen drive  thing was around 2 months old I think. So maybe that's the cause? I'm  completely new to Ubuntu, so I dunno anything about this.

(This is a repost. I posted the same thing in a wrong category, so I'm posting here. Sorry, dunno how to move it or if it is possible to delete it)

---

### Post by apoorvumang on 2010-08-08
Anybody knows why this is happening, or how to get it right?

---

### Post by eduangutan on 2010-09-17
I'm suffering from this too and have not found a fix anywhere, just some old posts and this recent one.

------------
What happened:
Started my Kubuntu 10.04 (with latest updates!) as usual (opened only ktorrent and emesene). Came back after a while and everything was frozen. Had to hard reset (button). Now when restarting this message is displayed:


---------------------------------
[weird hexadecimal codes]
Killed
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
---------------------------------

I know the hard drive is not dead because I can access it from a live cd ...

Any help is highly appreciated!! :-k

---

### Post by eduangutan on 2010-09-27
update: I got tired of waiting and re-installed kubuntu 10.04. Everything worked fine for about a week until the system froze again.
I've the same problem now :(

---

### Post by ishaangt on 2011-05-16
same thing happended to me too....
i got sic of all that...on top of gparted formated my whole drive so i lost watever was left..
i tried using the liveCD to recover the data but the Busy Box thing came up...EVEN With tHE LIVECD...!!
thats so awefull.....can anybody..those tech gurus sitting there help...

---

