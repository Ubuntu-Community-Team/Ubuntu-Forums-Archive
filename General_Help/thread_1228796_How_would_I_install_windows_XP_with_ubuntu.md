---
title: "How would I install windows XP with ubuntu?"
date: 2009-08-01
forum: General Help
---

### Post by XxPleaseHelpxX on 2009-08-01
Hi, I would like to install Windows XP with ubuntu and create a dual boot.  But how would I do this?  Please help soon...:confused:

---

### Post by W4l0ck on 2009-08-01
boot from a windows cd

---

### Post by cmost on 2009-08-01
You will need to start with a blank hard disk and always (ALWAYS) install Windows first.  Windows assumes its the only operating system in the world and therefore won't detect, let alone add, other operating systems to its boot loader.  So, install Windows onto a partition.  This can be accomplished by installing Windows normally but choosing not to utilize the entire hard disk.  Use what you need/want and leave the rest for Ubuntu.  When Windows is installed, then insert your Ubuntu CD and go through its installation.  Ubuntu will detect your Windows installation and add an option to boot Windows to its boot loader.  Obviously these are the simple instructions.  You should really try Googling for a full, in-depth tutorial.  There are literally thousands; many on these forums.

---

### Post by W4l0ck on 2009-08-01
Who would want to use windows anyways?

---

### Post by razorboy5 on 2009-08-01
> **cmost said:**
> You will need to start with a blank hard disk and always (ALWAYS) install Windows first. ...

i agree it's more difficult to install Windows on top of another OS however it is doable

if u wanna keep ur Linux then install XP to dual boot try this link
[http://apcmag.com/how_to_dual_boot_l...lled_first.htm]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm")

> **W4l0ck said:**
> Who would want to use windows anyways?

alot of gamers have no choice but to dual boot windows to play their favorites :P

---

### Post by Post Monkeh on 2009-08-01
i installed xp onto a laptop already housing an existing ubuntu installation less than a month ago, and it took me all of 5 minutes to get booted back into ubuntu.  it just adds another few steps to the process, but it isn't very difficult.

if you don't have anything installed at present, then yes, it's better to install windows first, but by no means is it essential.

---

### Post by Bucky Ball on 2009-08-01
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

Everything you're going to need. An excellent resource for all things dual-boot and beyond.

---

### Post by Post Monkeh on 2009-08-01
[http://ubuntuforums.org/showthread.php?t=1210455](http://ubuntuforums.org/showthread.php?t=1210455)

a thread explaining what you need to do if you DO already have ubuntu installed and want to add xp.

---

### Post by wtp00 on 2009-08-01
First you need to resize your main ubuntu partition and make an NTFS formatted partition for however much disk space you want Windows to have. Install Windows and make sure you choose the right partition for Windows to format. Then grab an ubuntu alteranate CD and,

1. Boot your computer up with Ubuntu CD
2. Go through all the process until you reach "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
swap

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

---

