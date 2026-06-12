---
title: "Can't boot Vista after installing Ubuntu"
date: 2009-10-13
forum: General Help
---

### Post by jackskett on 2009-10-13
I installed Ubuntu a few months ago, planning to run it as well as Vista, but since I installed Ubuntu I've been unable to boot Vista. The option is still there, but my computer freezes if I select it. I can access all the files on the Vista side of the partition from Ubuntu, but I've found that there are a lot of things I still need Vista for that Ubuntu just can't do. It's become quite inconvenient. Any help would be greatly appreciated.
Thanks.

---

### Post by mhgsys on 2009-10-13
Could you post your /boot/grub/menu.lst
typ ```
gksudo gedit /boot/grub/menu.lst
``` in terminal

And the output of sudo fdisk -l
typ ```
 sudo fdisk -l 
```

---

### Post by justleen on 2009-10-13
Did it ever work? Did you change anything to the disk order (in the bios or physically swapped drives) Do you get any error what so ever?

---

### Post by jackskett on 2009-10-14
My  /boot/grub/menu.lst is this:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

I tried typing sudo fdisk - l and got no response.

I don't recall getting any errors when I installed Ubuntu, but I did have a friend of mine do the installing while I watched, ironically so I wouldn't mess anything up!

---

### Post by mhgsys on 2009-10-19
Hey there; sorry for the delay,I was actually thinking other people on this forum would have also helped you, but they didn't so it seems.

Anyway; in the code ```

sudo fdisk -l 
```
remember; the l is a lower case L not a 1 or a | 

Anyway;thanks for posting your grub menu.
**_Is this really it? There should be more in that file._**
_If so; it seems that grub is not fully installed or at least is not installed properly._
[B][U]If not; please post the whole file and nevermind the codes below in that case; you said you had a option to choose vista, and it's not in the grub you've posted.
[/U][/B]
you should use the fdisk -l to verify ubuntu and windows are installed and try to reinstall grub.

To reinstall grub, this is a good way;


Bootup a live cd, open a terminal and do the following.
```

sudo grub
```

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

```

find /boot/grub/stage1

```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)
```


root (hd?,?)

```
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```

setup (hd0)

```
Finally exit the grub shell
```


quit

```
Hope this helps for you, and if not; we need some more information.

In order to get a clearer picture of your setup, boot from your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop from here;

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and type:

```


sudo bash ~/Desktop/boot_info_script*.sh

```
This will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

Hope this works out for you with reinstalling grub though,

---

### Post by kevinrogers1977 on 2009-10-19
i am not expert on grub  or ubuntu, but however a simular problem happend to me once when i was booting windows 7.

i wanted to boot ubuntu,but my boot loader is set to win 7 .

so i pressed the power button just after the bootloader to return to ubuntu.
wich bootet,later i wanted to boot windows 7 again and i i haulted just after selecting it from grub menu.

i fixed it but using the vista boot disc ,selecting fix my computer ,them command prompt, them CHKDSK ,i ran that and let i run compleately. then restarted ,booted in win 7 fine.

also other times when me vista/win 7 hasnt booted ,i boot from vista disc agian and run command prompt.

bootrec.exe /fixmbr this fixs the windows boot loader leaving the grub alone.

i not saying this is the soloution but if the other methos of fixing the grub dont work try this.

---

### Post by mhgsys on 2009-10-19
> **kevinrogers1977 said:**
> 


bootrec.exe /fixmbr this fixs the windows boot loader leaving the grub alone.

i not saying this is the soloution but if the other methos of fixing the grub dont work try this.


May I add; when using the bootrec.exe /fixmbr command **_you will lose grub if it's installed on the same disk (hd0) where vista is on._** 
You could try this, and reinstall grub after that (commands are in my post before) however;
I recommend you try chkdsk and sfc /scannow (Scans the integrity of all protected system files and repairs the system files if needed.
NOTE: Restores Vista's original setup of system files. (EX: Fonts, wallpapers, System32 files, etc.

---

### Post by mhgsys on 2009-10-19
srry dubbel posted.

---

### Post by donaldt on 2009-10-19
> **mhgsys said:**
> Hey there; sorry for the delay,I was actually thinking other people on this forum would have also helped you, but they didn't so it seems.

Anyway; in the code ```

sudo fdisk -l 
```
remember; the l is a lower case L not a 1 or a | 

Anyway;thanks for posting your grub menu.
**_Is this really it? There should be more in that file._**
_If so; it seems that grub is not fully installed or at least is not installed properly._
[B][U]If not; please post the whole file and nevermind the codes below in that case; you said you had a option to choose vista, and it's not in the grub you've posted.
[/U][/B]
you should use the fdisk -l to verify ubuntu and windows are installed and try to reinstall grub.

To reinstall grub, this is a good way;


Bootup a live cd, open a terminal and do the following.
```

sudo grub
```

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

```

find /boot/grub/stage1

```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)
```


root (hd?,?)

```
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```

setup (hd0)

```
Finally exit the grub shell
```


quit

```
Hope this helps for you, and if not; we need some more information.

