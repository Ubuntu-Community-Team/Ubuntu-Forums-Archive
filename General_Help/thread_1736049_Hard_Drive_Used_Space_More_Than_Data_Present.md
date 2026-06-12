---
title: "Hard Drive Used Space More Than Data Present"
date: 2011-04-22
forum: General Help
---

### Post by Russell_S on 2011-04-22
Hi, I hope someone can help me out here.

I have a separate 320gb SATA hard disk that I use purely for data and is not automatically mounted at boot time and is separate from my /home mount point.

I am having a hard time understanding why I am getting a discrepency between the reported used hard disk space and the size of the contents that are actually on the drive. Basically the system is reporting that I have 170.7gb of data on the drive but the used space is 282.4gb

What I don't understand is why are these two figures different and where has the extra 114gb disappeared to. Here is a screen shot of the drive properties showing the two figures.

[IMG]http://i93.photobucket.com/albums/l74/RussellS_2006/Misc%20Pictures/DriveProperties.jpg[/IMG]

I don't know if there is a logical explanation for this or if I have a problem but if anyone could help me out I would be very grateful.


Thanks

---

### Post by lmarmisa on 2011-04-22
Maybe this difference is due to the trash folder. Go to the root of the partition  of your external hard drive (/media/18308d...) and try to locate a hidden folder named ".Trash-xxxx" (where xxxx is a number). If you use Nautilus, select View -> Show Hidden Files. If that folder is there, select its properties in order to check how much space is occupying.

---

### Post by Russell_S on 2011-04-22
Hi and thanks for the reply.

I had already tried that and the .Trash-xxxx folder is empty.

If I show hidden files and then select everything on that drive it still only shows 170.7gb


I'm very confused

---

### Post by lmarmisa on 2011-04-22
Consider to use the program Applications -> Accessories -> Disk Usage Analyzer.

This command is more or less equivalent:

```

du -sh `ls -a /media/18308d1d-863e-40e4-81ce-8de7989ca255/`

```Could you post here the result of that command?.

---

### Post by lmarmisa on 2011-04-22
Have you defined more than one partition on your external hard drive?

---

### Post by Russell_S on 2011-04-22
Hi again,

I wasn't even aware of the Disk Usage Analyser so thanks for pointing that out to me.

Here is the output of the analyser:

[IMG]http://i93.photobucket.com/albums/l74/RussellS_2006/Misc%20Pictures/DiskUsage.jpg[/IMG]

This is indicating that the problem lies with the folder OLD_home. This was my /home on a previous install which has still got a lot of the original hidden folders and files in it and I think it is this that is causing my issues.

In my original post does the contents part indicating 170.7gb not take into account hidden files then as I was under the assumption that it would. If I get properties on that OLD_home folder then it indicates that the contents are only 87.9gb even though I have "show hidden files" selected.

So, basically, how can I find the size of the data in a folder including the hidden files (preferably from Nautilus).

---

### Post by lmarmisa on 2011-04-22
The commands "du" and "du -s" work pretty well. If you add the option -h the output is more readable.

In relation with Nautilus, I supposed that if you activate the "show hidden files" option, this would be taken into account in the calculus of the sizes of folders.

---

### Post by Russell_S on 2011-04-22
I can't seem to get the du command to work. Here is the output when I try it:

```
russell@russell-desktop:~$ du -sh `ls -a /media/18308d1d-863e-40e4-81ce-8de7989ca255/`
du: cannot read directory `./.config/menus/applications-merged': Permission denied
193G    .
du: cannot read directory `../lost+found': Permission denied
du: cannot read directory `../russell/.config/menus/applications-merged': Permission denied
193G    ..
du: cannot access `Atari': No such file or directory
du: cannot access `800XL': No such file or directory
503M    .cache
du: cannot access `Disabled': No such file or directory
du: cannot access `MAME': No such file or directory
du: cannot access `ROMs': No such file or directory
du: cannot access `KB': No such file or directory
du: cannot access `Mame': No such file or directory
du: cannot access `ROMs': No such file or directory
du: cannot access `OLD_home': No such file or directory
du: cannot access `puppy-arcade-10.iso': No such file or directory
du: cannot access `.Trash-1000': No such file or directory
du: cannot access `ubuntu-11.04-beta2-desktop-i386.iso': No such file or directory
du: cannot access `VirtualBox': No such file or directory
du: cannot access `Data': No such file or directory

```However, after a bit of googling I found that the problem with Nautilus not taking into account hidden files/folders when calculating used space is a bug (and has been for quite some while) as listed here:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/33883](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/33883)

I have now installed an alternative file manager called "PCMan File Manager" which reports the used space correctly.

---

### Post by lmarmisa on 2011-04-22
Try to change the command:

```

cd /media/18308d1d-863e-40e4-81ce-8de7989ca255/
sudo du -sh * .*

```These are other examples:

```

du -h ~
du -sh ~
du -sh `ls -A ~`

```

---

### Post by Russell_S on 2011-04-22
Thanks, that works better returning the following:

```
russell@russell-desktop:/media/18308d1d-863e-40e4-81ce-8de7989ca255$ sudo du -sh * .*
9.2M    Atari 800XL
4.0K    Disabled MAME ROMs
31G    KB
3.2M    Mame ROMs
183G    OLD_home
110M    puppy-arcade-10.iso
698M    ubuntu-11.04-beta2-desktop-i386.iso
51G    VirtualBox Data
264G    .
322G    ..
12K    .cache
16K    .Trash-1000

```The OLD_home folder is a slightly different size now because I have just deleted some of the hidden stuff that was left over from when it was a /home mount point.

Thanks very much for your time with this, I have learnt lots (mainly, don't rely on what a file manager tells you).

---

### Post by lmarmisa on 2011-04-22
I was looking for the most suitable du command.

Finally, this is my preferred option:

```

cd path_of_the_directory_to_check
du -sh `ls -A`

```Use sudo before du if necessary.

I have learned new things too.

Best regards,

Luis

---

