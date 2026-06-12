---
title: "no kde programs running"
date: 2006-02-28
forum: General Help
---

### Post by NCLife on 2006-02-28
im using gnome righ now, but i originaly downloaded and installed kubuntu so i have programs of both kde and gnome.
 Now since a few days im unable to open any kde programs, unless i do it with sudo in a terminal. 
 This is the error message im getting when i try to open k3b:
 
  kdeinit: Aborting. bind() failed: : Permission denied
  Could not bind to socket '/home/sinclair/.kde/socket-201/kdeinit__0'
  ERROR: KUniqueApplication: Can't setup DCOP communication.

 Any idea what is happening? could it be relationated with /etc/mtab or /etc/fstab? because i changed some lines there recently.

---

### Post by NCLife on 2006-02-28
and this is what is displayed when i run k3b with sudo.

Link points to "/tmp/kde-root"
kbuildsycoca running...
Error: "/var/tmp/kdecache-sinclair" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-sinclair" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
sinclair@201:~$ k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
Error: "/var/tmp/kdecache-sinclair" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-sinclair" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"

it does open but thats the only way, by sudo. And so it happens with almost all other kde programs that i want to run on gnome.

---

