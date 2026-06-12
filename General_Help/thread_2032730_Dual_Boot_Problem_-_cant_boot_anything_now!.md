---
title: "Dual Boot Problem - cant boot anything now!"
date: 2012-07-24
forum: General Help
---

### Post by aj5string27 on 2012-07-24
Hi,

My laptop is running Ubuntu 12.04 and Windows 7.  I've been using Ubuntu for about 6 years, but have been using this laptop for work, so have been using Windows a bit more.  I kinda no my way around Ubuntu, but am by no means an expert!!!

I was doing some cleaning (deleting unused partitions etc) and now when I go to turn my laptop on i get;

```
error: no such partition
grub rescue
```

So - I've deleted something I shouldn't have... the mbr i assume.  Not a problem I thought, I will make a bootable USB, 'try ubuntu', get hold of all my docs so that they are safe, and then I will sort it out properly.  When I did try that tho, I get this message;

```
An operating system wasn't found.  Try disconnecting any drives that don't contain an operating system
```

I have tried it with Ubuntu Live on a CD, and that (after the disc has whirred a bit) goes back to the first 'error; no such...' screen.

I'm confused!  I have no doubt that its something I've done, and Im totally fine with that, but I have all of my work docs on the laptop that I NEED to get to!  I am quite happy totally clearing the HD and doing fresh installs, but I need to get to my docs first!  Hopefully its something really simple?

Thanks in advance!

Alex.

---

### Post by CaptinGoogle on 2012-07-24
I suggest booting up a Live Ubuntu disk and then using Boot-Repair if you still have your Ubuntu partition.

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update

sudo apt-get install boot-repair

---

### Post by aj5string27 on 2012-07-26
HI - I've sorted it now, but thanks for the info.

Alex.

---

### Post by CaptinGoogle on 2012-07-27
Glad to hear. Could you please post how you corrected your issue and then mark the thread as solved?

---

