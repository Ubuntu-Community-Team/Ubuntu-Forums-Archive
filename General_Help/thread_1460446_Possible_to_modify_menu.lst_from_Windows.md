---
title: "Possible to modify menu.lst from Windows?"
date: 2010-04-22
forum: General Help
---

### Post by DrHow on 2010-04-22
I would like to be able to change which OS is the default for grub to boot, and I would like to be able to do so easily from either Ubuntu or Windows.  I suspect that this may be possible if I put /boot on an ntfs or FAT32 partition (though I do not wish to install Ubuntu itself on such a partition).  There I would put multiple versions of menu.lst specifying different defaults.  Then, before a restart, I can run a script which will copy, as the 'true' menu.lst, the one which specifies the desired default for my next boot.

Is this possible?  If so, what do I need to worry about?  (I must admit that it is unclear to me how the code in the MBR even finds the correct menu.lst.)

There is a thing I have worried about with a dual booted system and which I suspect I do not need to worry about.  However, I would like to be reassured.  I have ntfs partitions and removable drives which both Windows and Ubuntu can access.  If a crash occurs which leaves a drive "dirty" (e.g., after a power fail), I am assured that if I reboot the OS in which the crash occurred, it will realize that the drive is "dirty" and will take measures to assure that no corruption will ensue.  However, I am not so sure about the correct response if the next OS I boot is different from the one that crashed.  I think Ubuntu and Windows both use the same convention for noting that a drive is "dirty", in which case I am worrying about nothing.  Is it true?  Do they?

The relevance of the above worry in this menu.lst context is that, if it is important to reboot the same OS after a crash, then I would also include for each OS on _startup_ a script that would make itself be the default for a next boot.

---

### Post by 2hot6ft2 on 2010-04-22
What version of ubuntu are you running and did you upgrade from another version?
Because grub2 (grub-pc) does not have a menu.lst file.
In the old grub there was an option to boot to the last used but I don't know in grub 2.

---

### Post by DrHow on 2010-04-22
> **2hot6ft2 said:**
> What version of ubuntu are you running and did you upgrade from another version?
Because grub2 (grub-pc) does not have a menu.lst file.
In the old grub there was an option to boot to the last used but I don't know in grub 2.

I am running 9.10 to which I upgraded from 9.04.  AFAIK, grub has not been updated.  I read some about grub2, and I have no /boot/grub/grub.cfg file.  So I must assume that old grub is still using my old /boot/grub/menu.lst.

The grub2 business is news to me.  But I do want to switch to it.  So I want a solution that will work with /boot/grub/grub.cfg.  However, I don't think that changes the main thrust of my question.  It comes down to, "Can I put the /boot/grub directory somewhere where a script in Windows can replace the grub.cfg file, and will this work properly?"  I can see how to use /etc/default/grub to generate grub.cfg files with different defaults.  Now I wish I could change the title of this thread.  :(

---

### Post by quadproc on 2010-04-22
> **DrHow said:**
> I would like to be able to change which OS is the default for grub to boot, and I would like to be able to do so easily from either Ubuntu or Windows.  I suspect that this may be possible if I put /boot on an ntfs or FAT32 partition (though I do not wish to install Ubuntu itself on such a partition).  There I would put multiple versions of menu.lst specifying different defaults.  Then, before a restart, I can run a script which will copy, as the 'true' menu.lst, the one which specifies the desired default for my next boot.

I don't know what kind of issues that you might run into regarding the Microsoft stuff potentially damaging your Ubuntu system (Windows "fixed" my disk when I booted Windows once) but there is one big concern regarding your approach: the 'end of line' characters.  Linux uses a single LF to terminate a record while the Microsoft world generally uses CR followed by LF.  You may have to take special steps to see that you get the appropriate end of line characters in your files.

quadproc

---

