---
title: "Fedora installed alongside Ubuntu"
date: 2011-07-15
forum: General Help
---

### Post by tech291083 on 2011-07-15
Hi,

I had Ubuntu 10.10 installed using the install option called Use entire disk. Then I installed Fedora 14 on the same hard drive. I have only one hard drive. Now when I boot the pc there is no boot menu at the boot to choose one of the 2 OS. The pc directly boots into Ubuntu and there is no trace of Fedora whatsoever. I am no expert but I am sure that I installed Fedora on a separate partition. Can anyone please help me? Is it possible to have a pc with two different Linux distros on the same hard drive just like in this case of mine? Thanks a lot....

---

### Post by Ad@m on 2011-07-15
In ubuntu, open a terminal and type

sudo update-grub

This will update your boot menu and should add fedora as an option.

If you still do not see the boot menu, you will need to edit your grub settings and enable the menu.

[http://ubuntu.forumotion.co.uk/t2-how-to-enable-the-grub-boot-menu](http://ubuntu.forumotion.co.uk/t2-how-to-enable-the-grub-boot-menu)

Also make sure the GRUB_TIMEOUT=X option is set to an acceptable value, eg 10 seconds.

Remember to run **sudo update-grub** after changing the /etc/default/grub file.

---

### Post by ajgreeny on 2011-07-15
I think that fedora installs using lvm if you use the default install setup, and I remember having problems in the past with ubuntu not recognising fedora's existence unless I added a few lvm packages to ubuntu.

As I did not then understand anything about lvm, and to be honest the same applies today, I reinstalled fedora with pre-made partitions, not using lvm, and everything was then great, with ubuntu finding the fedora OS.

---

### Post by Ad@m on 2011-07-15
ajgreeny, you are right. Fedora does by default create a lvm layout. Something I hope the OP didnt go for.

---

### Post by tech291083 on 2011-07-15
Thanks a lot for the reply. I did all you have mentioned as a possible solution to my problem, but still when I reboot the pc there is no mention of Fedora in the boot menu. Instead all I see is different (5 of them I think ) options all beginning with the word Ubuntu. Can you please tell me as to how I can hold the boot menu at boot? Any key to be held down so that I can write down all the options and let you guys know, thanks

Here is what I see at the boot prompt...

>  Ubuntu with Linux 2.6.35-22 generic
Ubuntu with Linux 2.6.35-22 generic (recovery mode)
memory test (memtest86+)
memory test (memtest86+, serial console 115200)
Ubuntu with Linux 2.6.35-22 generic (on /dev/sda4)
Ubuntu with Linux 2.6.35-22 generic (recovery mode) (on /dev/sda4)

---

### Post by tech291083 on 2011-07-15
This is how my partition table looked before I installed Fedora 14 (Ubuntu 10.10 was already installed).

/dev/sda

>  /dev/sda1 ext4 36700MB 3000MB
/dev/sda3 ext4 524MB 46MB
/dev/sda4 ...no file type mentioned...  39656MB ..used size unknown...
/dev/sda1 swap 3143MB 0MB


I installed Fedora 14 on sda4.

---

### Post by Ad@m on 2011-07-15
Can you post the output of **sudo fdisk -l**

---

### Post by tech291083 on 2011-07-16
Hi Adam,

Here it is....

>  Device     Boot  Start End  Blocks Id System
/dev/sda1   *        1       3825    30720000   83      Linux
/dev/sda2       9348       9730      3069953     5     Extended
/dev/sda3       3825       3889        512000   83     Linux
/dev/sda4       3889       9347     43846656   8e     Linux LVM
/dev/sda5       9348       9730       3069952   82     Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by tech291083 on 2011-07-16
Hi,

Is there a command in Ubuntu which can be used in a terminal to know whether the pc is a dual boot one. Any way one can know if another OS be it Windows or another type of Linux exists on the same hard drive as Ubuntu does, thanks

---

### Post by wojox on 2011-07-16
Try:

```
sudo fdisk -l
```

---

### Post by tech291083 on 2011-07-16
Hi wojox,

Will this command clearly mention the name of the OS be it Windows or other distro of Linux? Why I am asking is due to the dual boot problem I am having with Ubuntu and Fedora 14. Here is my thread that deals with this very issue. 
[http://ubuntuforums.org/showthread.php?t=1804834](http://ubuntuforums.org/showthread.php?t=1804834)

When I type sudo fdisk - l command, here is what I get as output and I am not sure whether Linux LVM on /dev/sda4 means Fedora. 

>  Device     Boot  Start End  Blocks Id System
/dev/sda1   *        1       3825    30720000   83      Linux
/dev/sda2       9348       9730      3069953     5     Extended
/dev/sda3       3825       3889        512000   83     Linux
/dev/sda4       3889       9347     43846656   8e     Linux LVM
/dev/sda5       9348       9730       3069952   82     Linux swap / Solaris

Thanks....

---

### Post by wojox on 2011-07-16
Copy and paste the results up here. Make sure you use the code tags.

---

### Post by dFlyer on 2011-07-16
Boot off the live cd and use disk utilities to see what OS are installed. Another way is on boot check grub what choices it give you for OS to boot.

---

### Post by cariboo on 2011-07-16
I merged your 2 threads, as they are essentially the same question. Please don't create multiple threads on the same subject.

---

### Post by tech291083 on 2011-07-16
> **cariboo907 said:**
> I merged your 2 threads, as they are essentially the same question. Please don't create multiple threads on the same subject.

Apologies. I did not realise it. Thanks will keep this in mind.

---

### Post by wojox on 2011-07-16
By the looks you have Ubuntu and Fedora installed. What seems to be the issue?

---

### Post by tech291083 on 2011-07-16
> **wojox said:**
> By the looks you have Ubuntu and Fedora installed. What seems to be the issue?

Yes, I also think that Fedora 14 is there already installed, but at boot there is no boot menu to choose Fedora from. PC automatically boots into Ubuntu without displaying the boot options, thanks, please help me..

---

### Post by tech291083 on 2011-07-16
Hi wojox,

I tried to follow the instructions on this page after inserting the Ubuntu 10.10 CD.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

But despite having followed the instructions on this url, the pc still boots into Ubuntu automatically without showing Fedora on the boot menu. When I look at the partitions on the hard drive using the utility called Disk Utility in Ubuntu, here is what I get to see.

```
31 GB ext4 (/dev/sda1)
524 MB ext4
45 GB LVM2 Physical Volume (/dev/sda4)
Extended 3.1 GB
3.1 GB Swap
```

I first successfully installed Ubuntu using the install option Erase entire disk. Then I installed Fedora 14 by choosing the "Shrink drive space" install option. I shrunk the drive to 30000 MB.

---

### Post by tech291083 on 2011-07-16
I have also tried to follow the instructions given on this page at

[https://help.ubuntu.com/community/Grub2#Reinstalling%2520from%2520LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%2520from%2520LiveCD)

One of the things I did was modifying the **/etc/grub.d/40_custom **file in order to add Fedora 14 to the boot menu. Then I typed as root in a terminal the command.

```
update-grub
```

Now here is what my **/etc/grub.d/40_custom  **contains..

```
menuentry "Ubuntu" {
  set root=(hd0,1)
  search --no-floppy --fs-uuid --set cb201140-52f8-4449-9a95-749b27b58ce8
  linux /boot/vmlinuz-2.6.31-11-generic root=UUID=cb201140-52f8-4449-9a95-749b27b58ce8 ro quiet splash
  initrd /boot/initrd.img-2.6.31-11-generic
  }


menuentry "Fedora 14" {
  set root=(hd0,4)
  chainloader +1
  }
```

When restarted the pc did display Fedora as one of the boot options, but when I chose Fedora it showed an error called **Invalid signature, press any key to continue. **

---

### Post by tech291083 on 2011-07-16
Hi Friends,

I have done all I can with your help and that of the internet, but I am sad to accept the fact that it is simply beyond me, that does not mean it is beyond this forum. Still your suggestions are very welcome. 

Now  I feel a bit tired. Can anyone please simple  tell me as to how one can go about having a dual boot  (I have only one hard drive) system with Ubuntu and Fedora on the same hard drive? Which OS should I install first? Which option should I choose at install? Should I go for erase the entire disk or shrink disk or use free space?   Thanks please help me learn this dual boot set up thing, thanks a lot so far...

---

### Post by ajgreeny on 2011-07-16
Ad you already appear to have a non-functional Fedora installed along with a working ubuntu, just reinstall fedora, after first deleting the lvm partition(s) that fedora is on using gparted (from the live ubuntu CD/USB if necessary).

Now with the free space available to you, install fedora again, but this time **do not use the default lvm**, but make partitions manually, (no need for a second swap) and install to the new partition(s).  I have not installed fedora for many years, so I do not know what the installer uses for partitioning, but I suspect it must be fairly easy to sort out how to do what I am suggesting.

If there is an option to choose where grub is installed, and I'm sure there must be, put it on the partition where fedora is installed (sda4?), ignoring any messages about this not being recommended.  This will mean that your boot sequence will still be managed from ubuntu, and that ubuntu will be the only OS available to you when you reboot after the fedora install.  All you need to do now from ubuntu is run ```
sudo update-grub
```which will add fedora to the grub menu for the next boot.

---

### Post by tech291083 on 2011-07-17
Hi ajgreeny,

I am going to try reinstalling Fedora by deleting the lvm partition it installed and creating free space instead where I can install it. But for the time being I am trying two other options/methods and gonna tell you how they go. I will describe the two methods in my next post. Thanks.

---

### Post by tech291083 on 2011-07-18
[B][B][B]
Method one:[/B][/B][/B]

First I installed Ubuntu 10.10 on choosing this intall option Erase and use the entire disk, which actually erased all other partitions and operating systems if any. As I went ahead with the installation here is what the partition table looked liked.

sda

sda1 73319 ext4
sda2 2998   Extended
sd5   2998   Swap

I selected the sda1(73319 ext4) partition to install Fedora 14, pressed Next button and up came a dialog called Partitioning errors, which said that - You have not defined a root (/) partition- so I pressed OK button and then up came another dialog called Create Storage, where I chose Standard Partition and then chose the following parameters from the next Add Partition dialog Mount point (/), File sytem: ext4, Size: 30000 (MB), Fixed size. But this did not work as there was an error which said -Could not allocate requested partitions, not enough free space on disk . I tried smaller sizes such as 3000 MB, even 300 MB, but it would show the same error. 

So I selected the same partition sda1(73319 ext4) again pressed Edit button below and there came a dialog called Edit Partition where I set the following parameters - Mount point (/), Original File sytem: ext4, Format as: ext4, Resize: 2228 (this option was not visible or enabled though). Pressed OK button and a tick appeared next to the sda1(73319 ext4) partition.

Then I selected the same partition - sda1(73319 ext4), and clicked Next to face another dialog called Format Warnings, pressed Format button, then another dialog- Confirm, pressed Write to disk button.

Then on the screen I had - Install boot loader on /dev/sda with two options below.

1. MBR - /dev/sda
2. 1st sector of boot partition - dev/sda1.

I chose the 1st option MBR. Below there was a title called - Boot loader operating system list which had only one option under it called - Fedora /dev/sda1. 

Pressed Next. 

Installation done with no problems, rebooted and completed the remaining options such as license etc and the pc booted into Fedora 14. But when I rebooted the pc there was no boot menu to choose from. I expected it to show two OS - Fedora and Ubuntu. The pc always booted to Fedora no matter what. Where is Ubuntu gone in this case?
----------------------------------------------------------------------------------------------------

**[B][B]Method two:**[/B][/B]

First I installed Ubuntu 10.10 on choosing this intall option Erase and use the entire disk, which actually erased all other partitions and operating systems if any. As I went ahead with the installation here is what the partition table looked liked.

sda

sda1 73319 ext4
sda2 2998   Extended
sd5   2998   Swap

Then the exact story as in method one until I had the following on the screen

Install boot loader on /dev/sda- with two options below.

1. MBR - /dev/sda
2. 1st sector of boot partition - dev/sda1.

This time I chose the 2nd option - 1st sector of boot partition - dev/sda1. Below there was a title called - Boot loader operating system list which had only one option under it called - Fedora /dev/sda1. 

Fedora 14 installation completed. When I rebooted the pc it showed errors on the black screen as follows....

>                                                   Errors...

Booting from local disk...
error: File not found
grub rescue>                                 
I could not boot to Fedora from here. Here also there is not boot menu with two OS options and Ubuntu is completely missing.
---------------------------------------------------------------------------------

Long story, but it was necessary for me to describe as to how I went about setting up a dual boot system (on the same hard drive). So I have used two different methods to dual boot in the first I chose MBR and in the second method I chose First sector of boot partition. I am not sure which one I should be choosing, but the end result is the same, no dual boot possible. Please get me out of this mess. Thanks a lot.

---

### Post by tech291083 on 2011-07-19
This is method three:

This involves legacy distros namely Ubuntu 6.06 LTS and Fedora 12. Here I have just tried to follow the instructions give on this page.

[http://software.intel.com/en-us/articles/build-an-ubuntu-fedora-dual-boot-system/](http://software.intel.com/en-us/articles/build-an-ubuntu-fedora-dual-boot-system/)


I have reached the last step of the last stage called - Modifying Fedora to support dual boot- and I have reached the last step there - step 11. Which is like

> [FONT=&quot]11.[/FONT][FONT=&quot]Reboot and check that both OS&#8217;s work now.  If your Ubuntu doesn&#8217;t boot, check VERY carefully for typos as everything needs to be exactly right for this to work.[/FONT]
 Now the pc shows two distros when booted Ubuntu and Fedora, but it does not boot to Ubuntu. It only boots to Fedora. Do not know why? When I try to boot to Ubuntu comes an error 

> Error 15: File notc found press any key to continue...Here is the output of fdisk -l command in a terminal in Fedora 12

> [root@localhost bhavin]# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000eccce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4589    36861111   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda3   *        4590        4615      204800   83  Linux
/dev/sda4            4615        9355    38078095   8e  Linux LVM
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/dm-0: 36.9 GB, 36876320768 bytes
255 heads, 63 sectors/track, 4483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 2113 MB, 2113929216 bytes
255 heads, 63 sectors/track, 257 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition tableHere is how my boot/grub/menu.lst file looks in Fedora 12. I have modified it as per the Intel web page guidelines to add a few lines of Ubuntu...

> 
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/mapper/VolGroup-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=15
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.31.5-127.fc12.i686.PAE)
    root (hd0,2)
    kernel /vmlinuz-2.6.31.5-127.fc12.i686.PAE ro root=/dev/mapper/VolGroup-lv_root  LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.31.5-127.fc12.i686.PAE.img


title Ubuntu 
    root (hd0,0)
    kernel /boot/vmlinuz-2.6.15-23-generic root=UUID=cd194d06-1824-4aac-b67b-83f26fe6f743 ro quiet splash
    initrd /boot/initrd.img-2.6.15-23-generic


#title Ubuntu
#    rootnoverify (hd0,0)
#    chainloader +1
Here is how the same file ie - boot/grub/menu.lst looks in Ubuntu 6.06 LTS.

> 
 title Ubuntu 
    root (hd0,0)
    kernel /boot/vmlinuz-2.6.15-23-generic root=UUID=cd194d06-1824-4aac-b67b-83f26fe6f743 ro quiet splash
    initrd /boot/initrd.img-2.6.15-23-generic
Initially this file did not exist in Ubuntu 6.06 and I had to created one by typing the following command as root in a terminal, which basically asked me that the file did not exist and whether I would like to create one, to which I said yes. Then I types the same command ie - sudo update-grub to update grub.

> sudo update-grubThis is what I see using the Palimpsest Disk Utitlity program in Fedora 12. 

> 38 Gb File system 
Linux Ext3 (Version 1.0)

3.1 GB Extended (Contains logical partitions)

3.1 GB Swap space

210 MB File system
Linux Ext4 (Version 1.0)
Bootable

39 GB LVM2 Physical Volume

Here only one partitions is bootable and that is the 210 MB - Linux Ext4 - one. Should I also make all other paritions or any other partition in particular bootable?

I have almost done it, but there seems to be a small problem as of now. Can you please help me get over the last hurdle? Can you please guide me? If this does not work then I will follow Ajgreeny's steps. Thanks

---

### Post by ajgreeny on 2011-07-19
If I were you I would start again from square one, as I assume you have no usable OSs on the disk at the moment.

1.  Run Ubuntu 10.10 live CD and from there run System->Administration->Gparted and delete all the partitions on disk.

2.  Still with the live CD and Gparted, make a large extended partition of the whole disk.  Then within the extended partition make two new logical ext4 partitions of about 10GB each, a logical swap partition of about 2 - 4GB, and the rest as another large logical ext4 partition.

3.  Install fedora first, but at the partitioning step choose to set your own partitions (I don't know the exact wording, but it should be obvious and is usually the last option).

4.  Click on the first of the 10GB partitions and edit it to use as ext4, and mountpoint  / (root).

5.  Edit the large partition to use as ext4, mountpoint /home.  You do not need to format this partition again.

6.  As you have already made a swap partition you can ignore that; it will be found and used by your install without you doing anything.

7.  Make sure that the grub bootloader is put on /dev/sda, not to a partition such as /dev/sda1.  Continue the install choosing username etc etc to the end then reboot and check fedora works.

8.  Boot to the ubuntu live CD and start the install.

9.  When you get to the partitioning, make sure you choose the manual option.

10.  This time set the second 10GB partition to be used as ext4 and mountpoint /, but make sure you get the right 10GB partition or your fedora will be gone.

11.  Again use the large partition to be used as ext4 and mountpoint /home, but do not format it.  Ignore swap again; it will be found and used.

12.  Continue the install of ubuntu, making sure you choose a different username to the fedora.  Grub2 bootloader will be placed on /dev/sda by default, and should find and add fedora by default.

13.  Reboot.  You should see a grub menu with both ubuntu and fedora, and ought to be able to boot to either from that.

It is important to have different usernames for the two OSs as a shared home folder for each is impossible as fedora has a UID of 500 and above for its users, ubuntu starts at 1000, so you can not share a home, and it can make problems with shared data as well, though that can be overcome with a shared ntfs /data partition if you wish to go that far.

Sorry this is a long and complicated post, and I am sure there will be others who would do things in a different way, but this should work and overcome the LVM problems that fedora likes to throw at you if you choose the default partitioning scheme.

---

### Post by tech291083 on 2011-07-20
Hi,

Is it a good idea to use Ubuntu alternate install CD when creating a dual boot system with other OS such as Fedora as the alternate install CD is generally provides good support for Logical Volumes as used by OS such Fedora in particular? Thanks

---

### Post by Blasphemist on 2011-07-20
No, don't use the alternate cd and don't use lvm. Do just a prescribed in post 25.

---

### Post by tech291083 on 2011-07-20
> **Blasphemist said:**
> No, don't use the alternate cd and don't use lvm. Do just a prescribed in post 25.

Ok, thanks. I was a bit curious when I came across this url

[http://www.linuxbsdos.com/2011/06/20/dual-boot-fedora-15-and-ubuntu-11-04-with-either-side-on-an-lvm-partitioning-scheme/](http://www.linuxbsdos.com/2011/06/20/dual-boot-fedora-15-and-ubuntu-11-04-with-either-side-on-an-lvm-partitioning-scheme/)


It basically deals with a dual boot with Fedora 15 and Ubuntu 11.04. Here what the url says

> Ubuntu Desktop comes with a simple, point-and-click installer, but it does not have support for disk encryption and LVM, the [Linux Logical Volume Manager]("http://www.linuxbsdos.com/2008/11/17/linux-logical-volume-manager/"). The Alternate Installer edition uses an ncurses, keyboard-based navigation, but with support for LVM and disk encryption.

---

### Post by Blasphemist on 2011-07-20
I have both of those installed, among others. From what I've seen from those more knowledgeable than I in these forums it is not recommended to deal with lvm. I always partition ahead of time then tell my install what partition(s) to use as described above.

---

### Post by tech291083 on 2011-07-20
> **Blasphemist said:**
>  it is not recommended to deal with lvm. I always partition ahead of time then tell my install what partition(s) to use as described above.


Ok, yours is a very interesting observation, one which demands serious thinking on my part. Will definately keep this in mind in future efforts, thanks a lot..

---

### Post by tech291083 on 2011-07-21
> **ajgreeny said:**
> If I were you I would start again from square one, as I assume you have no usable OSs on the disk at the moment.


Right now, I have two OS installed Ubuntu 6.06 LTS and Fedora 12. But only Fedora 12 boots and Ubuntu doesn't, despite being there on the boot menu as one of the two options to choose from. But whatever the situation, I am going to delete all paritions and that too using that command as I feel more confident of using it again. Could be a correction here, so please feel free to do so.

> 
Sorry this is a long and complicated post, and I am sure there will be others who would do things in a different way, but this should work and overcome the LVM problems that fedora likes to throw at you if you choose the default partitioning scheme.

Please do not say sorry, you have been helping me out with this learning process with a great deal of patience and maturity of an experienced Ubuntu user and I appreciate the efforts you make for me and that is why I love this forum. 

My situation - I have only one hard drive ie 80 Gb and I need to dual boot with Fedora 12 or 14 and Ubuntu 6.06 or 10.10 - so where do I begin? Yes, I have 2 Fedora CDs one with Fedora 12 and another with Fedora 14 on it. The same goes for Ubuntu one is 6.606 LTS and the other is 10.10.

Please give me some good plan step by step, one that I can follow easily. I am desperate to learn dual-booting, thus need your help. Thanks, waiting for your reply.

---

### Post by tech291083 on 2011-07-22
I would like to dual boot with Fedora 14 and Ubuntu 10.10 if possible, please guide me, thanks

---

### Post by nothingspecial on 2011-07-22
Hi tech, you've been guided, but

Make 4 partitions

2x10-12 gig each for Ubuntu and Fedora

One 2gig for swap

The rest for your data.

Install Fedora to one of the 10-12 gig partitions. When creating your user use the fedoras installer option to specify your uid and gid. Set them to 1000

Install Ubuntu to the other one, use exactly the same username and password.

---

### Post by tech291083 on 2011-07-22
Hi nothingspecial,

Thanks a lot first of all for the reply, appreicated. 

As you can see I have tried many methods with different versions of Fedora (12 and 14) and different versions of Ubuntu as well (6.06 LTS and 10.10), but despite doing everything by the book or web sites mentioned earlier, I hae not been able to get a working dual-boot system. I have spent many hours figuring out what could have gone wrong, but I am no expert. People like ajgreeny and yourself and others on this forum have tried to help me. I appreciate that. 

This is my method four...

It involves Fedora 14 and Ubuntu 10.10. Here is the link to a site from where I followed the guidelines although the website has two other versions namely Fedora 15 and Ubuntu 11.04. 

[http://www.linuxbsdos.com/2011/06/20/dual-boot-fedora-15-and-ubuntu-11-04-with-either-side-on-an-lvm-partitioning-scheme/](http://www.linuxbsdos.com/2011/06/20/dual-boot-fedora-15-and-ubuntu-11-04-with-either-side-on-an-lvm-partitioning-scheme/)

Here is what I just did trying to dual boot with Fedora 14 and Ubuntu 10.10

1. Inserted Fedora 14 DVD and went to parition step after inistally choosing the Create Custom Layout option. 

2. Here what I did and here is how my partition table looked at that stage. But I could not go further from there after creating all the necessary LVM Logical Volumes for Fedora 14 that in my opinion (I could be 100% wrong here, please correct me if required) are generally necessary.

[PHP]Device      Size(MB)     Mount Point      Type       Format

LVM Volume Groups

FedoraVolGroup  36992

home             10016             /home            ext4        tick
root                5024              /                    ext4        tick
swap              2016              NA                swap       tick
free               19936

Hard Drives

sda

sda1          37000            FedoraVolGroup  Physical Vol(LVM)  tick
sda2          500                /boot                  ext4                      tick 
free            38818
[/PHP]

Apologies, the table does not look properly formatted, but I hope you will get the info.

After creating the above mentioned paritions root, swap and home as LVM Logical Volumes and boot partition as a Standard Partition (it would not allow me to mount boot partition on /boot when created it as an LVM Logical Volume 
so I had to create it as a standard partition), I started creating the same partitions (root, swap and home as LVM Logical Volumes and boot partition as a Standard Partition), but it would not allow me do so saying all the respective mount points were already in use namely /boot, /, /home. So am I wrong here by assuming that partitions for both Fedora and Ubuntu can be created in advance and both the OS can then be installed in their respective empty spaces? I have tried my best so far and I need some solid guidance now.

1. Which are the paritions that are a must for both the OS here considering the fact that it is a dual-boot system?

2. Should one be creating separate root, swap, home and boot partitions for both the OS?

3. After creating paritions for both of them is it necessary to select the respective free space line in the partition table during installtion of both the OS to make sure that they both are installed in their respective free spaces? Or the installer for both automatically does so and one does not need to select the free space and just press the button Install Now?

4. Where are the files and documents (created by users) actually stored in both OS? Is it the free space or home space?

I now believe that I should only be using the Ubuntu alternate install CD to make things ie partitoning issues easy for me. But I am not sure. What do you think? Can I do it without it? Here is what the site says here

[http://www.linuxbsdos.com/2011/06/20/dual-boot-fedora-15-and-ubuntu-11-04-with-either-side-on-an-lvm-partitioning-scheme/](http://www.linuxbsdos.com/2011/06/20/dual-boot-fedora-15-and-ubuntu-11-04-with-either-side-on-an-lvm-partitioning-scheme/)

> Ubuntu Desktop comes with a simple, point-and-click installer, but it does not have support for disk encryption and LVM, the Linux Logical Volume Manager. The Alternate Installer edition uses an ncurses, keyboard-based navigation, but with support for LVM and disk encryption.


---

### Post by nothingspecial on 2011-07-22
The use of the same uid and gid is the important bit. That's why I suggest installing fedora first because you can specify at install.

Install Ubuntu second because grub2 will pickup fedora when you install.

I do not have a shared /home or 2 seperate /homes in either install.

Both homes are included in the / directory. The shared Data partition is the key.

You then get rid of all the folders (Music, Documents etc) in both home directories and make them in the data partition. Then link them to both of your homes. Because you have the same uid and gid you will have r/w permissions to that partition from both distros.

---

### Post by tech291083 on 2011-07-22
> **nothingspecial said:**
> 
Make 4 partitions

2x10-12 gig each for Ubuntu and Fedora..One 2gig for swap....
The rest for your data.

This is really interesting as per the web site that I have mentioned earlier, I thought that I needed to create 4 partitions (boot - a standard partition, root, swap and home - these 3 LVM Logical Volumes) for Fedora and Ubuntu separately. This is the impression I got from that web site. May be I was misguided. 

After creating 4 paritions for both of them is it necessary to select the respective free space line in the partition table during installtion of both the OS to make sure that they both are installed in their respective free spaces? Or the installer for both automatically does so and one does not need to select the free space and just press the button Install Now?

Where are the files and documents (created by users) actually stored in both OS? Is it the free space or home space?

I now believe that I should only be using the Ubuntu alternate install CD to make things ie partitoning issues easy for me. But I am not sure. What do you think? Can I do it without it? Here is what the site says...

[http://www.linuxbsdos.com/2011/06/20/dual-boot-fedora-15-and-ubuntu-11-04-with-either-side-on-an-lvm-partitioning-scheme/](http://www.linuxbsdos.com/2011/06/20/dual-boot-fedora-15-and-ubuntu-11-04-with-either-side-on-an-lvm-partitioning-scheme/)

> 
Ubuntu Desktop comes with a simple, point-and-click installer, but it does not have support for disk encryption and LVM, the Linux Logical Volume Manager. The Alternate Installer edition uses an ncurses, keyboard-based navigation, but with support for LVM and disk encryption.



> 
Install Fedora to one of the 10-12 gig partitions. When creating your user use the fedoras installer option to specify your uid and gid. Set them to 1000


I do not know how to go about the user's uid and gid.

Thanks please do reply as I need a lot of guidance before I reach my destination.

---

### Post by nothingspecial on 2011-07-22
Forget all those complicated things you are reading and start the whole thing again with the latest version of both Ubuntu and Fedora.

Now while I could talk you through a Ubuntu install without looking (because I've done it hundreds of times), I'm not so experienced in Fedora, but.......

Somewhere in the Fedora installation process, when you create your user, there is an option to specify the uid and gid. Look out for it. You MUST set them to 1000 because that's what Ubuntu uses by default.

The config files will be stored in each distros /home/username, they do not take up much space.

Your data files however should be symlinked from the other partition.

When you change ownership and permissions in linux, you type your username but linux uses the uid and gid, that's why they are so important.

Boot up either live cd and make the partitions. I wouldn't choose to do it at install.

---

### Post by tech291083 on 2011-07-22
> **nothingspecial said:**
> Forget all those complicated things you are reading and start the whole thing again with the latest version of both Ubuntu and Fedora.


Ok, then I am starting all over again, this time with your guidelines in mind. I have Ubuntu 10.10 and Fedora 14 as the latest version for both the OS.

Now please guide me step by step. 

Which one I should install first? And how? Please tell me step by step. I will start with that one only. My hard disk is 80 GB in size.

---

### Post by nothingspecial on 2011-07-22
I don't think I'm explaining this very well. I'll try again.

Fedora will allow you to set uid and gid during install. Ubuntu will not.

Ubuntu will automatically add Fedora to your boot menu when you install, Fedora will not add Ubuntu.

_Steps_

**1.**

Make 4 partitions with either live cd before install.

1 12gig ext4
2 12gig ext4
3 whatever is left over ext4
4 2gig

Use the partitioner to label the large left over partition "data"

**2.**

Install fedora to one of the 12 gig partitions. Set it's mountpoint as /. Choose to use the 2 gig one as swap. Specify user uid and gid as 1000.

**3.**

Install Ubuntu in exactly the same way to the other 12 gig partition.

**4.**

Boot Ubuntu. Add the data partition to fstab (so that it mounts at boot)

```
[COLOR="Blue"]sudo[/COLOR] mkdir /media/data
echo 'LABEL=data     /media/data       ext4       defaults    0    0' | [COLOR="Blue"]sudo[/COLOR] tee [COLOR="Red"]-a[/COLOR] /etc/fstab
[COLOR="Blue"]sudo[/COLOR] mount -a
```

**5.**

Make sure you own the data partition.
```

[COLOR="Blue"]sudo[/COLOR] chown -R $USER:$USER /media/data
```

**6.**

Move your folders to the data partition and link them back to $HOME

```
mv Documents Downloads Music Pictures Ubuntu\ One Videos /media/data
ln -s /media/data/* ~/
```

You will see your folders reappear. They physically exist in the data partition but can be accessed through your home folder.

**7.**

Do exactly the same thing from fedora from step 4 onwards. The only difference is that unless you configure sudo (which this thread is not about), you have to do it as root. So type ```
su
```

Then repeat the steps removing the sudos highlighted in blue from each command. The only other difference is to delete the folders from the fedora home rather than moving them, because they are already on the data partition. So step 6 in fedora would be


```
rm -r Documents Downloads Music Pictures Videos
ln -s /media/data/* ~/
```



Whatever you do, do not miss the -a in the command in step 4.

That's it. Whenever you want a new folder in your home. Make it it your data partition and link it to your home.

---

### Post by tech291083 on 2011-07-22
> **nothingspecial said:**
> 

**1. **
Make 4 partitions with either live cd before install.

1 12gig ext4
2 12gig ext4
3 whatever is left over ext4
4 2gig

Use the partitioner to label the large left over partition "data"


Ok,

I have no operating system installed on the entire drive as I had earlier deleted all the partitions myself, so I just inserted the Ubuntu 10.10 CD and booted with it. After booting just used the GParted Partitioning program to do the following.

Created 4 partitions.

1st partition - 12 GB - ext4 - primary partition
2nd partition - 12 GB - ext4 - primary partition
3rd partition - 2 GB - swap
4th parition unallocated space converted into - ext4 - primary partition - labeld it data.

Restarted the pc with Fedora 14 DVD inserted in the DVD drive. Started installation. Reached the stage where installation method has to be chosen. Chose Custom Layout method and went to the stage where partitioning has to be done. Here this is how my partition table looks like.

sda1 - 12000 MB -  ext4   (no mount point)
sda2 - 12000 MB -  ext4   (no mount point) 
sda3 -  2000 MB -  swap
sda4 -  50318 MB -  ext4   (no mount point) - leftover - labeled data -

Chose the first 12 GB partition and pressed the Next button at the bottom, but there was an error - You have not defined a root (/) partition, which is required for installation of Fedora to continue.- I pressed OK and  again selected the  12 GB partition and pressed the create button and tried to create a standard partition - Chose / mount point - ext4 - size 2000 MB - Fixed size - Pressed OK button, but there was an error - Could not allocate requested partitions: not enough free space on disks -

Now, I am stuck here, please guide me. Thanks

---

### Post by Blasphemist on 2011-07-22
What you need to do is just edit and not create at the partitioning. I think it is just highlight the desired partition and press enter but you might need to double click. If there is an edit selection use that but I don't remember if there is. Then set the mount point as /, label the partition and check format the partition.

---

### Post by tech291083 on 2011-07-23
> **nothingspecial said:**
> 

**2. **Install fedora to one of the 12 gig partitions. Set it's mountpoint as /. Choose to use the 2 gig one as swap. Specify user uid and gid as 1000.




Ok, step one completed. Problem with step 2 do not know how to set up uid and gid. Googled but could not figure out.

---

### Post by tech291083 on 2011-07-23
> **Blasphemist said:**
> What you need to do is just highlight the desired partition and press enter but you might need to double click. 

Thanks a lot, I highlighted the parition and double clicked and it worked. Thanks a lot.

---

### Post by tech291083 on 2011-07-23
Ok, 

I managed to figure out how to set the uid and gid to 1000. It happen during the second stage of Fedora installation after rebooting. When specifying a user (not root, but ordinary user) there is one option under it called Advanced and that does the trick with a GUI. Thanks..

---

### Post by tech291083 on 2011-07-23
> **nothingspecial said:**
> 

**3. **Install Ubuntu in exactly the same way to the other 12 gig partition.



Just started step 3. 

Installing Ubuntu 10.10, reached the step - Allocate drive space - here when I select the second 12 GB partition - sda2 - it shows an error - No root file system - so I click Ok button and then double-click the same parition to create a root file system then there is one dialog box asking me to create a partition,  but what size should I choose for this parition? It should be ext4, right? Should I tick the Format this partition option as well? Ane mount point here should be / right? Thanks

---

### Post by tech291083 on 2011-07-23
Ok, solved this as well hopefully. I created the root partition with ext4, 2000 MB and ticked the format this parititon option as well. So the partition table was updated and a new entry for root parition was created with 2000 MB space. But the remaining of the second of the 12 GB parition meant for Ubuntu installation is now labled unusable with a reduced space size of around 10 GB. So I selected the newly created root parition and deleted it. Now the unusable space  is labled free space, so I selected it and edited it as a primary parition with mount point / and ext4 and then clicked Install Now button. The installation started without asking me for a root partition.

---

### Post by tech291083 on 2011-07-23
Bingo, Ubuntu 10.10 installation finished successfully and rebooted. Now I can see both the OS Ubuntu 10.10 and Fedora 14 on the boot menu. But it stays for a very small amount of time, say 5 seconds, so need to edit the /boot/grub/menu.lst file in Fedora, I think. This is amazing, I have been trying to see this for ages now. And guess what the system boots into both the OS. This is so far so good and I am very happy as of now. I am going nuts. Thanks a lot nothingspecial, your very special to me. Now need to do the remaining steps from 4.

---

### Post by tech291083 on 2011-07-23
Edited the /boot/grub/menu.lst file in Fedora and default timeout set to 120 seconds, rebooted, the boot menu still does not stays long enough, only 5 seconds. Do I need to change anything in Ubuntu now? Any similar files that control the boot menu there in Ubuntu? Thanks

---

### Post by tech291083 on 2011-07-23
The /boot/grub/menu.lst file in Ubuntu does not seem to exist. So I had a look at the equivalent file (if I am correct to call it so) called /boot/grub/grub.cfg - and is an entry made automatically by Ubuntu. Done automatically - Ubuntu is great and generous enough to accomodate Fedora, Fedora should do the same.

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Fedora (2.6.35.6-45.fc14.i686) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e60c5bc9-3a4a-4a23-91dd-8e421275ee71
    linux /boot/vmlinuz-2.6.35.6-45.fc14.i686 ro root=UUID=e60c5bc9-3a4a-4a23-91dd-8e421275ee71 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.35.6-45.fc14.i686.img
}

```

---

### Post by Elfy on 2011-07-23
If you installed ubuntu second then you need to deal with the ubuntu bootloader not the fedora one :)

```
gksu gedit /etc/default/grub
```

edit the grub timeout line, save, close gedit and update grub

```
sudo update-grub
```

As an aside if you had installed grub2 in fedora and run the command to update grub there it would have found ubuntu - or at least it worked fine for me ;)

---

### Post by tech291083 on 2011-07-23
> **forestpiskie said:**
> If you installed ubuntu second then you need to deal with the ubuntu bootloader not the fedora one :)

```
gksu gedit /etc/default/grub
```edit the grub timeout line, save, close gedit and update grub

Ok, so only the Ubuntu file needs to be modified, did not know that, thanks. Yes just edit the /etc/default/grub nad it works with the changed time. thanks a lot. 

[QUOTE]
```
sudo update-grub
```As an aside if you had installed grub2 in fedora and run the command to update grub there it would have found ubuntu - or at least it worked fine for me ;)No idea whether it is grub2 in Fedora. Need to check this...thanks

---

### Post by Elfy on 2011-07-23
It's not _unless you installed it_ - fedora uses the grub not grub2. No need to check :)

How it works basically (unless you tell whatever you are installing not to) is that the last installed system will install it's bootloader and takeover. 

Generally I install the first and let it install it's bootloader to the mbr, things I install afterwards I tell to install their bootloader to whatever partition I install it on - for instance I have fedora on sda4 (it's bootloader is there) eOS is on sda5 (same) then once I've finished I run the update grub command and hope it finds them.

Luckily for me I never used lvm in fedora ;)

---

### Post by tech291083 on 2011-07-23
> **forestpiskie said:**
>  fedora uses the grub not grub2. No need to check..


Yes you are right 100%

Just did in Fedora

```
grub --version
```It is grub 0.97.

> Last installed system will install it's bootloader and takeover.
Yes. I just realized that after trying so many methods and wasting more than a week.

>  Generally I install the first and let it install it's bootloader to the mbr, things I install afterwards I tell to install their bootloader to whatever partition I install it on - for instance I have fedora on sda4 (it's bootloader is there) eOS is on sda5 (same) then once I've finished I run the update grub command and hope it finds them.Great. I agree. First OS always on the MBR and the second, third on their respective partitions/free spaces (decided in advance) for them.

>  Luckily for me I never used lvm in fedora ;)I did not know that either. I thought it was always compulsory with Fedora. But this time in this method I have not used LVM at all even for Fedora just primary partitions throughout. Again you have  help me deal with another of my  misconceptions. Thanks a lot. Nice to have you  on this forum.

---

### Post by Elfy on 2011-07-23
> ...wasting more than a week...It's only wasted time if you forget what you have found out :)

> Great. I agree. First OS always on the MBR and the second, third on their respective partitions/free spaces (decided in advance) for them.While it works for me that way - linux is one of those things where you'll get many people all with different 'works for me's' :)

For instance - I never use a seperate /home - many people do. I much prefer a small / including /home and then all my data elsewhere mounted with fstab. Mostly because the first thing I do in whatever install is to install codecs and mount my music drive, much easier when it's on it's own somewhere :)

---

### Post by tech291083 on 2011-07-23
> **forestpiskie said:**
> It's only wasted time if you forget what you have found out :)

I wasted 10 days on this. Every day hours and hours, but I knew that they are people with good and practical knowledge like yourself and they would help me do things that I am not able to do generally due to lack of Linux experience. But I have always been proved right when it comes to help from online forums and this time too, it was no different. I win here again. You made this possible and so many others uncluding ajgreeny. I have learned Linux the hard way, but never given up. 

When I read that article on this site about dual booting, it misguided me completely. And I was forced to believe that without the Ubuntu alternate install CD, which is as per the site great at setting up LVMS etc, would be the only solution. I thought it was necessary to set up boot, root, home, swap and free space for both the OS in advance. So that would have been 5 paritions each and a total of 10 partitions. 

[http://www.linuxbsdos.com/2011/06/20/dual-boot-fedora-15-and-ubuntu-11-04-with-either-side-on-an-lvm-partitioning-scheme/](http://www.linuxbsdos.com/2011/06/20/dual-boot-fedora-15-and-ubuntu-11-04-with-either-side-on-an-lvm-partitioning-scheme/)

Never knew that swap could be common to both.
Never knew that / can contain /home
Never knew that Fedora does not always need LVM to be installed, but it is possible with primary/standard partitions. 

Thanks a lot

My Linux knowledge, very little though, comes from people like you, thanks a lot again. Now I need to focus on the remaining step from 4.

---

### Post by Elfy on 2011-07-23
Don't include me in your list of help - I turned up when most of the work had been done :)

> 4. Where are the files and documents (created by users) actually stored in both OS? Is it the free space or home space?IS this the #4 you mean? If so

All users get space in /home

If you had 3 users - 1,2,3 there would be 3 'folders' on /home

/home/1 , /home/2 and /home/3

If that's not the #4 it might be useful to state it again given the length of the thread.

---

### Post by tech291083 on 2011-07-23
This post is about post no. 39 by user nothingspecial, which basically describes the 7 steps. 

Now before I start doing the step 4 and followed till step 7, there are certain queries I need to make, so please help me here. so far so good.

As far as I understand step 4 to 7 are for making the data  partition (the largest one) accessible to both Ubuntu and Fedora , right?

During both Fedora and Ubuntu installations I gave set different passwords for root account and for the user (ordinary user as I generally refer to), will this cause a problem? Fedora root password is different than Ubuntu root password. Fedora user name and password both are different than Ubuntu username and password.

During Fedora installation I had to manually assign 1000 as uid and gid for the user, while Ubuntu does this by default, am I correct here?

If I am using Fedora and it has a total size of 12 GB as I understand then what happens if the data in Fedora partition exceeds 12 GB limit? If Ubuntu partition also has the same problem then what is the solution? Is it possible to store the remaining data for both the OS (over 12 GB) in the data partition? If I am not wrong that the reason for following the steps 4 to 7 for both the OS, am I correct here?

If for example I do not follow step 4 to 7, can I still use both the OS normally? Saving, creating, modify documents and files whenever I want in the respective partitions? Then what will happen to the data folder? Will I be able to devide it in half and give one half to Fedora and the other to Ubuntu partition? Sorry, it might seem silly, but I am in need to clarification here.

Next time in the same case, if I just start with 3 paritions one for Fedora, one for Ubuntu and one for swap (2 GB, common to both if I am correct and there is no need to create separate swap partition for each of the OS), will that still work as a dual boot? I will just do the math like. Devide the whole disk by two after taking away the 2 GB for common swap from the total disk size. Something like 80 GB total hard disk size - minus 2 GB for common swap - so remaining 78 GB - this means 39 GB each for Fedora and Ubuntu. I will keep storing documents in the respective paritions of the OS that I intend to use.

---

### Post by tech291083 on 2011-07-23
> **forestpiskie said:**
> 
All users get space in /home

If you had 3 users - 1,2,3 there would be 3 'folders' on /home

/home/1 , /home/2 and /home/3


Thanks you have given a great reply here.

---

### Post by tech291083 on 2011-07-23
> **forestpiskie said:**
> 
/home/1 , /home/2 and /home/3


Ok,

If I install only one OS (Fedora or Ubuntu) on the entire hard drive, which I often do as it seems to be the easiest thing to do, from a situation where there is nothing on the hard drive, no OS at all , as I now use the dd command and delete all the paritions using a live CD, will I have to create boot, swap, home and / partitions manually or they will be created automatically? I want to just click Next all the time and not worry about them. Thanks.

---

### Post by Blasphemist on 2011-07-23
> **tech291083 said:**
> Ok,

If I install only one OS (Fedora or Ubuntu) on the entire hard drive, which I often do as it seems to be the easiest thing to do, from a situation where there is nothing on the hard drive, no OS at all , as I now use the dd command and delete all the paritions using a live CD, will I have to create boot, swap, home and / partitions manually or they will be created automatically? I want to just click Next all the time and not worry about them. Thanks.

Using the default process where you just answer questions only / and swap partitions will be created. I do as described by someone else above and do my own partitioning but I don't created more that a / partition for any distro. I do have a shared data partition for music and pictures that I mount from all distros. You also need only one swap partition that all distros use. More than one isn't used at any one time so you just loose space but it isn't much and doesn't make a lot of difference.

---

### Post by tech291083 on 2011-07-23
> **Blasphemist said:**
> Using the default process - only / and swap partitions will be created.

Ok, I need to know that well enough.

> You also need only one swap partition that all distros use.
This is very important for me to know, if I in future have 3 or 4 distros on a single disk (I think it is possible, provided there is enough space), then this will help a lot. 

Thanks a lot for the reply, appreciated.

---

### Post by nothingspecial on 2011-07-23
You are almost there :D

It's important to understand that both your /home directories exist within each distros / partition.

Aslong as you are not going to install every app that exists then 12 gig will be fine.

Your settings will also be stored there.

The data partition is going to store your personal files (documents, music etc etc).

But you will have links to them in your /home

When you rip a cd to your Music folder in Fedora, next time you boot Ubuntu, it will be there and accessible. Next time you create an open(libre)office document in Ubuntu it will be there in your Documents folder next time you boot Fedora.

---

### Post by nothingspecial on 2011-07-23
> **tech291083 said:**
> 

During both Fedora and Ubuntu installations I gave set different passwords for root account and for the user (ordinary user as I generally refer to), will this cause a problem? Fedora root password is different than Ubuntu root password. Fedora user name and password both are different than Ubuntu username and password.



On this, I have to confess I am unsure. As far as I understand the theory, the username and password should not matter...... as I have said it is the uid and gid that is important.

However, due to my lack of understanding of this, I have always used the same username and password on both uid 1000 accounts.

Root password will not matter. The main thing is shared access to the data partition for both users, after all, root can do what she likes.

---

### Post by tech291083 on 2011-07-24
Hi nothingspecial,

Thanks for the reply. Really good ones to be honest with you. Now I am waiting for some really clear and to the point anwsers to a few questions that I have raised in post no. 57. I hope that someone will anwser them (please reply with quotes/questions as it is a bit difficult to move pages, thanks) to clarify my doubts regarding the whole dual boot method suggested by **nothingspeical**. Post no. 39 - 7 steps. His is the only method that has worked so far and seems relatively easy to follow. Thanks

---

### Post by tech291083 on 2011-08-10
Now, I am thinking of installing a third OS - Ubuntu 10.04 LTS alternate install CD version - on the same hard disk which already has a dual boot scenario with Fedora 14 and Ubuntu 10.10 as I followed the steps described by user named nothingspecial in post 39 of this thread only.

I hope that I can keep only one swap partition (a parimary partition created before installing Fedora 14 and Ubuntu 10.10) and install my 3rd OS - Ubuntu 10.04 LTS alternate install CD version. After that I might install 4th OS- Ubuntu 10.04 LTS, I know this is crazy, but I just want to try. 5th OS Gentoo 11.0, 6th OS Debian 6. Now I hope that the 3rd one, 4th one and 5th one, 6th one all will be using  the same swap partition as per my planning and understanding. My rough plan is

3rd distro - Ubuntu 10.04 LTS alternate install CD version 
4th distro - Ubuntu 10.04 LTS
5th distro - Gentoo 11.0
6th distro - Debian 6

Let us hope and pray that I get all of them, 6 in all, installed and working properly. Thanks

---

### Post by tech291083 on 2011-08-11
Ok,

I have installed my third OS/distro - Ubuntu 10.04 LTS alternate CD version - on the same hard drive alongside Fedora 14 and Ubuntu 10.10 and here is how my partition table looks like in an app called Disk Utility as shown in the images attached. Here is another info from commands..........

```
james@ubuntu10:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000034f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1530    12288000   83  Linux
/dev/sda2            1530        3060    12286976   83  Linux
/dev/sda3            3060        3315     2048000   82  Linux swap / Solaris
/dev/sda4            3315        4896    12695552   83  Linux

Disk /dev/sdb: 4009 MB, 4009754624 bytes
51 heads, 51 sectors/track, 3010 cylinders
Units = cylinders of 2601 * 512 = 1331712 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3011     3915204    c  W95 FAT32 (LBA)

```

As I understand I have used all the primary partitions above, 4 max allowed, I guess. And I now have no option but to install another OS, 4th one, in the free space of 40 GB as shown in the last image titled - PTable5thP.png - So how do I go about installing my 4th distro Ubuntu 10.04 LTS? I am not very comfortable with LVMs. So suggest me something. Thanks.

---

### Post by Blasphemist on 2011-08-11
You do need to make some changes. You'll need to boot to a live cd of ubuntu, gparted or some other distro or utility that includes gparted. 

I'll start with listing steps. First, delete the swap partition. Then move the existing to the left where the swap was. At this point the goal is to have free space all at the end of the disk and one free primary partition left to use. Don't worry if there is a small amount, mb's, unused between your partitions.

Then create an extended partition that includes all of the free space at the end of the drive. This will be about 42GB of course. Then you'll create all of the logical partitions within the extended partitions that you want. I have seven distro's and my swap in my extended partition. The space they use varies from 2.25 GB to 6.75 GB. A normal distro install will take less than 5 GB initially. After that the space you need depends on how much software you install and what else you store in the partition. I use a separate shared data partition for my documents, downloads, pictures, music, etc.. 

Create the swap last at the end of the drive. Make it a bit larger than the amount of memory you will be using.

---

### Post by tech291083 on 2011-08-11
> **Blasphemist said:**
> 
First, delete the swap partition. Then move the existing to the left where the swap was. At this point the goal is to have free space all at the end of the disk and one free primary partition left to use. 


Ok,
So if I delete the swap partition all the 3 distros will still work/boot properly? I am sorry to ask but I have not much clear understanding of the significance of swap partition.

I will then move the partition on the right to the space where swap was earlier. Yes, this will create more space at the end of the disk. I get this one. And there will be one more primary partition left to use. 

>  
Then create an extended partition that includes all of the free space at the end of the drive. This will be about 42GB of course. Then you'll create all of the logical partitions within the extended partitions that you want. 


Yes, at the end of the disk there will be 42 GB of free space left once the swap partition is deleted. So, here I can create the swap partition that I had created earlier, right? And this swap will also be a logical parition within a large, 42 GB, extended parititon. So after creating swap, I can just install my 4th distro here only in this extended parition in one of the logical partitions that I will be creating. 

In short any future OS/distros must be installed in one of the logical partitions within the large extended parition of 42 GB in total and this extended parition will also contain the newly created swap parition, which was there as a primary paritition earlier. Ok, tough task for me, but a good guide as looks to me now.

> 
I have seven distro's and my swap in my extended partition. The space they use varies from 2.25 GB to 6.75 GB. 


This is amazing and I am really very jealous of your right now and will be so until I get to the point where you are. Really amazing. People keep saying that they install more than 2 distros on the same drive, but I never really thought it was an easy thing to accomplish, but now my doubts are clear. Can you please tell me more about your paritions for all the distros, I mean can you give me outputs of some commands such as fdisk etc so that I can get the layout of the whole thing, thanks a lot for sparing time for me. I will get back to you soon, thanks again.

---

### Post by Blasphemist on 2011-08-12
I must have been unusually clear for me since you seem to have understood everything I said perfectly. I think you are at a place I eventually got to after a lot of study. All of a sudden, during a shower of all things, my disk organization became clear to me. I think that is where you are now.

Here is a screen shot from gparted that shows my configuration while I'm running my Ubuntu Main natty. My sda6 is set up to be shared no matter whether I'm in a linux or windows session. I don't use separate /Home partitions, just that shared partition that I mount as shared storage. I make sure all partitions are labeled. You only see mount points in this shot that are active while I'm booted to this distro. All of the other distros do show up though in nautilus by the label as you can see in that screen shot. Those partitions only get mounted when I right click and mount them. I could auto mount them, I just don't.

Think about this and then ask if you have other questions. Good Work!

---

### Post by tech291083 on 2011-08-12
> **Blasphemist said:**
> I must have been unusually clear for me since you seem to have understood everything I said perfectly. 


I am happy to say that you were pretty clear. Thanks. I am a Linux enthusiast for the last 5-6 years and have learned things through forums only. Tried and tested a lot of stuff on my own. But I am happy that there are people like yourself who are happy to help, always, no matter what, continuing the spirit of free learning and community development. This is indeed remarkable.


>  Here is a screen shot from gparted that shows my configuration while I'm running my Ubuntu Main natty. 

I can't believe this. You are a loyal Ubuntu fan no doubt about that. I have save these images to my personal folder for future reference and inspiration, thanks a lot, sir. But I am also doing the same now. I have already Ubuntu 10.10 and Ubuntu 10.04 LTS alternate install version installed. Now I am going to install  Ubuntu 10.10 alternate install version. This is a bit weird but gives me a chance to learn things faster and better.

>  I make sure all partitions are labeled. 

I need to do this as a habit and a good practice. Thanks

>  Think about this and then ask if you have other questions. Good Work!

Yes, sure I will ask you a lot of questions verysoon and hope that you will help me get better by the post at Linux, thank you my friend. Now I am downloading GParted Live CD iso then burn it to a CD and start the procedure as mentioned by you, see you soon, thanks.

---

