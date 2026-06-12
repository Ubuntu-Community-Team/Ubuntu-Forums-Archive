---
title: "Swap on, mountall problems; mozilla problem"
date: 2010-11-10
forum: General Help
---

### Post by j22 on 2010-11-10
Problem-cannot mount 2 other samba computers on my ubuntu 10.04 via 'sudo mountall'.  Additionally I now get Firefox/Thunderbird error messages as listed below.  Had no problems with ubuntu UNTIL I attempted install of VirtualBox running WinXP client in my Ubuntu host.  VirtualBox seemed to install ok but upon startup of WinXP client all I got was a black screen.  To close it I had to do "Power Off" which VBox manual says is like a hard power off and is to be avoided.  So I guess it's like I crashed XP within Ubuntu.

Now - ubuntu boots ok except will not auto mount other samba connected computers.  Manually running 'sudo mountall' in terminal gives --

                     p { margin-bottom: 0.02in; page-break-before: auto; }p.cjk { font-size: 10pt; }  *swapon: /dev/disk/by-uuid/24c4c591-47ec-44f1-ac52-c0e2f5850c18: swapon failed: Device or resource busy *
 *mountall: swapon /dev/disk/by-uuid/24c4c591-47ec-44f1-ac52-c0e2f5850c18 [2235] terminated with status 255 *
 *mountall: Problem activating swap: /dev/disk/by-uuid/24c4c591-47ec-44f1-ac52-c0e2f5850c18 *
 *retrying with upper case share name *
 *mount error(6): No such device or address *
 *Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) *
 *mountall: mount /media/samba_share [2239] terminated with status 32*


Additionally I now get these warning messages when Firefox and Thunderbird start.  (They do start and seem to work fine.)--


*Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)*

                     p { margin-bottom: 0.02in; page-break-before: auto; }p.cjk { font-size: 10pt; }  What I've tried-
1) fstab UUID matches error UUID above and matches UUID from blkid command:

fstab =#Entry for /dev/sdc2 : 
 UUID=24c4c591-47ec-44f1-ac52-c0e2f5850c18    none    swap    sw    0    0 
                       p { margin-bottom: 0.02in; page-break-before: auto; }p.cjk { font-size: 10pt; }  blkid = /dev/sdc2: UUID="24c4c591-47ec-44f1-ac52-c0e2f5850c18" TYPE="swap"  
 
2) reinstalled mountall from synaptic pkg manager;  did not try to remove mountall and reinstall.  To remove, removes LOTS of other packages from system - not brave enough to do that (yet).

3)                      Ran fsck on swap partition as below.  Swap not found. (that confuses me.)p { margin-bottom: 0.02in; page-break-before: auto; }p.cjk { font-size: 10pt; }  john@johndesk:~$ fsck /dev/sdc2 
 fsck from util-linux-ng 2.17.2 
 fsck: fsck.swap: not found 
 fsck: Error 2 while executing fsck.swap for /dev/sdc2 



                      p { margin-bottom: 0.02in; page-break-before: auto; }p.cjk { font-size: 10pt; }  4) deleted all the files in ~/.dbus/session-bus. Ubuntu just rebuilds the same file back.


 I've looked at lots of posts on mountall problems, stale NFS locks, etc.  Very confusing.


Can anyone please direct me to a solution?
Thanks much, j22

---

### Post by dino99 on 2010-11-10
about partitions:

check that the uuid into /etc/fstab are the good ones ( copy/paste if different)

sudo blkid

sudo gedit /etc/fstab

---

### Post by j22 on 2010-11-10
Dino, the UUID as listed by fstab and by blkid are identical.  They are listed in my original post (some of the forum message formating info is mixed in there - don't know how I managed that.)

---

### Post by j22 on 2010-11-12
Anyone out there to help?

---