### Post by DrHow on 2010-04-22
> **quadproc said:**
> I don't know what kind of issues that you might run into regarding the Microsoft stuff potentially damaging your Ubuntu system (Windows "fixed" my disk when I booted Windows once) but there is one big concern regarding your approach: the 'end of line' characters.  Linux uses a single LF to terminate a record while the Microsoft world generally uses CR followed by LF.  You may have to take special steps to see that you get the appropriate end of line characters in your files.

quadproc

Not a concern.  As I mentioned, I can see how to get grub_update to generate the various grub.cfg files I need.  Windows would only be copying one of them to be the active grub.cfg file.  This will not foul up the line endings.

My concerns are more along the lines of whether the MBR code can find grub.cfg when it is in a 'strange' place or on a logical partition with a file system different from that used for Linux.  There may also be unusual requirements for setting this up initially.

---

### Post by 2hot6ft2 on 2010-04-22
> **DrHow said:**
> 
My concerns are more along the lines of whether the MBR code can find grub.cfg when it is in a 'strange' place or on a logical partition with a file system different from that used for Linux.  There may also be unusual requirements for setting this up initially.
It should be ok on a FAT32 but not on NTFS. At least I wouldn't think it would work on NTFS since nfs-3g wouldn't be loaded yet.
It's a rather unusual plan you have so I better just leave it to those that know if it will work and sit back and watch. I will add that I'm sure you know linux doesn't care if it's an extended or a primary partition.
:popcorn:

---

### Post by DrHow on 2010-04-22
> **2hot6ft2 said:**
> It should be ok on a FAT32 but not on NTFS. At least I wouldn't think it would work on NTFS since nfs-3g wouldn't be loaded yet.  ...


Ahh!  That is precisely the sort of gotcha I hoped to be warned about.  Not knowing this, I would probably have chosen NTFS, as that seems more robust than FAT32 under most circumstances.

---

### Post by 2hot6ft2 on 2010-04-22
> **DrHow said:**
> Ahh!  That is precisely the sort of gotcha I hoped to be warned about.  Not knowing this, I would probably have chosen NTFS, as that seems more robust than FAT32 under most circumstances.
Good to know I could at least help a little. Interesting project you have in mind.

---

### Post by oldfred on 2010-04-23
I think what you want is built into grub2.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
See this section.
GRUB_DEFAULT - Sets the default menu entry. Entries may be numeric or "saved"

I remember with OS/2 we had a little program (something like dd?) that wrote the boot loader into the MBR from either windows or OS/2. You rebooted to your last selection unless you ran the program to change to the other one. Many times I rebooted to the wrong system because I forgot to switch boot loaders.

---

### Post by DrHow on 2010-04-23
> **oldfred said:**
> I think what you want is built into grub2.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
See this section.
GRUB_DEFAULT - Sets the default menu entry. Entries may be numeric or "saved"


I am sorry, but I do not understand.  In my second post in this thread, I wrote, "I can see how to use /etc/default/grub to generate grub.cfg files with different defaults."  Your reference to GRUB_DEFAULT above is, as far as I can tell, relevant in this /etc/default/grub context (to which I had already referred myself).  I.e., it affects the behaviour of grub_update when it creates a new grub.cfg file.  It is hardly anything that Windows can use to change the default.  What Windows can do is to copy an already-existing config file with the desired default to grub.cfg.

There is a behaviour of grub2 that I can use to obviate the need I spoke of to force the default in case of a crash to be whatever was last booted.  I would only change to some other default just before an _explicit_ reboot (i.e., no crash).

---

### Post by oldfred on 2010-04-23
I thought that was was "saved" was. It reboots to the saved entry unless you select something else.

---

### Post by DrHow on 2010-04-23
> **oldfred said:**
> I thought that was was "saved" was. It reboots to the saved entry unless you select something else.

Indeed.  However, the mechanism for selecting something else involves interacting with grub during startup.  I want to be able to make that selection in Windows (or Ubuntu) _before_ shutting down.

---

