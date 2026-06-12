---
title: "Not able to add all ISO files to the start up disk creator"
date: 2011-12-11
forum: General Help
---

### Post by Hantan on 2011-12-11
Hi all,
       I'm new here and i don't know if this is the right place to state this issue but here goes. I use ubuntu 10.10 and while creating a startup disk using my 16GB usb drive, i noticed that only a few ISOs i'm able to add, the rest even if i double click on them do not show up in the source disc image column. It worked fine with a kubuntu ISO and a linux mint ISO but not with fedora and arclinux. Any idea why? Any help would be appreciated. :)

Thanks.

---

### Post by veggen on 2011-12-11
I'm just guessing here, but maybe that tool is Ubuntu specific (I think it is), and thus only works with Ubuntu and Ubuntu-based systems (like Kubuntu and Mint in your case). I know there are other tools that work with any distro, but sadly can't remember the name...

---

### Post by c.cobb on 2011-12-11
A good one is the [MultiBootUSB]("http://ubuntuforums.org/showthread.php?t=1518273") script. This is nice as it's the only setup tool I found *that doesn't format your USB stick*. This uses Grub2 which may not install successfully on all USB sticks (I dunno what boot loader the startup disk creator uses).

---

### Post by ppeterb on 2011-12-12
> **Hantan said:**
> Hi all,
       I'm new here and i don't know if this is the right place to state this issue but here goes. I use ubuntu 10.10 and while creating a startup disk using my 16GB usb drive, i noticed that only a few ISOs i'm able to add, the rest even if i double click on them do not show up in the source disc image column. It worked fine with a kubuntu ISO and a linux mint ISO but not with fedora and arclinux. Any idea why? Any help would be appreciated. :)

Thanks.
I've got a fair bit of experience - and have the same problem with both 11.10 (an upgrade) and Mint 12 (a clean install.) My .iso is newly created by remastersys and is normal in every way as far as I can see. I have placed it on the desktop and in an ordinary folder. The <Other> button finds it but nothing appears in the application source window.

I have used remastersys for two years and neither unetbootin nor write-to-dvd has ever had a problem of this nature.

The developer of remastersys tells me he does not have this problem and his new image both boots fine and opereates as a live system. So - I have no suggestion - yet. Shortly I'll give it a try with 11.04 system.

---

### Post by ppeterb on 2011-12-12
No joy here. Nothing interesting in changelog. Tried to execute usb-creator-gtk from terminal and also as root - same result. Also tried 11.04 to no joy.

---

### Post by haplorrhine on 2012-07-17
PROBLEM:  I was having problems with random freezing during installation from my flash drive.  In Startup Disk Creator, although I could select different iso files in the menu, they didn't appear in the selection bar.  11.04 was always selected, and it always went onto the flash drive, even if I selected 12.04, which I could select before I had downloaded 11.04

SOLUTION:  I moved the iso files out of my download folder with the exception of 9.10.  The next time I opened Startup Disk Creator, it was pointing at 9.10 by default.  The 9.10 installer running from my flash drive didn't seem to have the random freezing problem.

---

