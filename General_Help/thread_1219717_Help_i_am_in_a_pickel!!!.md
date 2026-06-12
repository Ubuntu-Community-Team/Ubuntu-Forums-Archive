---
title: "Help i am in a pickel!!!"
date: 2009-07-22
forum: General Help
---

### Post by tlillies on 2009-07-22
Alright well i just got a new computer and i was bored so i wanted to try out the windows 7 RC. That was ok OS but kind of boring for me so then i wanted to try ubuntu. I researched dual booting and downloaded ubuntu and got it all set up but i think somthing went wrong in the intallation during the partition. I got all the way throught the installion and tried out ubuntu and i really liked it but i wanted to make sure that i still had windows. I tried logging on windows and it will just freeze up and then shut off the computer. I tired everything i could to start windows but nothing worked.
 
Then more trouble happend because now when i try to start up my BIOS it will not let me boot from a disk it goes straight to the hard drive even if i select it in the boot selection. Also if i try to go to anything else in BIOS it just does not work. I have tried every sigle route i could to not get to the hard drive but it still always boots to it not matter what i select or do! I have tried to look up solutions to any of this and have found nothing. 
 
Also i dont know why but my ubuntu is running pretty slow and some applications wont open like Snynaptc Package manager and computer janitor. Also randomly my keyboard and mouse will freeze up and i will have to restart my computer. Please help me! :(

---

### Post by nothingspecial on 2009-07-22
Boot ubuntu.

In your menus go accessories > terminal 

Type ```
sudo fdisk -l
```

Post the output here.

Then type ```
cat /boot/grub/menu.lst
```

And post the output aswell.

---

### Post by tlillies on 2009-07-22
Alright here is the first one
 
[FONT=Times New Roman][SIZE=3]tom@tom-desktop:~$  sudo fdisk -1[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]fdisk: invalid option -- '1'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Usage: fdisk [-b SSZ] [-u] DISK     Change partition table[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       fdisk -s PARTITION           Give partition size(s) in blocks[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       fdisk -v                     Give fdisk version[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Here DISK is something like /dev/hdb or /dev/sda[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]and PARTITION is something like /dev/hda7[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-u: give Start and End in sector (instead of cylinder) units[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-b 2048: (for certain MO disks) use 2048-byte sectors[/SIZE][/FONT]

---

### Post by tlillies on 2009-07-22
And here is the second
 
[FONT=Times New Roman][SIZE=3]tom@tom-desktop:~$ cat /boot/grub/menu.lst[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# menu.lst - See: grub(8), info grub, update-grub(8)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#            grub-install(8), grub-floppy(8),[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#            grub-md5-crypt, /usr/share/doc/grub[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#            and /usr/share/doc/grub-doc/.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## default num[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# Set the default entry to the entry number NUM. Numbering starts from 0, and[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# the entry number 0 is the default if the command is not used.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# You can specify 'saved' instead of a number. In this case, the default entry[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# is the entry saved with the command 'savedefault'.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# WARNING: If you are using dmraid do not use 'savedefault' or your[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# array will desync and will not let you boot your system.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]default             0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## timeout sec[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# Set a timeout, in SEC seconds, before automatically booting the default entry[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# (normally the first entry defined).[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]timeout                        10[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## hiddenmenu[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# Hides the menu by default (press ESC to see the menu)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#hiddenmenu[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# Pretty colours[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#color cyan/blue white/blue[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## password ['--md5'] passwd[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# If used in the first section of a menu file, disable all interactive editing[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# control (menu entry editor and command-line)  and entries protected by the[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# command 'lock'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# e.g. password topsecret[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# password topsecret[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# examples[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# title               Windows 95/98/NT/2000[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# root               (hd0,0)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# makeactive[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# chainloader   +1[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# title               Linux[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# root               (hd0,1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# kernel           /vmlinuz root=/dev/hda2 ro[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]### BEGIN AUTOMAGIC KERNELS LIST[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## lines between the AUTOMAGIC KERNELS LIST markers will be modified[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## by the debian update-grub script except for the default options below[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## DO NOT UNCOMMENT THEM, Just edit them to your needs[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## ## Start Default Options ##[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## default kernel options[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## default kernel options for automagic boot options[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## If you want special options for specific kernels use kopt_x_y_z[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## where x.y.z is kernel version. Minor versions can be omitted.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## e.g. kopt=root=/dev/hda1 ro[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]##      kopt_2_6_8=root=/dev/hdc1 ro[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]##      kopt_2_6_8_2_686=root=/dev/hdc2 ro[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# kopt=root=UUID=597020c1-72cc-4b7c-b254-a482c463af66 ro[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## default grub root device[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## e.g. groot=(hd0,0)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# groot=597020c1-72cc-4b7c-b254-a482c463af66[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## should update-grub create alternative automagic boot options[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## e.g. alternative=true[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]##      alternative=false[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# alternative=true[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## should update-grub lock alternative automagic boot options[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## e.g. lockalternative=true[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]##      lockalternative=false[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# lockalternative=false[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## additional options to use with the default boot option, but not with the[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## alternatives[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## e.g. defoptions=vga=791 resume=/dev/hda5[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# defoptions=quiet splash[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## should update-grub lock old automagic boot options[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## e.g. lockold=false[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]##      lockold=true[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# lockold=false[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## Xen hypervisor options to use with the default Xen boot option[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# xenhopt=[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## Xen Linux kernel options to use with the default Xen boot option[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# xenkopt=console=tty0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## altoption boot targets option[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## multiple altoptions lines are allowed[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## e.g. altoptions=(extra menu suffix) extra boot options[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]##      altoptions=(recovery) single[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# altoptions=(recovery mode) single[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## controls how many kernels should be put into the menu.lst[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## only counts the first occurence of a kernel, not the[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## alternative kernel options[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## e.g. howmany=all[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]##      howmany=7[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# howmany=all[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## specify if running in Xen domU or have grub detect automatically[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## update-grub will ignore non-xen kernels when running in domU and vice versa[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## e.g. indomU=detect[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]##      indomU=true[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]##      indomU=false[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# indomU=detect[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## should update-grub create memtest86 boot option[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## e.g. memtest86=true[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]##      memtest86=false[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# memtest86=true[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## should update-grub adjust the value of the default booted system[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## can be true or false[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# updatedefaultentry=false[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## should update-grub add savedefault to the default options[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## can be true or false[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# savedefault=false[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]## ## End Default Options ##[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]title                  Ubuntu 9.04, kernel 2.6.28-11-generic[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]uuid                 597020c1-72cc-4b7c-b254-a482c463af66[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]kernel              /boot/vmlinuz-2.6.28-11-generic root=UUID=597020c1-72cc-4b7c-b254-a482c463af66 ro quiet splash[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]initrd               /boot/initrd.img-2.6.28-11-generic[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]quiet[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]title                  Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]uuid                 597020c1-72cc-4b7c-b254-a482c463af66[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]kernel              /boot/vmlinuz-2.6.28-11-generic root=UUID=597020c1-72cc-4b7c-b254-a482c463af66 ro  single[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]initrd               /boot/initrd.img-2.6.28-11-generic[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]title                  Ubuntu 9.04, memtest86+[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]uuid                 597020c1-72cc-4b7c-b254-a482c463af66[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]kernel              /boot/memtest86+.bin[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]quiet[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]### END DEBIAN AUTOMAGIC KERNELS LIST[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# This is a divider, added to separate the menu items below from the Debian[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# ones.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]title                  Other operating systems:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]root[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# This entry automatically added by the Debian installer for a non-linux OS[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# on /dev/sda1[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]title                  Windows Vista (loader)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]rootnoverify    (hd0,0)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]savedefault[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]makeactive[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]chainloader      +1[/SIZE][/FONT]

---

### Post by nothingspecial on 2009-07-22
Its a little L not a number one

---

### Post by starcannon on 2009-07-22
NM I'm slow.

---

### Post by nothingspecial on 2009-07-22
In the first one I mean

```
sudo fdisk -[COLOR="Red"]l[/COLOR]
```

---

### Post by tlillies on 2009-07-22
O man sorry!! i feel really stupid here it is..
 
[FONT=Times New Roman][SIZE=3]Disk /dev/sda: 160.0 GB, 160041885696 bytes[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]255 heads, 63 sectors/track, 19457 cylinders[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Units = cylinders of 16065 * 512 = 8225280 bytes[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Disk identifier: 0x93d593d5[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]   Device Boot      Start         End      Blocks   Id  System[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]/dev/sda1   *           1       13050   104824093+   7  HPFS/NTFS[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/dev/sda2           13051       19457    51464227+   5  Extended[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/dev/sda5           13051       19189    49311486   83  Linux[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/dev/sda6           19190       19457     2152678+  82  Linux swap / Solaris[/SIZE][/FONT]

---

### Post by starcannon on 2009-07-22
Shortly after bios post watch for a message that says Grub Loading press ESC, it'll have a 3 second count down timer, so you gotta be right there; press ESC as it instructs, and you should see your Windows install on a list, just arrow down and press enter.

I'm not sure why your not getting it to boot from a CD at this point though. Perhaps resetting cmos would be the thing to do, and then just run Bios Setup when you boot up afterwards.

---

### Post by tlillies on 2009-07-22
And by the way thanks so much for your help i am only 14 and i am new to this kind of stuff so thanks!!

---

### Post by nothingspecial on 2009-07-22
Everything looks alright to me. Did you manage to boot windows.

---

### Post by tlillies on 2009-07-22
I am not sure i am getting that when i start up. I get the main bios screen for a split second and then it gives my hard drive information and it will let me press Alt-A to see more but then after that it goes strait to more hard drive information and then it does to my boot menu.

---

### Post by tlillies on 2009-07-22
Noi dont know why i didnt but that weird thing is when i was going through the files on ubuntu i found all of the windows files like system32 and things like that so does that have somthing to do with why it does not work and is ther anything i can do to fix it?

---

### Post by nothingspecial on 2009-07-22
Does it try to boot windows?

Did you resize partitions before you installed ubuntu?

How did you resize?

Did you defrag windows first.

Also from ubuntu can you access your data from your windows partition. It should be in your places menu. 

*****EDIT - I see you`ve answered the last question already.

---

### Post by tlillies on 2009-07-22
Alright thats good i have labout a 150 GB hard drive and i partitioned it to 50GB for ubuntu and 100GB for windows. The weird thing is is that ubuntu says that it has 107 GB of hard drive but i am sure that i gave it 50. When i did partition it there was about a 2 second freeze up but i did not think of it as anything. And no i did not defrag my hard drive before installing do you think that could be the problem?

---

### Post by nothingspecial on 2009-07-22
I`ve heard it can be. The trouble is your getting help from the wrong person here. I dual boot but I`ve never had windows so I`ve no experience.

I think it`s something to do with the way windows stores it`s data all over the drive. If you don`t defrag when you partition you can loose data but I`m not really sure on that.

First, if you haven`t already (which you should have done) back up all your photos, music and any other stuff you don`t want to loose to some sort of external media.

Then go to your first post here, click edit, then go advanced. Change the title from Help I`m in a pickle to Can`t boot windows or something like that. Hopefully someone who knows more about this will dive in.

You said some of your apps like synaptic aren`t opening. What happens when you open a terminal and type
```
sudo synaptic
```

---

### Post by tlillies on 2009-07-22
Oh awesome thanks! Snyaptic came right up without a problem. The good news is i have no pictures or media or anything of the sort on the computer so i am set. Thanks so much for all your help i [COLOR=black][FONT=Verdana]appreciate [/FONT][/COLOR]it very much! I have heard that in Snynaptic you can reformat your hard drive (I am not sure if that is true or not) so is that what i should do from here?

---

### Post by nothingspecial on 2009-07-22
Have you got a windows disk that came with your computer. If so you can install windows then reinstall ubuntu ( a hell of a lot easier than installing windows after ubuntu)

I`d wait around and see if someone knows what your windows problem is though first.

I`n the meantime, have a play around with ubuntu. Any problems make a new thread here.

---

### Post by tlillies on 2009-07-22
Alright thanks! The only problem is is that my bois will not let me boot from a disk. Maybe i will try to put my windows on a flash drive and try and boot it from there because i have heard of people doing that. I dont know i guess there are a lot of different things i could try. So far i have had a lot of fun with ubuntu! Thanks again!

---

### Post by Tyke91 on 2009-07-22
I've got a windows/ubuntu dual boot.

@nothingspecial defragging doesn't usually help. gparted doesn't really have problems reading ntfs partitions and changing the file locations on them. This article is pretty interesting and shows how windows stores it's data (vs linux). 
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

@tlillies

Synaptic will not reformat your hard drive, synaptic will install packages (using apt).

gparted WILL reformat the drive, though it will be tough without the ability to boot from a CD.

in a terminal type ```
gksu gedit /boot/grub/menu.lst
``` to pull up that file in a text editor. Scroll all the way to the bottom. You should see this
```

[FONT=Times New Roman][SIZE=3]## ## End Default Options ##[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]title                  Ubuntu 9.04, kernel 2.6.28-11-generic[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]uuid                 597020c1-72cc-4b7c-b254-a482c463af66[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]kernel              /boot/vmlinuz-2.6.28-11-generic root=UUID=597020c1-72cc-4b7c-b254-a482c463af66 ro quiet splash[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]initrd               /boot/initrd.img-2.6.28-11-generic[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]quiet[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]title                  Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]uuid                 597020c1-72cc-4b7c-b254-a482c463af66[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]kernel              /boot/vmlinuz-2.6.28-11-generic root=UUID=597020c1-72cc-4b7c-b254-a482c463af66 ro  single[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]initrd               /boot/initrd.img-2.6.28-11-generic[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]title                  Ubuntu 9.04, memtest86+[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]uuid                 597020c1-72cc-4b7c-b254-a482c463af66[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]kernel              /boot/memtest86+.bin[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]quiet[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]### END DEBIAN AUTOMAGIC KERNELS LIST[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]# This is a divider, added to separate the menu items below from the Debian[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# ones.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]title                  Other operating systems:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]root[/SIZE][/FONT]


[FONT=Times New Roman][SIZE=3]# This entry automatically added by the Debian installer for a non-linux OS[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# on /dev/sda1[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]title                  Windows Vista (loader)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]rootnoverify    (hd0,0)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]savedefault[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]makeactive[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]chainloader      +1[/SIZE][/FONT]
```[FONT=Times New Roman][SIZE=3]

copy the entire windows vista entry and move it to the top of the list, to look like this.
[/SIZE][/FONT]```

[FONT=Times New Roman][SIZE=3]## ## End Default Options ##[/SIZE][/FONT]

 [FONT=Times New Roman][SIZE=3]# This entry automatically added by the Debian installer for a non-linux OS[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]# on /dev/sda1[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]title                  Windows Vista (loader)[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]rootnoverify    (hd0,0)[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]savedefault[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]makeactive[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]chainloader      +1[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]title                  Ubuntu 9.04, kernel 2.6.28-11-generic[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]uuid                 597020c1-72cc-4b7c-b254-a482c463af66[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]kernel              /boot/vmlinuz-2.6.28-11-generic root=UUID=597020c1-72cc-4b7c-b254-a482c463af66 ro quiet splash[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]initrd               /boot/initrd.img-2.6.28-11-generic[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]quiet[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]title                  Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]uuid                 597020c1-72cc-4b7c-b254-a482c463af66[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]kernel              /boot/vmlinuz-2.6.28-11-generic root=UUID=597020c1-72cc-4b7c-b254-a482c463af66 ro  single[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]initrd               /boot/initrd.img-2.6.28-11-generic[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]title                  Ubuntu 9.04, memtest86+[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]uuid                 597020c1-72cc-4b7c-b254-a482c463af66[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]kernel              /boot/memtest86+.bin[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]quiet[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]### END DEBIAN AUTOMAGIC KERNELS LIST[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]# This is a divider, added to separate the menu items below from the Debian[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# ones.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]title                  Other operating systems:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]root[/SIZE][/FONT]


[FONT=Times New Roman][SIZE=3]# This entry automatically added by the Debian installer for a non-linux OS[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# on /dev/sda1[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]title                  Windows Vista (loader)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]rootnoverify    (hd0,0)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]savedefault[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]makeactive[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]chainloader      +1[/SIZE][/FONT]
```[FONT=Times New Roman][SIZE=3]

if it doesn't boot, you should get your windows vista install disk and (somehow) boot it, and run the chkdisk utility.
[/SIZE][/FONT]

---

### Post by tlillies on 2009-07-22
Alright thanks! I tried typing that into the terminal and it seems to be loading but nothing comes up.

---

### Post by nothingspecial on 2009-07-22
Thankyou tyke91 - I know when to bow out when I don`t know what I`m talking about.

@tilles You`re not typing a one instead of an L again are you? Copy and paste this
```

sudo cp /boot/grub/menu.lst ~/menu_backup
```

This backs up your original boot file so that if anything goes bad atleast you can restore to where you were.

Then copy and paste this

```
gksudo gedit /boot/grub/menu.lst
```

What tyke91 wants you to do is move the entry for windows in your boot menu to the top of the list so your default boot is windows. So copy the very bottom paragraph in the file that comes up and paste it just above the Ubuntu stuff underneath the line 

```
## ## End Default Options ##
```

 The /boot/grub/menu.lst file tells the linux boot loader where all the operating systems are and in what order to put them in (that`s sort of over simplifying it). 

Hopefully if windows is at the top it will boot.

***I don`t know why you would leave the windows entry at the end of menu.lst but then I know knothing of this windows malarky***

---

### Post by tlillies on 2009-07-23
Alright thanks for your help everyone! i have fixed the problem. Btw I could get the windows to boot but when it would start to boot it would freeze and the computer would reboot. But thanks goodness i fixed it i was finally able to boot from a disk by pressing F12 repeatably (I mean a lot) while it was starting up. Then i had to manage through some weird different boot menus until finally i found a boot that said DVD and CD drive (the CD drive i tryed to boot off of before was called just CD drive). After that another BIOS screen came up for about 2 seconds saying to boot form CD or DVD press any key now. I don't know why my BIOS is so weird i guess it is because it is a custom built PC. Then i reinstalled windows and ubuntu and everything works like a charm! Thanks again!

                          -Tlillies

---

