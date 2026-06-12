---
title: "How to mount a Samba share"
date: 2010-12-11
forum: General Help
---

### Post by Daniel1256 on 2010-12-11
I need to mount two Samba shares from my Ubuntu Server to my Desktop they are:

[shared]
path = /media/share
read only = no
guest ok = yes

[www]
path = /var/www
read only = no

I made two directories in my home folder on the desktop called share and www how do I mount these now? I have to use the terminal btw.

If I run the command: smbclient -L //192.168.10.101 which is the IP of my server it works.

---

### Post by pfnorris on 2010-12-11
Daniel

You have two ways you can approach this - a manual method if you only need to do it once or occasionally; or an automatic method if you want them mounted at boot up.

Manual method just issue the command:

sudo mount -t cifs -o username=<username>,password=<password> //192.168.10.101/shared /~/shared

Use the same command for the www share just change the share name. Cifs tells mount to use the  appropriate filesystem protocol. Use your own username and password.

If you want to have the shares mounted at boot time you need to put an entry for each one in /etc/fstab along the lines of:

//192.168.10.101/shared   /home/<username>/shared   cifs   username=<username>,password=<password>,uid=<UID>,gid=<GID>users   0 0

This is all one line. You would need to enter your own username, password, uid number and group id number in the appropriate places. If you do not want to have your personal credentials stored in plain text in a file like fstab, you can create a hidden file in your home directory called .creds, and store them there one entry per line thus:

username=<username>
password=<password>

This has the advantage that it is only readable by you and it is hidden from view by default (leading dot).

You would then change the fstab entry as follows:

//192.168.10.101/shared   /home/<username>/shared   cifs  creds=/home/<username>/.creds,uid=<UID>,gid=<GID>users    0 0

You can then run the command 'sudo mount -a' to mount the shares. In future they will be mounted automatically at boot time.

---

