---
title: "Initramfs on one of the kernels"
date: 2010-08-28
forum: General Help
---

### Post by linux_game on 2010-08-28
I am using Ubuntu 9.10 and am facing an issue while booting up. It goes into initfs command prompt on one of the 4 kernels that show up in the boot menu. I tried to look around for a likely solution and hence did the following:

1. ran "chkdsk c: /f" in my windows partition.
2. Added "rootdelay=90" in "/boot/grub/menu.lst" file.

This is how my /boot/grub/menu.lst file looks and the problem is with the kernel 2.6.31-20-generic:

title          Ubuntu 9.10, kernel 2.6.31-20-generic
uuid           ceacd229-2b68-41bf-a967-8ee470085fd8
kernel         /boot/vmlinuz-2.6.31-20-generic root=UUID=ceacd229-2b68-41bf-a967-8ee470085fd8 ro quiet splash rootdelay=90 
initrd         /boot/initrd.img-2.6.31-20-generic
quiet

title          Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid           ceacd229-2b68-41bf-a967-8ee470085fd8
kernel         /boot/vmlinuz-2.6.31-20-generic root=UUID=ceacd229-2b68-41bf-a967-8ee470085fd8 ro  single
initrd         /boot/initrd.img-2.6.31-20-generic


title           Ubuntu 9.10, kernel 2.6.31-19-generic
uuid            ceacd229-2b68-41bf-a967-8ee470085fd8
kernel          /boot/vmlinuz-2.6.31-19-generic root=UUID=ceacd229-2b68-41bf-a967-8ee470085fd8 ro quiet splash rootdelay=90
initrd          /boot/initrd.img-2.6.31-19-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid            ceacd229-2b68-41bf-a967-8ee470085fd8
kernel          /boot/vmlinuz-2.6.31-19-generic root=UUID=ceacd229-2b68-41bf-a967-8ee470085fd8 ro  single
initrd          /boot/initrd.img-2.6.31-19-generic
......

Any help will be nice.

---

### Post by ranch hand on 2010-08-28
Well first off you only have two kernels in your menu 2.6.31-19 and 2.6.31-20.

The first (top) entry for each is to boot to the desktop and the other to boot to recovery.

Which one is giving you trouble?

---

### Post by linux_game on 2010-08-28
> **ranch hand said:**
> Well first off you only have two kernels in your menu 2.6.31-19 and 2.6.31-20.

The first (top) entry for each is to boot to the desktop and the other to boot to recovery.

Which one is giving you trouble?

I have 4*2 such entries and have shown shown only the entries for top 2 kernels. I can print the entire menu if that helps. The kernel that is troubling me is "2.6.31-20" while "2.6.31-19" is working fine.

Thanks for looking into it.

---

### Post by ranch hand on 2010-08-28
Is this the newest kernel,  I am on 10.10 testing right now and do not have access to any 9.10 installs right now?

Is the trouble with booting to the desktop or recovery or both?  If you can boot to recovery I would;
A>choose the "dpkg fix broken packages" option.
B>chose the root shell option and run;
```

uppdate-initramfs -u

```
This needs to be the recovery mode for the kernel that is acting up.

---

### Post by linux_game on 2010-08-28
> **ranch hand said:**
> Is this the newest kernel,  I am on 10.10 testing right now and do not have access to any 9.10 installs right now?

Is the trouble with booting to the desktop or recovery or both?  If you can boot to recovery I would;
A>choose the "dpkg fix broken packages" option.
B>chose the root shell option and run;
```

uppdate-initramfs -u

```This needs to be the recovery mode for the kernel that is acting up.


I tried to do the same but realized that I can't enter the recovery mode as well for the kernel. It also leads me to the initramfs prompt. :(

---

### Post by ranch hand on 2010-08-28
You might try booting to the -19 kernel, removing the -20 kernel (completely remove) through synaptic and then reinstalling it.

I would, before reinstalling, go to /var/cache/apt/archive and make sure that the -20 kernel and associated .tars are not in there.  If they are delete them.

