---
title: "Automount Windows Share"
date: 2010-07-31
forum: General Help
---

### Post by Russell_S on 2010-07-31
Hi, hopefully someone can help me out with this problem.

I am running Ubuntu 10.04 and I am trying to automatically mount a windows share by following the advice in this Ubuntu wiki page [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

However, when I edit the /etc/fstab file as advised and then "sudo mount -a" I get the following message in the terminal window:

> wrong fs type, bad option, bad superblock on //192.168.1.1/Music,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
The share in question is on a FreeNAS server and the CIFS share is "//192.168.1.1/Music"

I have added the following line to /etc/fstab 
> //192.168.1.1/Music  /home/russell/AutoMounts/Music cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0Can anyone see where I am going wrong and point me in the right direction please.


Many thanks

Russell

---

### Post by PaulW2U on 2010-07-31
I don't know the answer to your problem but here is my entry from /etc/fstab:

```
//hs-dhgla3b/share /mnt/share cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

There seems to be a few options that I have added that you haven't, may be there's something there for you to try. As far as I can remember I got that line from posts on these forums and didn't have to fiddle to get the share working at all.

Hope that helps.

---

### Post by Russell_S on 2010-07-31
Thanks for the help.

however, I've tried the line you suggested (obviously replacing you share etc with my own) but I get the same problem.

Any other ideas anyone. Just in case it is relevant, I have only just installed 10.04 yesterday. I was running 9.10 before and I had the share automounting in that fine but when I copied the fstab line from 9.10 into the 10.04 one it didn't work. In view of this is my problem because something else is missing and requires installing.


Regards

Russell

---

### Post by Mark Phelps on 2010-07-31
I also automount an MS Windows share, but in my case, the FSTAB line include the phrase "credentials=/root/.cifscredentials" -- which is a hidden file where I store my login credentials for the machine hosting the share.

And in my case, the .cifscredentials file include the following two lines:
username=guest
password=

Perhaps that's the part that you're missing.

---

