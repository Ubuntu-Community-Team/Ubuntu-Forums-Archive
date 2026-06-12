---
title: "Default software installation directory?"
date: 2010-11-09
forum: General Help
---

### Post by sshh on 2010-11-09
I'm using Ubuntu 10.04
I was thinking about how can I change the installation directory of the applications I install?
I'm new to ubuntu and don't have a lot of free space on the drive Ubuntu is on, and I usually install program on my external drive.
On Ubuntu I'm not given the chance to choose where do I want to install it. It's much easier that way, but I'd really like to change it.
Any ideas?

---

### Post by mcduck on 2010-11-09
Sorry, but you really can't.

Linux has no single "program files" directory or anything like that, all the files of a package are put into different places based on that file's purpose. So all executable files go to one place, libraries to another place, manuals and documentation to yet another directory and so on.

It is *possible* to move all these directories to another drive, but  that's not the simplest of a thing to do and you'll most likely just end wasting disk space, as you'd have to estimate the amount of space each directory will need perfectly or you'd easily end running out of space on one partition while another having plenty that you can't use.

The better route is to leave all the system stuff and programs where they are, and instead use the extra drives/partitions for your personal files.

---

### Post by sshh on 2010-11-10
Thank you. 
I think I'll survive. But it would be nice if there was such an option.

---

### Post by SeijiSensei on 2010-11-10
There are such options, but you need to know what you're doing.

A normal Linux distribution shouldn't ever consume much more than 10-20 GB no matter how much software you install.  It's the /home and /var directories where things get created, either by users in /home or by the system in /var (log files, for instance).

Unix does support mounting /usr, which is where nearly all programs and their supporting files are kept, on a separate filesystem from the root (/).  You could, therefore, create a separate partition on the hard drive, format it with an ext4 filesystem, and copy the entire contents of /usr onto that partition.  Then you'd need to change /etc/fstab to mount that partition at /usr during boot.  To delete the transferred files you'd need to boot into single-user mode and delete the contents of /usr on the original drive, then reboot.

So it's not impossible, but not something you should undertake until you have a lot more experience with Linux.  If you understood that paragraph completely, then give it a shot.  If not, stick with what you have now.

---

### Post by sshh on 2010-11-10
Thank you, I think I will try to do that.

---

