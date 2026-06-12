---
title: "lubuntu + windows 7 urgent plz"
date: 2010-03-09
forum: General Help
---

### Post by mox7 on 2010-03-09
Hi all .. 

I don't know what I have done but really need your help please ... 
here's my story, 
I was working with windows 7 ultimate then I decided to install the LUBUNTU alpha 3 which is based on UBUNTU if i'm not mistaken. however, I downloaded the OS annd I burned it to a DVD to give it a try with live boot. in contrast, I fall in love with it ;) so I decided to install it and I kept in mind I don't wanna lose windows 7 because all my files in there ** I WANT IT AS DUAL BOOT ** what happened is I followed this youtube video to install -- [http://www.youtube.com/watch?v=9V5zlhq8-l4](http://www.youtube.com/watch?v=9V5zlhq8-l4) -- but after the install finished and reboot the system I surprised that no DUAL BOOT. the system directly boot the LUBUNTU :-(

now my questions are: how do I check if windows 7 still there or not? if still there how to access it??
- How do I import the files from windows 7 to LUBUNTU ??
- How do I uninstall the LUBUNTU ??

please help me I am doing my final year project and everything is inside windows :-(

---

### Post by patchwork on 2010-03-09
First thing to check is to reboot, and press SHIFT after the bios screen and before the linux boots.  This should display your grub (bootloader menu).  Once the menu displays, look at the boot options.  If the only things listed are linux kernels and memory test, you have a problem.  If your Windows is listed, it's not a problem, and will only take a quick setting change to enable the menu to show on each reboot.

EDIT:  ...or to default boot into Windows, if that's what you want

---

### Post by mkvnmtr on 2010-03-09
You mightn try rebooting and pay attention to see if the boot loader does not give you the option to boot into Ubuntu or windows. If installed correctly it should. But the instalation of alpha software is not recomended on critical systems that you are not prepared to lose.

---

### Post by mox7 on 2010-03-09
I will give it a try and hope it is there

---

### Post by mox7 on 2010-03-09
no options are given directly to the lubuntu's log in screen ..

what should I do !!!

---

### Post by lakersforce on 2010-03-09
```
sudo update-grub
```

Restart your pc and choose Windows. If it's not there, you have deleted it!

---

### Post by patchwork on 2010-03-09
> no options are given directly to the lubuntu's log in screen ..

what should I do !!!

Do you mean that the bootloader menu did not display or that Windows was not on it?

If the menu did not display, try again, repeatedly tapping shift (it takes good timing sometimes).

---

### Post by L0neRanger on 2010-03-09
I've gone through the video and I don't see him setting up a multi-boot system.
If you followed everything to the letter as shown in the video, I'm afraid there IS no windows partition for you to go back to.

---

### Post by lakersforce on 2010-03-09
> **patchwork said:**
> 
If the menu did not display, try again, repeatedly tapping shift (it takes good timing sometimes).

If the grub bootmenu does not display, it means that only one kernel and no other OS is aviable.

---

### Post by patchwork on 2010-03-09
> If the grub bootmenu does not display, it means that only one kernel and no other OS is aviable.That's not necessarily true, as by defualt the installation includes three menu entries (kernel, recovery, and memtest).  Even with only one kernel installed, the menu should be visible.

---

### Post by akand074 on 2010-03-09
Ah, I'm not on ubuntu right now I'm on my laptop right now now on Windows but you can also go to System > Administration and there should be a start up setting that you can check all the operating systems installed. If its like the person in front of me said and you deleted it, then it MAY be recoverable (probably won't boot but you can at least copy and paste your important data to the Ubuntu partition. Use this:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

If your lucky it will find the Windows partition you deleted in a sector of your hard drive and recreate it, then you can mount it in Ubuntu and copy and paste the files. Good luck.

---

### Post by Kevbert on 2010-03-09
Run up Lubuntu and open LXTerminal and enter
```
sudo fdisk -l
```
This will show what partitions you have on your hard disk.  If you have any NTFS patitions then you haven't completely lost Windows 7 (but have lost the Windows boot).

---

### Post by mox7 on 2010-03-09
@lakersforce: I have updated and it gives these options
-ubuntu, with linux 2.6.3 genric 
-ubuntu, with linux 2.6.3 recovery mode
- memory test
- memory test 

what do you think ??

@patchwork: the same output as above 

please guys help

---

### Post by mox7 on 2010-03-09
mo@mo-laptop:~$ sudo fdisk -l
[sudo] password for mo: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0x210dccc6

@Kevbert: this is the output:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         193       15492   122897250   83  Linux
/dev/sda3           15493       30401   119756542+   7  HPFS/NTFS

---

### Post by lakersforce on 2010-03-09
> **mox7 said:**
> what do you think ??


Your partition is still there (looks like it is /dev/sda3.) You should be able to mount it and your files should be there.

To make it auto-mount at boot, you could do the following:

```
sudo blkid
```
this should give you a list with UUID's. Copy the UUID for sda3 (including the UUID=).
```
gksudo gedit /etc/fstab
```
At a new line insert:

UUID=your.uuid.number <tab here>   /your/mount/point/here  <tab here> ntfs  <tab here> rw,user,auto <tab here>  0 <tab here>  2

save and restart

if it does not work, try out akand074's suggestion.

It is wierd that grub has not made sda3 aviable for boot, though.

---

### Post by patchwork on 2010-03-09
Aye, between Kevbert, akand, and lakersforce (sorry, no sleight intended), hopefully you can get this sorted out.  I have zero experience with trying to recover windows or it's files.

Wish you luck, though.

---

### Post by mox7 on 2010-03-09
@lakesforce:

sorry brother I have no experience with commands I got the UUID's
to execute the second step should I copy this ** /dev/sda3: LABEL="Data" UUID="20582F92582F65AE" TYPE="ntfs" ** and paste it to what you said I should do if not please rearrange the command for me GOD BLESS YOU

---

### Post by lakersforce on 2010-03-09
Just copy this part:
```
UUID="20582F92582F65AE"
```

and don't write <tab here>, just press tab. Study the fstab file and you should be able to figure it out.

the /your/mount/point/here part, should be a path availible. For exzample you could make one availible by doing a
```
sudo mkdir /media/sda3
```
at the command line and then ofc your /your/mount/point/here should then be /media/sda3


Alternatively, you might be able to see your drive just by navigating to the Places on your desktop (the top bar, if you are using the gnome desktop (default))

---

### Post by mox7 on 2010-03-09
@lakesforce:
while compiling this command [QUOTE]gksudo gedit /etc/fstab/QUOTE] I think a file going to open but nothing appears !!

---

### Post by lakersforce on 2010-03-09
Are you using gnome or kde? It only works on gnome.

gksudo gedit /etc/fstab

or

sudo nano -w /etc/fstab (works on pretty much all systems, except windows)

---

### Post by patchwork on 2010-03-09
```
cat /etc/fstab
```

This will display (but not let you edit) the contents of the file.  I am only offering this in case you mistyped the command or your editor didn't open properly, and should confirm or refute that your fstab is MIA

---

### Post by mox7 on 2010-03-09
the second command brought me this

[PHP]  GNU nano 2.2.2              File: /etc/fstab                        Modified  

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1











^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell
 [/PHP]

---

### Post by lakersforce on 2010-03-09
```

sudo mkdir /media/sda3
```

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
UUID="20582F92582F65AE" /media/sda3 ntfs rw,user,auto     0       2

```

---

### Post by mox7 on 2010-03-09
^
after I paste the second code what to do !! 

sorry guys I have no knowledge about linux **

---

### Post by patchwork on 2010-03-09
Again, I'm not an expert on this, so take this with a grain of salt.

This method seems to be designed for you to be able to access your files (and retrieve them), as opposed to getting your windows partition to become bootable.  

As such, save the fstab, make the mount point:```
sudo mkdir /media/sda3
```
and mount the drive ```
mount /dev/sda3 /media/sda3
```  Once the drive is mounted, try to access your files and copy them to a backup location (I would personally put them on cd or flash drive, and copy them to lubuntu...the more the merrier).

If you can retrieve the files, post back and someone may be able to help you get your windows bootable again (I'm not sure if this will work, but it may involve reinstalling grub)

---

### Post by mox7 on 2010-03-09
[IMG]http://img2.pict.com/c5/6b/2e/3079852/0/800/201003100434421280x800scrot.png[/IMG]

according to the picture above it seems that I deleted the C drive which consists windows 7 system files but the D drive still as it is nothing happened to it .. I am going to format the C drive again and install windows 7 so I can back up my files ..

---

### Post by lakersforce on 2010-03-09
As far as I can see, you succesfully mounted your partition. It is availible at /media/sda3 and you can browse your files using your favorite GNU/Linux file browser.

At default the file browser is opened at /home/<yourusername>. Just browse to /media/sda3.

There's no need to install Windows 7 just to take backup (unless of course you can not live without Windows.)

---

### Post by madscientist032 on 2010-03-09
> according to the picture above it seems that I deleted the C drive which consists windows 7 system files but the D drive still as it is nothing happened to it .. I am going to format the C drive again and install windows 7 so I can back up my files ..

umm correct me if I'm wrong, but wouldn't installing Windows 7 overwrite anything you already have on your hard drive? (AKA: the files you are trying to recover?)

---

### Post by patchwork on 2010-03-09
Shouldn't, if they are on separate partitions like the OP implied (barring human error)

---

### Post by mox7 on 2010-03-09
I formatted the C drive and installed win 7 again. thank god I found my files in a very good condetion :biggrin: .. 
 
>  There's no need to install Windows 7 just to take backup (unless of course you can not live without Windows.) 
 
I prefer to Dual Boot with linux because i need time to be familir with linux unless you advice me to go directly to linux, to be honest i'm not going to use lubuntu again even though i love it but i think i would install either ubuntu or mint instead ...
 
THANK YOU VERY MUCH FOR YOUR HELP GOD BLESS YOU .. 
 
>  umm correct me if I'm wrong, but wouldn't installing Windows 7 overwrite anything you already have on your hard drive? (AKA: the files you are trying to recover?) 
 
I don't understand what mean but i think when i installed lubuntu i have formatted the C drive. however, when i tried to install win 7 again it refused because it says the partition format does not match with win 7 so i had to format the drive again 
 
THANKS FOR YOUR HELP GOD BLESS YOU 
 
>  
Shouldn't, if they are on separate partitions like the OP implied (barring human error)

 
I already did :biggrin: 
THANKS FOR YOUR HELP GOD BLESS YOU 
 
 
 
** THANKS FOR ALL OF YOU FOR YOUR HELP GOD BLESS YOU **
 
see you guys in another problems :biggrin: CHEERS

---

