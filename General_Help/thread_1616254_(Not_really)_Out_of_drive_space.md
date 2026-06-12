---
title: "(Not really) Out of drive space"
date: 2010-11-08
forum: General Help
---

### Post by appalbarry on 2010-11-08
I installed Lucid Lynx using the Wubi installer a while back - love it. I did nothing, no partitioning, just ran it and it set everything up so that it just works.

EXCEPT Ubuntu keeps banging it's head against some imaginary lack of space on the hard drive.

I know I've got a couple of hundred gigs of space, but Ubuntu can't seem to use it.  I'm sure there's a simple solution, but my linux knowledge isn't quite enough yet to understand what it is.

Here's waht I've got:


barry@Barry_Desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/loop0            16876388  15846288    172808  99% /
none                   1540904       364   1540540   1% /dev
none                   1545568       564   1545004   1% /dev/shm
none                   1545568       356   1545212   1% /var/run
none                   1545568         0   1545568   0% /var/lock
none                   1545568         0   1545568   0% /lib/init/rw
/dev/sda3            477835260 309218024 168617236  65% /host
none                  16876388  15846288    172808  99% /var/lib/ureadahead/debugfs
barry@Barry_Desktop:~$ 

I'm unclear about what /dev/loop0/ might be, but assume that the problem is connected to that?

How can I fix this?

Thanks,

Barry

(I'm running a pretty vanilla Dell 64 bit system, with a seldom used Vista dual boot.)

---

### Post by Verbeck on 2010-11-08
> **appalbarry said:**
> I installed Lucid Lynx using the Wubi installer a while back

how much did you allocate for ubuntu from the installation?
the default is 8 gb and that's quite small if you save stuff in your home folder

---

### Post by P4man on 2010-11-08
/dev/loop0 is your virtual file system root,  so yeah there is your problem. Its full.  The best solution is doing a proper, non wubi install and move your files over. But there are ways to extend a wubi install, though cumbersome and not sure Id recommend it:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

---

### Post by appalbarry on 2010-11-08
Thanks folks - I've got it now.  I'll try the resizing first and see if that solves the problem.  A full install would be best, but lord I don't know if I have time for that right now.  Looks like the wubi default leaves something to be desired.

---

### Post by P4man on 2010-11-08
> **appalbarry said:**
> Looks like the wubi [s]default[/s] leaves something to be desired.

Fixed that for you. Wubi is intended to just test ubuntu, for people wary of repartitioning. Its not meant to actually be used extensively. They might make that a bit more clear in the installer.

---

### Post by appalbarry on 2010-11-08
Although I have to say, aside from this space issue, it has run flawlessly from day one - first time ever that I tried Linux and didn't nuke it out of frustration.

---

### Post by appalbarry on 2010-11-08
Followup:

1) Downloaded [**LVPM**]("http://lubi.sourceforge.net/lvpm.html")
2) Installed and ran it in Ubuntu.
3) Selected "Resize" and 50,000 megs
4) Let it run; when it was done followed the instructions:
5) Reboot into Windows 
6) Find **c:/ubuntu/disks/root.disk** and backed it up
7) Changed **c:/ubuntu/disks/new.disk** into **root.disk**
8) Rebooted back into Ubuntu and everything is fine.

---

