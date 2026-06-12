---
title: "&quot;fixing&quot; MBR broke my entire boot sequence"
date: 2010-05-30
forum: General Help
---

### Post by Biopyro on 2010-05-30
I installed windows yesterday, which stopped me booting into windows. I was advised I needed to fix the MBR, and I did so using the instructions here.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Unfortunately, when I boot up I now get a cli which lists a bunch of options, which I don't really understand.
[http://i50.tinypic.com/2zqrh4i.jpg](http://i50.tinypic.com/2zqrh4i.jpg)
I am running windows 7 enterprise on its own partition, and my normal OS is Ubuntu 9.04. I appear to have Grub 1 as I have menu.lst in the grub folder..
I'd like to be able to choose to boot into either windows or Ubuntu at startup.
I am currently working on a 10.04 live usb

---

### Post by inso_741 on 2010-05-30
can you boot into any of the os?
if not reinstall grub from a live cd

---

### Post by Biopyro on 2010-05-30
I just get that screen, since I reinstalled grub. Before I followed those instructions it just booted straight into windows.

---

### Post by ankspo71 on 2010-05-30
Hi, the link you gave says this:
> If you downloaded Ubuntu Karmic 9.10 Live CD, but your installed version of Ubuntu uses Grub Legacy, go back to the beginning and download Ubuntu Jaunty 9.04 CD. Continue with instructions for Grub Legacy. 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

You won't be able to use the Ubuntu 10.04 cd because it is using grub2, so you will need to download and run Ubuntu 9.04 (aka Jaunty). I assume it says that because Grub 1 (grub legacy) can't be reconfigured correctly by grub2. If I remember correctly, grub 2 differs greatly from grub legacy because it is a complete rewrite in code.

Just in case you need to get into windows to burn another cd/usb image:
Here is a microsoft link that explains how to restore your windows mbr using a windows cd  [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Hope this helps.

---

