---
title: "Horrible Ubuntu or horible Windows ?"
date: 2012-03-10
forum: General Help
---

### Post by Ubuntter on 2012-03-10
Hi,

I've installed (tried to install) Ubuntu on USB drive in  Windows 7 environment using Unetbootin.
After installation, Ubuntu has changed the date and time setting!
When reboot, I have multiple choices between Linux 2.3 (not Ubuntu?!!), Memory test, Windows loader (not windows 7 !!!)...etc. 
I am not familiar at all with Ubuntu and I think it is not for me! 
Now, I would like to completely remove it without trouble with Windows but I don't find the trick! 
I searched in the windows installed program list but it is not there! 
So my question, how can I remove Ubunto after I installed it from USB drive, alongside with Windows? 
On the USB drive I find Wubi and when click on it, I have the choice to install Ubuntu, not to uninstall it!!

Pleas tell me how to remove Ubuntu peacefully !!
 
Thanks

---

### Post by sudodus on 2012-03-10
Hi Ubuntter :-)

Take it easy for a while. There is no reason to panic.

> When reboot, I have multiple choices between Linux 2.3 (not Ubuntu?!!), Memory test, Windows loader (not windows 7 !!!)...etc. 

I think you are looking at the grub menu. You select line with the arrow keys and start with the Enter key.

- 'Linux 2.3' points to Ubuntu
- 'Memory test' points to a mini program dedicated to test that your RAM is healthy.
- 'Windows loader' points to Windows 7

You can get used to that, and if you don't like it, later on you can edit the grub menus to get whatever text you prefer. See
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1195275_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")

So I suggest that you try and see what happens when you select the various options in the grub menu. And later on maybe you want to remove Ubuntu. At that stage, don't just remove it, make sure you have the right tools and commands to be able to boot Windows afterwards!

---

### Post by Ubuntter on 2012-03-10
> **sudodus said:**
> Hi Ubuntter :-)

Take it easy for a while. There is no reason to panic.

 

I think you are looking at the grub menu. You select line with the arrow keys and start with the Enter key.

- 'Linux 2.3' points to Ubuntu
- 'Memory test' points to a mini program dedicated to test that your RAM is healthy.
- 'Windows loader' points to Windows 7

You can get used to that, and if you don't like it, later on you can edit the grub menus to get whatever text you prefer. See
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1195275_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")

So I suggest that you try and see what happens when you select the various options in the grub menu. And later on maybe you want to remove Ubuntu. At that stage, don't just remove it, make sure you have the right tools and commands to be able to boot Windows afterwards!

Thanks sudodus.

Actually, I wished to install Ubuntu completely and independently on USB drive but this is not possible apparently! It always uses/needs Windows resources on C drive! 
I thought it should be possible to install Ubuntu on an external USB drive without need to Windows resources!
But definitely, you are right! Linux 2.3 pointed to Ubuntu and Windows loader to Windows 7.
However, I don't see any tool to uninstall Ubuntu safely, neither when I reboot with Windows 7 nor with Ubuntu!
So, what is the right mode to uninstall Ubuntu and eventually re-install it side by side with windows or in a virtualbox?

---

### Post by stn21 on 2012-03-10
> **Ubuntter said:**
> Hi, I've installed (tried to install) Ubuntu on USB drive in  Windows 7 environment using Unetbootin.

From where exactly do you want to remove ubuntu ? USB-Drive or harddisk?

Unetbootin installs ubuntu on your USB-stick. It does **not** normally install ubuntu on your harddisk, at least not without intentionally activating some additional options. So, how did ubuntu get on your harddisk?

---

### Post by dandnsmith on 2012-03-10
There is one added bit of information you need to supply in order for a proper answer to your question - if you boot the system without the USBdrive in place do you see the grub choices menu?

a) if 'yes', then you need to repair the boot setup from Win7, and nothing else is need to complete the uninstall (except for wiping the USBdrive)

b) if 'no', then there is nothing to remove from the HDD, all you need is to wipe the USBdrive

Eventual re-installation depends on how you want the resultant to look - there will be different methods for side-by-side installation on your HDD, and installing in a virtualbox.

