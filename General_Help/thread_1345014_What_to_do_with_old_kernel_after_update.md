---
title: "What to do with old kernel after update?"
date: 2009-12-03
forum: General Help
---

### Post by NTHQ on 2009-12-03
After every kernel update, I see in grub that the old version is still present as a choice of OS to boot. I saw that the files were also still in my file system along side the new version.
Can I just delete the whole folder to make it disappear? If not, how do I edit grub to make it not show anymore?

---

### Post by falconindy on 2009-12-03
You can remove old kernels through synaptic. Do a quick search for packages called 'linux-image'. It's advisable to would keep around at least 1 old kernel just in case you have problems with the new one.

---

### Post by Gillingham on 2009-12-03
I normally keep at least one working kernel after an update as I have had a couple of kernel updates that broke stuff.  

But once I'm happy I remove the old kernel via Synaptic, there probably will be several packages with the same version number.

---

### Post by isee on 2009-12-03
System > Administration > Start-up Manager > Advanced

You can choose how many kernels to display at boot, although I don't know if it removes the files from your drive or not.  I think it's recommended to keep at least two.

---

### Post by NTHQ on 2009-12-03
> **isee said:**
> System > Administration > Start-up Manager > Advanced

You can choose how many kernels to display at boot, although I don't know if it removes the files from your drive or not.  I think it's recommended to keep at least two.

I don't see Start-up Manager under Administration. There is a Startup Applications in Preferences but it doesn't look like that's what you're talking about. I am on 9.10 by the way.

---

### Post by isee on 2009-12-03
> **NTHQ said:**
> I don't see Start-up Manager under Administration. There is a Startup Applications in Preferences but it doesn't look like that's what you're talking about. I am on 9.10 by the way.

Open Synaptic Package Manager in Sys > Adm

search for "startupmanager", mark for installation and apply.

Then it should be in your menu.  Samething in either 9.04 or 9.10.

---

### Post by NTHQ on 2009-12-03
> **isee said:**
> Open Synaptic Package Manager in Sys > Adm

search for "startupmanager", mark for installation and apply.

Then it should be in your menu.  Samething in either 9.04 or 9.10.
I got Start-up Manager now but there doesn't seem to be an option to select how many kernels to display. I can select which to be the default one though. And in the Advanced tab there's just a drop down list for the bootloader resolution and a button to create a rescue floppy.

---

### Post by isee on 2009-12-03
NTHQ I'm sorry my mistake:oops:.  The option is not available in 9.10's Start-up Manager.  

I guess in Karmic it can only be done like the other posters describe, through Synaptic.

---

### Post by NTHQ on 2009-12-03
> **isee said:**
> NTHQ I'm sorry my mistake:oops:.  The option is not available in 9.10's Start-up Manager.  

I guess in Karmic it can only be done like the other posters describe, through Synaptic.

Very well then. I appreciate your help.

---

### Post by filip007 on 2009-12-03
It's only about 25MB am i right so why bother...

I like to have 2.6.32 where is it i can't see it? :p

---

### Post by NTHQ on 2009-12-04
> **filip007 said:**
> It's only about 25MB am i right so why bother...

I like to have 2.6.32 where is it i can't see it? :p

It's not the size that bothers me. It's just having too many things displayed in grub that kinda annoys me.

---

### Post by filip007 on 2009-12-05
You can edit Grub...

install mc with

sudo apt-get install mc

sudo -s 

mc

and look for

/boot/grub/grub.cfg

PS: Be careful what you do and look first how boot code works 

Still no no word on new 2.6.32 ???

---

### Post by NTHQ on 2009-12-05
Ok I'll look into the boot code.
As for removing the old kernel, should I mark it for Removal or Complete removal? What's the difference?

---

### Post by filip007 on 2009-12-06
You're taking about Synaptic?

If size is not a problem the just clear out Grub.cfg

I my self don't touch kernel i just install weekly updates what ever are they and don't have any boot selection...yes if got multi boot for W. that's your choice.

---

### Post by NTHQ on 2009-12-06
K, thanks for your help.

---

### Post by oldos2er on 2009-12-06
Editing /boot/grub/grub.cfg is not the way to go. See [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by t0p on 2009-12-06
NTHQ: remove the old kernel-image* files through Synaptic.  Mark them for Complete Removal, and it'll also remove the old entries from the grub menu.  You shouldn't have to edit the grub menu yourself.

Remember to keep at least one old kernel, in case of problems.

> **filip007 said:**
> It's only about 25MB am i right so why bother...


That depends on how many old kernel images you've got.  On this machine I've had Hardy running since soon after its release (April 2008 ).  I deleted old kernel images from this machine for the first time a couple of weeks ago, and according to *df -h* it freed up nearly half a gigbyte of disk space.  Not to be sniffed at.

---

### Post by filip007 on 2009-12-06
Then do clean install with every new release if you can...

This should be done automatically then...

Yes you're right more space on HDD the faster it will be, on SSD is probably don't matter any more.

I checked Kernel size is 60MB Packed and 340MB unpacked, it's probably strip down by hardware when install, i remember some distro asked me for removing kernel drivers.

Someone post for removing non use kernels on UbuntuTweak site that will make things more simple.

---

### Post by oldos2er on 2009-12-06
Kernels are 3.8MB in Ubuntu 9.10

-rw-r--r--  1 root root 3.8M 2009-10-16 10:12 vmlinuz-2.6.31-14-generic
-rw-r--r--  1 root root 3.8M 2009-11-10 09:46 vmlinuz-2.6.31-15-generic
-rw-r--r--  1 root root 3.8M 2009-12-03 17:00 vmlinuz-2.6.31-16-generic

---

### Post by HomoGleek on 2009-12-06
UbuntuTweak is a great little tool for cleaning up your system

---

### Post by lidex on 2009-12-06
+1 for ubuntu tweak. Makes managing kernel and header files a breeze. Also provides a gui to clean out old packages as well as your apt cache.

---

### Post by filip007 on 2009-12-07
**lidex** you're absolutely right...

[IMG]http://i45.tinypic.com/25hekwm.jpg[/IMG]

On Ubuntu we can relax with some cleaning time to time \\:D/

Thanks again!

---

