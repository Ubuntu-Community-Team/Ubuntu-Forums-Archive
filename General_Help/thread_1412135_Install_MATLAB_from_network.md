---
title: "Install MATLAB from network"
date: 2010-02-20
forum: General Help
---

### Post by honeybadger on 2010-02-20
Hi,

I installed ubuntu 9.10 last week (so far very enjoyable), but am having difficulty installing MATLAB. My school provides licenses and instructions for how to install from the network, but I am failing at getting the install to work. Specifically: I attempt this code:

# mount -t smbfs -o username=SCHOOL\\<netid> //files.school.edu/Licensed /mnt/licensed.dist

And get this error:

mount: wrong fs type, bad option, bad superblock on //files.school.edu/Licensed,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Does anyone know how I can make this go?

Thanks,
Jeremy

---

### Post by honeybadger on 2010-02-21
bump

---

### Post by mali2297 on 2010-02-21
I do not know, but my guess is that you first need to install the package [smbfs]("http://packages.ubuntu.com/karmic/smbfs"). 

Also, you might need to run the command as root by adding *sudo* in front of it.

---

### Post by gfuggs on 2010-02-21
Make sure you've created the directory that you're trying to mount it in.  Also try including your password:

# mkdir /mnt/something

# mount -t smbfs -o username=netid,password=password //files.school.edu/Licensed /mnt/something

---

### Post by honeybadger on 2010-02-22
Thanks for the help! It turns out I needed to install smbfs.

---

