---
title: "Unable to use sudo and su - commands."
date: 2011-05-23
forum: General Help
---

### Post by karthick87 on 2011-05-23
I am unable to use sudo and su - commands. Please check my output below,

```
ubuntu@user1:~$ su -
Segmentation fault
ubuntu@user1:~$ sudo visudo
bash: /usr/bin/sudo: Permission denied
ubuntu@user1:~$ sudo chmod -R 0777 /home/user1/Desktop/
bash: /usr/bin/sudo: Permission denied
ubuntu@user1:~$ 

```

Can anyone help me to solve this issue. Thanks in advance.

---

### Post by Grenage on 2011-05-23
Is this user the only user on the machine?  Was this user later added, but doesn't yet have sudo rights?

---

### Post by Rubi1200 on 2011-05-23
It might help if you post the output of this command:
```
groups
```Thanks.

Also, the output of this please:

```
cat /etc/passwd
```

---

### Post by karthick87 on 2011-05-28
Hi Rubi1200,

 Pls find the below results,
```

ubuntu@user1:~$ groups
ubuntu adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin sambashare
```

```

ubuntu@user1:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
dhcp:x:101:102::/nonexistent:/bin/false
syslog:x:102:103::/home/syslog:/bin/false
klog:x:103:104::/home/klog:/bin/false
hplip:x:104:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:105:113:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
gdm:x:106:114:Gnome Display Manager:/var/lib/gdm:/bin/false
pulse:x:107:116:PulseAudio daemon,,,:/var/run/pulse:/bin/false
messagebus:x:108:119::/var/run/dbus:/bin/false
avahi:x:109:120:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
polkituser:x:110:122:PolicyKit,,,:/var/run/PolicyKit:/bin/false
haldaemon:x:111:123:Hardware abstraction layer,,,:/var/run/hald:/bin/false
ubuntu:x:1000:1000:TMEUB24,,,,:/home/ubuntu:/bin/bash
sshd:x:112:65534::/var/run/sshd:/usr/sbin/nologin
jdstme:x:1001:1001:,,,:/home/jdstme:/bin/bash
```

---

### Post by karthick87 on 2011-05-30
Bump for a move..

---

### Post by karthick87 on 2011-06-05
Final bump to close this thread..

---

### Post by Rubi1200 on 2011-06-05
Hi,
I am a bit confused about what you are trying to do here.

The commands you are running are as ubuntu and /etc/password has ubuntu and jdstme whereas groups only has ubuntu???

Did you change the permissions for ubuntu?

And what is this please?
> TMEUB24

What exactly do you want to achieve?

---

### Post by karthick87 on 2011-06-06
When i run 

```
su - 
```

or

```
sudo <command>
```

in terminal. I get the permission deneid error.

---

### Post by Rubi1200 on 2011-06-06
Karthick,
I understand. Your /etc/passwd looks like this:

```
ubuntu:x:1000:1000:TMEUB24,,,,:/home/ubuntu:/bin/bash
```


On my machine, it is like this:

```
ubuntu:x:1000:1000:ubuntu,,,:/home/ubuntu:/bin/bash
``` 


Do you see the difference, including the extra comma in your line?

Either you or someone else must have changed this I think and I believe that is why you are getting those errors.

As a test, does user jdstme have administrative rights and can he/she use sudo?

---

### Post by karthick87 on 2011-06-07
I dont think that was the problem, even after removing the comma i get the same error.

---

### Post by Rubi1200 on 2011-06-07
The only other possibility I can think of is that the user was removed from sudoers or the permissions were incorrectly changed.

That is where I would look next.

---

### Post by coffeecat on 2011-06-07
> **Rubi1200 said:**
> The only other possibility I can think of is that the user was removed from sudoers or the permissions were incorrectly changed.

That is where I would look next.

I agree that we need to look at the sudoers file.

@karthick87, if you "cat /etc/sudoers" in a system without the problems you describe you get a permission denied error, so you'll need to boot up the live CD to examine that file. See if you can look inside the contents of /etc/sudoers on your permanent installation from the live CD and post it. Be careful not to change anything in it.

---

### Post by karthick87 on 2011-06-16
I have upgraded to newer version and the problem is rectified.


Thanks a lot for those who helped me :)

---

