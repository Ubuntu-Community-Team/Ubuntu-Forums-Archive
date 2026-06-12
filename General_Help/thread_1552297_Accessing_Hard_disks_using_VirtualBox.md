---
title: "Accessing Hard disks using VirtualBox?"
date: 2010-08-13
forum: General Help
---

### Post by meburke on 2010-08-13
I installed VirtualBox from the VB downloads section and installed it using dpkg,,,worked fine, I got windowsXP to load, run and update normally. (Note: I needed to use the PUEL version from VB in order to access USB drives; the repository version wouldn't work, and neither did the first version, 3.2.6. It MUST be 3.2.8 on my system or USB doesn't work.)

Now I need to access an older Windows hard drive, and I'm having no joy.

After much experimentation I got the message:

RAW host disk access VMDK file /home/meburke/.VirtualBox/Vista.vmdk created successfully.

Unfortunately, I can't seem to see it from the guest OS (WindowsXP...The disk is an mbr-cleaned drive from the last Vista system that crashed on me.) I can see it just fine from the Host OS (Ubuntu Karmic 9.10) and have been able to transfer, read and write files from the disk, so I know it is working up to that point. The .vmdk is "../.VirtualBox/Vista.vmdk -rawdisk /dev/sdc -partitions 2 -relative" (which is what the manual says I should use if I want the guest to access only that part of the drive). The disk is connected to the 3rd SATA connection on my motherboard, so I don't have any usb complications.

I can't seem to add the vmdk from the Virtual media Manager. In the details I get:

Result Code:
NS_ERROR_FAILURE (0x80004005)
Component:
Medium
Interface:
IMedium {1d578f43-5ef1-4415-b556-7592d3ccdc8f}
Callee:
IVirtualBox {3f36e024-7fed-4f20-a02c-9158a82b44e6}

I checked for partitions using: VBoxManage internalcommands listpartitions -rawdisk /dev/sdc

I get:

Error opening the raw disk: VERR_ACCESS_DENIED

I have changed the file permissions to 777 on the assumption that if it is permissions I can reduce privileges later, but I still get the same results. I had to change the owner from root to me in order to get these results from:

VBoxManage internalcommands listpartitions -rawdisk /dev/sdc
Oracle VM VirtualBox Command Line Management Interface Version 3.2.8
(C) 2005-2010 Oracle Corporation
All rights reserved.

Number  Type   StartCHS       EndCHS      Size (MiB)  Start (Sect)
1       0x27  0   /1  /1   1023/254/63          9993           63
2       0x06  1023/254/63  1023/254/63        466945     20467712

So I'm pretty sure the disk is showing up. I can read and write to it from the Host. Now I just need the last step to allow me to read and write from the Guest.

Can anybody help me on this?

Thanks,

Mike

---

### Post by Irony on 2010-08-13
I assume you are referring to guest additions which amongst other things will allow you to set up shared folders. For example I have share my Ubuntu downloads folder with Windows 7 guest where it shows up as a drive in  Windows 7;

[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders)

