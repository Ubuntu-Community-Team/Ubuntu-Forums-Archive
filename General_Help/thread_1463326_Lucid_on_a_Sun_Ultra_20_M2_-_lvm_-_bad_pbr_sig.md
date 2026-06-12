---
title: "Lucid on a Sun Ultra 20 M2 - lvm - bad pbr sig"
date: 2010-04-26
forum: General Help
---

### Post by bignose on 2010-04-26
Hi,

I installed lucid a few days ago on on my Ultra 20 M2 [basically an Opteron machine]

Anyways, I used the alternate DVD, and installed with LVM in a raid 1 configuration accross 2 500 gig drives.

To test, unplugged drive 2 and booted off just drive 1, worked no problems.

Then I tried booting off just drive 2, and gotthis error message before any Ubuntu screens

"bad pbr sig"

Did some googling ,found this [http://asupergeek.blogspot.com/2007/06/bad-pbr-sig.html](http://asupergeek.blogspot.com/2007/06/bad-pbr-sig.html) among lots of other links about solaris 9.. :)

Anyways, installed grub with apt, and started to run the commands you see in that page, and when i ran setup, here is what I got.

grub> device (hd1) /dev/sda

grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

So now I'm kinda stuck.

---

### Post by -humanaut- on 2010-04-26
If its just an x86_64 machine you should make sure your media is good.

---

### Post by tilapia on 2010-05-11
There appear to be some issues with raid installs on Lucid at the moment. I spent the weekend facing similar issues. There's a workaround (of sorts) on Launchpad.

---

