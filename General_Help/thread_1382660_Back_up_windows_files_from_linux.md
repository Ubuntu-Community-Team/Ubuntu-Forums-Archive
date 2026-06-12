---
title: "Back up windows files from linux"
date: 2010-01-16
forum: General Help
---

### Post by ARom on 2010-01-16
is there a way I can back up windows files from ubuntu 9.04 (wubi install)? and then store them on another medium, format the hard drive, and replace my important files?

I don't know if cross forum posting is allowed but I got a fairly nasty virus in windows xp: [http://forum.notebookreview.com/showthread.php?p=5742085#post5742085](http://forum.notebookreview.com/showthread.php?p=5742085#post5742085)

Someone suggested I mount the windows partition, but I do not know how to do that.

I googled and tried this tutorial: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

... but some options are missing from my Ubuntu install (wubi).

For instance, when I click Places, I do not see "x.0 GB media" like it has in the tutorial.

And, when I try to install NTFS configuration tool, it installs normally, but I can't see it under Applications --> System Tools.

Suggestions Please?

---

### Post by Ugluk on 2010-01-16
I would not recommend backing up Windows files with Linux tools, because it will not store file ownership and permissions properly.

If you use Wubi install, your partition which holds Ubuntu image is already mounted as /host. If you have other partitions, they will be available as /dev/sdXY, where X is physical drive letter (a, b, etc.) and Y is partition number, 1-4 for primary and 5+ for extended partition logical volumes.

You may mount them into some folder, f.ex. ~/tmp, by using "sudo mount /dev/sdXY /usr/your-name/tmp"; when you find your windows partition, just remove Windows directory, and rename "Documents and Settings" or "Users" directory, whichever is present. Then boot up from Windows CD/DVD, enter Recovery console and issue 'fixmbr' command (as security measure for some MBR viruses). Then reinstall Windows as usual (do not reformat the drive), it should not affect your existing Wubi installation.

In future, please restrain yourself from installing rogue antivirus software. If you're looking for free stuff, Avira, AVG and Avast are free antiviruses and Malvare Antibytes is a free spyware solution (which you don't need. BTW).

---

### Post by ARom on 2010-01-16
> **Ugluk said:**
> 
In future, please restrain yourself from installing rogue antivirus software. If you're looking for free stuff, Avira, AVG and Avast are free antiviruses and Malvare Antibytes is a free spyware solution (which you don't need. BTW).

Excuse me, I did not install any rogue anti-virus software (that would be silly). I have been using Avira and AVG for years and years, this particular bug installs itself and I'm dissapointed Avira did not catch it.

Malware Bytes caught the virus... but the virus imbedded itself in some critical windows files which malwarebytes then deleted. I should have had the malwarebytes live protection running as this would have stopped it, Avria did not stop the program from installing itself.

---

### Post by Ugluk on 2010-01-16
Do not use account with administrative privileges. Create a new account with password and make it Administrative. Demote all other user account to Limited. I will stop 90% of trojans and viruses from accessing your system.

As for our business, were you able to find/mount your Windows partition? How many drives and partitions do you have?

---

### Post by ARom on 2010-01-16
> **Ugluk said:**
> Do not use account with administrative privileges. Create a new account with password and make it Administrative. Demote all other user account to Limited. I will stop 90% of trojans and viruses from accessing your system.

As for our business, were you able to find/mount your Windows partition? How many drives and partitions do you have?

Somone on another forum suggested I try VistaPE to boot, obtain my old files, and then format the drive using WineHQ.

---

### Post by ARom on 2010-01-16
ok, I think I'm close to a solution.

I want to partition the "real" ubuntu so that I can use this tutorial to get to my hard drive: [http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

Can I download and install 9.10 from the ubuntu website and have three paritions? (windows xp (dead), 9.04, 9.10?

Or, can I just update to 9.10 to void the wubi installation so that I can have ALL the menu options?

I will try WineHQ and BartPE .

---

### Post by ARom on 2010-01-16
None of my previous methods worked, so I'm trying to get a visual mounting program to work, but none are showing up in the menu. (system tools).

I found out this info though: /dev/sda1   *           1       20672   156280288+   7  HPFS/NTFS

Are you suggesting I try: sudo mount /dev/sda1/usr/andy/tmp

?

---

### Post by jamesisin on 2010-01-16
I'm a little unclear on your current position but I'm going to throw some things out there as food for thought.

First, you might try this solution to recover your Vista build:

[http://www.soundunreason.com/InkWell/?p=470](http://www.soundunreason.com/InkWell/?p=470)

There are Vista instructions and this tool is pretty amazing (ComboFix).

Next, you certainly may have a triple boot system running Vista, 9.04, and 9.10.  Really, just about any combination.

If you want to move from a Wubi installation to a regular Ubu install, you could tar your home directory to another location, install Ubu, and then untar your home directory to that new location.

Finally, gparted is capable of shifting partitions around.  So this could all potentially be accomplished without wiping your Windows partition.

---

### Post by Ugluk on 2010-01-16
If you have a Wubi install, and a single hard drive with one partition, you should be able to access it via /host.

---

### Post by ARom on 2010-01-16
> **jamesisin said:**
> I'm a little unclear on your current position but I'm going to throw some things out there as food for thought.

First, you might try this solution to recover your Vista build:

[http://www.soundunreason.com/InkWell/?p=470](http://www.soundunreason.com/InkWell/?p=470)

There are Vista instructions and this tool is pretty amazing (ComboFix).

Next, you certainly may have a triple boot system running Vista, 9.04, and 9.10.  Really, just about any combination.

If you want to move from a Wubi installation to a regular Ubu install, you could tar your home directory to another location, install Ubu, and then untar your home directory to that new location.

Finally, gparted is capable of shifting partitions around.  So this could all potentially be accomplished without wiping your Windows partition.

thanks for the advice, and I'm actually running (or trying to fix) xp.

---

### Post by ARom on 2010-01-16
> **Ugluk said:**
> If you have a Wubi install, and a single hard drive with one partition, you should be able to access it via /host.

what is /host? 

what do I do with /host?

---

### Post by ARom on 2010-01-16
> **Ugluk said:**
> If you have a Wubi install, and a single hard drive with one partition, you should be able to access it via /host.

thank you thank you thank you thank you.

It was simply under filesystem/host, all of my files are there!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

In fact, I could delete the virus files from the ubuntu side (filesystem/host/windows) if I knew the names but I'm not going to take that chance. I'm going to save my files via email and wipe this thing clean.

---

### Post by jamesisin on 2010-01-16
Sorry, thought you were running Vista.  That link I provided does also include XP instructions and I have used ComboFix many times on XP with terrific success.

---

### Post by ARom on 2010-01-16
**Solution**

I found my windows files in "file system/host" (ubuntu). :rolleyes: 

All windows files of a wubi ubuntu install are stored in "file system/host". (courtesy of ubuntu forums.org)

**For future reference:**

- If you did not do a wubi install but the normal ubuntu install, simply click - Places/x.0 GB Media (computer, x.0GB Media) 

- If you did not do a wubi install but the normal ubuntu install, and you cannot see the Media Drive, try mounting your windows drive with the ntfs configuration tool: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

- check: "filesystem/host" regardless

- If you do not have any version of linux installed but have come across this problem (Bsod), boot up a live ubuntu cd: 
[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

- If you do not have any version of linux installed and prefer a windows based alternative to seek the files on your hard drive try a live windows cd: [http://www.dedoimedo.com/computers/livecd.html](http://www.dedoimedo.com/computers/livecd.html) (Bart's PE Builder)

Thanks guys.

---

