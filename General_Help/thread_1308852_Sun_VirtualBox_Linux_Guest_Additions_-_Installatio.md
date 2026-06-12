---
title: "Sun VirtualBox Linux Guest Additions - Installation?"
date: 2009-10-31
forum: General Help
---

### Post by GPJones on 2009-10-31
[B]Can anyone here instruct a total newb on how to install the Sun VirtualBox Linux Guest Additions?
[/B]
This is from the VirtualBox Helpfile:

4.3.1. Installing the Linux Guest Additions
The VirtualBox Guest Additions for Linux are provided on the same ISO CD-ROM as the Additions for Windows described above. They also come with an installation program guiding you through the setup process, although, due to the significant differences between Linux distributions, installation may be slightly more complex.

Installation involves the following steps:

Before installing the Guest Additions, you will have to prepare your guest system for building external kernel modules. This works similarly as described in Section 2.3.2, “The VirtualBox kernel module”, except that this step must now be performed in your Linux guest instead of on a Linux host system, as described there.

Again, as with Linux hosts, we recommend using DKMS for Linux guests as well. If it is not installed, use this command:

sudo apt-get install dkms
Install DKMS before installing the Linux Guest Additions.

Mount the VBoxGuestAdditions.iso file as your Linux guest's virtual CD-ROM drive, exactly the same way as described for a Windows guest in Section 4.2.1.1, “Mounting the Additions ISO file”.

Change to the directory where your CD-ROM drive is mounted and execute as root:

sh ./VBoxLinuxAdditions-x86.run
In a 64-bit Linux guest, use VBoxLinuxAdditions-amd64.run instead.

The VirtualBox Guest Additions contain several different drivers. If for any reason you do not wish to install them all, you can specify the ones which you wish on the command line - for example

sh ./VBoxAdditions.run x11
to install the X Window graphic drivers. Type in the command

sh ./VBoxAdditions.run help
for more information.

To recompile the guest kernel modules, use this command: 

/etc/init.d/vboxadd setup
After compilation you should reboot your guest to ensure that the new modules are actually used.

---

### Post by GPJones on 2009-11-01
Hello Anyone:
 
What I am asking for here is not VirtualBox help, I am asking for someone to show me step by step how to run the commands as pasted into the previous post.
 
There is a cd image on the desktop that when I click on it, shows the guest additions run file.
 
I can't figure out how to switch to "root" and navigate to that folder to run that file. So as I see it, it is actually a Ubuntu command that I am asking help with.
 
Any help is appreciated but preferrably from someone used to using both the command line and the graphical interface.
 
I really want to learn this system but for now want it in a VirtualBox.
 
Thanks!

---

### Post by GPJones on 2009-11-02
Hello All:

I figured this out myself and learned a little about terminal commands in the process.

Steps:
1.) Opened Accessories > Terminal
2.) cd /media/cdrom0
3.) type: "sudo apt-get install dkms" without the quotes.
wait for it to process
4.) type: "sudo sh ./VBoxLinuxAdditions-x86.run" without the quotes.
wait for it to process.
Restart.

In the VirtualBox Machine Menu there will be additional selections and now I can resize my screen to my 24" monitor and use Ubuntu like I want to.

Trial and error got me there. That's why I wanted to put it in a VirtualBox so I can learn without disrupting the Host system.

---

