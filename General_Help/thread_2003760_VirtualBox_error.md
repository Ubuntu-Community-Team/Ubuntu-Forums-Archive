---
title: "VirtualBox error"
date: 2012-06-14
forum: General Help
---

### Post by qwertyjjj on 2012-06-14
Trying to change some settings in the VB screen but I get this error:
Failed to save the settings of the virtual machine Poker to /home/j-media-centre/VirtualBox VMs/Poker/Poker.vbox.

Runtime error opening '/home/j-media-centre/VirtualBox VMs/Poker/Poker.vbox-tmp' for reading: -250 (Unresolved (unknown) device i/o error.).

/home/vbox/vbox-4.1.16/src/VBox/Main/src-server/MachineImpl.cpp[8702] (nsresult Machine::saveSettings(bool*, int)).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: VirtualBox
Interface: IVirtualBox {c28be65f-1a8f-43b4-81f1-eb60cb516e66}
Callee: IMachine {5eaa9319-62fc-4b0a-843c-0cb1940f8a91}

---

### Post by hwttdz on 2012-06-14
Presumably it's having difficulty finding the file which contains the virtual drive, what are the contents of "/home/j-media-centre/VirtualBox VMs/Poker/"?

---

### Post by qwertyjjj on 2012-06-16
> **hwttdz said:**
> Presumably it's having difficulty finding the file which contains the virtual drive, what are the contents of "/home/j-media-centre/VirtualBox VMs/Poker/"?

The actual file works as I can run the guest OS systems correctly...I just can't make changes to the settings.

```

j-media-centre@jmediacentre-A880G:~$ cd /home/j-media-centre/VirtualBox\ VMs/Poker
j-media-centre@jmediacentre-A880G:~/VirtualBox VMs/Poker$ ls =l
ls: cannot access =l: No such file or directory
j-media-centre@jmediacentre-A880G:~/VirtualBox VMs/Poker$ ls -l
total 13129828
drwx------ 2 j-media-centre j-media-centre        4096 2012-06-14 21:27 Logs
-rw------- 1 j-media-centre j-media-centre       11070 2012-05-30 14:06 Poker.vbox
-rw------- 1 j-media-centre j-media-centre       11070 2012-05-30 14:06 Poker.vbox-prev
-rw------- 1 j-media-centre j-media-centre           0 2012-06-13 07:52 Poker.vbox-tmp
-rw------- 1 j-media-centre j-media-centre 13444886528 2012-06-16 09:35 Windows XP.vdi


```

---

### Post by qwertyjjj on 2012-06-16
I recreated the selection by Adding a New guest and selsecting the old hard drive...seemed to work.

---

