---
title: "NFS mounts in fstab ignored"
date: 2006-06-15
forum: General Help
---

### Post by cjb on 2006-06-15
Hi all.
I'm running the amd64 6.06 kubuntu. My NFS mounts are not becoming available after boot, and I wonder if someone can help me with that.

This is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda9       /tmp            ext3    defaults        0       2
/dev/sda6       /usr            ext3    defaults        0       2
/dev/sda7       /var            ext3    defaults        0       2
/dev/sda8       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
192.168.2.1:/home/shares/music  /mnt/music      nfs     rw      0       0
192.168.2.1:/home/shares/films  /mnt/films      nfs     rw      0       0
192.168.2.1:/home/cjb   /home/cjb       nfs     rw      0       0

```

As you can see, there ae three NFS mounts, including my home directory.

Here's a Konsol session from shortly after booting. The contents of /home/cjb listed first are those from the directory on the local drive. The last directory listing from /home/cjb is the listing for the remote drive.

```

cjb@manny:~$ ls
Desktop  Examples  install_flash_player_7_linux
cjb@manny:~$ sudo mount -a
Password:
mount: 192.168.2.1:/home/shares/films already mounted or /mnt/films busy
mount: 192.168.2.1:/home/cjb already mounted or /home/cjb busy
cjb@manny:~$ ls
Desktop  Examples  install_flash_player_7_linux
cjb@manny:~$ cd ..
cjb@manny:/home$ cd
cjb@manny:~$ ls
altered-fetchmailrc          Muevete.mp3
attempt                      music_directory.txt
bb.pdf                       mypass
ch910505.gif                 mypass~
contact2.html                NatWest download 20040223.csv
contact.html                 Newcastle.zip
contents2index.pl            NEW_CV.doc
copy.tar                     next_albums
crontab~                     next_albums~
database.zip                 Nine Minute Guide to Salsa.ppt
debian.sources               perl_quine
Desktop                      perl_quine~
DocMem1_45.exe               personal_statement.doc
easyjet.txt                  php_cl_test.php
elixena.txt                  php-scripts.tar
filerserver_IP               plsqldev-v5.exe
files.zip                    postponed
firewall                     ppp-login

```

So all the remote mounts can be made to work, it's just that at the moment I have to manually "mount -a" them. I wonder if this is just a performance issue? Where can I go to find the log files?

Thanks for any help,
James

---

### Post by scxtt on 2006-06-15
check this out:

[nfs-common](http://www.ubuntuforums.org/showpost.php?p=1140489&postcount=5)

---

### Post by cjb on 2006-06-15
[QUOTE=scxtt]check this out:

[nfs-common](http://www.ubuntuforums.org/showpost.php?p=1140489&postcount=5)[/QUOTE]

Works a treat now, thanks :)

---

