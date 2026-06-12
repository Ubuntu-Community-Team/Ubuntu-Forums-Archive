---
title: "I killed my Ubuntu...."
date: 2011-10-18
forum: General Help
---

### Post by Ken.P on 2011-10-18
I was having warnings that my hard drive was on it's way out, so I used Acronis to clone my complete drive onto a new hard drive.
I then swapped the drives.
Now when I boot up, Grub still works, so does Windoze, but not Ubuntu.

So I tried to install the latest version of Ubuntu from USB, but during the preparations for install it keeps telling me that it has found no operating system on my drive.
I guess that if I install Ubuntu it will overwrite the Windoze XP... :(

Any suggestions to get a version of Ubuntu back on my laptop would be extremely welcome!

---

### Post by oldfred on 2011-10-18
Welcome to the forum.

Do you still have both drives plugged in?

Post this and a screenshot from gparted.
```

sudo fdisk -lu
```

---

### Post by Ken.P on 2011-10-18
Thanks oldfred.

All I do is use Ubuntu, so anything more technical than a complete beginner will need serious guidance!

When I try to boot to Linux I get the following screen.

--------------------------------------------------------------

Gave up  waiting for root device. Common problems:
Boot args (cat/proc/cmdline)
Check rootdelay= (did the system wait long enough?)
Check root= (did the system wait for the right device?)
Missing modules (cat/proc/modules; lss/dev)

ALERT! /dev/disk/by-uuid/7d7c95f4-1d60-47cf-8371-56c9c12df794 does not exist.

Dropping to a shell!

BusyBox v1.13.3 (ubuntu 1:1.13.3-1ubuntu11) buitl-in shell (ash)
Enter "help" for a list of commands.

----------------------------------------------------------

I entered "sudo fdisk -lu" and it said "Sudo: Not found"

---

### Post by Ken.P on 2011-10-18
I should have said, only one drive connected now, but tried the old drive and it doesn't want to work at all now.
At least I managed to save all the important stuff before I started!

---

### Post by oldfred on 2011-10-18
Linux is case sensitive. So not Sudo but sudo.

Run this from liveCD:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Or download this into liveCD or download its liveCD as it runs script and may be able to make some repairs:

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Ken.P on 2011-10-19
I booted from the USB, then ran Yanni's boot repair.

Looks like a 100% success! :D

Thanks for the help oldfred.

---