---

### Post by linux_game on 2010-08-28
> **ranch hand said:**
> You might try booting to the -19 kernel, removing the -20 kernel (completely remove) through synaptic and then reinstalling it.

I would, before reinstalling, go to /var/cache/apt/archive and make sure that the -20 kernel and associated .tars are not in there.  If they are delete them.


I am not sure about why 4 kernels were created during my install. I commented the first kernel in the .lst file mentioned above and everything seems to work fine for me. I mean I am ok to work with the kernel 19 instead.

Please help me understand the reason why 4 kernels are created and is there anything wrong in commenting the ".lst" file. I am not very used to such changes in the Linux System, please excuse the immaturity in my questions.

---

### Post by ranch hand on 2010-08-29
Well I do not know as you have never said when you installed.  There are security updates that come in from time to time and they are usually in the form of an updated kernel.

I have had time to check one of my 9.10 installs and see that it is working on 2.6.31-22.

Have you run an update lately?  I would not, in these conditions us Update Mangler.

The best thing to do would be to go to Applications>Accessories>Terminal and run;
```

sudo apt-get update

```
and then
```

sudo apt-get upgrade

```
If there is a problem there should be an error message.  Post it here.

Lets see if we can get your OS up to date and working on the correct kernel.

If you just installed it there was probably an update/upgrade run when you first booted to the new install.  This should not have installed more than the newest kernel available so why you have more than that is beyond me.

If this is an older install then you should have several kernels unless you removed them.

Seeing how you are using grub-legacy (grub0.98) instead of grub2 (grub1.97 I think in 9.10) I assume this was an upgrade from an install of 8.10.  Installed from a Live CD you should be using grub2 as that is the default boot loader (came into 9.10 at the Alpha 2 point in development).

There has been some problems with the system, particularly on upgrades, where you have both kinds of grub and the OS really does not know what it is using.

It would be good if you would run, in terminal;
```

grub-install -v

```
All that will do is tell you what version (-v) of grub you have installed.  Please post that here too.

Between getting up to date and finding out what the grub version is and you saying what kind of install this is (clean or upgrade) we should be on the road to knowing what is going on.

---

### Post by linux_game on 2010-08-29
> **ranch hand said:**
> Well I do not know as you have never said when you installed.  There are security updates that come in from time to time and they are usually in the form of an updated kernel.

I had made a fresh install of ubuntu 9.10 (if I remember it correctly), about a year back. Since its been very long it might have been an upgrade from 9.04.

> **ranch hand said:**
> I have had time to check one of my 9.10 installs and see that it is working on 2.6.31-22.

Have you run an update lately?  I would not, in these conditions us Update Mangler.

The best thing to do would be to go to Applications>Accessories>Terminal and run;
```

sudo apt-get update

```

I got the following error while doing an update in kernel "kernel 2.6.31-19-generic":

Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2836CB0A8AC93F7A


> **ranch hand said:**
> and then
```

sudo apt-get upgrade

```If there is a problem there should be an error message.  Post it here.

This is what my upgrade shows:
0 upgraded, 0 newly installed, 0 to remove and 105 not upgraded.

> **ranch hand said:**
> 
Lets see if we can get your OS up to date and working on the correct kernel.

If you just installed it there was probably an update/upgrade run when you first booted to the new install.  This should not have installed more than the newest kernel available so why you have more than that is beyond me.

If this is an older install then you should have several kernels unless you removed them.

Seeing how you are using grub-legacy (grub0.98) instead of grub2 (grub1.97 I think in 9.10) I assume this was an upgrade from an install of 8.10.  Installed from a Live CD you should be using grub2 as that is the default boot loader (came into 9.10 at the Alpha 2 point in development).

There has been some problems with the system, particularly on upgrades, where you have both kinds of grub and the OS really does not know what it is using.

It would be good if you would run, in terminal;
```

grub-install -v

```All that will do is tell you what version (-v) of grub you have installed.  Please post that here too.