[http://www.dedoimedo.com/computers/virtualbox-guest-addons.html](http://www.dedoimedo.com/computers/virtualbox-guest-addons.html)

[http://www.youtube.com/watch?v=75FeKOkpSKk](http://www.youtube.com/watch?v=75FeKOkpSKk)

The video is most useful.

---

### Post by meburke on 2010-08-16
I appreciate your help, but this is not working, and I don't think it is what I really want (but I may be wrong).

Using VBoxManage I created a .vmdk file. The implication is that this file can be added to the virt guest and will perform just like a disk partition (thus the rawdisk access). The further implication is that I can add the .vmdk file using the "Virtual Media Manager" option from the "File" menu in the menu bar.

What happens is that when I try to open the .vmdk using this process I get:

Failed to open the hard disk /home/meburke/.VirtualBox/Vista.vmdk.

Could not open the medium '/home/meburke/.VirtualBox/Vista.vmdk'.

VD: error VERR_ACCESS_DENIED opening image file '/home/meburke/.VirtualBox/Vista.vmdk' (VERR_ACCESS_DENIED).

Opening up "Details" shows:

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Medium
Interface: 
IMedium {1d578f43-5ef1-4415-b556-7592d3ccdc8f}
Callee: 
IVirtualBox {3f36e024-7fed-4f20-a02c-9158a82b44e6}

So, since I can access the directory, the file permissions seem to be good (777) and the file shows up in my Media Manager process, I think I'm close but very frustrated that I'm not getting what I expect and need.

I did try to come at it from your direction. I do not have to access the drive raw if there is a good sharing solution. I just haven't found one. I tried to get to where I can see the disk partition as a shared folder, but I can't seem to get it to open.

I have file and printer sharing enabled.

I used the command: net use p: \\VBOXSRVR\OldVista from the command line, but it

I can see \\VBOXSRVR\OldVista in the "FOlders" explorer bar.

Yet, when I try to open the folder "Hard Disks" I get a document that says "Vista.vmdk" that cannot be opened either as a document or as a hard drive. AAAaarghhhh!

The third point, as an aside, is that by searching and references to other instructions such as you gave me, I am in a hell made up of piecemeal links to incomplete and obfuscated directions. I swear, that if I ever get to the point where I can actually help someone, I will NEVER direct them to another site! I will ALWAYS give full, step-by-step instructions with the expected results,and checklists. I will only use links to acknowledge where I found the sources of my instructions.

To give you an example of how this can be confusing:

The first link you gave me tells me to "mount -t vboxsf share mountpoint" Makes sense, except that neither "vboxsf" nor "vboxfs" is right. I get "mount: unknown filesystem type 'vboxfs' " on both options.

Ahh...OK, the link at [http://my-wd-local.wikidot.com/otherapp:configure-virtualbox-shared-folders-in-a-windows-host](http://my-wd-local.wikidot.com/otherapp:configure-virtualbox-shared-folders-in-a-windows-host) tells me to use: "# mount.vboxsf VirtualBox /mnt/vbox_share" ...OK, that makes sense also...I just have to use internal commands instead of common LINUX commands, right?

Nope. I get: "The program 'mount.vboxsf' is currently not installed.  You can install it by typing:
apt-get install virtualbox-ose-guest-utils"

Uhh, huh.. Now since I'm running PUEL instead of OSE, do I really want to install those utilities? There is no single source that tells me what the consequences might be. I'm beginning to think I could write a Master's theses on the possibility tree for getting Windows to run as a VirtualBox guest on Ubuntu 9.10.

I really appreciate your help. One of my problems is that I seldom have more than an hour or so at a time to work on this problem before I have to attend to something else. By the time I get back to it I've lost the continuity or flow that I had before.

Thanks,

Mike

---

### Post by yendorian on 2010-08-16
The only way I know is to re-install the old OS on its original .vdi drive and transfer the required data to your shared folder.

---

### Post by meburke on 2010-08-18
Nope. Not going to happen. (Famous last words?)

However, I did get access to my disk using sharing instead of rawdisk access. For those of you interested, I went to the "Devices" menu on top after booting my guest. I then selected "Shared folders" and browsed to the disk I wanted to share. I enabled file sharing in my guest (WindowsXP), and I used the tools menu from the Explorer pane to map the network drive. I made it permanent and rebooted my guest. The shared folder/files/network share showed up fine in my Explorer pane (My Computer).

This brings on other problems:

See, the goal of this whole experiment is to get my old Outlook.pst file somewhere where I can recover the data. Now I can see it, but I can't copy it by dragging and dropping nor can I use the command line.

I get messages to the effect that the parameter is incorrect. This may be related to the fact that the drive is NTFS formatted and I have no idea what the alleged format is on the virtual box .vdi.

Outlook won't import it; it says it is not a .pst file.

readpst tells me it can't get the root record, so there goes my first attempt at creating an mbox-type file.

I downloaded Thunderbird, which is supposed to import from .pst files. The wizard just assumes the only .pst file I'm interested in is the one created when I installed Outlook. I have no choice in where to look for the file.

scanpst tells me it can't access the file.

I have installed another hard drive, and some files give me the same messages when I try to access them.

The Stellar Phoenix pst repair program seems to hang up. (My .pst is 3.6G, but it was created in Office 2003, so that should not be the problem.

Unless someone can tell me why I get the "wrong parameter" message when trying to copy, This thread is pretty much closed.

Conclusions:
1. Drive access doesn't always work for some reason.
2. Sharing works better than rawdisk access at this point.
3. USB access gives I/O errors unless the drive is formatted NTFS.
4. Ubuntu forums work better than VirtualBox forums for getting relevant answers.

I appreciate everyone's help. Time for a new thread.

Thanks,

Mike

---

### Post by meburke on 2010-09-06
OK, still can't access the drives raw, but the share works fine. I discovered that the drive I most needed to access was going bad, which was responsible for a lot of my problems. Still, I managed to recover 67,000 old emails in .pst archives into Outlook on my virt.

Thanks for the help.

Mike

---