In order to get a clearer picture of your setup, boot from your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop from here;

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and type:

```


sudo bash ~/Desktop/boot_info_script*.sh

```
This will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

Hope this works out for you with reinstalling grub though,

May I please ask for assistance for a similar problem?

I have a windows xp system running on a Fujitsu p-1610 lifebook.  I use it as an electronic flight bag to store FAA approved instrument approach plates for use in aircraft.  The Fujitsu screen is sunlight readable and provides excellent visibility in the cockpit.  

I have been running Ubuntu 9.04 on a 250 gb, USB powered hard drive plugged into a Sony portable (BIOS modified to boot USB first) with great success for about 8 months.  I developed a problem while trying to extend a small windows partition on the external hard drive that ran my Ubuntu system.  After much hassle, I gave up and did a complete re-install, this time using the Fujitsu as the host computer.  I was able to get Ubuntu  installed and working, but in the process the boot up of the XP system was damaged.  Now the only way to gain access to the XP system is to plug in the external hard drive.  It provides a dual boot message (if I push all the appropriate buttons during start up) that allows a choice of either system.  The dual boot apparently resides on the external hard drive, because I can boot either XP or Ubuntu 9.04 (and they both work as advertised) but only if the hard drive is plugged in.  It must contain the primary drive that allows the dual boot.

Question, how can I get Windows XP to boot again (all files and programs are working fine) and also get the external hard disk drive containing the Ubuntu 9.04 system to boot without being plugged in to the XP computer?

I have read dozens of expert opinions about how the master boot record does such and such, but none of it really says how to correct this specific problem (in my opinion).

I am a convert to Ubuntu and want to continue to use and learn the features.  In the past, whenever I have asked for help, some geek always says something about an inappropriate thread or an off topic issue, so please be gentle.  My level of ignorance is fairly high, but I don't need any more lectures.

Thanks!

donaldt

---

### Post by oldfred on 2009-10-19
I am not a geek, but you do get better response with your own thread and title that has your problem. 

You have two hard drives each with a MBR. Somehow in your install on the internal hard drive Grub was installed to the removable. (You probably had the external set to boot first.) The first hard drive is what the BIOS uses to boot from.

If you want specific instructions please output (paste command into terminal) which will list your partitions:

```
sudo fdisk -l
```

If you know what partitions your have ubuntu in you can reinstall grub to the MBR of your internal drive  (if you are booting first from the removable drive you will have to install grub to hd1):

Quick Re-Install GRUB, if file locations are known
4-step short story

In terminal
  sudo grub
  root (hd[COLOR=DarkRed]0[/COLOR],x)    <-- this must point to location of 'stage1', else see nb:
  setup (hd[COLOR=DarkRed]0[/COLOR])     <-- installs grub IPL to MBR of first hard drive. Prefered method.
  quit

Reboot

nb: if location of 'stage1' is unknown,
  find grub/stage1
or
  find /boot/grub/stage1
is needed, after step #1

I like to have grub in the mbr of every hard drive that has an operating system.

---

### Post by oldfred on 2009-10-19
After thinking some more if you are booting from the removeable drive there is confusion one which drive is drive 0 when it is removed. I am not sure if you have to say drive 0 on the root but drive 1 on the setup. It may be more straigtforward to use the install CD. Post your fdisk so we can see the partitions.

---

### Post by mhgsys on 2009-10-20
> **donaldt said:**
> May I please ask for assistance for a similar problem?



Sure you may; first of all I agree with user oldfred.
 You have two hard drives each with a MBR. Somehow in your install on the internal hard drive Grub was installed to the removable. (You probably had the external set to boot first.) The first hard drive is what the BIOS uses to boot from.

So; If you indeed installed (the working) grub onto the external hd, you might want to recover the mbr on the windows drive (hd0) (where bios boots from) 
To do that you'll need a XP recovery cd. **_ UNPLUG THE EXTERNAL DRIVE BEFORE YOU DO ALL THIS_**

# Insert the Windows XP CD into your CD drive and restart your computer. If you are prompted, select any options required to start (boot) from the CD.
# When the text-based part of Setup begins, follow the prompts. Select the repair or recover option by pressing R.
, select the installation that you want to access from the Recovery Console.
# When you are prompted, type the Administrator password or press enter if none.
In the console typ; 
```
 fixmbr

```
This command will overwrite the existing mbr on the drive and creates a new one,