Between getting up to date and finding out what the grub version is and you saying what kind of install this is (clean or upgrade) we should be on the road to knowing what is going on.

%grub-install -v
grub-install (GNU GRUB 0.97)

As per the above lines I should be upgrading to later version of grub (probably grub2). Is that correct ?

Am curious if my kernel got updated after doing the operations listed above ?

---

### Post by ranch hand on 2010-08-29
You must have upgraded to 9.10 as you are using grub0.97 which is the default grub for 9.04 and earlier.  On upgrades they stuck with the old one.

I think that this was a mistake as there is confusion within grub as to what to look for.  I would like you to;
```

sudo gedit /boot/grub/grub.cfg

```Post that here.  There should be such a file but I want to see what is in it.

Under grub2 this is where your screen menu is generated.  If you want a simple over view of grub2 check the first post in the link in my sig.

We will worry about that latter except for the .cfg file.

Are you dual booted with any other OS(s).  My wife isn't on her laptop (9.10).  I would have to count mine to be sure but I think I have about 20 on 3 drives.  Most drives boot independent of each other and there is one I seldom go to so I can't remember what is on it.  I do know that none of it is MS.
> 
This is what my upgrade shows:
0 upgraded, 0 newly installed, 0 to remove and 105 not upgraded.
This indicates that nothing was upgraded.  It also shows that there are 105 packages that need upgrading.

There are probably more packages than that as some of the 105 will have depends that need installed (the -22 kernel should have 3).

I would run;
```

sudo apt-get dist-upgrade

```I would like the output from that command.  If you have upgrades that can be run that would be a good idea.  Do it after getting the initial output copied and before giving the OK for the upgrade.  You may (probably will) get a message that there are some unknown packages and do you want to install them anyway.  You do.  This is the problem with your gpg key and I am not sure which one you are missing.  Just run the buggers.

If it will not run the upgrades we need the output from that too.

---

### Post by linux_game on 2010-08-29
> **ranch hand said:**
> You must have upgraded to 9.10 as you are using grub0.97 which is the default grub for 9.04 and earlier.  On upgrades they stuck with the old one.

I think that this was a mistake as there is confusion within grub as to what to look for.  I would like you to;
```

sudo gedit /boot/grub/grub.cfg

```Post that here.  There should be such a file but I want to see what is in it.

The file is empty....
Should I be looking at a different file ?

> **ranch hand said:**
> Under grub2 this is where your screen menu is generated.  If you want a simple over view of grub2 check the first post in the link in my sig.

We will worry about that latter except for the .cfg file.

Are you dual booted with any other OS(s).  My wife isn't on her laptop (9.10).  I would have to count mine to be sure but I think I have about 20 on 3 drives.  Most drives boot independent of each other and there is one I seldom go to so I can't remember what is on it.  I do know that none of it is MS.
Yes I have a Windows Vista Partition.

> **ranch hand said:**
> This indicates that nothing was upgraded.  It also shows that there are 105 packages that need upgrading.

There are probably more packages than that as some of the 105 will have depends that need installed (the -22 kernel should have 3).

I would run;
```

sudo apt-get dist-upgrade

```I would like the output from that command.  If you have upgrades that can be run that would be a good idea.  Do it after getting the initial output copied and before giving the OK for the upgrade.  You may (probably will) get a message that there are some unknown packages and do you want to install them anyway.  You do.  This is the problem with your gpg key and I am not sure which one you are missing.  Just run the buggers.


The last few lines after running the command were as follows:

Setting up okular-extra-backends (4:4.4.2-0ubuntu1~karmic1~ppa1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
If it will not run the upgrades we need the output from that too.

I hope I did all the expected things. 
Thanks.

---

### Post by linux_game on 2010-08-29
Looks like there has been some problem in the steps executed on the previous update. After booting, it says the following for all the kernels:
Boot from (hd0, 0) ext3  ceacd229-2b68-41bf-a967-8ee470085fd8
Error 15: File not found

I cannot boot into any of the kernels or recovery kernels. What should I do to fox this situation.

Thanks.

---

### Post by ranch hand on 2010-08-29
Well it would have been nice to have the output before you OKed the upgrade but that is fine.  It appears to have worked.

I would run the first 2 commands again (update and upgrade) and see if anything else shakes out.  If needed run the dist-upgrade command too.

Then check your menu.lst and see if there are any changes.  You might also check synaptic to see what the newest kernel you have installed is.  Be a good idea to check that against what is in the menu.lst.

The empty grub.cfg file is a good thing although there should have been something in there about not editing that file I think.  All being empty means is that you are, for sure, running on 0.97.  That was my concern.  Sometimes there is a little confusion and nothing works quite right.  Now if we decide that grub is part of this problem we will just work with grub-legacy as that has been working for you all a long.

If you decide to upgrade to 10.04 I would back up all your data and do a clean install of it so that you get the new grub, ext4 and the other changes without complication.  Of coarse if you are on two partitions (/ and /home) you could do an install from disk without formatting your /home (backup recommended) and probably come through fine.   I am not saying you should upgrade, 9.10 is a great OS, I just think that you are going to run into problems with the upgrade of grub and ext4 is very nice too.

After checking for any further upgrades reboot using what ever is default according to grub.

Assuming it boots, run;
```

uname -a

```
and post that result here.

---

### Post by linux_game on 2010-08-29
> **ranch hand said:**
> Well it would have been nice to have the output before you OKed the upgrade but that is fine.  It appears to have worked.

I would run the first 2 commands again (update and upgrade) and see if anything else shakes out.  If needed run the dist-upgrade command too.

Then check your menu.lst and see if there are any changes.  You might also check synaptic to see what the newest kernel you have installed is.  Be a good idea to check that against what is in the menu.lst.

The empty grub.cfg file is a good thing although there should have been something in there about not editing that file I think.  All being empty means is that you are, for sure, running on 0.97.  That was my concern.  Sometimes there is a little confusion and nothing works quite right.  Now if we decide that grub is part of this problem we will just work with grub-legacy as that has been working for you all a long.

If you decide to upgrade to 10.04 I would back up all your data and do a clean install of it so that you get the new grub, ext4 and the other changes without complication.  Of coarse if you are on two partitions (/ and /home) you could do an install from disk without formatting your /home (backup recommended) and probably come through fine.   I am not saying you should upgrade, 9.10 is a great OS, I just think that you are going to run into problems with the upgrade of grub and ext4 is very nice too.

After checking for any further upgrades reboot using what ever is default according to grub.

Assuming it boots, run;
```

uname -a

```and post that result here.


I am unable to reboot and hence cannot do the above said. There has been some problem in the steps executed on the previous update.  After booting, it says the following for all the kernels:
Boot from (hd0, 0) ext3  ceacd229-2b68-41bf-a967-8ee470085fd8
Error 15: File not found

I cannot boot into any of the kernels or recovery kernels. What should I  do to fox this situation.

---

### Post by ranch hand on 2010-08-29
This is not good.

Do you have a Live CD for 9.04 or older Ubuntu?

---

### Post by linux_game on 2010-08-29
> **ranch hand said:**
> This is not good.

Do you have a Live CD for 9.04 or older Ubuntu?

I dont have it by myself but my room-mate must have it. I presume 9.04 and later versions will be necessary ?

Can you tell me the steps to perform once I have the required CD.

---

### Post by ranch hand on 2010-08-29
Well I thought we should start by just trying to reinstall grub on the MBR.  This may just be a case where the stuff there does not match the grub on your install quite right.  This may not be the case but it is worth a try.

You will need a Live CD 9.04 or OLDER.  This is because you are using grub-legacy and 9.10 and newer ISOs have grub2 on them so they do not recognise the commands for grub-legacy (just one of the reasons I do not like the upgrade path that leaves grub-legacy on your install).

I am running in and out right now, will post again in a few minutes with the commands for that.  Used to know them in my sleep but went to grub2 with 9.10 (installed it on my 9.04 even) and just don't use it any more.  Would hate to give you a bad command.

---

### Post by ranch hand on 2010-08-29
Better yet, from back when I was a lost noob trying to learn about grub, this post was recommended to me and it is pretty well maintained.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Do NOT use the instructions for installing on a partition.

If you have trouble DO use the instructions, below the partition installation instructions, for chrooting into the OS itself to run the commands.

The very first instructions should work quite well all by themselves.  Pretty simple and straight forward, well tested and proven in the field for years.

Grub2 is a little more complex from the CD, have to use chroot, but is a piece of cake if you can boot to the OS you want to use for your menu (more than one grub2 using Linux install needed, of coarse).

Grub-legacy may be the best chioce, right now, for those with MS on there box.

 [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

I believe this is MS just trying to be as big a pain as they can.  Does not effect grub-legacy as the room needed in that area is just for stage1.  Grub2 has the kernel image info there and takes more room so it gets over written.

---

### Post by linux_game on 2010-08-29
> **ranch hand said:**
> Better yet, from back when I was a lost noob trying to learn about grub, this post was recommended to me and it is pretty well maintained.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Do NOT use the instructions for installing on a partition.

If you have trouble DO use the instructions, below the partition installation instructions, for chrooting into the OS itself to run the commands.

The very first instructions should work quite well all by themselves.  Pretty simple and straight forward, well tested and proven in the field for years.

Grub2 is a little more complex from the CD, have to use chroot, but is a piece of cake if you can boot to the OS you want to use for your menu (more than one grub2 using Linux install needed, of coarse).

Grub-legacy may be the best chioce, right now, for those with MS on there box.

 [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

I believe this is MS just trying to be as big a pain as they can.  Does not effect grub-legacy as the room needed in that area is just for stage1.  Grub2 has the kernel image info there and takes more room so it gets over written.

I am not sure if I missed out something. I did the following but to no avail.

grub> find /boot/grub/stage1
 (hd0,0)

grub> root  (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

---

### Post by ranch hand on 2010-08-29
So, we have grub installed where it should be.  But it will not see your OS.

I have no idea what you do with your install or how much info you have on it so it is a little hard to say what the next step should be.

There are a number of things that could be done here in a chroot environment from the Live CD.  We could reconfigure things (dpkg --configure -a and dpkg-reconfigure -a would be a good place to start), we could purge some things and reinstall them.

This is, if you have never done it before, a pain to walk through on the forums.  We can do that and it is fun.

If you, however, do not have a lot of data to back up, or can back it up to the MS partition (I would use the LiveCD for any backup) or have some RW DVDs, it may just be easier to do a clean install.

I have no idea how your partition table is set up but I would take the partitions you have for Ubuntu and get rid of them and make that whole area an "extended" partition.  You can only have 4 primary partitions on a drive.  An extended partition is a type of primary partition that you can put any number of "logical" partitions inside of.  Very handy indeed (I have 15 partitions counting swap on this drive).

Just do this after you back up using System>Administration>Gparted on the Live Session.

Put the Swap partition at the end of the extended. Put a 15Gb ext4 partition at the beginning of the extended for / (root) and format the rest ext4 for /home.  Write down the partition designations for those est4 partitions.

When you get to the installer partitioner choose the "manually set the partitions" option.  This will let you say where you want the installer to put things.  Just right click on the partition and edit it.  There is a pop up box and you just tell it to use the partition as ext4, mount point / (for the root partition) and there is a check box for formatting or not.  You can format or not as they would already be formatted.

This is a good way to install as you can reinstall by just choosing to format the / partition and not the /home partition if you need to do that in the future.  Backing up is still a good idea but I have never lost data doing that.

On the last page of things you need to go through is the page where you approve the install.  Before you do that click on the "advanced" button that you will see there.  You will find a place to sellect where grub is installed.  Make sure that it is (hd0) or sda and no place else.  Not as big a problem in 9.10 as 10.04 but occasionally it installs to partitions and this over writes the boot sector of MS.  Not a real good thing if you want to boot to MS.

I would keep the menu entry for booting for MS from your grub.lst just incase you need it.  Shouldn't need it but...

I do not like reinstalling but it may just be the easiest thing.  Your call.  Let me know.  I am up for anything you want to do.  You may want to consult with your room mate.  Think it through, do not rush (I am good at rushing things).

---

### Post by linux_game on 2010-08-30
> **ranch hand said:**
> So, we have grub installed where it should be.  But it will not see your OS.

I have no idea what you do with your install or how much info you have on it so it is a little hard to say what the next step should be.

There are a number of things that could be done here in a chroot environment from the Live CD.  We could reconfigure things (dpkg --configure -a and dpkg-reconfigure -a would be a good place to start), we could purge some things and reinstall them.

This is, if you have never done it before, a pain to walk through on the forums.  We can do that and it is fun.

If you, however, do not have a lot of data to back up, or can back it up to the MS partition (I would use the LiveCD for any backup) or have some RW DVDs, it may just be easier to do a clean install.

I have no idea how your partition table is set up but I would take the partitions you have for Ubuntu and get rid of them and make that whole area an "extended" partition.  You can only have 4 primary partitions on a drive.  An extended partition is a type of primary partition that you can put any number of "logical" partitions inside of.  Very handy indeed (I have 15 partitions counting swap on this drive).

Just do this after you back up using System>Administration>Gparted on the Live Session.

Put the Swap partition at the end of the extended. Put a 15Gb ext4 partition at the beginning of the extended for / (root) and format the rest ext4 for /home.  Write down the partition designations for those est4 partitions.

When you get to the installer partitioner choose the "manually set the partitions" option.  This will let you say where you want the installer to put things.  Just right click on the partition and edit it.  There is a pop up box and you just tell it to use the partition as ext4, mount point / (for the root partition) and there is a check box for formatting or not.  You can format or not as they would already be formatted.

This is a good way to install as you can reinstall by just choosing to format the / partition and not the /home partition if you need to do that in the future.  Backing up is still a good idea but I have never lost data doing that.

On the last page of things you need to go through is the page where you approve the install.  Before you do that click on the "advanced" button that you will see there.  You will find a place to sellect where grub is installed.  Make sure that it is (hd0) or sda and no place else.  Not as big a problem in 9.10 as 10.04 but occasionally it installs to partitions and this over writes the boot sector of MS.  Not a real good thing if you want to boot to MS.

I would keep the menu entry for booting for MS from your grub.lst just incase you need it.  Shouldn't need it but...

I do not like reinstalling but it may just be the easiest thing.  Your call.  Let me know.  I am up for anything you want to do.  You may want to consult with your room mate.  Think it through, do not rush (I am good at rushing things).

I have decided to completely format my system (including Windows) and  start afresh. I have backed up all my data in a external hard drive. I  am now on the verge of installing Ubuntu 10.04. I believe i should be  following the same partition summary posted by u ? 

If I  understood correctly, I should :
1. Boot using Live CD for 10.04
2.  Use Gparted to do the following:
[INDENT]a. Create an extended  partition and an another ntfs partition
b. In the extended partition  make and label 3 sub partitions for root, home and swap resp
c. Then  while installing associate the partitions to root and home
d. Once  that is done and Ubuntu installation is complete, install Windows.

[/INDENT]I  have a couple of problems/questions here :

[LIST=1]
[*]I am in step 2b  above and when I commit the changes from the Live CD it fails with an  error message stating "libparted is in use". Am I missing something here  ?
[*]In step 2d, I fear Windows instal might over-write my  Linux menu. Should I be making sure of any particular thing while  installing Windows ?
[/LIST]
Thanks

---

### Post by linux_game on 2010-08-30
My problem seems to be strikingly similar to [http://www.linuxquestions.org/questions/fedora-35/kernel-unable-re-read-partition-table-on-disks-when-i-start-gparted-783997/](http://www.linuxquestions.org/questions/fedora-35/kernel-unable-re-read-partition-table-on-disks-when-i-start-gparted-783997/) and I also have a Dell Laptop but a XPS studio. Does that makes sense ?

---

### Post by ranch hand on 2010-08-30
I am of little use in advise about MS products.  They are not allowed in this house.

I do know that MS likes to be installed in the first partition and should probably do its own partitioning.

If you have gparted still up it would cause that error.  If not I suspect that, with premade partitions if you don't tell the installer partitioner to format the drives you will not have that problem.

Another way to install MS is to just use the whole drive for Ubuntu (20 t025 Gb for /) and then install MS in Virtual Box.  This will make MS much more secure and eliminate conflicts between the 2.

I am not a gamer but I have heard that some games do not perform well in VB so that might be an issue.

---

### Post by linux_game on 2010-08-30
> **ranch hand said:**
> I am of little use in advise about MS products.  They are not allowed in this house.

I do know that MS likes to be installed in the first partition and should probably do its own partitioning.

If you have gparted still up it would cause that error.  If not I suspect that, with premade partitions if you don't tell the installer partitioner to format the drives you will not have that problem.

Another way to install MS is to just use the whole drive for Ubuntu (20 t025 Gb for /) and then install MS in Virtual Box.  This will make MS much more secure and eliminate conflicts between the 2.

I am not a gamer but I have heard that some games do not perform well in VB so that might be an issue.

I will install MS in VirtualBox as I only use it in places where once cant do without it.

That said, I could not understand your comments about Gparted. Currently I have no partition and in this state I am trying to perform the above listed steps via booting into Live CD.

---

### Post by ranch hand on 2010-08-30
The Live CD is the way to go.  I did not mean to confuse you.  Sorry.

I would use gparted (System>Administration>Gparted) to do your partitioning.  When you set up your ext4 partitions make sure to make the / (root) partition large enough so that you have room for apps (like VB and all the rest).  They will all be in your / partition.

When you get to the installer you need to direct the installer partitioner where to put your install.  Do so but do not direct the installer partitioner to format the partitions.  This should avoid that error.

If not reboot and try it again.  I have not had any trouble with the 10.04.1 partitioner in doing this or for that matter the 10.04 (before the 10.04.1 step release) partitioner using manual partitioning.  I do not usually have it format the partitions as I have them already formatted.

I hope that clears up the confusion, if not, holler at me again.

---

### Post by ranch hand on 2010-08-31
If you continue to have a problem with the installer download the Alt install disk.  It uses the old Debian text installer and also has a very nice rescue feature.

The installer is not flashy but it is proven over the years.
[http://cdimage.ubuntu.com/lucid/daily/current/](http://cdimage.ubuntu.com/lucid/daily/current/)

---

### Post by linux_game on 2010-08-31
I made two primary partitions (instead of extended) one for root and home as described. And kept the swap as the third partition. NTFS is my 4th partition. 

I understand the benefits of an extended partition but looks like there were some issues with my laptop. 

Will this setup work fine ? Does it have any disadvantages that you can think of, apart from the loss of flexibility provided by extended partitions.

Thanks for looking into my problem.

---

### Post by ranch hand on 2010-08-31
Nope, if that is the partitions you need that is fine.  It is not as flexible but external drives are not hard to get if you need more, there may even be another bay in your box.

You can have 4 partitions, you have 4 partitions.  Should be great.

---

### Post by linux_game on 2010-08-31
> **ranch hand said:**
> Nope, if that is the partitions you need that is fine.  It is not as flexible but external drives are not hard to get if you need more, there may even be another bay in your box.

You can have 4 partitions, you have 4 partitions.  Should be great.


Thanks again for patiently looking into my issue.

---

