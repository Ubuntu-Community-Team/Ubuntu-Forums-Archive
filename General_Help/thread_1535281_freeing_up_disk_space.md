---
title: "freeing up disk space"
date: 2010-07-20
forum: General Help
---

### Post by mancocapa on 2010-07-20
I still feel as though I should be posting in Beginer Talk but was told that general help could work as well.
 
I am currently using ubuntu jaunty jackalope and completely unfamiliar
 
I am unable to download updates due to their not being enough free disk space
 
The sudo apt-get clean and autoclean commands do not free up any space?
 
I have tried tinkering with ubuntu tweak and add remove programs as well but nothing coming.
 
Any help here is appreciated.

---

### Post by MaxIBoy on 2010-07-20
The biggest thing to do is [delete old kernels]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/"). That could potentially free up a couple of gigs!

Next, if you haven't already, try emptying your trash. Right click on the "trash" icon in the left pane of your file browser, and click "empty trash."

Finally, see if you can remove some programs you don't need. Pull up the Synaptic Package Manager. Click on "status" in the lower left, then "installed" in the upper left. Click on the "Size" column to sort packages by size; the bulkiest ones will show up earlier in the list. Be sure you know what you are removing! Sometimes, if you remove one package, it will automatically remove a bunch of others that depend on it, which may not be what you want to do.

Those three steps should get you enough room to make your system usable again. 

One question though, how much room have you given Ubuntu in your partitions? It's possible you just don't have enough space.

---

### Post by mancocapa on 2010-07-21
MaxIBoy
 
Thanx for the reply
 
 
I did manage to delete one kernel as that was the only extra since my system is new
 
One question though when I pulled up all the packages with Synaptic I had no idea what to remove?  Are there lists of what is preferred and what is not necessary?
 
Finally how does one find out how much space ubuntu has in partitions?

---

### Post by MaxIBoy on 2010-07-21
In Synaptic, if you sort by size as I described, just the top few on that list are going to be the ones which concern you. You can look at the description of each package, google the name of that package for more info if you still don't understand, and come to a decision on which ones you feel like keeping around. 

Keep in mind that some packages rely on others. So for example, even if you don't like the Evolution email program, you need to keep that because the GNOME desktop environment relies on it and if you remove it your panels stop working. (I think it's stupid that the panels rely on an email client and I think the GNOME people should have organized their code better, but that's how it is.) Sometimes you'll select to remove a package, and you'll see a bunch of other packages getting automatically removed as well. In those cases, you should consider carefully and probably you'll want to cancel the operation.

Synaptic can list "Installed (Auto Removable)" packages as well, and you can also sort by size on that list. Packages in that list are *usually* safe to remove, but still google them if you're not sure what they're for (you can never be too cautious.)

You can see how big your partitions are with the System Monitor (System->Administration->System Monitor.) Go to the "File Systems" tab.

Also, there should be a program in Applications->Accessories->Disk Usage Analyzer, which will list all your files by size. You can then look at what files are taking most space, and some of those files belong to packaged programs which you don't need. It will also tell you how much space is available. However, it won't give you reliable numbers for total capacity (due to symbolic links, which are like shortcuts, some files get counted twice, and that skews the results.) 

