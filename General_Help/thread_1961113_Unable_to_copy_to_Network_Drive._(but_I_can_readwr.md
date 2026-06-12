---
title: "Unable to copy to Network Drive. (but I can read/write some things)"
date: 2012-04-18
forum: General Help
---

### Post by Capt.Insano on 2012-04-18
I am having the weirdest problem on a new 11.10 install. I have my NetworkDrive mounted just like it was previously on a 10.04 install but I am having problems:

My network drive fstab line looks like this:

```
//192.168.1.2/PUBLIC    /media/FREECOM        cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

I can access /media/FREECOM on the machine and see all folders + files, I can even create test files with

```
touch /media/FREECOM/test.txt
```
and delete files and folders...

But when I try to use the cp command to copy something from the 11.10 machine; the whole command line freezes. I can then see the file on the network drive (using a different PC) but the file has a really small filesize (806KB for example).

The network drive is running perfectly for other (WIN7) computers on the network. But I have ran precautionary diagnostics on the network drive just incase and everything was perfect; the problem definitely does not start there.

Any ideas?

Much appreciated,
The Capt.

---

### Post by Capt.Insano on 2012-04-18
After testing many different things I now think there is something wrong with my method of mounting the drive:

If I use cifs in the fstab (as above) or even in a command:

```
sudo mount -t cifs //192.168.1.2/PUBLIC /media/FREECOM --verbose -o username=guest,password=guest,iocharset=utf8,file_mode=0777,dir_mode=0777
``` 

I get read access but only weird write access (files appear but not properly and the system stall trying to create files larger than ~1MB)

BUT: 

if I just navigate to smb://192.168.1.2/PUBLIC in my file manager I have read/write access no problems..

Can anyone see what is wrong with my fstab/mount command?

Thanks Again!!

---

