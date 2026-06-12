---
title: "vga deprecated error"
date: 2010-01-13
forum: General Help
---

### Post by lepadatu.lucian on 2010-01-13
hi, i am using ubuntu karmic and its updated to the last version of kernel and grub. a few days ago i got this message at boot time: "vga=775 is deprecated. Use set gfxpayload=1280x1024x8,1280x1024 before linux command". and I cannot boot into ubuntu after this. i read some post that i have to edit /boot/grub/grub.cfg file. but how can i do this if i can't boot into the os? I bet it's an easy solution to this but i am kind of a beginner. so if anyone knows and willing to share...

---

### Post by warfacegod on 2010-01-13
When you boot up, use the recovery mode for the latest kernel header. When it's done loading, there should be a option something like "fix xorg" can't quite remember the exact name at the moment.

---

### Post by lepadatu.lucian on 2010-01-15
It seems that my ubuntu can't load the recovery mode completly. and i am not able to do anything. i tried booting using different kernel versions but still no success. I was hoping that there is a solution other than a reinstall..

---

### Post by warfacegod on 2010-01-15
You should be able to use a LiveCD to go into the /boot/grub/grub.cfg file.

---

### Post by plucky on 2010-01-15
> **lepadatu.lucian said:**
> It seems that my ubuntu can't load the recovery mode completly. and i am not able to do anything. i tried booting using different kernel versions but still no success. I was hoping that there is a solution other than a reinstall..

At the grub menu press **e** and go into grub edit mode.

Add "gfxpayload=1280x1024x8" to the same line as "quiet splash" and then continue to the boot command.

If that works and allows you to login,you have to edit "/etc/default/grub" to include that command and then "update-grub".


Good Luck

---

### Post by lepadatu.lucian on 2010-01-16
i tried to edit the boot command list as *plucky* suggested but the error persisted.
I then used the live cd to edit the file /etc/default/grub in the hope that this way will work but when i "update-grub" it says something like "grub-probe error: cannot find a device for /." 
i also tried to edit the "/boot/grub/grub.cfg" file by adding the command "set gfxpayload=1280x1024x8" (i read on another forum about this and where to insert the command) and it didn't let me save the file( the error was like "tou are accessing a read-only disk") although working as a root.

---

### Post by warfacegod on 2010-01-16
What filesystem is the hard drive?

---

### Post by lepadatu.lucian on 2010-01-16
the partition on which ubuntu is installed is ext4 i believe, the default type created by the OS at installation(i have a dual boot with windows 7 and the 2 windows partitions are ntfs)

---

### Post by warfacegod on 2010-01-16
> **lepadatu.lucian said:**
> the partition on which ubuntu is installed is ext4 i believe, the default type created by the OS at installation(i have a dual boot with windows 7 and the 2 windows partitions are ntfs)

Out of the box, Ubuntu can read and write to ext4 (obviously) but it can only read NTFS. I doubt it very much but that *could* be the issue.

---

### Post by warfacegod on 2010-01-16
Have you tried ubuntu with a different monitor?

---

### Post by Yellow Pasque on 2010-01-16
> "vga=775 is deprecated. Use set gfxpayload=1280x1024x8,1280x1024 before linux command"
I get this too. It's just a warning and shouldn't prevent booting.

---

### Post by pbrane on 2010-01-16
Normally the warning you described does not stop you from booting. I have vga=791 in my kernel command line and it works fine. With the warning of course. gfxpayload does NOT work as intended in Ubuntu. For me anyways. 

Do what plucky recommended but instead of adding gfxpayload, just remove the vga=755 from the kernel line. After that you should be able to boot normally and remove that line in /boot/grub/grub.cfg

From what you have said I guess the warning appears and then nothing happens after that? You never get to a login no matter how long you wait? On my Karmic system the warning appears for about 3 seconds and then boots normally. As I said this is normally a warning and not an error.

---

### Post by lepadatu.lucian on 2010-01-16
well, now that *plucky* mentioned it, i connected an external monitor (i have ubuntu installed on a laptop) and made the 2 working as mirror screens. i booted into ubuntu and edited the /etc/default/grub file and then updated the grub(this time it worked). next i restarted the laptop without the other monitor connected and i get the same error(vga=775 deprecated ).

no,* pbrane*, i never get to the login screen. but after connecting the other monitor the boot starts.
without the other monitor connected,i tried removing the vga=775 from boot options, i didn't get the error but it still won't get me to the login screen. so i think there's no point in editing the grub.cfg file yet.

---

### Post by pbrane on 2010-01-16
It may be that this is an Xorg configuration issue. How did you setup the dual monitor config? Have a look at /etc/X11/xorg.conf. The vga=xxx should not keep you from booting to a login screen. If X is configured for one monitor and you are using another it *may* cause problems. Like X sending output to a monitor you don't have plugged in.

---

### Post by lepadatu.lucian on 2010-01-17
i don't think this is the cause because i connected the other monitor while booted in windows. and then i unplugged it, tried to boot into ubuntu, got the error, wait some time but nothing happened and then i plugged in the other monitor and ubuntu starts booting as usual and the image appears on both monitors.

I was hoping to solve this linux style but i'm getting tired of this and it's easier for me to just reinstall the OS(only takes about 10 minutes). hope this won't happen after i do a fresh install and update the system. 

Anyway, thanks all for your help, and if I get the same error I will post it here in case you will be willing to help me again.

---

### Post by warfacegod on 2010-01-17
> **lepadatu.lucian said:**
> i don't think this is the cause because i connected the other monitor while booted in windows. and then i unplugged it, tried to boot into ubuntu, got the error, wait some time but nothing happened and then i plugged in the other monitor and ubuntu starts booting as usual and the image appears on both monitors.

I was hoping to solve this linux style but i'm getting tired of this and it's easier for me to just reinstall the OS(only takes about 10 minutes). hope this won't happen after i do a fresh install and update the system. 

Anyway, thanks all for your help, and if I get the same error I will post it here in case you will be willing to help me again.

If you are going to reinstall anyway then try erasing the contents of your xorg.conf file. With 9.10, it ships blank. If that doesn't work then, by all means, reinstall.

---