---

### Post by sudodus on 2012-03-10
> **Ubuntter said:**
> Thanks sudodus.

Actually, I wished to install Ubuntu completely and independently on USB drive but this is not possible apparently!

Indeed it is!
> 
It always uses/needs Windows resources on C drive!

If it is a wubi install, otherwise it is independent of Windows. Is there a /host directory (partition) seen from Ubuntu?
>  
I thought it should be possible to install Ubuntu on an external USB drive without need to Windows resources!

This is normal with Unetbootin (as told in an earlier post).
> 
But definitely, you are right! Linux 2.3 pointed to Ubuntu and Windows loader to Windows 7.
However, I don't see any tool to uninstall Ubuntu safely, neither when I reboot with Windows 7 nor with Ubuntu!
So, what is the right mode to uninstall Ubuntu and eventually re-install it side by side with windows or in a virtualbox?
Browse the internet for ***windows 7 repair boot*** and read for example [[COLOR="Red"]_http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html_[/COLOR]]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html")

---

### Post by Ubuntter on 2012-03-10
Thank you all for your answers.

> **dandnsmith said:**
> 
a) if 'yes', then you need to repair the boot setup from Win7, and nothing else is need to complete the uninstall (except for wiping the USBdrive)

Yes indeed, I have grub menu when I reboot without the USB drive! 
What do you mean by "repair the boot setup"? 
How to repair it? 

Thank you 

Regards,

---

### Post by stn21 on 2012-03-10
> **Ubuntter said:**
> ... Yes indeed, I have grub menu when I reboot without the USB drive! 
How did that happen? Unetbootin normally does not do that. Did you maybe click on "show all drives" in unetbootin and then selected C: ?


> What do you mean by "repair the boot setup"?  ...
Boot your windows 7-dvd, on the first or second screen you can select further options, like boot-repair

---

### Post by Ubuntter on 2012-03-10
Ooh sorry! I didn't see the post of sudodus!
Well, I'll try to repair it with windows ".exe" file! 

Thanks

---

### Post by Ubuntter on 2012-03-10
> **stn21 said:**
>  How did that happen? Unetbootin normally does not do that. Did you maybe click on "show all drives" in unetbootin and then selected C: ?

I don't know how it happened but I'm sure I choose the USB drive as installation target!

> **stn21 said:**
> 
Boot your windows 7-dvd, on the first or second screen you can select further options, like boot-repair
I don't have DVD! I have only .exe file. 
When I try to re-install windows, it propose me to re-install from scratch! This is not what I need! 
Strange!

---

### Post by stn21 on 2012-03-10
By the way: the most reliable way to get your windows bootable again is to install ubuntu beside windows, using either a bootable stick (you may already have one) or an ubuntu-cd. That will automatically get you a boot-menu where you can select windows and ubuntu.

In ubuntu's installer you have the option to shrink the windows partition and install ubuntu beside windows. 

Careful: Do **not** choose "wipe the whole harddisk".

The "boot repair" or windows I have found to be unreliable. And you can still do that later if you feel the need...

---

### Post by Ubuntter on 2012-03-10
> **sudodus said:**
>  Indeed it is!

This was not the case for me!

> **sudodus said:**
> 
If it is a wubi install, otherwise it is independent of Windows. Is there a /host directory (partition) seen from Ubuntu?

Actually, when I used Unetbootin, I had Wubi file in the USB
drive, and on Ubuntu desktop I also have the Install file too!
All files and folder I created were deleted when I reboot Ubuntu!
This means that it was not installed on USB drive but it was an image, or just virtual installation!

---

### Post by Ubuntter on 2012-03-10
> **stn21 said:**
> By the way: the most reliable way to get your windows bootable again is to install ubuntu beside windows, using either a bootable stick (you may already have one) or an ubuntu-cd. That will automatically get you a boot-menu where you can select windows and ubuntu.
...

Initially, I wanted to have Ubuntu installed on USB drive, not as side-by-side with windows! 
If so, I will have the boot menu choices only if I insert the USB drive, on which Ubuntu was installed! This is not the case for now!
I probably missed the trick!

---

