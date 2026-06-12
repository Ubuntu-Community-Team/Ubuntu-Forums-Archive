---
title: "Viewing files from Win 7 on Ubuntu OS"
date: 2012-04-17
forum: General Help
---

### Post by RClaudio on 2012-04-17
I'm completely new to ubuntu, but I recently installed it beside my Windows 7 OS on my laptop. However, whenever I boot up using the ubuntu OS, I am unable to view or access the files or programs installed under the Windows7 OS. Am I able to view and access the files and programs already insalled on my computer, and if so, how do I do it?

---

### Post by oboedad55 on 2012-04-17
> **RClaudio said:**
> I'm completely new to ubuntu, but I recently installed it beside my Windows 7 OS on my laptop. However, whenever I boot up using the ubuntu OS, I am unable to view or access the files or programs installed under the Windows7 OS. Am I able to view and access the files and programs already insalled on my computer, and if so, how do I do it?

Have you installed ntfs-3g? Do a search in Synaptic or Software Center for "ntfs". You should be able to view files that way, but as far as running Windows programs I highly don't recommend trying to run the programs through Ubuntu. You can run some Windows programs through Wine, but if you're dual-booting I think it's far better to run them natively. In any case, you'd have to reinstall them in Ubuntu with Wine anyway, and some things work and some don't. [http://www.winehq.org/](http://www.winehq.org/)

---

### Post by RClaudio on 2012-04-17
Thank you for your help so far. I did as you said, I searched for ntfs in the ubuntu software center, and installed the ntfs-3g app. then when I clicked on it, it prompts me for an authentication password. I enter the password, but nothing happens. I still can't see my files. Any suggestions?

---

### Post by RClaudio on 2012-04-17
I'm using the newest version of ubuntu, the 11.10 version. Maybe the app isnt set up for this newest version?

---

### Post by oboedad55 on 2012-04-17
> **RClaudio said:**
> Thank you for your help so far. I did as you said, I searched for ntfs in the ubuntu software center, and installed the ntfs-3g app. then when I clicked on it, it prompts me for an authentication password. I enter the password, but nothing happens. I still can't see my files. Any suggestions?

Did it install? You can also use Synaptic and install it that way, doesn't matter. In any case, look in either program and see if it's installed. If not, then install it.

---

### Post by efflandt on 2012-04-18
A normal 11.10 installation includes **ntfsprogs** by default which should include anything that Linux is capable of doing with ntfs file systems.  With that I have no trouble accessing files in Win7 ntfs partitions.  Mounting them is as simple as clicking on the partition in the file manager.

If you install **ntfs-3g** it removes **ntfsprogs** because they conflict.  But I do not know what the differences are between those two packages.

Note that if Windows uses proprietary logical volumes instead of normal msdos partitions, Linux cannot access the Windows logical volumes.  You might want to post the output of **sudo fdisk -l** (small L) and wrap that in code tags by highlighting that text and clicking **#** in the message window.

This assumes that you are the administrative user that you configured when installing Ubuntu.  If you are running as a different user you might not have proper permissions to mount other drives automatically with the file manager.

---

### Post by cheat117 on 2012-04-18
Ubuntu will not run programs that are installed in Windows inside ubuntu without wine. (that may be cryptic but basically no running windows installed programs from ubuntu) Usually Ubuntu plays nice enough with windows to mount into /media or /mnt on launch if it is not then I would ask how to find out if it is mounted. Good Luck!

---

### Post by HiImTye on 2012-04-18
hit ctrl+alt+t and type this into a terminal, to make sure that you have the ntfs file system management package
```
sudo apt-get install ntfs-3g
```then open your file manager and click on it on the left hand side, it should look something like this:
[ATTACH]216216[/ATTACH]

I would not recommend running windows programs installed on an ntfs file system in Ubuntu using any method, however, simple file system navigation/copying from the file system should be relatively safe

---

### Post by mastablasta on 2012-04-18
they should mount automaticly in Nautilus file manager, however the disks/partitions are often labeled differently than in windows. usually with a disk label or it can also say for example if partition C:\ is 50 GB big -->  "50 GB file system" instead of C:\

---

### Post by mastablasta on 2012-04-18
> **HiImTye said:**
> hit ctrl+alt+t and type this into a terminal
 
why walk when you can ride?
 
why type when you can copy&paste the command into terminal.

---

### Post by HiImTye on 2012-04-18
> **mastablasta said:**
> copy&paste the command into terminal.
or that

---

### Post by Mark Phelps on 2012-04-18
> **RClaudio said:**
> Am I able to view and access the files and programs already insalled on my computer, and if so, how do I do it?

View and access the files -- YES.  Although, I strongly recommend that you do not CHANGE any of the files inside Win7 OS partition from Ubuntu.  Doing so risks filesystem corruption, which can then render Win7 unbootable.

Access programs -- NO.  To run MS Windows programs in Wine, you have to reinstall them, and often, they don't work well even after that.  IF you need to use your Windows apps on a regular basis, it's best to stick with using Win7 for that.

---

