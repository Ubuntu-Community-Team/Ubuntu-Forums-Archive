---
title: "Help with finding files"
date: 2009-10-21
forum: General Help
---

### Post by Rancidgore on 2009-10-21
Hey Everyone, I'm very new to Ubuntu, and I'm only using it to access files on a computer that crashed.  I understand that a reoccuring problem is people having issues mounting their hard drive.  When I open the file browser, under "computer" it does not show my hard drive.  Does any one know why this is and how I can fix it?  Any and all help is much appreciated.  Thank You

Rancidgore

---

### Post by martrn on 2009-10-21
If you are in natalus and you click on the computer icon it should give you a view of looking at your hard drive from the perspective of media devices, such as hard drives ect.

Everything on an ubuntu or any gnu/linux distribution is that there is only one file system, per computer and when that computer is booted and the root file systems starts at /

If you click on home or your home directory and move 'up' in the directory structure twice you should find a directory called media.  If you enter the directory called media you should find a list of your media devices, which should be listed there.

hda1 is your first partition on your first hard drive.
hda2 is your second partition on your first hard drive.
hab1 is your first partition on your second hard drive.
hab2 is your second partition on your second hard drive.
hdc1 is your first partition on your third hard drive.

etc...ect...ect...

---

### Post by P4man on 2009-10-21
I assume you are booting off an ubuntu livecd to try and recover files from a windows install?

If the windows ntfs partition wasnt cleanly shut down, ubuntu will not mount the partition to avoid (further) data loss. You can force this, but its generally not a good idea. Ubuntu does support ntfs, but its not as good managing a broken windows filesystem as windows, so the recommended approach is to run windows checkdisk on it from windows.

If thats not possible, you can install testdisk from the synaptic package manager (in system > administration. then open a terminal and type

```
sudo photorec
```

to try and recover files from the ntfs partition without mounting it.

---

### Post by martrn on 2009-10-21
You can mount an ntfs file system if it is not mounted and your have a fully setup ubuntu installation on a pendrive for example or other disk.  Just type > sudo apt-get install pysdm and isnstall pysdm.

If you only have a live cd and need to mount an ntfs drive you will need to use the command line to mount a your ntfs drive.
See : [http://ubuntu.swerdna.org/ubuntfs.html]("http://ubuntu.swerdna.org/ubuntfs.html")

---

### Post by Rancidgore on 2009-10-21
I tryed installing pysdm and it said

root@ubuntu:~# sudo apt-get install pysdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pysdm

and when i tryed to check the partitioned discs, it doesnt show up.  My hard drives aren't even being recognized.

---

### Post by martrn on 2009-10-22
It might be a hardware problem ?

Try :-
```
sudo gparted
``` to see if gparted recognises the hard drive, if it doesn't even recognise the hard drive, then its a hardware fault. Quit gparted and don't make any changes.

If it does recognise the hard-drive then try testdisk recovery software -
[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") - to recover what data you can and then re-install your operating system.

If you wish to install ubuntu as a new operating system on your hard drive or at a later stage, say when you have a new hard-disk then visit [http://www.ubuntu.com/GetUbuntu/download]("http://www.ubuntu.com/GetUbuntu/download") and download a cd image or a thumb drive img file and burn/copy that to a cd or thumbdrive.  You can also request a free cd by clicking on request a free cd on the left hand menu bar, which will be sent out by ship-it.

Best of luck.

---

