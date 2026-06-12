---
title: "What should I backup to protect my system?"
date: 2011-05-27
forum: General Help
---

### Post by Syris on 2011-05-27
I am relatively new to Linux, What files/Folders should be backed up and what ones are not necessary?
This is my 2nd install of 11.04 because I screwed the 1st one, so Im not  sure what to backup to prevent having to reinstall if I screw up again.

BTW I am using Deja dub backup

---

### Post by mike555 on 2011-05-27
Basically backup everything that is important to you and didn't come with the install ......... but most will say backup your "Home" folder to an other partition or external drive or cloud .

---

### Post by LordNeo on 2011-05-27
For an basic backup just back up your /home folder and the list of your installed programs (i don't remember the command to get it, but you will find it easily on google)
If posible, while installing create a separate home partition and you are set.

---

### Post by Syris on 2011-05-27
Thx for the advice

Found the command too for a list of installed apps and how to restore in case of disaster

"dpkg --get-selections > installed-software" + "dpkg --set-selections < installed-software"

---

### Post by linuxinstalledfromhdd on 2011-05-27
You should make a clone live disc of your system so you can reinstall it after another crash (if a crash occurs) with Remastersys.  It's about half the way down this step-by-step guide:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by ShakeyJake on 2011-05-27
Depends. If all you want to do is make sure you have your data if and when you screw up the install then having your /home in a separate partition or disk will accomplish that. 

It won't however be a 'proper' back up. There won't be any facility to restore a file is you delete it, it gets corrupted, or your disk fails. All of these things require proper, regular backups to a separate drive or ideally a different machine altogether.

I backup my /home folder as well as as few system config files such as /etc/fstab just to save me having to redo them next time. Backintime every day to a mirror drive in my pc and when I remember to an external usb hard drive.

---

### Post by linuxinstalledfromhdd on 2011-05-27
I do nightly backups with Remastersys to a disc. I save all my work to a LAN file server (or you could use Dropbox or whatever you prefer) and even a external USB drive is handy too.  I love remastersys for the fact that backups are idiot proof. I can reinstall my system in 10 minutes from a live USB stick backup made with Remastersys.. Nothing else is this quick and painless that I have researched. :)

---

### Post by Syris on 2011-05-27
mmm i was looking for more of an imaging software like Acronis that i use for my MS PCs. But didn't think there was one for Linux so I was going to use Deja dub backup. So does Remastersys basically do images? I'll have to check that out.

---

### Post by linuxinstalledfromhdd on 2011-05-27
Well, what I was looking for originally wasn't a backup solution. I just wanted to create a live bootable custom disto of Ubuntu to reinstall on other (like architecture) systems. Eventually I came to realize the value in it for nightly backups of my configuration settings, bookmarks, passwords, and everything else.  That way I can roll it back from the rematersys dist iso created if something happened. Or I can install a clone of my system to another computer in a hurry.  Also another thing I use is a NAS box hooked to the router so I can do fresh installations of Ubuntu over the local LAN network.  And it's lightning quick too and you can use install scripts which save so much time.

---

### Post by WorMzy on 2011-05-27
Backup anything important to you that isn't easily replaceable. e.g. Documents, databases, websites, pictures. I don't see the point of making a backup of your system files + settings, unless your machine is critical to your business or something. If you have a LiveCD/USB handy, you can reinstall Ubuntu and install + configure all the apps you use in an hour or two (internet connection permitting). If that hour or two will cost you money, then by all means use remastersys to create a restore disk for your installation.

---

### Post by katykat on 2011-05-27
Backup /home, /etc, /boot, and to be safe - /bin and /lib

(I've had an accidental install of busybox screw up /bin!).

I currently back up to another linux drive, but would like to find a reliable utility to keep file permissions on an NTFS external drive (grsync not). 

/etc is particularly important if something screws up  the configuration. 
/boot if something messes with grub. 

Ideally, everything should be backed up, but that can be rather cumbersome. 
rsync is good for doing that, but those incremental files wind up taking huge amounts of space....

---

### Post by wildmanne39 on 2011-05-27
Hi, I used simple backup configuration to back up my system and it asked if I wanted to back up the everything, but I think that my home folder would be enough is that right? Also it asked if I wanted to make it a compressed file and I said yes to save space  was that the right choice? Thanks in advance for all advice, I appreciate it.

---

