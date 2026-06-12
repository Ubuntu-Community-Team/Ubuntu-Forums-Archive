---
title: "VirtualBox exclusively"
date: 2011-04-22
forum: General Help
---

### Post by noworldorder on 2011-04-22
I am considering running Ubuntu with Ubuntu in VirtualBox.  And I am considering using the virtual hard drive exclusively.  This is the reason:

I seem to jsut get my system the way I want it and then something goes wrong with my computer and I need to start from scratch with a new computer.  I could easily backup my virtual hard drive and if my computer died I could install virtualBox on a new computer and put my virtual hard drive on it and I would have my same set up.

So... is this crazy?
..... how much performance would I lose?
...... is there a better way to do something like this than what I am considering?
..

thanks

---

### Post by UranUtan on 2011-04-22
Hi,

This is how I learn Ubuntu 2 years ago (running Ubuntu in Virtualbox on a Windows 7 host). Then after 2 or 3 months, I installed Ubuntu for real in dual boot on a Desktop computer (along with Windows Vista). After a year, I didn't boot Vista a single time, so I re-installed Ubuntu as single OS.

Virtualbox is very good. You will get roughly 90% to 95% of the performance of a physical machine, with the condition you don't do too much I/O intensive operations (like DB Server, Media encoding, etc.)

Any better way than what you planned? I think that once you get comfortable with Ubuntu (I now use LinuxMint) you will notice that it's a pain to boot the host machine, then boot the VM. That takes a lot of time. It's more fun (and boot faster) when you have Linux installed for real. Use a spare hard drive to play around. You seems to relies on backing up the VM as the reliability factor. I am not a guru in linux but I never had anything messed up anything in my machine. I just use the technique of separating 3 partitions: /boot (200 MB, etx2), / (20 GB, etx4), swap (2GB) the rest to /home (ext4). If ever something bad happen I just re-install LinuxMint (or Ubuntu in your case) by taking care of not reformatting the /home partition.

Actually it's the opposite that I do. When I really need to do something that absolutely needs Windows, I run it as a Virtualbox VM  on the Linux host.


Good lucks.

---

### Post by mikewhatever on 2011-04-22
You could use Clonezilla to clone the Ubuntu partition and restore it when needed.

---

### Post by robertcoulson on 2011-04-22
I use virtual box to run Ubuntu 11.04 beta and Mint linux ( I like Mint, it looks great)...so my Ubuntu 10.10 doesn't get out of shape... Works good for me that way.

Robert

---

### Post by techunit on 2011-04-22
Don't bother just back up your home folder. Problem solved. Good Luck.

---

### Post by noworldorder on 2011-04-22
thanks for all the feedback

Regarding Clonzilla - this only works if your computer does not fail.  That is, you cannot restore on a different computer.

And as far as backng up my home directory - this would not backup the programs I have installed would it?

@Robert - do you keep all you files on the host operating system and access them from the virtual operating systems?  Also, are thee any tips you have regarding this?

thanks

---

### Post by mikewhatever on 2011-04-22
Clonezilla should work on any computer, regardless of whether the original one failed or not.

---

### Post by robertcoulson on 2011-04-22
noworldorder...Yes, the nice thing about virtual box is if something goes wrong or you get bored of a OS (windows, linux, etc.) you can wipe it or install it again and again....I had 11 OS's installed at one time...!!!
Robert

---

### Post by robertcoulson on 2011-04-22
Sorry..P.S...I would use the virtual box download from their web site.....The one that you download from "Ubuntu software center" is not as good as the web site version.

Robert

---

### Post by Hedgehog1 on 2011-04-23
I run an number OS's in virtual box, and do my 'experiments' in them as well:

[IMG]http://img219.imageshack.us/img219/455/vbox01.png[/IMG]

You use the 'export virtual appliance' and 'import virtual appliance' to do fast saves, restores and to replicate an install to modify to newly created copy.


***The Hedge***

:KS

---

### Post by noworldorder on 2011-04-23
> I run an number OS's in virtual box, and do my 'experiments' in them as well:

How large do you make the Virtual Drives?  And do you share the files of each machine with the host?

thanks

---

