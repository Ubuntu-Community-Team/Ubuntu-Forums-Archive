---
title: "Cant boot ubuntu"
date: 2010-04-06
forum: General Help
---

### Post by w3dge on 2010-04-06
I installed a update on a driver now i cant boot ubuntu.
i select ubuntu,then ubuntu generic then i get this message.


[ 1.772486] Kernel Panic -Not syncing :VFS: Unable to mount root FS on unknown Block (8,1)

can anyone help?

---

### Post by w3dge on 2010-04-06
noone knows?

---

### Post by QIII on 2010-04-06
An hour and a half is a bit quick for a bump.  Remember that we are all  here voluntarily on our own time and cannot always get to every question  immediately.

But we certainly want to help -- so don't take that as a scolding!  Just  an explanation.

Could you give us some more information on the specs of your machine, how many drives/partitions you have (I ask because of part of the message),  which version you are using, the driver you installed and the steps you took to install the driver?

---

### Post by w3dge on 2010-04-06
sorry about that
i booted using a lower number after it says ubuntu generic
managed to get on

---

### Post by r_s on 2010-04-06
did you use another kernel to boot?

---

### Post by w3dge on 2010-04-06
i think so.
there was 2 options(minus recovery) starting 2.6.31-something
i was clicking on the highest number before but clicked on the lower number and ubuntu booted.

---

### Post by r_s on 2010-04-06
there might be some problem with your latest kernel.

---

### Post by QIII on 2010-04-06
It looks like you are using Karmic, judging from the kernel.

And your problem may be (this is why I asked about disks/partitions) that there is something in GRUB2 trying to look at a partition that does not exist.  (8,0) is pretty odd.

From the kernel you can get into, use the terminal and issue

```
sudo update-grub2
```

You will be asked for your password.  Type in your normal password.  Nothing will show.  That is normal.

Watch the output and see if it catches the higher-numbered kernel without error.

After the update is done, exit the terminal, shut down and restart.  See if you can get in.

If not, go back to the kernel you can boot with and come back so we can see if we can get further.

---

### Post by QIII on 2010-04-06
> **r_s said:**
> there might be some problem with your latest  kernel.

I'm liking that possibility, since he installed a driver and a module  may have screwed things up.

But the "Block (8,0)" is also of concern.

---

### Post by lidex on 2010-04-06
For your kernel panic:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/24]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/24")

---

### Post by QIII on 2010-04-06
You'll have to forgive my ignorance of Wubi here, but what in his post indicated that this was a Wubi install?

In another thread, he said he had a dual-boot.  

I understand that some folks have a different notion of dual-boot when working with Wubi.

But I have gotten a nearly identical error message from time to time updating kernels on Fedora -- in a genuine dual-boot configuration on separate physical drives.

---

