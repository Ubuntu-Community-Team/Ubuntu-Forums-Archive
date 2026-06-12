---
title: "mount cifs permissions?"
date: 2010-06-28
forum: General Help
---

### Post by LuniTux on 2010-06-28
Hello,

I have a Windows shared folder that I mount on startup of my ubuntu 9.10 machine. The mount works correctly but I can't write to the folder without sudo. I have tried:

```

sudo chmod 777 /mnt/pdfs
sudo chown (myusername) /mnt/pdfs
sudo chgrp (myusername) /mnt/pdfs

```

but still can not write to the folder without sudo. I can mount and write to other linux machines correctly though. What do I have to change for the mount to allow write access? Here is my /etc/fstab mount:

```

//192.168.xxx.xxx/pdfs	/mnt/pdf	cifs	credentials=/.../.smbcredfile	0	0

```

---

### Post by kalistona on 2010-06-28
properties on windows and rules of shared files in windows
i suppose on ubuntu, you could do better, but if a shared file is crypted, windows does not
allow you (sometimes)...question of permission i suppose.

---

### Post by LuniTux on 2010-06-28
Would it be a Windows permission issue or an Ubuntu permissions issue?

---

### Post by LuniTux on 2010-06-28
Would it be a Windows permission issue or an Ubuntu permissions issue?

---

### Post by kalistona on 2010-06-28
you are in dual-boot i suppose or in wubi ?
the first has all the rights.
ubuntu issues ? in command line, you can do powerfull things and that, i do not know this issue.

---

### Post by dino99 on 2010-06-28
install and use mountmanager to deal with partitions and devices rights easily (system admin mountmanager)

ntfsprogs need to be installed too

---

### Post by LuniTux on 2010-06-28
I am using an Ubuntu machine mounting to a W2003 server via network. Sorry if I was unclear.

---

### Post by LuniTux on 2010-06-28
SOLVED!!!

The ch* statements were not working because the folder was already mounted.

folder permissions were:

drwxr-xr-x 2 root root

I unmounted
chmod 777 pdf, chown (me) pdf, chgrp (me) pdf

then ls -l

now folder permissions are:

drwxrwxrwx 2 jose jose

---