If you find a big file, *DON'T JUST DELETE IT!* First, if you have the name of a file and you want to see if it belongs to a package, pull up a terminal (Applications->Accessories->Terminal) and type in "dpkg -S" followed by the name of the file. For example: ```
maxtothemax@maxtothemax-mint ~ $ dpkg -S /bin/bash
bash: /bin/bash
maxtothemax@maxtothemax-mint ~ $ dpkg -S /bin/ls
coreutils: /bin/ls
```I can see that the file "/bin/bash" belongs to a package called "bash," and the file "/bin/ls" belongs to a package called "coreutils." To remove those files, I'd remove those packages. (DO NOT REMOVE EITHER OF THOSE PACKAGES. THAT WAS JUST AN EXAMPLE. IF YOU REMOVE THEM YOUR SYSTEM *WILL* BECOME UNBOOTABLE!) 

If you find out that a very big file belongs to a package, you can use Synaptic to remove that package and free up the space.



If you have a brand new system and you're already short on space, did you go on a spree of installing a bunch of software or do you have a bunch of documents/videos migrated to your Ubuntu install? The Ubuntu installer sometimes migrates stuff automatically from Windows installs during a dual-boot, but if the material is still on your Windows partition you don't need the extra copies. Also, consider moving some videos to an external hard drive if appropriate.

---

### Post by drs305 on 2010-07-21
The following link offers help in analyzing and correcting disk space issues.

[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

The most common problems are undeleted root trash (which doesn't get deleted when you empty *your* trash), large log files, and backups mistakenly made to the system partition instead of the intended backup partition (by apps such as *sbackup*). Since it's your system partition, make sure you umount all your non-system partitions - if they are mounted they may hide the problem.

---

### Post by linux18 on 2010-07-21
Well I'd like to start by asking how much disk space is in you ubuntu partition if your running  out you probably have a small partition, virtualbox, wine, a full trash bin.

---

### Post by mancocapa on 2010-07-22
MaxIBoy
I have ubuntu 9.04 and I cannot find the size column anywhere?

---

### Post by mancocapa on 2010-07-22
drs305
there is a great deal of information in your guide but I just don´t know where to begin and most I don´t understand 
 
Right now I am still at the stage where I can only follow short step by step instructions
 
Computers definitely aren´t my first love they just happen to exist in this world

---

### Post by drs305 on 2010-07-22
> **mancocapa said:**
> drs305
there is a great deal of information in your guide but I just don´t know where to begin and most I don´t understand 
 
Right now I am still at the stage where I can only follow short step by step instructions
 
Computers definitely aren´t my first love they just happen to exist in this world

When it comes to the command line I know it can be a bit intimidating. 

Some important things are to run commands only if you understand what they will do or trust the source. 

Copying the command (copying as you would in Windows, but pasting into a terminal window with CTRL-*SHIFT*-V instead of just CTRL-V) helps prevent mistakes.

Take your time with the commands. And if you make an error, often Linux will tell you what to do to correct it.

If you don't understand how to interpret the results of a command, just post them here and someone will usually be right along to help explain them.

If there is anything you need more clarification on I'd be happy to elaborate.

---

### Post by libssd on 2010-07-22
> **mancocapa said:**
> I still feel as though I should be posting in Beginer Talk but was told that general help could work as well.
 
I am currently using ubuntu jaunty jackalope and completely unfamiliar
 
I am unable to download updates due to their not being enough free disk space
 
The sudo apt-get clean and autoclean commands do not free up any space?
 
I have tried tinkering with ubuntu tweak and add remove programs as well but nothing coming.
 
Any help here is appreciated.
Open terminal, and type df, then copy/paste the output in a forum message; *e.g.*:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             30521876   4695652  24275760  17% /

```

I have installed Ubuntu 10.04 on an gb SDHC memory card, leaving about 4gb of free space. If you have less than 8gb of disk space, it's going to be a tight fit. 

Assuming 1) you have at least 8gb disk space, and 2) you can save your data files to another device, rather than upgrade from Jaunty, I would strongly recommend a clean install of Lucid. I started with Jaunty a year ago, and (except for the learning required to familiarize with the differences of grub2), I have found Lucid to be far superior.

---

### Post by mancocapa on 2010-07-23
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              7692876   7056916    245184  97% /
tmpfs                   901356         0    901356   0% /lib/init/rw
varrun                  901356       216    901140   1% /var/run
varlock                 901356         0    901356   0% /var/lock
udev                    901356       144    901212   1% /dev
tmpfs                   901356       708    900648   1% /dev/shm
lrm                     901356      2192    899164   1% /lib/modules/2.6.28-16-generic/volatile

---

### Post by linux18 on 2010-07-23
this is more helpful:
sudo find / -maxdepth 30 -size +16M -print | sort > size.log

this will list all files larger than 16MB and some errors post the file if you need help knowing what to delete

---