### Post by Ubuntter on 2012-03-10
I just add, when I use Windows 7 installer file (.exe) (bought from Microsoft store), it does not proposes "repair boot or startup errors", rather it proceeds for Windows 7 installing from scratch or upgrade!

---

### Post by stn21 on 2012-03-10
> **Ubuntter said:**
> Initially, I wanted to have Ubuntu installed on USB drive, not as side-by-side with windows! ...

Let me clear up how this works.

Unetbootin does not "install ubuntu", not on USB nor elsewhere. It creates a bootable USB-stick that will work exactly like the ubuntu-live-cd you can burn with an ISO-download from ubuntu.com.

So if you want to install ubuntu you 

1) first have to create a bootable medium, either your stick or a live-cd. You can create a stick with unetbootin.

2) Then you boot that usb-stick (or cd)

3) Then on your desktop you will find "install ubuntu"

That way you can in principle install ubuntu on a USB-stick or an external USB-harddrive. I have done that occasionally myself. But: you need another stick for that. Your boot-stick is already taken by the live-system.

I suggest that it may be less confusing to burn and boot a live-cd. You can boot that and work almost like with an installed ubuntu and it disappears completely once you take out the CD.

And later you can use the startup-creator to make a bootable USB-stick that will even allow you to install software and make changes to the system. You cannot AFAIK do that with a stick created with unetbootin, only ubuntu itself can do that. This stick also will not change your harddisk and will completely disappear once you remove it.

---

### Post by stn21 on 2012-03-10
On the matter of general frustration with ubuntu:

Unetbootin and similar programs and ubuntu-live-cd are very safe ways of trying ubuntu and none of them will normally change anything on your  harddisk, especially not anything related to booting windows.

I cannot explain what happened on your computer but I can assure you  that you were on the right track and you simply had some unfortunate  incident. Next time try a live-cd and you may find yourself with linux  being a new friend for life :smile:

---

### Post by matt_symes on 2012-03-10
Hi

> After installation, Ubuntu has changed the date and time setting!

To address the above point, Ubuntu uses UTC time and Windows uses local time. That is the reason for the change in your clock settings.

Ubuntu can be configured to use local time with the command

```
sudo hwclock --localtime
```

I am not sure if this will survive a reboot on a USB stick though. You may want to create a persistent USB stick.

Don't panic. Ubuntu is new to you, that is all. There are plenty of people on these and other forums who are prepared to help out other users.

Stick with it and don't be afraid to post any questions.

Kind regards

---

### Post by The Cog on 2012-03-10
This article describes how to replace the MBR.
[http://ubuntuforums.org/archive/index.php/t-194340.html](http://ubuntuforums.org/archive/index.php/t-194340.html)

Note that I haven't tried this myself. I can't imagine ever wanting to remove Linux to make Windows work.

Interestingly, testdisk is in the Ubuntu repositories, so you could presumably run Ubuntu, install testdisk, replace the MBR and reboot straight into windows. Then all you have to do is delete the unanted Ubuntu partitions.

---

### Post by sudodus on 2012-03-10
Hi again Ubuntter,

After reading all the posts, I think that there is a lot of confusion. In order to help you, we need more information about your current situation. It might even be the case that you have a good installation of Ubuntu, that works, and that there is no need to reinstall. Maybe it was 'too easy' to install it, so that you did not realize that you had succeeded. But it might also be something that you don't want.

Anyway, are you familiar with the command line terminal in Ubuntu? You start it with ***ctrl + alt + t*** (press all 3 keys at the same time). Then you type commands and start executing them when you press the ***Enter*** key. ***Please run the following commands and post the output*** (result) in a reply. You can copy and paste between the windows and put code tags around that text (use the # icon above your editing window)
```
sudo fdisk -lu
```
```
df
```
```
sudo blkid
```
```
ls -l /host
```

---

### Post by Mark Phelps on 2012-03-11
You're not telling us the name of the ".exe" file you're running, so without that, we can't provide you any advice.  We're not mind readers here.

Since you apparently have GRUB loaded to your MBR, you should look into the information on Boot-Repair:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

That has been used to repair Win7 boot problems.

---

