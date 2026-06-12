---
title: "Can't access Windows partition"
date: 2009-09-01
forum: General Help
---

### Post by starbright on 2009-09-01
Hey,

I just installed Xubuntu and now I wanted to access my Windows partition from Xubuntu, but I can't. I don't have anything under places and when I try to access it with Gigolo I get an error message: 

[CENTER]"Connecting to 'XP' Failed
         You are not supposed to show G_IO_ERROR_FAILED_HANDLED in the UI"[/CENTER]

I have no idea what that means and what I should do to try to fix it.

Help would be really appreciated :)

---

### Post by gldearman on 2009-09-01
Does your Windows partition have an entry in [/etc/fstab]("https://help.ubuntu.com/community/Fstab")?  You could set it up to auto-mount every time.

---

### Post by starbright on 2009-09-01
I just checked, and no I don't. So what would I have to do now?

---

### Post by DeMus on 2009-09-01
> **starbright said:**
> I just checked, and no I don't. So what would I have to do now?

Try this:

**_Auto mount Windows disks_**
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus (Gnome filemanager in Ubuntu).
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

---

### Post by starbright on 2009-09-01
Thanks. I did what you said and it worked. I can now access my windows partition. But how come I can't see it in the Filer Manager or on my desktop. It's also not under Places. Do I have to mount it again in some other way or can I just access the partition using gigolo( remote filesystems)?

---

### Post by DeMus on 2009-09-01
> **starbright said:**
> Thanks. I did what you said and it worked. I can now access my windows partition. But how come I can't see it in the Filer Manager or on my desktop. It's also not under Places. Do I have to mount it again in some other way or can I just access the partition using gigolo( remote filesystems)?

Well, in Ubuntu the mounted disks show up. I don't know about Xubuntu since I don't use it. Sorry.
Maybe somebody else knows this and likes to help to help you.

---

### Post by petrus4 on 2009-09-01
> **starbright said:**
> Thanks. I did what you said and it worked. I can now access my windows partition. But how come I can't see it in the Filer Manager or on my desktop. It's also not under Places. Do I have to mount it again in some other way or can I just access the partition using gigolo( remote filesystems)?

The automounter may or may not cause you further problems later on, knowing what Ubuntu/Debian's "user friendly," options are like.  I will explain how to do it via /etc/fstab.  You probably won't like this, but it will ensure that you have less problems than going through potentially opaque GUI programs.

The first step is to find out what the device name of your Windows partition is.  If it's the first one on your disk (i.e., Windows was on your system before Ubuntu) it's probably called /dev/sda1.

To make sure, though, open a terminal and enter this:-

```
sudo fdisk /dev/sda
```

In fdisk, press p to list your partition table, and look for the word "NTFS," since that is the name of the Windows file system.  The device name/number (/dev/sda1 as an example) will be next to it.

Once you've recorded that, hit q to get out of fdisk.  Now we need to make a directory to serve as a mount point for the disk.  I use /mnt, which is traditional, but Ubuntu generally uses /media, which truthfully I consider somewhat retarded, but it's part of the standard, these days.  

```
sudo mkdir /media/winc
```

Hopefully that will be reasonably self-explanatory; winc being the name of your Windows C drive.  Now we need to open /etc/fstab.

```
sudo nano /etc/fstab
```

You will hopefully see a textual table listing a couple of your already mounted drives, including your Linux boot partition, although given the falsely "user friendly," opaque abomination Ubuntu is these days, anything is possible.

Go down to the bottom of that file; you need to enter in a new entry for your Windows partition.

```
/dev/sda1  /media/winc  ntfs  ro  0  0
```

Put that, as I said, at the bottom of /etc/fstab, and remember that sda1 there is only an example.  If you found out from fdisk that the device number of the partition is something different, you need to put that in place of sda1.  Also make sure those two 0s at the end of the line are there, and don't change them to anything else, either.

The above will mount the NTFS drives read-only, but to be truly safe, that is the only way I'd use them, in Linux.  If you want to write to them, do that from in Windows.

Now, uninstall that automounter to make sure it doesn't conflict with this in any way.

```
sudo aptitude remove ntfs-config
```

The last step is to use the mount command to make sure the drive gets mounted.

```
sudo mount -a
```

If you have any other Windows partitions, you can follow this procedure to add them as well.

At the risk of causing controversy here, I'm also going to tell you to use the command line to solve problems if you want them to stay solved.

It might seem a bit harder at first, but it will save you more problems later on, and if you do learn to use it, even if you do get something else breaking, you'll have a better chance of successfully fixing it.

---

### Post by starbright on 2009-09-01
Okay, so I did everything and I have it mounted. Now it just doesn't appear in Places, on my desktop or in the File Manager.

Anyone know what to do? Or does it just not show up in Xubuntu, because I know it does in Ubuntu.

---

### Post by JKyleOKC on 2009-09-01
Open Places, and navigate down the file system until you show the directory where your Windows disk is mounted (such as /media/winc). Highlight that directory and drag it over to the shortcut pane at the bottom left of the File Manager window. Now close Places, and re-open it. Your Windows directory should appear where you dragged it. At this point you can highlight the shortcut, right-click, and rename it to whatever you want; this won't change the directory name, just the name of the shortcut itself.

I've done this on two Xubuntu boxes. Note that File Manager opens automagically when you select it in Places, and the dragging should be done there.

---

### Post by starbright on 2009-09-01
I never thought of dragging it over. Thanks, now I finally have it in Places :)

---

