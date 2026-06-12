---
title: "Samba Issues"
date: 2006-04-01
forum: General Help
---

### Post by WillisBueller on 2006-04-01
Hello, I'm curious how I can mount a windows root share directory

ie.
*mount -t smbfs -o username='whatevs',password='' /computerIP/ /media/mntpoint*

**instead of **
[I]
mount -t smbfs -o username='whatevs',password='' /computerIP/directory /media/mntpoin[/I]

I don't want to have the mount the specific sub directories, and samba seems to force me to do it. Any ideas?

Thanks in advance,
Willis

---

### Post by binarysleeper on 2006-04-01
*\\computername* is not a shared resource
*\\computername\sharedresourcename* is a shared resource and can be mounted  using the smbfs filesystem type providing it is an SMB file share.
As far as I'm aware you can't mount  a computer name as an SMB filesystem, as it is not a shared SMB resource per se. 
I hope this makes sense.

Caveat: I'm saying this from a Windows technical perspective. there may be a SAMBA tool that will do this, in fact something like LISA would do.

HTH

Let me know if I can clarify any of this.

---

### Post by WillisBueller on 2006-04-01
Gnome is able to mount a windows share just by an IP and displays all shared directories. I'm looking to be able to do that from the command line

---

### Post by binarysleeper on 2006-04-01
Sorry for asking, as I'm a KDE user, does gnome actually mount them to the file system? or does it just display them in a browser?

---

### Post by WillisBueller on 2006-04-01
it doesn't seem to actually mount them in the filesystem (that'd be awesome tho). I think it uses GnomeVFS or something

---

### Post by binarysleeper on 2006-04-01
The only things I can suggest are:
1.a script that enumerates the shares then mounts them, or
2. Automating Gnome via the command line to launch the brower for you. I think that can be done with something called DBUS (or DCOP for KDE, not sure if gnome supports it)

HTH

---

### Post by WillisBueller on 2006-04-02
Yeh I'm thinking a scripting method is the way to go.
Thanks for your help, I appreciate your time.

Willis

---