### Post by mancocapa on 2010-07-25
root1@prueba-desktop:~$ sudo find / -maxdepth 30 -size +16M -print | sort > size.log
[sudo] password for root1: 
find: `/proc/4500/task/4500/fd/5': No such file or directory
find: `/proc/4500/task/4500/fdinfo/5': No such file or directory
find: `/proc/4500/fd/5': No such file or directory
find: `/proc/4500/fdinfo/5': No such file or directory
find: `/home/prueba/.gvfs': Permission denied
find: `/home/root1/.gvfs': Permission denied
root1@prueba-desktop:~$

---

### Post by linux18 on 2010-07-25
sorry, I should have mentioned that the list is in your home directory under the name size.log

---

### Post by Vimmander on 2010-07-25
> **MaxIBoy said:**
> The biggest thing to do is [delete old kernels]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/"). That could potentially free up a couple of gigs!

That's a good idea.  But just out of plain curiosity, is Ubuntu "smart" enough to put a boot menu entry in the right place if you decide to reinstall an old kernel.  Example:

Kernel 3
Kernel 3 (Recovery Mode)
Kernel 2
Kernel 2 (Recovery Mode)
Kernel 1
Kernel 1 (Recovery Mode)

If Kernel 2 is removed, then reinstalled later, would the above ordering be preserved, or would this happen:

Kernel 2
 Kernel 2 (Recovery Mode)
Kernel 3
Kernel 3 (Recovery Mode)
Kernel 1
Kernel 1 (Recovery Mode)

---

### Post by drs305 on 2010-07-25
It will place them back in the newest to oldest order (3,2,1). You can specify the default entry in the /etc/default/grub file with a title instead of a number if that is what you are concerned with:
> 
GRUB_DEFAULT="Ubuntu, with Linux 2.6.32-24-generic"

Just use whatever is between the quotes of the menuentry in /boot/grub/grub.cfg.

**Added:**
Testing in a VM found the following:
With a new kernel, the number for the default OS does not change. Therefore, a newer kernel will be used. If GRUB_DEFAULT was 0, it will be the latest kernel; if an older kernel was used, a newer kernel will be used upon reboot. Grub 2 will boot the same menuentry *number*. 

If you want to use a specific kernel, use the exact title in the GRUB_DEFAULT line or use "saved" and run "grub-set-default" with the desired menuentry number.

If the grub-pc package is updated and the maintainer's version is accepted, the default number is changed to "0".

---

### Post by mancocapa on 2010-08-06
Took a bit of a siesta from trying to figure this out   Now that I have the energy to fiddle with my computer again I am back
 
How does one go about unmounting non-system partitions?  I am sure I read the answer to this in your recover lost disk space post but there was such a vast amount there I could not make heads or tales of it
 
Thanx

---

### Post by drs305 on 2010-08-06
> **mancocapa said:**
> How does one go about unmounting non-system partitions?  

If you are using Gparted, select the the partition in the lower panel, then right click and "Unmount". Or you can select the partition in the upper panel and then select "Partition, Unmount". For a swap partition, you select "Partition, Swapoff".

There are several things to note. You can't unmount the extended partition until all the logical partitions within it are unmounted. You also cannot umount a system partition if you are running it, which is why you have to do this from a LiveCD or equivalent.

You can also use the command line to umount some partitions. You can see which partitions are mounted with this command (the second part reduces the output to your 'normal' partitions):
```
mount | grep "/dev/sd"
```
You should be able to unmount non-system partitions not being used with:
```
sudo umount /dev/sdXY
```
Example: 
*sudo umount /dev/sda7*

---

### Post by K.Kong on 2010-09-21
I am critically low on disk space.  I find some big files in /var/cache/apt.  Can I just delete those?
 
Despearte and thanks.

---

### Post by drs305 on 2010-09-21
> **K.Kong said:**
> I am critically low on disk space.  I find some big files in /var/cache/apt.  Can I just delete those?
 
Despearte and thanks.

Yes, you can do it from terminal with:
```
sudo apt-get clean
```
which will remove all downloaded packages from that folder. It won't effect your installed apps.

---

