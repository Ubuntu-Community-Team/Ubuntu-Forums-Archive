---
title: "How can I reinstall ubuntu or remove it without lossing data ?"
date: 2010-12-02
forum: General Help
---

### Post by drdigital on 2010-12-02
Hello every one,
I'm happy to join the ubuntu world and i'm keen to learn every thing.

I was a windows user and I want to move to linux. I can now do the basic tasks in ubuntu and I want to know. If I want to remove ubuntu either to try another copy of it or to install another version. I want to learn how to uninstall the system, reinstall it or changing the version or any thing.
What data will i loss? where ate the untouched data segment? If I use windows with linux, can I handle th issue of sharing my data between them and reinstall or remove any without data loss problems ?

If there are any helpful tutorials teaching those issues, pls post them. 

Thaaaaanks in advance.

---

### Post by nothingspecial on 2010-12-02
Hi,

Take a look at this.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

you should have backups you know. All drives fail eventually.

---

### Post by drdigital on 2010-12-02
I need that because UBUNTU some times put restrictions on the non-linux (not under root) partitions. I can't install to or from them and keep data without problems.

I'm I wrong on this point ?

---

### Post by nothingspecial on 2010-12-02
Are you talking about backing up data to external drives?

---

### Post by 3rdalbum on 2010-12-02
You can't install to a partition that isn't already formatted as a Linux filesystem. If you install to a partition that does not already contain a copy of Ubuntu, you will lose all the data in that partition.

If you install Ubuntu fresh over an earlier copy of itself, or an earlier version, using the manual partitioning method in the installer, then it will ask you if you want to preserve the contents of /home. You probably do want to.

Alternatively, you can put /home onto a different partition or different disk, and then your data is safe even if you decide to install a different distribution.

---

### Post by drdigital on 2010-12-02
Great. How can I do this ? Putting /home in another partition ?

---

### Post by drdigital on 2010-12-02
@nothingspecial: 
No Sir. Just my normal work days

---

### Post by oldfred on 2010-12-02
These are all really the same just using a different command for copying. I let you decide which is more clear in explanation. If you have permission issues after copying, see last link:

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by potat on 2010-12-18
I moved my /home to a separate partition but I haven't actually reinstalled Ubuntu yet. Is there a way to reinstall such that Ubuntu recognizes your existing /home partition? Or does it have to be added in fstab after the fact? In the latter case, would all the files in my home folder have to be chowned to the "new" me?

---

### Post by katykat on 2010-12-18
> **drdigital said:**
> Hello every one,
I'm happy to join the ubuntu world and i'm keen to learn every thing.

I was a windows user and I want to move to linux. I can now do the basic tasks in ubuntu and I want to know. If I want to remove ubuntu either to try another copy of it or to install another version. I want to learn how to uninstall the system, reinstall it or changing the version or any thing.



There are many ways to go about this. 

For me the simplest method is to simply use different drives for different Operating systems. 

I now use three drives with WindowsXP in a removable caddy, and two others set as plugins for that drive. 
The second drive has Fedora installed on it. 
The third drive has Meerkat. 

Using a Rescatux boot CD I have all three caddy drives booting into Grub2 on Meerkat. 
And I am not restricted to using XP on the caddy drive. I can install any OS on a caddy drive and experiment with it (and just unplug the secondary channed with Meerkat/Fedora if there is any risk of interference). 

I also just recently found a neat Win utility called MBRFIX which will allow you back up and replace the boot sectors of all the drives so they can be restored if anything goes wrong. 

The beauty of using additional drives is that when not in use they can be spun down in linux (still trying to figure out that trick in win). And that should a disk fail you can have multiple fully functioning drives. 

So you never have to REMOVE ubuntu versions. You can play as you want as separate drives set to use -or not - a main Version, such as Meerkat or Lucid. 

If doing Ubuntu versions you should be able to just copy home over to the new test drive. 

SOme people have had luck upgrading systems. I tried to do the upgrade path from Jaunty to Meerkat, and all it did was cause 4 days of grief and a ton of aggrivation, with their freaking dependency hell. However, my installation is rather large. A backup for me is  around 2 miilion files. Simplest solution  was to install Meerkat and port over what could be used, and just reinstall all the main apps

Naturally this info is for desktops, who have room to expand hard drives.

---

### Post by Elfy on 2010-12-18
> **potat said:**
> I moved my /home to a separate partition but I haven't actually reinstalled Ubuntu yet. Is there a way to reinstall such that Ubuntu recognizes your existing /home partition? Or does it have to be added in fstab after the fact? In the latter case, would all the files in my home folder have to be chowned to the "new" me?

When you install - use manual partioning instad of letting it choose wher to install.

Assuming you also have a partition that you want to install the os to - 

OS partition - select and edit - choose / as a mountpoint - allow it to format

Home partition - select and edit - choose /home as a mountpoint - do NOT allow it to format

---

### Post by potat on 2010-12-27
Thanks. I was always worried about choosing /home as a mountpoint because I assumed it would screw up my data. Thankfully I have a backup now so that shouldn't be an issue.

---

