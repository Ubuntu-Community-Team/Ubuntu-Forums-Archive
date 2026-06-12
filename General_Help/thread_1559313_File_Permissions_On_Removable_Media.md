---
title: "File Permissions On Removable Media"
date: 2010-08-23
forum: General Help
---

### Post by jim_deadlock on 2010-08-23
When I copy files to any removable media they adopt full permissions like this:

-rwxrwxrwx

... which is fine, but it becomes a pain when I copy them back to the main filesystem and they maintain these properties. Is there a way to set the "default" permissions on the main filesystem to something like -rw-rw-r--

---

### Post by anirudhtomer on 2010-08-23
on my system the permissions on the USB DISK for a file xyz are - rwxrwxrwx

when I copy they become 

rwx-wx-wx 

because I have set the umask as 044 on my system.

since u want the file permissions to change as -rw-rw-r-- when u copy 
type this on the shell
$ umask 113

& then copy the file...this will surely help u out

---

### Post by jim_deadlock on 2010-08-23
Ah that does the trick, thanks.

Is there any way to make nautilus respect the umask settings?

---

