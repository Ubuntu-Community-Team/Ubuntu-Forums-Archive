---
title: "Partition resizing help"
date: 2009-08-03
forum: General Help
---

### Post by Primefalcon on 2009-08-03
I seem to have made a little mistake I installed windows xp pro and Ubuntu

anyhow when installing I messed up the sizes ended up with xp taking 90% of the drive up, anyhow I booted from the live disk and shrunk the xp partition using gparted, however it won't let me enlarge the ubuntu partition, here's a screenshot of the area, anyhow help asap would be appreciated

[IMG]http://i28.tinypic.com/16j22o2.jpg[/IMG]

---

### Post by drs305 on 2009-08-03
I wrote this guide for expanding / by taking space from Windows:
[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

It was for failed installs that created only a 2.5GB / partition, which looks like what happened to you. There are also instructions for how to reinstall and prevent it from happening again if you prefer to do it that way.

Your situation is a bit easier since you already have unallocated space, so you can skip a step or two.

---

### Post by Primefalcon on 2009-08-03
> **drs305 said:**
> I wrote this guide for expanding / by taking space from Windows:
[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

It was for failed installs that created only a 2.5GB / partition, which looks like what happened to you. There are also instructions for how to reinstall and prevent it from happening again if you prefer to do it that way.

Your situation is a bit easier since you already have unallocated space, so you can skip a step or two.
the problem is it won't let me resize the ubuntu partition it just doesn't show that as an option, it stays faded out when I have ubuntu partition area selected and it's showing a key in the area next to it, I'm not sure what that means

---

### Post by merlinus on 2009-08-03
You will have to work with the extended partition first.

---

### Post by Primefalcon on 2009-08-03
> **merlinus said:**
> The key shows that the partition is locked, and you cannot do anything until it is unmounted.  However, you obviously cannot unmount the partition you are working on, so use gparted on the ubuntu live cd or its own.
I am on the livecd

---

### Post by merlinus on 2009-08-03
Yes, sorry, I realized that and edited my original post.  drs's guide should explain how to resize the extended partition first.

Click on sda6 and choose swapoff.

---

### Post by drs305 on 2009-08-03
It's explained in the guide, but the short answer is probably that you have to turn off the swap partition. Right click the swap partition, then Swapoff. The swap partition still has the "key" symbol, which means it's mounted.

---

### Post by Primefalcon on 2009-08-03
> **drs305 said:**
> It's explained in the guide, but the short answer is probably that you have to turn off the swap partition. Right click the swap partition, then Swapoff.
Ok thank you heaps :-) I' cant do it a the moment I adjusted the partitions around a little, and now since I grew the windows partition a couple of Gb's  up to 45 and it's taking ages, I'll have to wait the half an hour or so for this to do it, my feeling is it prob not safe to cancel a partition resize

Btw is there anyway I can thank a user  on these forums?

---

### Post by merlinus on 2009-08-03
Definitely do not cancel the resize, or the partition will be unusable.

---

### Post by Primefalcon on 2009-08-03
Thx figured as much, Kinda already sorry I have to deal with windows, already I've noticed I'm going to have to go hunting all over for drivers, for stuff I've never had an issue with in Ubuntu.

I wish the world wasn't so widows oriented and that I didn't need it to test internet pages in IE.

---

### Post by merlinus on 2009-08-03
Why not run windows in a vm such as virtualbox?  Or use wine?

---

### Post by Primefalcon on 2009-08-03
> **merlinus said:**
> Why not run windows in a vm such as virtualbox?  Or use wine?
I've been using wine for small things over the past 3 years or so, but there are things I need windows for unfortunately and unfortunately I can't test IE8 in wine, and unfortunately I need full speed so VM is not an option

---

### Post by merlinus on 2009-08-03
FWIW, the one and only windows app I use runs much, much faster in virtualbox on linux than it ever did on windows, and it is graphics-intensive.

---

### Post by Primefalcon on 2009-08-03
virtualbox, is that just install windows xp into a virtual computer? if so I don't really have the ram for that.

---

### Post by merlinus on 2009-08-03
VirtualBox is a linux vm.  I have 4G RAM and give it 1.5 when it is running.

---

### Post by Primefalcon on 2009-08-03
unfrotunately I don't have that much ram atm only I'll be chucking in anothe ram stick for 1 gig of ram....

And ok that worked perfectly with the partitions after all this is done, its just  a matter of turning swap back to on I assume.

Thx again for all the help

---

### Post by merlinus on 2009-08-03
Yes.  swapon is the command.

---

### Post by Primefalcon on 2009-08-03
> **merlinus said:**
> Yes.  swapon is the command.
out of curiosity does that need to be done or is it only mounted with the Livecd so that the livecd can use the swap?

---

### Post by merlinus on 2009-08-03
Used by both the live cd and ubuntu.

---

### Post by Primefalcon on 2009-08-03
> **merlinus said:**
> Used by both the live cd and ubuntu.
ahh that's why it mounts automatically when you boot the livecd

---

