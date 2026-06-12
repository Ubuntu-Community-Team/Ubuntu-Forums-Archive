---
title: "chainload GRUB2 from NTLDR"
date: 2010-07-02
forum: General Help
---

### Post by alienkid10 on 2010-07-02
My internal is sda windows = sda1 recovery = sda2
my external is sdb storage = sdb1 linux sdb2

GRUB is on sdb2's first sector. I tried coping it to grub.mbr on  sda1 and added C:\grub.mbr="ubuntu linux" all I get when selecting it is _ blinking and no booting. USB booting from BIOS works but I don't want family to have to mess with unplugging and replugging it when they want to boot to Windows. I also tried installing GRUB2 to MBR of sdb and copying same problem. Can anyone help? Please do not question the way I do it unless you need to know to help. It's the way that I want to do it if all you're going to do is complain about my set-up don't post.

see post 13 for new question.

---

### Post by oldfred on 2010-07-03
I am not posting.

But you can make windows the default on the external and set the time down to 3 seconds (you have to be  quick to get to Ubuntu) and everyone else gets to windows without any issue or even having to make a choice. With the mbr bin you still have to choose in windows boot.ini or BCD.

---

### Post by synapsys on 2010-07-03
> **oldfred said:**
> I am not posting.

But you can make windows the default on the external and set the time down to 3 seconds (you have to be  quick to get to Ubuntu) and everyone else gets to windows without any issue or even having to make a choice. With the mbr bin you still have to choose in windows boot.ini or BCD.

That's just plain confusing.

The way I see it you have 3 choices.

1. Download EasyBCD for windows (i think thats what oldfred was talking about) and set it up to be able to boot your ubuntu and windows partitions. 

2. Install GRUB to sda (when installing it will automatically detect windows and ubuntu) then set windows as the default.

3. Set your bios to boot from the external, set windows to default in GRUB.

PS I am going to complain about your setup.... you'd be better off getting a 2nd internal drive and using that for Ubuntu and make the external all storage. An internal hard drive with a SATA connection will work faster than an external through USB, it will also run cooler because the inside of your computer has fans blowing all around. With the frequency you need to access that external drive just to run ubuntu it's really going to heat it up and if that hard drive dies, so does the storage.... just something to think about....

---

### Post by artemyv on 2010-07-03
> **synapsys said:**
> 
1. Download EasyBCD for windows (i think thats what oldfred was talking about) 

I think he is talking about the option

> USB booting from BIOS works 

- Select this option by default
- in grub - select booting windows by default
- ...

---

### Post by alienkid10 on 2010-07-03
GRUB default might work. I didn't buy an internal for a few reasons, 1. I didn't have cables to set it up 2. I have not clue what type of HDD I would need for it and 3. some people have parents that won't let them (even on another HDD) do anything close to installing Linux.

The other is would it be possible to take this drive to another computer to boot and have it boot correctly (just wondering)

Reason I want NTLDR is again parents don't want me messing with the BIOS setup.

@[synapsys]("http://ubuntuforums.org/member.php?u=850688"): 2. and when the drive is not present?

---

### Post by oldfred on 2010-07-03
I am not a fan of adding another boot loader (easyBCD) into the mix as that just adds more confusion. You still have to choose what to boot on start up.

With #2 you cannot boot without the external. You would have to add a grub partition to the internal to make it work.

Choice #3 is what I recommend. Changing boot order in BIOS is no big deal. If external is not there it just defaults to the internal. With grub in the external it will let you boot if plugged into another system. And with grub set to boot windows, you get windows no matter what without any selection.

---

### Post by alienkid10 on 2010-07-03
how to set GRUB2 default to sda1 (WIN)? I am not going to mark solved yet I know it's possible I just need someone who does it to tell me how. Also just a little thing can I make GRUB2 not add sda2 (RECOVERY) to the menu?

---

### Post by oldfred on 2010-07-03
the easy way tochange what boots:

Startup manager in synaptic will allow you to set boot default and the timeout even in lucid.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.

the less easy but fully customized If you want to edit names the easiest is to just copy them to 40_custom:
Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)
OR Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

---

### Post by alienkid10 on 2010-07-03
with OS_Prober disabled will the Kernel updates not be added to GRUB menu?

---

### Post by synapsys on 2010-07-03
> **oldfred said:**
> I am not a fan of adding another boot loader (easyBCD) into the mix as that just adds more confusion. You still have to choose what to boot on start up.


EasyBCD is NOT a boot loader, it simply modifies boot.ini in windows so you don't have to.

---

### Post by oldfred on 2010-07-03
With os-prober disabled it does not find other systems. So only if you install a new operating system would you have to turn it one again, if you want it to give you the entry. The Ubuntu updates still work. It prevents duplicate entries from the prober and your manual entries in 40_custom.

---

### Post by alienkid10 on 2010-07-03
EasyBCD is for Vista not NTLDR/XP isn't it?

---

### Post by alienkid10 on 2010-07-18
Ok got it to work.

How:

Install Ubuntu to sdb2/hd1,1 formatted as ext3(4 would probably work)
at the final screen click advanced and have bootloader install to sdb
reboot to Windows and download GRUB4DOS place grldr at the root of C: make a menu.lst at the root of C: then add ```
timeout 0
default 0
title grub2
kernel (hd1,1)/boot/grub/core.img
boot
```

add ```
C:\grldr="Ubuntu"
``` to the last line of boot.ini
reboot
at the NTLDR menu pick Ubuntu after a few seconds it will show GRUB then boot Ubuntu. Only problem is I don't see boot splash or and boot info it just stays black until GDM/desktop.

---

