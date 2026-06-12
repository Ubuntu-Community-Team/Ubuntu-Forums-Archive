---
title: "How to boot windows in virtualbox?"
date: 2010-02-12
forum: General Help
---

### Post by lakelovers on 2010-02-12
I have VirtualBox installed as well as Wine, and I want to run Windows from the VirtualBox (Ubuntu 9.04 is my OS). VirtualBox won't start because "no bootable medium found." Another words I don't have an OS on VirtualBox. How do I get Windows install on VirtualBox, or how do I get Windows to boot through Wine in VirutalBox?

---

### Post by jken146 on 2010-02-12
WINE is for running Windows programs *within linux*. Virtualbox is for running a fake computer (virtual machine).

If you want to run Windows in Virtualbox, then you'll want to create a virtual hard disk (this is done with the wizard when you make a new virtual machine) and then install Windows on it.  You'll need Windows installation media (e.g. CD or CD image), which you'll need to point Virtualbox at before you start the VM.

---

### Post by lakelovers on 2010-02-12
I believe I have done both. I created the virtual hard disk when I installed VirtualBox, and I have downloaded a CD ISO which appears on the VirtualBox. Also, I have set the virtual CD as the first boot device. I'm still getting that message that there is "no bootable medium found." I'm doing something wrong or I'm missing something. What do you suggest?

---

### Post by jken146 on 2010-02-12
Check your steps again. Make sure that you really have told virtualbox to mount the ISO.

If that's all set up correctly, and you still have no luck, it could be the ISO itself.

---

### Post by lakelovers on 2010-02-14
I'm trying to install WindowsXP from a cd into VirtualBox and I reached a screen to select the partition to install XP. I stopped because I'm no sure which to select and afraid the setup will format a partition endangering my "/" partition or some other. I need advice.

---

### Post by nos09 on 2010-02-14
> I'm trying to install WindowsXP from a cd into VirtualBox and I reached a screen to select the partition to install XP. I stopped because I'm no sure which to select and afraid the setup will format a partition endangering my "/" partition or some other. I need advice.

dont worry about anything in virtual box. in virtualbox as the name says its virtual it would not harm your computer.
and did you ever installed widows on any of your computer then its the same way to install in virtualbox and if not then " [http://www.buildeasypc.com/sw/windows_xp.htm](http://www.buildeasypc.com/sw/windows_xp.htm) " follow the link to see how to install it. and if you want the vedio then "http://www.metacafe.com/watch/795442/how_to_install_windows_xp/"

good luck..

---

### Post by lakelovers on 2010-02-14
I'm back. . .
I stopped the XP installation, then after reading your post I started up again but kept getting the message "error booting the os" or something like that. It appears that the VirtualBox is not seeing the CD. I have placed the CD in the first boot position but I still get the error message. I've installed XP before but it has been a long time. I'll look at the links you posted. However, if you have an idea where I'm going wrong let me know. Thanks.

Edit: Retry Report: Well, I'm about ready to give up. I got back into the XP installation by "resetting" in the device menu. So, thinking I was on the way, everything proceeded until nearly the end of the installation when an error message popped up saying: "Invalid parameter was pass to a service or function." I tried re-installing a couple of times and reached the same point of the error.

---

### Post by mharrison on 2010-02-14
> **lakelovers said:**
> I'm back. . .
I stopped the XP installation, then after reading your post I started up again but kept getting the message "error booting the os" or something like that. It appears that the VirtualBox is not seeing the CD. I have placed the CD in the first boot position but I still get the error message. I've installed XP before but it has been a long time. I'll look at the links you posted. However, if you have an idea where I'm going wrong let me know. Thanks.

Have you mounted the CD drive or ISO image in Virtualbox, as setting the CD drive to boot first is meaningless unless you have a CD or ISO image mounted to the drive...this can be done by click on Devices, and then selecting either the CD Drive the XP CD is in, or selecting the ISO image.  You may have to click on More CD/DVD Images and browse to find the ISO.

HTH

---

### Post by Easy Limits on 2010-02-14
It really is quit simple.

Open VB.  Stick your XP disc in to the drive.  Then select New in the top left corner of VB then follow the Wizard.

---

### Post by lakelovers on 2010-02-15
I may have a faulty CD. I still get the error message that "lsass.exe cannot be found" then the installations stops. I'm using a reinstallation CD that came with my computer, and in the dark corners of my fuzzy brain I seem to recall that when I used this CD before, I had to enter a purchase key/number. I have a number but I can't be sure that it's the required #, and I haven't seen any place to insert a number during my attmepts at installing XP. I originally down loaded a Windows ISO which I couldn't get to load in VB. I'd try it again but I can't remember how I initiated the ISO within VB and now I don't see that option.

---

### Post by Raik.48 on 2010-02-15
After creating a virtual hard drive, you will see a name that you have chosen for your operating system, you can right click> setting>CD-DVD>and check the mount cd dvd drive. 

it seems that the copy of xp you use is cracked one, so serial key asking is always not the case, sometime it does and sometime it doesn't. You fault seems to be on the cd of windows xp. try changing the cd.

---

### Post by lakelovers on 2010-02-15
Still looks like am whacked. I don't have another WinXP, and apparently, the one I have cannot be copied. I started looking for a free iso but didn't come up with any though I read that Mircosoft has released the XP for free downloading.

---

### Post by nos09 on 2010-02-20
download it form any torrent. and you are using it in virtual-box no one is gonna know about it that its not registered.

---