reboot; and see if  windows will bootup again normally without the external drive plugged in.

 
If your system still doesn't boot properly, repeat the steps above, but use the ```
fixboot
``` command instead



Hope's this helps you out.

---

### Post by donaldt on 2009-10-20
Thanks to you both for the prompt (and helpful) response.  I found an online program that does the same thing you proposed for the XP system and used it to restore XP on the Fujitsu.  All is now normal there and all programs are operating with all files intact.

Now, it seems my Ubuntu program is in need of intensive care.  I get the dual boot menu (Ubuntu or Windows XP) from the new XP recovery, but when I plug in and try to launch Ubuntu 9.04 (still residing on the external Hard Drive), the Logo appears and after about a dozen trips back and forth across the screen, the barometer disappears and nothing happens.

Any insight into what may have caused Ubuntu to fail? 

I agree with the idea of a MBR on every hard drive.  How do I do that?  

Thanks for the help!

donaldt

---

### Post by oldfred on 2009-10-20
For the boot time check, next time you boot, choose the ubuntu you want from the grub menu and hit "E" to edit, scroll down to the second line which starts "kernel" and hit "E" again. Now scroll to the end of the line and delete the words "usplash quiet" from the end. Hit enter to accept the edit and then "B" to boot. You will now see all the text that is usually hidden by the splash screen, and it may show you, or give you a clue about where the problem is.

The way to install grub I posted above. If you have reinstalled windows you have windows in the MBR of the internal drive.

---

### Post by donaldt on 2009-10-21
OK.  I got to the second line.  There is no "usplash quiet" at the end of the line.

---

### Post by mhgsys on 2009-10-21
@Dondaldt
What happens if you try to bootup from the external drive?

Here's what you did now; you restored the mbr on the internal drive, where windows is located. So when you power up your computer you're windows is booting fine from (hd0).

The moment you plug in you're external disk the bios boot priority will change and the external disk will become the disk to boot from.

So, plugging it in while trying to boot ubuntu (external) from the internal disk won't work.

So; My advice is this; When you want to use your ubuntu; Bootup with the external disk attached, this will cause the system to boot from the external hd, and everything should be booting like a charm, if your windows fails to boot from the external hdd's grub menu ; bootup ubuntu from it and open up a terminal 
typ; ```
 sudo fdisk -l 
```
to get a good view which disk contains the windows and post output here
typ; ```
gksudo gedit /boot/grub/menu.lst
``` 
and post output here.

---

### Post by jackskett on 2009-10-21
Hey, yeah I just checked the grub again and it looks like I managed to only copy a part of it last time. Hopefully this is the information you need.

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=341620c8-5864-4b2e-a932-a096c7e281a9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=341620c8-5864-4b2e-a932-a096c7e281a9

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        341620c8-5864-4b2e-a932-a096c7e281a9
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=341620c8-5864-4b2e-a932-a096c7e281a9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        341620c8-5864-4b2e-a932-a096c7e281a9
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=341620c8-5864-4b2e-a932-a096c7e281a9 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        341620c8-5864-4b2e-a932-a096c7e281a9
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=341620c8-5864-4b2e-a932-a096c7e281a9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        341620c8-5864-4b2e-a932-a096c7e281a9
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=341620c8-5864-4b2e-a932-a096c7e281a9 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        341620c8-5864-4b2e-a932-a096c7e281a9
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=341620c8-5864-4b2e-a932-a096c7e281a9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        341620c8-5864-4b2e-a932-a096c7e281a9
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=341620c8-5864-4b2e-a932-a096c7e281a9 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        341620c8-5864-4b2e-a932-a096c7e281a9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=341620c8-5864-4b2e-a932-a096c7e281a9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        341620c8-5864-4b2e-a932-a096c7e281a9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=341620c8-5864-4b2e-a932-a096c7e281a9 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-11-generic
uuid        341620c8-5864-4b2e-a932-a096c7e281a9
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=341620c8-5864-4b2e-a932-a096c7e281a9 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid        341620c8-5864-4b2e-a932-a096c7e281a9
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=341620c8-5864-4b2e-a932-a096c7e281a9 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.04, memtest86+
uuid        341620c8-5864-4b2e-a932-a096c7e281a9
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1

I also managed to get a response from sudo fdisk -l. Turns out I needed to open a new Terminal! I feel like such a dunce! Anyway, here's what came out:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13f782bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         702     5632000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         703        7180    52034535    7  HPFS/NTFS
/dev/sda3            7181        9486    18522945   83  Linux
/dev/sda4            9487        9729     1951897+   5  Extended
/dev/sda5            9487        9729     1951866   82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281    c  W95 FAT32 (LBA)

Thanks again for your help!

---

### Post by mhgsys on 2009-10-22
@jackskett


Hi there, 

My first thought is that you would be helped by booting up a vista repair cd/dvd. (choose repair> prompt)  typ;```
bootrec.exe /fixboot 
```  in the prompt. Hit enter > let it finish > reboot and try to boot vista from grub.,


I do have my doubts however because of this error in your fdisk -l output. ```
 Partition 1 does not end on cylinder boundary.
