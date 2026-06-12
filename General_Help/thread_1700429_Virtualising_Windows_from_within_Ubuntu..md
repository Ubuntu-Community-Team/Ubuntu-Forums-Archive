---
title: "Virtualising Windows from within Ubuntu."
date: 2011-03-05
forum: General Help
---

### Post by SkullTraill on 2011-03-05
Alright guys, I want to virtualise windows from ubuntu. 
I have 10GB for ubuntu, and another 10GB which I am willing to convert to ext3/4 to hold the windows virtual machine. I **also need the virtualised windows to be able to use my other ntfs drives which have all my important files. I know ubuntu has a problem writing to ntfs, I want to know if the smae problem is there while using a windows VM through ubuntu**.
I need a guide/recommended software for this. Thank you.
:popcorn:

---

### Post by Hedgehog1 on 2011-03-05
> **SkullTraill said:**
> Alright guys, I want to virtualise windows from ubuntu. 
I have 10GB for ubuntu, and another 10GB which I am willing to convert to ext3/4 to hold the windows virtual machine. I **also need the virtualised windows to be able to use my other ntfs drives which have all my important files. I know ubuntu has a problem writing to ntfs, I want to know if the smae problem is there while using a windows VM through ubuntu**.
I need a guide/recommended software for this. Thank you.
:popcorn:

SkullTraill,

XP will fit into a 10 gig Virtual Box 'Virtual Machine'.  Windows 7 will need 20 gig.

