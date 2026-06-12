---
title: "&quot;Try hd(0,0) NTFS5&quot;"
date: 2010-10-27
forum: General Help
---

### Post by rbsis on 2010-10-27
Well I installed Ubuntu with Wubi and it was working great but the boot splash screen was messed up so I used this guide:[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml") to try to fix it but now when I try to boot Ubuntu it just says "Try hd(0,0) HTFS5" and then reboots. I can't even get into GRUB recovery.

Any idea how to fix this? I thought I could just open the .disk files and edit Ubuntu to what it was before but I can't find any programs that will edit .disk files.

---

### Post by Hippytaff on 2010-10-27
Have you got loads of important stuff on the ubuntu Wubi? if not maybe reinstall it or if you like ubuntu and intend using it more then you could just install 10.10 on a real partition (rather then the wubi which is kind of inside windows) :-)

or ignore me and wait for some real advice :-D

---

### Post by rbsis on 2010-10-27
> **Hippytaff said:**
> Have you got loads of important stuff on the ubuntu Wubi? if not maybe reinstall it or if you like ubuntu and intend using it more then you could just install 10.10 on a real partition (rather then the wubi which is kind of inside windows) :-)

or ignore me and wait for some real advice :-D
I don't have loads of important stuff but I just finished installing all my drivers and getting my system to the way I want. I'm going to try to get on a LiveCD and edit everything back to normal and see if that works.

---

### Post by Hippytaff on 2010-10-27
Not sure, but because wubi isn't an actual partition you might not have much joy trying to fix stuff with a liveCD...but I could be wrong :-)

---

### Post by oldfred on 2010-10-27
I do not know wubi but saved these links:

How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

---

### Post by bcbc on 2010-10-27
Even though your situation is different to the upgrade issue, the symptoms are very similar (rebooting after selecting Ubuntu). I would try this fix first. [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

I saw another thread where the user installed startup manager and it caused problems with wubi. Not sure why this would be.

---

### Post by drs305 on 2010-10-27
If you can get to a grub prompt: It's called the "Grub Rescue" thread but you might be able to boot via the command line using the section "Wubi Only".
[http://ubuntuforums.org/showthread.php?t=1594052]("http://ubuntuforums.org/showthread.php?t=1594052")

---

### Post by rbsis on 2010-10-28
> **bcbc said:**
> Even though your situation is different to the upgrade issue, the symptoms are very similar (rebooting after selecting Ubuntu). I would try this fix first. [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

I saw another thread where the user installed startup manager and it caused problems with wubi. Not sure why this would be.
Thank you!
 
I used the link in your post to mount the disk and I edited everything to what it was originally and then followed your instructions and it worked. But I still have the problem where I get a blinking courser for around 30 seconds before I see the boot splash screen.

---

### Post by bcbc on 2010-10-28
> **rbsis said:**
> Thank you!
 
I used the link in your post to mount the disk and I edited everything to what it was originally and then followed your instructions and it worked. But I still have the problem where I get a blinking courser for around 30 seconds before I see the boot splash screen.

There is a fix to show the boot splash (rather than the blinking cursor) but it won't fix the boot up time. If you think the boot time is abnormal look in your logs for any problems.

The splash fix can be seen here - it's for 10.04 but I believe the same fix works for 10.10

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)
> Other graphics card users including nVidia may get a black screen with flashing cursor and then a very short duration plymouth. 
[https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801](https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801)
One fix for this is to create this file.
Code:
gksu gedit /etc/initramfs-tools/conf.d/splash
and add this option FRAMEBUFFER=y, save the file.
Then
Code:
sudo update-initramfs -u

I tried the fix on my original upgrade to 10.04 and it worked fine, but when I get the problem on some of my test installs these days I just ignore it.

---

