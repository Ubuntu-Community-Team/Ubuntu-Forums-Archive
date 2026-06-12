---
title: "Backup &amp; serial port"
date: 2011-10-26
forum: General Help
---

### Post by 10.04 Newbie on 2011-10-26
Hi all, I'm messing around with 10.04, but Ubuntu still is not nearly user-friendly enough in my opinion.

I am able to use some windows programs with 'Wine", that's cool.
But, I can find no program or simple method to make a backup image or clone/restore a partition or complete drive.

Also, I need a functioning serial port. With XP, it was no problem using a usb-RS232 adapter....not so on Linux. Anyone know if an rs232 cardbus adapter is worth a try? I [found this one]("http://www.ebay.com/itm/RS232-DB9-Serial-Port-PC-Card-PCMCIA-CardBus-Adapter-/180722385227?pt=LH_DefaultDomain_0&hash=item2a13e4c14b") that says it will work with Linux.

appreciate any help.

---

### Post by quadproc on 2011-10-26
> **10.04 Newbie said:**
> 
But, I can find no program or simple method to make a backup image or clone/restore a partition or complete drive.

I am not sure exactly what you would like to do, but I have been using sbackup on 10.04 for all of my routine backups and have had good luck with it.  Unfortunately, the 10.10 version of Ubuntu broke the sbackup program - it won't allow me to backup to a drive of my choice any more.  So I stick with 10.04 for backups.

Perhaps you might be able to use Clonezilla for entire disk copies.  This is a program that duplicates everything from one disk onto another.  Note that the disk's UUID will also be copied so you may need to manually change that after cloning.

It is also possible to use dd to copy an entire disk.  However, if you make a mistake in the arguments to dd you can destroy everything on the disk so I do not recommend using dd unless you are comfortable with it.

quadproc

---

### Post by pretty_whistle on 2011-10-26
+1
Clonezilla.

I use it.

---

### Post by oldtimer7777 on 2011-10-26
It is called Relinux.  Clonezilla is way way too overkill for what you want to do. That is like recommending to someone Norton Ghost when they just want to backup their My Documents folder and settings. Relinux will create a resque disk/live stick of Ubuntu to reinstall from in the future..  You can even share it with other people or make a private copy of everything on your system to boot from live on another system. Clonezilla is just cloning from one drive to another drive. 

> **10.04 Newbie said:**
> Hi all, I'm messing around with 10.04, but Ubuntu still is not nearly user-friendly enough in my opinion.

I am able to use some windows programs with 'Wine", that's cool.
But, I can find no program or simple method to make a backup image or clone/restore a partition or complete drive.

Also, I need a functioning serial port. With XP, it was no problem using a usb-RS232 adapter....not so on Linux. Anyone know if an rs232 cardbus adapter is worth a try? I [found this one]("http://www.ebay.com/itm/RS232-DB9-Serial-Port-PC-Card-PCMCIA-CardBus-Adapter-/180722385227?pt=LH_DefaultDomain_0&hash=item2a13e4c14b") that says it will work with Linux.

appreciate any help.

---

### Post by 10.04 Newbie on 2011-10-28
much thanks for all the replies. I tried Clonezilla....it will work on a PC,
but for some reason, this old laptop will not boot with the live CD.
I found [Relinux here]("http://sourceforge.net/projects/re-linux/files/"), but could you pls tell me how to install it from the tar file?
thanks

---

### Post by dargaud on 2011-10-28
About the serial port, see if you have this when your USB adapter is connected:
```
$ ls -alF /dev/ttyUSB*
crw-rw---- 1 root dialout 188, 0 2011-10-18 15:06 /dev/ttyUSB0
```
If so you can use minicom to connect to your device. Be warned that the syntax of minicom is weird. Run it first just for configuration:
```
sudo minicom -s
```
And change all the settings: Ctrl-A, Ctrl-Z, Serial port setup [O], Then serial device (/dev/ttyUSB0), Bps/par/bits, No flow controls. Save setup as dfl, exit. 

Change the permission on the /etc/minicom/minirc.dfl file so a normal user can change it. Also add your user to the uucp, adm and dialout groups (not sure which one is actually necessary nowadays).

Then simply run minicom as a normal user.

---

### Post by 10.04 Newbie on 2011-10-29
thanks for your reply, I [followed this]("http://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html"), but to no avail.
minicom was not installed, followed the command to install it.


I am not clear on changing all the settings.  /dev/ttyUSB0 done, set no flow control.
What do I set the Bps/par/bits to? now it's 115200 8N1
Ctrl-A, Ctrl-Z ?? where do I use this?

Remember, I'm a newb here, do not want to screw up my system, and have no idea how to: "Change the permission on the /etc/minicom/minirc.dfl file so a normal  user can change it. Also add your user to the uucp, adm and dialout  groups (not sure which one is actually necessary nowadays)."

ok, finally got it to save as dfl.   I get 'permission denied' when trying to Change the permission on the /etc/minicom/minirc.dfl

---

### Post by 10.04 Newbie on 2011-10-30
Can anyone explain how to install this Relinux?  thanks

---

### Post by 10.04 Newbie on 2011-11-01
Nobody? After 2 days? gee, how encouraging.:confused:

---

