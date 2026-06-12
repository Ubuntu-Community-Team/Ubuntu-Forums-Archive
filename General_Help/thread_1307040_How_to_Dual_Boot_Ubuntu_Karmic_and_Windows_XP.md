---
title: "How to Dual Boot Ubuntu Karmic and Windows XP"
date: 2009-10-30
forum: General Help
---

### Post by arepaking on 2009-10-30
Hi Folks,
I have two hard drives: 

sda -> Runs Ubuntu Karmic
sdb -> Runs Windows XP Pro

Does anyone knows how can I dual boot this two hard drives under Grub2?

I was using Jaunty with the following menu.lst for my windows hard drive and always worked flawless for me:

```
title         Windows XP Pro
root        (hd1,0)
savedefault    
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader     +1
```

I know that I need to modify /etc/grub.d/40_custom but I tried to copy the code above and it did not work. 

Any ideas?

Thanks in advance,
AK

---

### Post by KinKiac on 2009-10-30
Ive always found the easiest way is to just install windows first.  Then install ubuntu and Grub will take care of itself, at least it did for me last night on a a sony vaio that was simply partitioned into 2 100gig sections, 1 for windows and one for ubuntu.

---

### Post by teward on 2009-10-30
Use the live CD to reinstall GRUB automatically (if you have one).

Otherwise, couldn't you just use something like Super Grub Disk to reinstall the GRUB bootloader?

---

### Post by arepaking on 2009-10-30
Thanks folks for your reply.

Two things:
- I am using two hard drives in this scenario. No dual boot partitions. I need to run windows and ubuntu on differents hard drives.

- Grub2 is working fine I just need to add some unknown parameters into 40_custom so Grub2 can be able to boot windows on a separate hard drive.

Thanks in advance for your feedback.

---

### Post by claymater on 2009-10-30
> **KinKiac said:**
> Ive always found the easiest way is to just install windows first.  Then install ubuntu and Grub will take care of itself

Agreed, I have 2 drives and windows is on one, ubuntu is on the other. 

Works like a charm! ;)

---

### Post by darkksyde on 2009-10-30
correct me if im wrong but if you have two hard drives and your mobo allows it, cant you just press F8 or F12 and select the hard drive in which either linux or windows xp is installed and boot like that?

---

### Post by 46jeepster on 2009-10-30
Being that i'm not very computer savy, i decided to use the F12 button to do a dual boot until i can develop a better understanding of grub. I just got a new pc from Walmart yesterday with Win 7 installed. Opened it up,discvonnected the Win7 drive,hooked up a second drive.Turned it on and set the boot order to boot the second drive first. Installed Ubuntu on the second drive. Made sure that Ubuntu worked ok then turned the pc off, hooked the Win7 drive back up. Now if i turn it on, Ubuntu will boot without doing anything, If i need to use Win7, I press the F12 key on startup and the boot option screen shows up. I can select the Win7 drive to boot or any other Drives that i may install later. I know the experts can do all this with grub but its still a little complicated for me right now. Its been working good though and i'm having a lot of fun with Ubuntu.

Emachines ET1331G-03W

---

### Post by arepaking on 2009-10-30
Sorry fellas but my MoBo does not support the F8 or F12 to select either hard drive...

---

### Post by phillw on 2009-10-31
> **arepaking said:**
> Sorry fellas but my MoBo does not support the F8 or F12 to select either hard drive...


I've come into this thread quite late.....

