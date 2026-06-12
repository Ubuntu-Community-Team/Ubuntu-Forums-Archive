---
title: "Wubi and Evolution:hidden folders"
date: 2009-10-24
forum: General Help
---

### Post by marco77 on 2009-10-24
Hi All,

I need to reinstall ubuntu because I am not able to start it anymore (see [http://ubuntuforums.org/showthread.php?t=1298536](http://ubuntuforums.org/showthread.php?t=1298536)). 
But I need to save my evolution folder. I have Vista in C: and ubuntu in D:
I installed Ubuntu through Wubi.
I cannot see C:ubuntu. I can see D:Ubuntu.
In Ubuntu directory I can see the following directories : Disks, Install, winboot.
I checked the tool option in vista to see all the files and folders hidden. I did a search for Evolution in the hidden files as well.
nothing.
Is there a way to see this evolution directory in vista?
Thanks
Marco

---

### Post by martrn on 2009-10-24
There is only one way to explore a virtual volume on windoze and access that virtual volume while running windoze.  The virtual volume is an LVM ext 2/3/4 file.
See: [www.chrysocome.net/explore2fs]("http://www.chrysocome.net/explore2fs")

You could mount the device under any ubuntu system, as a loop-back mounted device.

---

### Post by marco77 on 2009-10-24
Thanks [martrn]("http://ubuntuforums.org/member.php?u=495007").
But I am not very good with these stuff. I have not find it very clear. I installed both explore2fs-1.08beta9.exe and virtual volume. But I do not find any Ubuntu directory. I am sure I am supposed to do something different with these programs.
Please, do let me know what I would need to do.
Thanks!

---

### Post by marco77 on 2009-10-25
Ok, it is a bit clearer now.
I download ubuntu.iso on my C: desktop.
I run the virtual volume program and I double click on ubuntu.iso.
Here it opens NTI Media Maker 8 and asks to burn the .iso on a CD. I do not want it, I just need to run ubuntu on a virtual machine. Any help?

---

### Post by martrn on 2009-10-25
I know what it is that you want, but can't give you any advice on what to do.

Your wubi files are ext2, ext3 or ext4 files that are local virtual files that are represented as a real file system by some trickery of the wubi kernel, and I don't know fully how it works.

If you want access to your files, then from the wubi guide at [wiki.ubuntu.com/Wubi]("https://wiki.ubuntu.com/WubiGuide") :
[SIZE="5"]How can I access my Wubi install and repair my install if it won't boot?[/SIZE]
1. Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:

```
sudo mkdir /win
sudo mount /dev/sda1 /win
```

2.Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein
```

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
```
**[COLOR="Red"]Change the above ^^^ if your file is in a diff location *impt*[/COLOR]**

Now the content of the virtual disk will be visible under /vdisk. 

3. To check the filesystem you can use:
```
sudo fsck /win/ubuntu/disks/root.disk
```

You need to run a full version (which the **live cd is a full version**), or run a windows program to revover your files, (virtual systems or wubi won't work)!  The reason virtual systems (which wubi is actually one) don't work is because they are run with a kernel running in userspace (a virtual kernel).  This prevents the virtual kernel from grabbing hold of the full use of the computer systems hardware from which the virtual system is run upon.  This has the advantage of protected the system from corruption, but this has a disadvantage of *not* giving the virtual kernel full use of all of the system resources.

I don't know how [www.chrysocome.net/explore2fs](www.chrysocome.net/explore2fs) works as its a windowze program, but there are reports of it working. Again I don't use windowze regularly.

I hope that helps (but doubt it a bit), a windoze user would be more help. Sorry.

EDIT:  To the moderators can we stop promoting wubi as a simple installation, wubi runs ontop of the another instalation and it runs a host but behaves as if it were a separate computer. Its more on an advanced topic / installation that a standard install.  PLEASE ??????

---