Virtual Box is free, and can be downloaded from here: [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

Virtual Box can share folders to ext3/4 and ntfs partitions.  Whatever problems you are experiencing writing the ntfs partitions will not change - the virtual machine see the world through the Host OS (Ubuntu) and read and writes using it.

If you use a common ntfs drive or partition (Not the one Windows is installed on) to share your ntfs data, that works well for most of us.

***The Hedge***

:KS

---

### Post by SkullTraill on 2011-03-05
> **Hedgehog1 said:**
> SkullTraill,

XP will fit into a 10 gig Virtual Box 'Virtual Machine'.  Windows 7 will need 20 gig.

Virtual Box is free, and can be downloaded from here: [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

Virtual Box can share folders to ext3/4 and ntfs partitions.  Whatever problems you are experiencing writing the ntfs partitions will not change - the virtual machine see the world through the Host OS (Ubuntu) and read and writes using it.

If you use a common ntfs drive or partition (Not the one Windows is installed on) to share your ntfs data, that works well for most of us.

***The Hedge***

:KS

Damn. I just need to know whether I can do things like:
[LIST]
[*]Set up uTorrent in the windows VM
[*]Make the downloads folder in the NTFS drive
[/LIST]
Will that work? I didn't really get what you said xD

---

### Post by Verbeck on 2011-03-05
it seems a little bit overkill to make a VM just to run a specific torrent client...
have you considered using a native linux application?

---

### Post by flyerbrooks on 2011-03-05
You can set up uTorrent as you wish and from my experience depending on how much memory you have given the VM you may see a drop in normal performance of uTorrent. The only way i know of to keep the downloads folder separate is to create 2 Virtual disks. 1 for windows and 1 for the download folder (which you can pre-sellect in the storage options of your VM).

---

### Post by Hedgehog1 on 2011-03-05
> **SkullTraill said:**
>  I just need to know whether I can do things like:
[LIST]
[*]Set up uTorrent in the windows VM
[*]Make the downloads folder in the NTFS drive
[/LIST]
Will that work? I didn't really get what you said xD

SkullTraill,

If the application you want to run in XP is uTorrent, there is a ***much less painful*** way to do this.

The Ubuntu Software Center has Deluge - it is a bit torrent client that is as fast as uTorrent.  The UI is even similar.

You can have it download directly into NTFS partitions.

***The Hedge***

:KS

p.s. Ubuntu loaded 'Transmission' when it installed.  This is another bit torrent client, but the UI is quite a bit different from uTorrent.

---

### Post by SkullTraill on 2011-03-05
Lol guys, the torrent thing was just an example.
Basically; I just need the VM to be able to directly communicate with my ntfs drives.

---

### Post by coldraven on 2011-03-05
Why use a VM?
I have a 1TB USB drive formatted NTFS, Ubuntu and Windows have no problems read/writing to it.

---

### Post by wirepuller134 on 2011-03-05
I don't remember exactly how one of our clients was doing it, but when they would copy files to an external storage location (read nas or usb device here) they were only copying links to the file location not the actual file.  This was causing all kinds of issues for them, as our server ran Ubuntu and the rest of the company was running Various versions of Windows.  The Ubuntu server was the only one that could see the links on the external devices.  Don't know if this helps, but might be something to look at.

---

### Post by howefield on 2011-03-05
> **SkullTraill said:**
> Basically; I just need the VM to be able to directly communicate with my ntfs drives.

Use the VirtualBox shared folders option ?

---

### Post by SkullTraill on 2011-03-05
> **howefield said:**
> Use the VirtualBox shared folders option ?

But since that would use Ubuntu's file handling to read.write to the NTFS drives, wouldn't it be buggy? IDK, I'll try this. Have you done it before? Has it worked?

---

### Post by gradinaruvasile on 2011-03-05
1. VirtualBox (and virtualization software in general) DO NOT write directly to your partitions/drives.
Everything goes through a driver that connects the virtual machine to the kernel (which in turn uses the systems file system drivers to read/write). The Windows installed inside VBox has a driver that fakes a Windows sharing interface through which you mount the shared folder from the host Linux system.
So you cant use your Windows installation from another partition (there is a complicated way to transfer them inside a VM, but you need huge amounts of disk space).
Also virtualization software introduces very high amount of memory overhead (and CPU, but this may be smaller and variable).

2. NTFS is a proprietary Windows file system - the specs are not published fully, so the drivers (ntfs-3g) used in Linux rely partly on reverse engineering - this means that it is not 100% compatible, but you can read/write on them withouth major concerns/issues.
3. Torrent software reads/writes many-many small parts of the downloaded file, and it seems that the aforementioned ntfs-3g driver does not cope very well with this kind of sustained activity leading to high CPU usage and slowing down the system (this is my own finding).

So, ideally you have to use a native linux torrent client AND write to a native linux file system such as ext3/4 to avoid this kind of issues. Deluge for example is a very very good cross platform client.

PS. There is really no need to use a virtual machine for one program that has very good Linux counterparts.

---

### Post by SkullTraill on 2011-03-05
> **gradinaruvasile said:**
> 1. VirtualBox (and virtualization software in general) DO NOT write directly to your partitions/drives.
Everything goes through a driver that connects the virtual machine to the kernel (which in turn uses the systems file system drivers to read/write). The Windows installed inside VBox has a driver that fakes a Windows sharing interface through which you mount the shared folder from the host Linux system.
So you cant use your Windows installation from another partition (there is a complicated way to transfer them inside a VM, but you need huge amounts of disk space).
Also virtualization software introduces very high amount of memory overhead (and CPU, but this may be smaller and variable).

2. NTFS is a proprietary Windows file system - the specs are not published fully, so the drivers (ntfs-3g) used in Linux rely partly on reverse engineering - this means that it is not 100% compatible, but you can read/write on them withouth major concerns/issues.
3. Torrent software reads/writes many-many small parts of the downloaded file, and it seems that the aforementioned ntfs-3g driver does not cope very well with this kind of sustained activity leading to high CPU usage and slowing down the system (this is my own finding).

So, ideally you have to use a native linux torrent client AND write to a native linux file system such as ext3/4 to avoid this kind of issues. Deluge for example is a very very good cross platform client.

PS. There is really no need to use a virtual machine for one program that has very good Linux counterparts.

Bravo! Exactly the kind of reply I needed.
Oh well, poor me, I'll have to dual-boot argg.

PS. They have very good alternatives, where the term "Very good" includes the fact that they are free. But the functionality and easy of use offered by certain windows software is not to be found in their linux alts. Even if they were eaqual, the fact that I've gotten accustomed to those programs [some of them being pretty advanced] means I'd be less likely to switch.
I'm talking about photoshop mainly, EVERYTHING [almost] else has proper alternatives in linux except Photoshop. Say what you will, but I think GIMP is pretty sucky.

---

### Post by Mark Phelps on 2011-03-05
> **SkullTraill said:**
> PS. They have very good alternatives, where the term "Very good" includes the fact that they are free. But the functionality and easy of use offered by certain windows software is not to be found in their linux alts. Even if they were eaqual, the fact that I've gotten accustomed to those programs [some of them being pretty advanced] means I'd be less likely to switch.
I'm talking about photoshop mainly, EVERYTHING [almost] else has proper alternatives in linux except Photoshop. Say what you will, but I think GIMP is pretty sucky.

BEFORE everyone jumps in here because this guy had the nerve to offer a negative opinion .. can we please NOT turn the rest of this thread into a Windows-vs-Linux debate? Please!

That kind of stuff belongs in the Community Forums or in Recurring Discussions.

---

### Post by SkullTraill on 2011-03-06
It was just my opinion. Nothing wrong with that...

---

