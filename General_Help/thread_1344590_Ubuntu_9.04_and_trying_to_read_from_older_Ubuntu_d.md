---
title: "Ubuntu 9.04 and trying to read from older Ubuntu disk"
date: 2009-12-03
forum: General Help
---

### Post by L a r r y on 2009-12-03
My computer died.  In it I was running Ubuntu 8.04 and Windows XP Professional.  I have a hard drive from that computer set as master, and containing the operating systems and Home directory.  A slave disk contains some backup files and some music files in Ubuntu 8.04's journaling file system, version 3, and for the life of me I can't recall its name.

I brought out a computer from the back room that was running Kiwi version of Ubuntu 8.04 and Windows XP Home, but it has a 200GB hard drive set as a Sata drive.

I attempted to attach the slave drive from the old computer, but I grabbed the master by mistake.  Up came Ubuntu 8.04 and trying to run in a new motherboard environment.  Shut it down and put in the intended slave, and up comes a copy of Windows Me that had been upgraded to Windows XP some time ago, but the slave drive was nowhere to be detected by the bios.

OK, I put the Sata drive in by itself and Windows XP or Kiwi were available as before.  I downloaded a copy of Kiwi 9.04 and burned it to a disc, and boy does it love this computer!

However, I shut down and pulled the Sata drive out of the system and put in the master with Windows XP Pro and Ubuntu 8.04 from the dead computer.

Booted on the Live CD for Kiwi 9.04 and I cannot access files in my 8.04 home directory, but I can access files in the NTFS partition for Windows.

[B]So my question is, how do I go about accessing my files on the hard drive in the Ubuntu partition?  Since I am on a Live CD, I have not set up a password with which to sudo anything.
[/B]
My plan is to install Kiwi 9.04 on the Ubuntu partitions and then retrieve the tar file of my home directory stored on the slave drive.

I might even want to consider getting a clean hard drive and installing Kiwi on it as a master so I can put both the old master as a slave and then the old slave as a slave to copy files over to the new installation.

There are some things in Windows that I can access with Linux that I want to salvage, as well, so I don't want to reuse these hard drives just yet.

Sorry for the long post, but I am still relatively new at this.

Thanks in advance.  (My signature contains data on the dead computer.) Edit: Or it doesn't -- I had forgotten what I had in there!

---

### Post by L a r r y on 2009-12-04
bump

---

### Post by L a r r y on 2009-12-04
Here is some more information:  I am running the Live CD, and I tried sudo, even though I have no password set.  I can sudo dir directories that deny permission when I dir the directories without sudo.  No password is requested.

While I can dir my Desktop on the disk from the 8.04 installation using sudo, I cannot cd to it without being denied permission, I cannot sudo cd to it either.

I get sudo: cd: command not found.

Edit:
Further update:  I can sudo dir Desktop, and I can sudo firefox Desktop/musicfile.mpga, which according to the information in the Terminal, runs the totem plugin, so:

I can sudo totem Desktop/misicfile.mpga as well and have it play.

Further, I can sudo mkdir directory
 and then I can sudo chown ubuntu:ubuntu directory
to change owner and group to "ubuntu" which is the Live CD user.

So I think if I at least chown everything to ubuntu I should have regained access to everything.

---

### Post by Some Penguin on 2009-12-04
> **L a r r y said:**
> My computer died.  In it I was running Ubuntu 8.04 and Windows XP Professional.  I have a hard drive from that computer set as master, and containing the operating systems and Home directory.  A slave disk contains some backup files and some music files in Ubuntu 8.04's journaling file system, version 3, and for the life of me I can't recall its name.

ReiserFS?  XFS?  JFS? 

> However, I shut down and pulled the Sata drive out of the system and put in the master with Windows XP Pro and Ubuntu 8.04 from the dead computer.

Booted on the Live CD for Kiwi 9.04 and I cannot access files in my 8.04 home directory, but I can access files in the NTFS partition for Windows.

Re:  your 'sudo cd', that won't work because cd is a shell built-in, not a separate command.  However, I would not be terribly surprised if

  sudo bash

worked (substitute your preferred shell) which should give you a root shell (provided that /etc/sudoers lets you, and there's not much point in writing an /etc/sudoers that will block shells but will let them edit the /etc/sudoers file!).

---

### Post by L a r r y on 2011-11-12
> **Some Penguin said:**
> ReiserFS?  XFS?  JFS? 



Re:  your 'sudo cd', that won't work because cd is a shell built-in, not a separate command.  However, I would not be terribly surprised if

  sudo bash

worked (substitute your preferred shell) which should give you a root shell (provided that /etc/sudoers lets you, and there's not much point in writing an /etc/sudoers that will block shells but will let them edit the /etc/sudoers file!).
I'm sorry I didn't get back to this thread to see an answer from two years ago.  I was running EXT3 filesystem here since my first install of Ubuntu 6.06.  

The comment with regard to sudo cd does explain why that didn't work.  

I offer my belated thanks for the information.

Mark this one solved.

---

