---
title: "Help grub rescue"
date: 2010-12-27
forum: General Help
---

### Post by firefighternnc on 2010-12-27
I am using a Acer Aspire 5315 with Windows Vista Home and loaded ubuntu 10.10 dual boot. The system loaded great and after the first boot it detected several updates. It loaded those updates and then I assume grub2 did something to the partitions. Ive read hundreds of post to try to get the system to fix the issue but I cant get the computer to boot with a recovery disk made as directed. It either gives me NLTDR missing or No Media or disk. 
 
 
Please HELP, I would just like to get back into it so I can convert to Ubuntu and get rid of Windows!!

---

### Post by drs305 on 2010-12-27
firefighternnc, 

Welcome to the Ubuntu forums. And if your name indicates your profession, thank you for that as well.

It sounds like you might have installed Ubuntu within Windows (Wubi). If so, please refer to the Wubi Megathread here:
[http://ubuntuforums.org/showthread.php?t=1639198]("http://ubuntuforums.org/showthread.php?t=1639198")

If it was a normal installation, please download and run the boot info script and post the RESULTS.txt contents here.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by firefighternnc on 2010-12-27
Yes and for the record we dont spend a lot of time with computers so I'm a little slow.  I'm just really frustrated with how Windows messed with the partitions!

---

### Post by firefighternnc on 2010-12-27
Mr. Dr,
 
Okay, Ive tried to use the instructions from the link.  I get either remove disk or other media "press any key to restart" or Nltdr missing "press any key to restart"
 
Any help or ideas?

---

### Post by drs305 on 2010-12-27
OK. Please run the boot info script and post the contents of RESULTS.txt. That information should give us a good idea of what is happening with your boot files.

You can run it from the LiveCD.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by firefighternnc on 2010-12-27
Ok, could you tell me how to get a LiveCD going because based on experience from last night it wouldn't let me get anywhere either unless I'm doing something wrong.  Sorry for all the trouble and thanks in advance for all the help!

---

### Post by drs305 on 2010-12-27
> **firefighternnc said:**
> Ok, could you tell me how to get a LiveCD going because based on experience from last night it wouldn't let me get anywhere either unless I'm doing something wrong.  Sorry for all the trouble and thanks in advance for all the help!

From your first post, you mention recovery disk. Are you referring to the installation disk, aka LiveCD, which allows you to try or install Ubuntu? If you are having problems booting it, make sure the BIOS boots to the CD-
ROM drive first.

If you are still having problems, how did you install Ubuntu? Whatever medium you used to install Ubuntu should also provide you the opportunity to "Try", which would take you to the Desktop. That is where you want to be, so you can start Firefox and download/run the boot info script.

---

### Post by firefighternnc on 2010-12-27
I loaded it with the Windows Installer and it loaded fine but then after the first boot it loaded several updates and by all indications I've read I guess the partition was lost and now it boots to grub rescue and I've tried the following:
 
Windows Vista Recovery (I dont have the original)
LiveCD
BootSuite 2010 (Yes I paid for it)
 
I've changed to boot sequence and tried from CD and USB both with the same lack of success.  
 
It goes back to grub rescue everytime.

---

### Post by drs305 on 2010-12-27
Most solutions require a LiveCD or Windows repair CD to correct the problem, and this is where we normally tell you you have to burn a new CD. But we can try something else.

Go to the Grub Rescue Megathread and following the WUBI instructions for booting from the Rescue prompt.

The failure you are getting is most likely due to the upgrades and the fix is well documented. Unfortunately you normally have to get to a Live Desktop. Try booting using the directions from the Rescue megathread. If you are able to boot, you will want to return to the Wubi thread and review the "make the fix permanent section".

Here is the link to the rescue thread. Use the "Wubi Only" instructions.
[http://ubuntuforums.org/showthread.php?t=1594052]("http://ubuntuforums.org/showthread.php?t=1594052")

---

### Post by amsterdamharu on 2010-12-27
We mean you have to boot from an Ubuntu CD. The normal Ubuntu CD has an option in the startup menu saying something like "try Ubuntu". 
It would run Ubuntu from memory and you can run the script. It has firefox so you can post the output here using the live CD.

Starting with the Windows disk probably tried to repair Windows and screwed stuff up royally.

As for getting rid of Windows; I would advice against it, you might find yourself in a situation where you need it for some program or reading a CD that won't read in Ubuntu and just get more frustrated.

---

### Post by firefighternnc on 2010-12-27
When I attempt the manual version the "ls" only gives me the (Hd0) and according to the directions I need something else?

---

### Post by amsterdamharu on 2010-12-27
If you have a working computer with Internet and don't want to wait too long for the live CD download you can download tinycore Linux (only 10MB). Then use a program called unetbootin to create a USB stick that can boot into tinycore for you.

Tinycore doesn't run the bootscript for you but you can open a terminal and type the following command:
```
sudo fdisk -l
```
When you post the output of that someone can help you further:


Tinycore can only install grub 0.97 I am not sure if that can boot Ubuntu for you, once your in you can install grub2 from your working Ubuntu install.
[http://www.tinycorelinux.com/install.html#6_Installing_GRUB](http://www.tinycorelinux.com/install.html#6_Installing_GRUB)

---

### Post by firefighternnc on 2010-12-27
Just attempted the Tiny boot and will not boot at all.  After I select CD it appears to access the CD then goes straight to the error: no such device: lots of numbers the grub rescue>

---

### Post by amsterdamharu on 2010-12-27
You did not boot tinycore because it uses syslinux and will not have any grub error.

Are you sure it boots from the CD? My guess is it starts from harddisk and gives you the same boot error. Check your BIOS settings and make sure it boots from CD, maybe it's burned wrong. I always use USB because it's too much of a hassle when it isn't burned right.

If you get a grub rescue prompt you can type commands right?

I don't know if this works for grub2 but what is the output of the following command:

```
find /boot/vmlinuz(press tab here for autocomplete or a list of options)
```

---

### Post by DuskNight on 2010-12-27
Ugh, I just found the answer to my issue right after I wipe out Windows and install only Linux to make it work..
Well, all things happen in time.

8 more hours until I install Windows Vista, replacing Windows 7.

---

### Post by firefighternnc on 2010-12-27
Everytime I attempt to use any CD/USB it usually gives me the message Remove disk or other media-Press any key to restart-Can anyone help?  It seems as if Ive tried everything and it takes me right back to grub rescue! I dont want to format the disk if I dont have too.

---

### Post by amsterdamharu on 2010-12-27
Must be some BIOS setting that won't allow you to boot off anything but the harddisk.
Ubuntu live CD would give you a menu when start that so does tinycore.

The usual key to press to go into the bios is delete but it can be anything, check what messages come on screen before it reads any hard disk or CD.

Does the grub rescue give you an option to type commands? If so what did you get when you tried my suggestion in post 14?
[http://ubuntuforums.org/showpost.php?p=10284527&postcount=14](http://ubuntuforums.org/showpost.php?p=10284527&postcount=14)

---

### Post by firefighternnc on 2010-12-27
It does allow me to select another bios setting other than the hard drive it just gives me the remove disks or other media then press other key.  As for the grub rescue, yes i can type in it but the command line you mentioned says "unknown command"

---

### Post by firefighternnc on 2010-12-27
So is this a lost cause.  Should format the drive and if so how do I format it since it goes straight to grub rescue?

---

### Post by amsterdamharu on 2010-12-27
What happens if you press a key with the media still in there?

---

### Post by wilee-nilee on 2010-12-27
> **firefighternnc said:**
> So is this a lost cause.  Should format the drive and if so how do I format it since it goes straight to grub rescue?

What you need probably which is hinted at here is the per-session boot menu key prompt, on my computer it is just hitting the f12 key at turning on several times immediately.

If you name the computer model I can probably find the key prompt for you on the web.

---

### Post by amsterdamharu on 2010-12-27
No, don't format. I found the commands for grub2:

When in the grub2 command mode type the following command:
```
search --file /boot/grub/ext2.mod
```This should give you hd0,7 (0,7 is an example you might have different values)

Then type the following commands (replace 0,7 with the values you got from the first command) In this I use root=[COLOR=Red]/dev/sda3[/COLOR] that is where Ubuntu was installed. I am just guessing here you can try 1 through 12, the wrong one gives you a kernel panic so you have to retry another one like /dev/sda4:
```
insmod ext2
set root='(hd0,7)'
linux /boot/vmlinuz(press tab to autocomplete or get a list) root=/dev/sda3
initrd /boot/initrd(press tab, make sure the initrd has the same version number as vmlinuz)
boot
```

---

