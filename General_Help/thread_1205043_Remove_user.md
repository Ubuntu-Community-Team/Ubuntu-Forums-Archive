---
title: "Remove user"
date: 2009-07-05
forum: General Help
---

### Post by henrywm on 2009-07-05
I deleted a user account, and now I am trying to add a new account by the same name, but Ubuntu tells me that the user name already exists. The user name does not appear in the Users and Groups dialog, and I deleted the old user's home directory, but Ubuntu still insists that the user name exists.

---

### Post by michy99 on 2009-07-05
Have you rebooted since deleting the user?

---

### Post by henrywm on 2009-07-05
Yes.

---

### Post by taurus on 2009-07-05
How did you delete the other account?  What is the username that you are trying to create?

Post the outputs of these commands from a terminal.

```
cat /etc/passwd
ls -la /home
```

---

### Post by henrywm on 2009-07-05
It is named "guest"
I created it as a general usage guest account.

I first tried to delete it through the Users and Groups dialog, but somehow it was still present. I noticed that the guest home folder still existed, and so I deleted it with "rm -Rf guest"

In the meantime I created a general usage guest account called "guest1." I would prefer to just call it "guest" for simplicity.

---

### Post by henrywm on 2009-07-05
When I insert the output results of "cat /etc/passwd" I am told that I included too many images.

The output for "ls -la /home" is:

total 16
drwxr-xr-x  4 root   root   4096 2009-07-05 14:21 .
drwxr-xr-x 22 root   root   4096 2009-07-03 10:35 ..
drwxr-xr-x  2 guest1 guest1 4096 2009-07-05 14:21 guest1
drwxr-xr-x 44 henry  henry  4096 2009-07-05 20:42 henry

---

### Post by reverend27 on 2009-07-08
I am having this exact issue, excepting that my "stuck" user name is "brad" and not "guest".  From cli I have run:
sudo deluser --force --remove-home brad
sudo delgroup brad

Both resulting in success messages.  

An ls -al of /home results in:
drwxr-xr-x  3 root     root     4096 2009-07-08 06:00 .
drwxr-xr-x 21 root     root     4096 2009-06-25 07:16 ..
drwxr-xr-x 41 reverend reverend 4096 2009-07-08 06:14 reverend

and cat /etc/passwd:
reverend@san-jose:/etc$ cat /etc/passwd
```
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
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
hplip:x:103:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:104:110:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
gdm:x:105:111:Gnome Display Manager:/var/lib/gdm:/bin/false
saned:x:106:113::/home/saned:/bin/false
pulse:x:107:114:PulseAudio daemon,,,:/var/run/pulse:/bin/false
messagebus:x:108:117::/var/run/dbus:/bin/false
polkituser:x:109:118:PolicyKit,,,:/var/run/PolicyKit:/bin/false
avahi:x:110:119:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
haldaemon:x:111:120:Hardware abstraction layer,,,:/var/run/hald:/bin/false
reverend:x:1000:1000:Pete Jones,,,:/home/reverend:/bin/bash
```

Using System --> Adminstration --> Users and Groups I can re-add the group "brad" but when I attempt to re-add the user I get the message:
User name "brad" already exists.

What else can I try to wipe out all traces of the original so that a new user of the same name can be created?  Thanks a bunch.

---

### Post by e24ohm on 2009-07-10
> **henrywm said:**
> I deleted a user account, and now I am trying to add a new account by the same name, but Ubuntu tells me that the user name already exists. The user name does not appear in the Users and Groups dialog, and I deleted the old user's home directory, but Ubuntu still insists that the user name exists.

Delete the user account, then search for a group of the same name. Once you have delete the user account, and group. User a command line and perform the follwoing.

/home
sudo chmod 777 userfolder
sudo rm -r userfolder

then you should be able to create the user account again.

thanks. let me know how it goes

---

### Post by henrywm on 2009-07-11
I already deleted the guest folder. Ubuntu thinks the user still exists.

---

### Post by twoflatfish on 2009-07-29
> **e24ohm said:**
> Delete the user account, then search for a group of the same name. Once you have delete the user account, and group. User a command line and perform the follwoing.

/home
sudo chmod 777 userfolder
sudo rm -r userfolder

then you should be able to create the user account again.

thanks. let me know how it goes
Thanks e24ohm...I have the same problem. A search brought me here and your solution worked for me.
SJF

---

### Post by Raffles10 on 2009-07-29
Using the cli has always been the most efficient way to remove users...

```
userdel -r *username*
```

will remove user and home directory.

---