try [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

As to the buttons to get the BIOS boot sequence up, it's F2 or 'esc' most time.

Phill.

---

### Post by arepaking on 2009-10-31
Thanks phillw, 
But these instructions are for GRUB... Karmic has GRUB2 defaulted and my hard drives are SATA. I looked over your information but they reference the old GRUB. I don't think is applicable to Karmic...

---

### Post by QIII on 2009-10-31
Try this:

```
sudo apt-get install os-prober
```

```
sudo os-prober
```

```
sudo update-grub2
```

---

### Post by arepaking on 2009-10-31
This is what I got:

sudo os-prober:
```
/dev/sdb1:Microsoft Windows XP Professional:Windows:chain
```



sudo update-grub2:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

done

```

Check this out: My Windows HD is sdb1 but for some reasons the grub.cfg shows the following:

```

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

```

Why (hd0)? Shouldn't be (hd1,1)?

---

### Post by arepaking on 2009-10-31
I finally got it to work. Here is how:

1) Since 30_os-prober did not see the drive correctly I decided to disable by executing:

```
sudo chmod -x /etc/grub.d/30_os-prober
```

2) I added the following entry to 40_custom:
```

menuentry "Microsoft Windows XP Professional" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set B458A94158A9036A
    drivemap -s (hd0) ${root}
    chainloader +1
}

```
And it work like a charm. Now, I don't know if Karmic is flying on my PC but I noticed that WinXP was slower. I don't think that this GRUB2 config/mapping could affect the performance for the other hard drive.. isn't???


Thank you all for your help.

---

### Post by KinKiac on 2009-10-31
> **darkksyde said:**
> correct me if im wrong but if you have two hard drives and your mobo allows it, cant you just press F8 or F12 and select the hard drive in which either linux or windows xp is installed and boot like that?

Unfortunately, if your Ubuntu is loaded on to hd(0), and you load windows on to hd(1)(or however the labels go)- windows will still load its boot loader on to hd(0) and completely overwrite your MBR and grub, leaving you with a system that only loads windows.  I made that mistake on my last install of 9.04 when I decided after having 9.04 loaded that I was going to install the Win7 RC on a secondary IDE drive.  Trust me, install windows first, then ubuntu onto whatever drive you want, doesnt matter, grub will take care of itself and allow you to choosed between the 2.  

> **46jeepster said:**
> Being that i'm not very computer savy, i decided to use the F12 button to do a dual boot until i can develop a better understanding of grub. I just got a new pc from Walmart yesterday with Win 7 installed. Opened it up,discvonnected the Win7 drive,hooked up a second drive.Turned it on and set the boot order to boot the second drive first. Installed Ubuntu on the second drive. Made sure that Ubuntu worked ok then turned the pc off, hooked the Win7 drive back up. Now if i turn it on, Ubuntu will boot without doing anything, If i need to use Win7, I press the F12 key on startup and the boot option screen shows up. I can select the Win7 drive to boot or any other Drives that i may install later. I know the experts can do all this with grub but its still a little complicated for me right now. Its been working good though and i'm having a lot of fun with Ubuntu.

Emachines ET1331G-03W

See above ^^^^.  You shouldnt have to muck around with boot order if you install Ubuntu second, and Im a Linux beginner myself.  I just started using Ubuntu full time after 9.04 was released so I couldnt tell you much how to mess with grub.  All I know is that if Windows is already installed, and you go ahead and install ubuntu on another drive, the same drive different partition or alongside windows, it doesnt matter.  Grub will simply load at boot and give you the option of loading windows or Ubuntu, or any other OS you have on any other drive(s).  The only time when it would be prudent to disconnect a second drive with another OS is when you already have Ubuntu and are installing windows to a second drive.  MS likes to think they are the only OS out there so they dont take into account that you might have another OS when creating their installer.  Linux distros assume you do have another OS, or at least that its a good possibility and have designed the installer to accommodate(at least my my understanding).

---

### Post by phillw on 2009-11-02
I'm pretty sure you've been swapping notes ... becuase this is nearly a mirror ;)

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1282978](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1282978)

Phill.

---

### Post by F_C on 2009-11-02
[[IMG]http://brainstorm.ubuntu.com/idea/22223/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22223/)

---

### Post by phillw on 2009-11-02
> **F_C said:**
> [[IMG]http://brainstorm.ubuntu.com/idea/22223/image/1/[/IMG]]("http://brainstorm.ubuntu.com/idea/22223/")


Thanks, but I still like [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

Plenty of screen shots, and a good 'hold-your-hand' one.  But, the more tutorials out there, the better:D

Phill.

---

