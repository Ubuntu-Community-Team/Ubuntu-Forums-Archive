---
title: "Unable to Mount External Drives"
date: 2012-02-10
forum: General Help
---

### Post by Dangx3 on 2012-02-10
Hi, Since upgrading to 11.10, I changed my password and in doing so, I seem to have lost some admin privileges. Now when I try to Mount anything, say an external HD, I get a message telling me I don't have permission. I've also noticed that when I go to User Accounts, I can not unlock the page though my profile still says Administrator. I've tried to find a fix several times but have failed and so I come to you dear forum people for assistance. (one last issue that is likely linked to this, when I say to shut down or re-start, I am merely logged out and have to manually shut off the computer, it no longer shuts itself down unless I log into XP instead of Linux...) 

Any suggestions would be appreciated!

---

### Post by Vishnu V on 2012-02-10
Hi
Try this
Open terminal 
```

sudo su
usermod -aG sudo,adm username

```

if sudo su gives error  loggin into the root account the password may be the old userpassword 
try
```

su root

```
If you dont know the password boot into recovery mode and select drop me to root shell

---

### Post by Dangx3 on 2012-02-12
> **Vishnu V said:**
> Hi
Try this
Open terminal 
```

sudo su
usermod -aG sudo,adm username

```if sudo su gives error  loggin into the root account the password may be the old userpassword 
try
```

su root

```If you dont know the password boot into recovery mode and select drop me to root shell

Thanks, I tried that but it doesn't come back with an error, or anything for that matter. It does accept my password and allow me into root but I'm still locked out of many things on the computer. Recently I re-set my wireless and now It's locked me out of this as well. I'll keep looking for another cause...

---

### Post by Vishnu V on 2012-02-13
Is that solved your mounting problem ?
if yes you need to set some more secondary groups that may solve your problem. Normally an admistrator user has the following secondary groups 
adm dialout cdrom sudo dip plugdev lpadmin sambashare
to add these
use
```

sudo usermod -aG adm,dialout,cdrom,sudo,dip,plugdev,lpadmin,sambashare username

```

All the best

---

### Post by HiImTye on 2012-02-13
I hope you've rebooted, you will need to enter your password to unlock the default keyring. it will likely be your old password

---

### Post by Dangx3 on 2012-02-13
Hey, thanks for the code Vishnu V, I gave it a try and I've been trying to find a code for my keyrings. When I enter the keyring app it's self I find it empty. I'm still not able to mount, and I'm wondering if anyone has come across a sudo/terminal command for mounting drives manually, just to see if that will work. 

I've rebooted and updated several times in trying to solve the problem, but to no avail. 

When I bring up the usermod options, I tried using --unlock, and --password. 
When I used unlock, if I wasn't in root, I'd get this message:

```
xxxxx@xxxxx-Aspire-5680:~$ usermod --unlock xxxxx
usermod: cannot lock /etc/passwd; try again later.
```

In root, nothing would happen. 
Same goes for some of the other options I tried. When I try to mount from terminal I get a very similar message. 
```

xxxxx@xxxxx-Aspire-5680:~$ sudo mount VERBATIM
mount: can't find VERBATIM in /etc/fstab or /etc/mtab
```

---

### Post by Dangx3 on 2012-02-13
[http://ubuntuforums.org/showthread.php?t=1924318](http://ubuntuforums.org/showthread.php?t=1924318) 

vfat mounting issues. While I am also running a partition XP / Ubuntu setup, I am not having trouble with Vfat that I know of, but it seems some of the other issues may be similar, so I'm going to carefully check it out. I'll post back if I'm successful.

---

### Post by Dangx3 on 2012-02-13
fstab won't unlock and I can't mod it. This brings me back to my access problem. It would seem that even though I'm admin and have access to root and updates and the usual, I am locked out of may other functions. It's like i'm missing a key ring, or a large chunk of my default admin privileges.

---

### Post by Vishnu V on 2012-02-13
Open terminal and change login as root
now try editing fstab using nano or any other command line editors,(GUI editors like gedit may not work from root shell)
```

nano /ec/fstab

```

or you can directly mount drives from root shell using 
```

mount /dev/sdaXY /payh_to_mountpoint

```

NB: Replace X & Y with your drive details.mount point must be created before mounting

---

