---
title: "Triple Boot Problem"
date: 2010-10-08
forum: General Help
---

### Post by Shadow21 on 2010-10-08
I'm trying to triple boot Windows 7, Ubuntu, and BackTrack. I installed Windows 7 and Ubuntu first and everything was working correctly but after I installed BackTrack the GRUB messed up and it displayed six different Ubuntu options (it usually displays three) but no BackTrack options. When I select one of the first three Ubuntu options it boots into Backtrack and when I select one of the other three Ubuntu options it says "Error 15; File not found". I'm not able to boot into Ubuntu at all after installing Backtrack.

I tried uninstalling Grub and reinstalling it from the Ubuntu Live CD but it was still messed up.

Is there anything that I can do to make Grub work with Windows, Ubuntu, and BackTrack?

---

### Post by DeMus on 2010-10-09
> **Shadow21 said:**
> I'm trying to triple boot Windows 7, Ubuntu, and BackTrack. I installed Windows 7 and Ubuntu first and everything was working correctly but after I installed BackTrack the GRUB messed up and it displayed six different Ubuntu options (it usually displays three) but no BackTrack options. When I select one of the first three Ubuntu options it boots into Backtrack and when I select one of the other three Ubuntu options it says "Error 15; File not found". I'm not able to boot into Ubuntu at all after installing Backtrack.

I tried uninstalling Grub and reinstalling it from the Ubuntu Live CD but it was still messed up.

Is there anything that I can do to make Grub work with Windows, Ubuntu, and BackTrack?

Maybe you have to install Windows first, then Backtrack and finally Ubuntu so the Grub which comes with Ubuntu will take over control of the boot process. For now it would be sufficient, I guess, to re-install Ubuntu on the same partitions (or disk) you installed it already so when Grub is installed it will look for other OS'ses and include them in the boot list.
If that doesn't work then maybe you have to start all over, but still use the order: Windows, Backtrack, Ubuntu.
Success.

---

### Post by andrewthomas on 2010-10-09
Are you sure you reinstalled grub correctly?

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Backtrack is ubuntu/debian based so grub should pick it up

Boot a live CD and go to 

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

follow the instructions and reply with the results

---

### Post by Shadow21 on 2010-10-09
I'm pretty sure I reinstalled grub correctly because I followed [this]("http://ubuntuforums.org/showthread.php?t=224351") guide.

I'm wondering if I'd be able to manually correct the problem by editing the GRUB file and adding the Ubuntu partion.

I'll try what DeMus recommended if I can't correct it manually.

---

### Post by andrewthomas on 2010-10-09
> **Shadow21 said:**
> I'm pretty sure I reinstalled grub correctly because I followed [this]("http://ubuntuforums.org/showthread.php?t=224351") guide.

I'm wondering if I'd be able to manually correct the problem by editing the GRUB file and adding the Ubuntu partion.

I'll try what DeMus recommended if I can't correct it manually.
That guide is for legacy grub.  Use the links that I posted.

---

### Post by Shadow21 on 2010-10-09
> **andrewthomas said:**
> That guide is for legacy grub.  Use the links that I posted.


Here's the results from the bootinfo script.

---

### Post by andrewthomas on 2010-10-09
Your backtrack partition has control of the mbr.  If I were you I would follow this link

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

and booting from the live cd.  Follow the instructions in the above link,  using

```
sudo mount /dev/sda3 /mnt
```and
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```and put grub2 back in control of your MBR.

---

### Post by Shadow21 on 2010-10-09
> **andrewthomas said:**
> Your backtrack partition has control of the mbr.  If I were you I would follow this link

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

and booting from the live cd.  Follow the instructions in the above link,  using

```
sudo mount /dev/sda3 /mnt
```and
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```and put grub2 back in control of your MBR.

Now I can boot into Ubuntu but there is not an option to boot into BackTrack on the Grub menu.

---

### Post by andrewthomas on 2010-10-09
```
sudo update-grub
```

when booted into ubuntu

---

### Post by Shadow21 on 2010-10-09
> **andrewthomas said:**
> ```
sudo update-grub
```

when booted into ubuntu

That added BackTrack but it named it Ubuntu for some reason but I guess I can just change that in the Grub menu file.

Thanks for the help! :)

---

### Post by andrewthomas on 2010-10-09
Glad to be of help.

Grub might parse /etc/issue or /etc/issue.net to get the info from Backtrack, you really shouldn't edit grub.cfg so you might be best off looking in those files in backtrack and editing there.

Or maybe it might look at /etc/lsb-release

---

### Post by Shadow21 on 2010-10-17
Thanks for the help :)

---

