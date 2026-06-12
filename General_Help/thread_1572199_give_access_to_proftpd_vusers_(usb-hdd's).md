---
title: "give access to proftpd vusers (usb-hdd's)"
date: 2010-09-10
forum: General Help
---

### Post by PhilAd on 2010-09-10
hey,

i am using proftpd-mod-sql on ubuntu 10.04lts and i am trying to give the ftp users access to my external usb hdd's because the internal drive is too small.
I am using vusers in a sql db. They are associated to the ftpuser and ftpgroup. My drives are mounted to /media/... and belong to my user and group. The rights are set to 0700. So my ftp users have no access to it and i cannot change it. I could change the vusers uid/guid to my username but i think, that is not a good solution.
I would like to have access to the usb drives with the ftp users and with my ordinary username (for xbmc and samba access). Is there any solution for that? 


greets

PhilAd

---

### Post by ubulal on 2010-09-10
I'm assuming that all users that login by FTP have the rights of the user ftpuser and the group ftpgroup on your local system?  Then just change the group of your external disks to ftpgroup and give it the desired rights.

```

chgrp -R ftpgroup /media/usbdisk
chmod -R g+rw /media/usbdisk

```

Change "g+rw" to "g+r" for read-only access.

---

### Post by ubulal on 2010-09-10
Oh, and add yourself to the group ftpgroup to be able to access the files uploaded by ftp, as they'll be owned by ftpuser.

---

### Post by PhilAd on 2010-09-10
hey,

thanks for your quick answer ... i have already tried st like that by using sudo chmod 0706 as an example, but he is not changing it. there is no message so that you think that he has changed it, but when u do ls -al it is still 0700 and my group. Yes the virtual ftp users belong to the ftpuser and the ftpgroup.

---

### Post by ubulal on 2010-09-10
The disks aren't NTFS formatted, are they? :)

---

### Post by PhilAd on 2010-09-10
They are ntfs formatted xD
No way with ntfs? Do i have to format them with ext4?

---

### Post by ubulal on 2010-09-10
> **PhilAd said:**
> They are ntfs formatted xD
No way with ntfs?
There are mount time options to set the user, group and permissions of *all* files on the partition. But it's impossible to set other values for individual files 'n folders.

> Do i have to format them with ext4?

I would strongly recommend so.  If you're not going to plug them into a Windows box directly you'll lose nothing, but gain a real Unix file system :)

---

### Post by PhilAd on 2010-09-10
I dont think so, after changing the filesystem i will be able to modify the rights with chgrp/chmod, right? 
I will try it tomorrow. Thanks for your help so far :)

Greets

PhilAd

---

### Post by ubulal on 2010-09-10
> **PhilAd said:**
> I dont think so, after changing the filesystem i will be able to modify the rights with chgrp/chmod, right?

Yes.

> 
I will try it tomorrow. Thanks for your help so far :)


You're welcome.  Don't forget to backup any existing files first.

---

### Post by PhilAd on 2010-09-11
i have changed the filesystem to ext4 now ...
i had to bind the media folders to /home/ftp because i am using defaultroot ~
but i have to set chmod 770 ... with chmod 760 it is not working ... drwxrwx--- is currently set. I don't know why ... usually it should be enough for ftp users to have read and write rights? i dont want to give them execute rights :-/

---

### Post by ubulal on 2010-09-11
Don't worry.  FTP users can *only* transfer files, *never* execute something on your system.

When you want someone to have normal read access to a directory, you *must* give him read *and* execute permissions for the dir.  The "execute" bit on a directory means that you can access the content of the dir.  With read permission but without execute permission, you're only allowed to *list* the content of the dir, i.e. see the names of contained files and folders.  But your not allowed to cd into the dir or it's subdirectories or read the content of the files.  That's why you'll very very rarely see a directory with only the read bit set but without execute bit, because that's almost never useful.

Make sure proftpd is configured to give newly created files 660 or 662 permissions and new directories 770 or 775.  So the files will never have the execute bit set and you can't accidentally start an uploaded program.

---

### Post by PhilAd on 2010-09-11
ok ... when u instantly know how to configure it please tell me ^^
i will google it in the meantime ... i have configured proftpd using a mysql database instead of files or systemusers.

and thanks for your explanation :-)

---

### Post by ubulal on 2010-09-11
[http://www.proftpd.org/docs/howto/Umask.html](http://www.proftpd.org/docs/howto/Umask.html)

---

### Post by PhilAd on 2010-09-11
ok ... with my understanding i had to set umask 002 :-)
thanks for your help and explanation :-)

SOLVED

---

