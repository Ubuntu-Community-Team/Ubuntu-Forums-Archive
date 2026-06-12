---
title: "Ubuntu Won't Boot"
date: 2011-03-07
forum: General Help
---

### Post by Lennatron on 2011-03-07
Hi. I have dual booted Windows 7 and Ubuntu. I installed Ubuntu using Wubi installer a couple months ago because Windows got a virus and I thought that if Windows got destroyed I'd have an alternative. So anyway I got he virus off and Windows is back to normal but the little time I spend in Ubuntu I really liked. So now I use it occasionally and am starting to use it more. Yesterday there were a lot updates about (200MB)So I installed them. Today Ubuntu won't boot. When I start my computer I have the option to start Windows 7 or Ubuntu. I chose Ubuntu and the screen just flashes white and it brings me back to the boot screen. It never loaded Ubuntu. I don't know what is causing this. I'm very new to Ubuntu and I know there is something called Grub. On Windows there's a folder called Ubuntu. There is a sub folder called disks> Boot> Grub. The Grub is empty. I don't if its supposed to be like this or not. The last time it was modified was November 20.

Thanks for your help.

---

### Post by bcbc on 2011-03-07
See the [wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198"), problem #2, solution 1. After you get it booting, you need to apply the Permanent Fix described.

---

### Post by Lennatron on 2011-03-07
> **bcbc said:**
> See the [wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198"), problem #2, solution 1. After you get it booting, you need to apply the Permanent Fix described.

Thanks. I'll try this know. The description of the problem is exactly what I am experiencing.

---

### Post by Lennatron on 2011-03-07
On this page:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It says to boot into any Linux based operating system but the only one I have is the one that won't boot.

---

### Post by drs305 on 2011-03-07
> **Lennatron said:**
> It says to boot into any Linux based operating system but the only one I have is the one that won't boot.

Normally this is run from the LiveCD or USB from which you installed Ubuntu originally. Insert the CD or USB, let it boot, and select "Try Ubuntu". It should boot to the Desktop, where you can open Firefox, download the script and create the RESULTS.txt file.

If the CD doesn't boot, you may need to change the BIOS order so it is the first selection in the boot process.

---

### Post by bcbc on 2011-03-07
If you installed just using Wubi.exe you'll have to create an Ubuntu CD from windows (see instructions [here]("http://www.ubuntu.com/desktop/get-ubuntu/download"))

---

### Post by Lennatron on 2011-03-07
I wasn't sent a CD and I don't have it in a flash drive. I went to Ubuntu's website and downloaded it using wubi. It installed it all for so I didn't have to partitionmy hard drivemyself. Do you mean I should redownload dubious and let it install it again?

---

### Post by bcbc on 2011-03-07
Actually you still have a copy of it on your drive - but it's hidden and the name has changed. Wubi stores it in the (if I recall correctly) \ubuntu\install directory. You could just burn that to CD.

---

### Post by bcbc on 2011-03-07
Yep, here you go - I found an old thread where we confirmed that: [http://wwww.ubuntuforums.org/showthread.php?t=1663306](http://wwww.ubuntuforums.org/showthread.php?t=1663306)

---

### Post by Lennatron on 2011-03-08
> **bcbc said:**
> Yep, here you go - I found an old thread where we confirmed that: [http://wwww.ubuntuforums.org/showthread.php?t=1663306](http://wwww.ubuntuforums.org/showthread.php?t=1663306)

Thanks for finding that thread. So I use USB Write to put the .fusehidden on my flash drive but then do I try to boot from that? Also will doing so erase my existing Ubuntu but not touch Windows?

---

### Post by bcbc on 2011-03-08
> **Lennatron said:**
> Thanks for finding that thread. So I use USB Write to put the .fusehidden on my flash drive but then do I try to boot from that? Also will doing so erase my existing Ubuntu but not touch Windows?

Go to [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) , scroll to step 2, click on USB stick, and then click SHOW ME HOW. When it comes to choosing your ISO, just point it at the .fusehidden (I'd rename it to the actual ISO first to avoid confusion).

You DO NOT want to install from it... you have to boot from the USB in "live USB" mode. Which means you restart your computer, press the BIOS boot options key, then select to boot from the USB device, then you select "try it" or "try without installing". This will not affect your hard drive in any way. Then follow the instructions in the Wubi megathread on how to mount your Wubi root.disk and edit the grub.cfg file so it can boot normally. Then reboot into your Wubi ubuntu and apply the Permanent Fix.

---

### Post by Lennatron on 2011-03-08
> **bcbc said:**
> Go to [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) , scroll to step 2, click on USB stick, and then click SHOW ME HOW. When it comes to choosing your ISO, just point it at the .fusehidden (I'd rename it to the actual ISO first to avoid confusion).

You DO NOT want to install from it... you have to boot from the USB in "live USB" mode. Which means you restart your computer, press the BIOS boot options key, then select to boot from the USB device, then you select "try it" or "try without installing". This will not affect your hard drive in any way. Then follow the instructions in the Wubi megathread on how to mount your Wubi root.disk and edit the grub.cfg file so it can boot normally. Then reboot into your Wubi ubuntu and apply the Permanent Fix.

Thanks I'll do that.

---

### Post by Lennatron on 2011-03-13
Sorry it took me so long to reply. Since I don't have any documents on Ubuntu could I put Ubuntu on a flash drive and just boot over the already existing Ubuntu partition, so I can just start fresh?

---

### Post by bcbc on 2011-03-13
You installed with Wubi which uses a virtual disk so if you reinstall Wubi again it will delete that virtual disk and create a new one. 

Don't install from the USB - wubi doesn't work well with USB's. (It's OK for a partition install).

If you have an older version of the desktop ISO e.g. 10.04.1 then it won't work well with Wubi anymore either due to the way that it works (it's a bit convoluted to explain, but basically it will go and check the md5sum and download the latest ones for 10.04.2 and this will cause it to fail).

So the only way to get it to reinstall without downloading a fresh copy is to take the wubi.exe (off the ISO), put it in the same folder as the ISO you recovered, and then run wubi.exe from there with the --skipmd5check option. 
> To modify options, right-click Wubi.exe and select "Create Shortcut". Then right-click the shortcut, select Properties, and modify the Target line, for example: "C:\Documents and Settings\<user>\Desktop\wubi.exe" --skipmd5check

On top of that, when you run the Update manager it will try and take you up to 10.04.2 and the grub problem will reoccur (unless you lock the grub-* packages first).

Personally, I'd just follow the wubi megathread and try and fix it.

---

### Post by Lennatron on 2011-03-18
> **bcbc said:**
> You installed with Wubi which uses a virtual disk so if you reinstall Wubi again it will delete that virtual disk and create a new one. 

Don't install from the USB - wubi doesn't work well with USB's. (It's OK for a partition install).

If you have an older version of the desktop ISO e.g. 10.04.1 then it won't work well with Wubi anymore either due to the way that it works (it's a bit convoluted to explain, but basically it will go and check the md5sum and download the latest ones for 10.04.2 and this will cause it to fail).

So the only way to get it to reinstall without downloading a fresh copy is to take the wubi.exe (off the ISO), put it in the same folder as the ISO you recovered, and then run wubi.exe from there with the --skipmd5check option. 


On top of that, when you run the Update manager it will try and take you up to 10.04.2 and the grub problem will reoccur (unless you lock the grub-* packages first).

Personally, I'd just follow the wubi megathread and try and fix it.

Sorry I'm still a little confused. You mean that I can download Wubi again and it will get rid of the Ubuntu thats already installed right?

I tried downloading the Wubi again but it says that there is already there on my computer which it is because I didn't delete it. If I delete the folder will it cause issues?

Thanks for your patience.

---

### Post by bcbc on 2011-03-18
You can just run Wubi standalone but it will download the CD ISO again and you already have this on your computer.
So, place the Ubuntu Desktop CD ISO and wubi.exe in the same folder and run Wubi from there. 

When you run Wubi again, it will first prompt you to uninstall the existing Wubi install and this will delete any data you have under the current install.

---

### Post by Lennatron on 2011-03-18
Thanks for replying so quickly. This is what I get when I try to install it suing Wubi:
[https://picasaweb.google.com/111266105252930089281/Wubi?authkey=Gv1sRgCIOm0NKZnYfSIA&feat=directlink](https://picasaweb.google.com/111266105252930089281/Wubi?authkey=Gv1sRgCIOm0NKZnYfSIA&feat=directlink)

---

### Post by bcbc on 2011-03-18
> **Lennatron said:**
> Thanks for replying so quickly. This is what I get when I try to install it suing Wubi:
[https://picasaweb.google.com/111266105252930089281/Wubi?authkey=Gv1sRgCIOm0NKZnYfSIA&feat=directlink](https://picasaweb.google.com/111266105252930089281/Wubi?authkey=Gv1sRgCIOm0NKZnYfSIA&feat=directlink)
that's strange - normally Wubi will just uninstall the existing install. You might need to follow the [manual uninstallation instructions from the wubi guide]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?")

I wonder if you shouldn't also run CHKDSK (My Computer, right click on C:, Properties, Tools, Check disk for errors, Fix automatically). Or maybe the problem is that when you fixed Windows it removed the registry information so Wubi doesn't see it as installed anymore. In that case the manual uninstall is all you need.

---

### Post by Lennatron on 2011-03-19
Hi,

I deleted the Ubuntu folder and then Wubi worked and I successfully installed Ubuntu. I see there are about 300MB of Ubuntu updates available. Is it safe to download them or will it cause Ubuntu not to boot again?

Also the other version of Ubuntu 10.04 (The one that stopped working) is still there on the boot menu. Is there a way I can get rid of it?

Thanks

---

### Post by bcbc on 2011-03-19
It's ok to run the updates as long as you lock packages grub-pc and grub-common first. Go to synaptic, search on them, select each one, and then click on Package, Lock version.

To get rid of that extra boot entry, you need something like easyBCD or you can use Microsoft's command line tool bcdedit.

---

