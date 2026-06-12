---
title: "USB Flash Clone / Image question"
date: 2010-11-06
forum: General Help
---

### Post by pruitthall on 2010-11-06
Evening all.  I'd like to thank everyone that helped me a week ago on a strange issue I had with my sudoers file.  In the end, with much gnashing of my teeth, I just started over and created a new 4gb flash.  And, as one helper told me, it was truly easier a second go around.  Not quick, mind you, but easier :)

Now that I've got my flash somewhat stable, I'd like to know how to make a mirror image 'clone' of this flash to another, just like it.  Between my Broadcom drivers, nVidea drivers, updates and flash/java, I've gotten pretty protective of this little flash drive!

I've head 'dd' will do it, but, as a newb, is their an application or tool that might make the job easier.

Again, thanks in advance to everyone; this site is an immense help.

---

### Post by Neek0 on 2010-11-06
Try using dd.

dd if=/dev/hd? of=/dev/hd? bs=16384 conv=notrunc,noerror

"if" (input file) is the drive you want to copy and "of" (output file) is the drive you want it to copy to.

if that doesn't do it for you then there is always parted magic, which you can find at distrowatch.com. it has an imaging program built in.

third, you could get clonezilla, also from distrowatch.

and a fourth option is "ultimate boot cd for windows" or ubcd4win. i know, how dare i mention windows here! but it is really a good tool. it is a live cd that has a program called SelfImage, which is a great imaging tool. works on linux partitions as well. it needs to be used in conjunction with another program on the disk called MBRWizard. which saves the mbr and restores it to the new drive.

---

### Post by pruitthall on 2010-11-06
NeekO,

Many thanks!

---