```

There's a good chance your vista will be booting again, since it seems like (hd0,1) is the vista partition and not (hd0,0) which probably is the vista repair partition. (yes; in grub the first partition would be (hd0,0) and the second (hd0,1) correct me if I'm wrong. 

However: I wouldn't be happy about that error;since it could lead to data loss in case partitions overlap. also it seems pretty nasty to solve; except recreating the entire partition. 

Anyway; Please give an update if the bootrec.exe /fixboot helped or didn't help booting up your vista again;

---

### Post by jrrader on 2009-10-22
This might be too late now, but installing Ubuntu on a hard drive with Vista will cause vista to give the autochk error.  There are plenty of complex solutions to this, some might even make Ubunutu unusable as well.  

This works.  I have done it many times:

The easy solution is to pull your hard drive out, connect it to another motherboard (friend's computer will work if you only have one, go to a computer repair store and ask them to hook it up if you don't have friends).  Turn it on and Vista will boot again.  Why?  I don't know.  Put the hard drive back in your computer and the problem is gone.

---

### Post by donaldt on 2009-10-23
OK.  Many thanks for the help.  I bought a program to re-install the MBR on my Windows XP system.  It now resides on a USB stick.  It's a mini windows system and I have used it several times.  I also learned the Ubuntu live CD trick and using a terminal (hd1,4) have been able to re-boot my newly re-installed Ubuntu 9.04.

So far, so good.  I have changed the BIOS boot order on my two computers, one Vista and one XP, so they boot first from an external hard disk dirve.  When I plug in the external hard disk drive (loaded with Ubuntu 9.04)it reports stage 1.5, error 17 and will not boot.  Tried it on two separate computers.  However, when I manually select boot the internal hard disk drive of the Fujitsu, and (only when I have the external drive plugged in), I am offered either system and am able to boot either system.  

I seem to be in a continuous do-loop.  Whenever I try to boot the external drive first, Ubuntu reports the usual error 17.  When I select windows XP it does error 21.  Either operating system seems to require the external hard disk to be plugged in to boot up.

Any ideas how to break the chain of errors that occur?

donaldt

---

### Post by mhgsys on 2009-10-24
@Donaldt; Let's check if I got the story straight, When booting from the external hd you get a grub error 17 when booting ubuntu and a grub error 21 when booting xp.

However; when you boot the internal hard disk drive of the Fujitsu with the external drive plugged in you get a proper grub with all OS options; 

When the external disk is not plugged in > what happens ? do you also get the boot options? (Ubuntu won't boot of course because it's and the external hdd)
But do you get the grub menu while booting from the internal disk?


Then all you have to do is reinstall grub on the external hdd's grub, and add the vista and xp option later in /boot/grub/menu.lst .You might want to unplug the xp/vista drive when reinstalling grub just to be absolutely  sure it will be installed on the right hdd.

To make it all a little easier; why don't you just restore the windows mbr to original; so there will be no grub installed on the internal hdd, and reinstall grub on your external hdd.
So when you select the internal disk to boot from; you won't get any grub and it will boot straight into vista/xp, and when you select your external hdd to boot from you get a grub menu with the choice for an OS. ( add the vista and xp option in 
boot/grub/menu.lst)

---

### Post by donaldt on 2009-10-25
Well, I'm tired of fixing one system and in the process breaking another.  I have an operable (albeit a slightly awkward) Ubuntu 9.04 system and two windows systems.  One is an operable XP system that will boot Ubuntu from the external hard disk drive.  The other is Vista and it will not boot Ubuntu from the same external drive.  It is disgusting to keep seeing error 17.

Every time I try to repair Ubuntu (and it still doesn't work) I disable the host windows system and I then have to go back and re-install the MBR.  

I have downloaded Super Grub Disk .9799.tar.gz, but can't get it to install on a USB drive.  

I guess I will live with a crippled system because there is no way (at least none that I can understand) to fix Ubuntu so it will boot on my Vista system.  I know it works.  I know it is all there, but I can't get at it.

I can't believe Ubuntu would claim to be a main stream system when the system changes the numbering of hard disk drives between releases and has no convenient way of fixing itself without a 40 step, 4 page procedure.  

I'm disgusted and ready to give it up.

---

