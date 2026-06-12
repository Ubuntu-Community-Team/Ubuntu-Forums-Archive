---
title: "Grub Boot Windows XP from 2nd HDD"
date: 2010-11-30
forum: General Help
---

### Post by faithfracture on 2010-11-30
So here's my situation. I work at a university. Our machines have 2 HDD in them. Up until now, we had one drive disable and one enabled. On drive has our normal install on it which dual boots Ubuntu 10.04 and Windows 7. The second drive has the same partition scheme on it and we use it for special things, like if we need to push out a custom install of Ubuntu for something (programming contest, exams, etc). Up until this point we would simply go in and switch the active drives when we needed to do something particular so we wouldn't have to mess with our normal lab image. Now we have a situation though where we need to triple boot Ubuntu, Windows 7 and Windows XP for one particular class. We already have Windows XP installed on the second hard drive and it boots just fine when that drive is the only one enabled. However, when we enable both drives, Ubuntu and Windows 7 boot just fine, but when XP boots we get the normal Windows XP startup screen, then it gets into a screen where it gives a message saying "autocheck program not found. skipping autocheck", then I get a quick flash of a screen that looks like a blue screen and the machine reboots.

The following is in the 40_custom grub configuration script:

```

menuentry 'Microsoft Windows XP' {
        insmod ntfs
        set root='(hd1,2)'
        drivemap -s (hd0) ${root}
        chainloader +1
}

```We've tried a bunch of different ways to get this to work and the result is either the same as what I previously described, or we get a "Disk read error, press ctrl-alt-del to reboot" message.

It seems that we're on the right track here, but that something is missing and we aren't sure what it is. My guess is that Windows XP is expecting itself to be located on drive C:, but because it is now located on the 2nd hdd, it is mapping the drive it's actually installed on as a different drive there, which is why it can't find what it needs to boot.

We've also tried doing:
```

drivemap (hd0)(hd1)
drivemap (hd1)(hd0)

```instead of:
```

drivemap -s (hd0) ${root}

```but that gives the same blue screen reboot result.

Does anyone have an idea of what we might be missing here?

---

### Post by galvatron408 on 2010-11-30
here are a few things you could do to get more info for yourself.

#1 - get yourself in to your XP OS an tell XP not to reboot on fatal errors. You can do this from the control panel and system settings (I don't have XP so can't tell you exactly but look around, it's a check box)Once this is set, when XP crashes on boot up, you'll actually get to see the error. Hopefully that will take you to where you want to be.

#2 - instead of adding your own custom menu entry, use "grub-mkconfig" and it will probe all your disks for an OS. 

Hey, look.... it found Vista on my laptop!

Found Windows Vista (loader) on /dev/sda1
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set eaee-eb49
	chainloader +1
}

---

### Post by Quackers on 2010-11-30
If you boot up the Ubuntu system and run sudo update-grub it should pick up all other operating systems on the machine - unless the 30_os-prober has been switched off.

---

### Post by oldfred on 2010-11-30
Since your second drive was always configured as the first drive, is the boot.ini still referring to drive 0? 

I am not sure drivemap works the way we think, but it may not convert the drive to drive 0.

Is the boot complete in the XP partition. Windows usually combines boots into one even from two drives, so you only can boot windows thru one windows partition. XP can be repaired to boot independantly, but you have to be careful that then it does not include the win7 partition and copy its boot loader to the XP partition.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by faithfracture on 2010-12-01
galvatron, your suggestion to tell XP to not reboot on fatal errors did the trick... I didn't have to change anything else. I just booted XP, switched that off, and then tried to boot from grub again and it worked. That doesn't really make any sense to me. I was expecting that I would just get to the blue screen and see the error.

I did try using 30_os-prober, but I had the same blue screen / reboot situation. On top of that, we can't use the os-prober because we have other things on the drives that we don't want available to users all the time. We have a number of different boot partitions that we push out to different labs depending on the labs purpose. As cool as the new grub2 scripting stuff is, it just doesn't work for how we have our environment set up here, so we just write our menu entries in the 40_custom script and keep it simple.

So, I can't really explain why it's working now, but setting XP to not reboot on fatal errors, for whatever reason, fixed the problem and the system is working like I need it to now.

Thanks for the help!

---

