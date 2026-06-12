---
title: "Can't Mount Network Drive ubuntu 9.10 64bit"
date: 2010-04-28
forum: General Help
---

### Post by markg777 on 2010-04-28
I cant seem to figure out why i cant mount any network folders.  when i when i was going through this forum, [http://ubuntuforums.org/showthread.php?t=1318748](http://ubuntuforums.org/showthread.php?t=1318748) i got stuck on the first step.  

smbclient -L //10.1.1.3 (insert your windows machine ip instead)

i get this error.  
bob@bob-ubuntu:~$ smbclient -L //192.26.92.21
Enter bob's password: 
signing_good: BAD SIG: seq 1
session setup failed: NT_STATUS_OK
bob@bob-ubuntu:~$ 

i am using ubuntu 9.10 64 bit.  

any help would be great!

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
[http://lists.samba.org/archive/samba/2005-January/098500.html](http://lists.samba.org/archive/samba/2005-January/098500.html)

---

### Post by markg777 on 2010-04-28
so Sin@Sin-Sacrifice i need different version of kerbios?..   

I also forgot to add this.  not sure why i am getting this error also.  this is when i try to actualy mount a folder from the proceeding steps of that other article.  

bob@bob-ubuntu:~$ sudo mount -t cifs //192.26.92.21/bbob  /home/bob/shares/bbob -o username=username,password=password,iocharset=utf8,file_mode=0777,dir_mode=0777
mount error(12): Cannot allocate memory
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
bob@bob-ubuntu:~$

---

