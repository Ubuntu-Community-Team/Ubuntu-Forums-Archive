---
title: "ecryptfs-mount-private  - operation not permitted"
date: 2010-01-03
forum: General Help
---

### Post by cmpcmp on 2010-01-03
I can't acces the home-folder. There is a problem with ecryptfs


computer@computer:~$ cd /
computer@computer:/$ ecryptfs-mount-private
Enter your login passphrase:
Inserted auth tok with sig [  ] into the user session keyring
mount: Operation not permitted


 Does someone know how to fix it?

---

### Post by cmpcmp on 2010-01-09
I think it can be done with the command

```
chmod
```but what directory do I have to change the permission of?

---

### Post by cmpcmp on 2010-01-10
I edited permissions of
/home
/usr/bin
/usr/share/ecryptfs-utils
/sbin


still no permission when :  ecryptfs-mount-private  




does someone know the right answer?

---

### Post by michy99 on 2010-01-10
You shouldn't be altering permissions of those directories. You will be lucky if you haven't messed up your whole system. What you should try is[code]sudo ecryptfs-mount-private[code]

---

### Post by cmpcmp on 2010-01-13
The system doesn't boot any more (now boot with livecd)
I tried from recovery mode to change the permissions to 644
```
chmod 644
``` to directories I edited
When I try  to login there's a message
'could not cd to /home/computer/'


I tried it with sudo (before I did the chmod command)
but then another error message: no such file or directory.
On some forums it is said that it doesn't work with sudo

now what?

---

### Post by cmpcmp on 2010-01-16
The system doesn't boot,

 but I copied the encrypted files to an external disk.

I copied the directory /home/name
 there-in is the directory:          .ecryptfs
there-in is the directory:           name
there-in are two directories:         .ecryptfs         and          .Private
the directory .Private is 11,3 GB


Is it possible to decrypt them from the external disk?

or is there a way to set the permissions from the directories back to default?



PS : Is there a better way to get help for ecryptfs?

---

### Post by U_Academical on 2010-01-16
> **cmpcmp said:**
> The system doesn't boot,
 PS : Is there a better way to get help for ecryptfs?

 man ecryptfs - next time try the manual. Sorry unhelpful I know, but true, sounds like you've broken bits of it by playing around changing permissions for bits of the system.  Re-Install time, next time use sudo ecryptfs or sudo su and login as root and use ecryptfs as the root user!  As to recovering the contents of private, when you setup ecryptfs it would have created a copy of the password hash in a config file, you will need a copy of that hash so it can verify the password if you want to recover the documents later & no I dont know where it's stored as it's been a while since I used it myself. Unlucky..  P.S: Directory permissions on ~/Private should be 700  [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

---

### Post by cmpcmp on 2010-01-16
what is the password hash?
I have written the mount-passphrase when installing ecryptfs.
but with ecryptfs-mount-private it doesn't ask the mount-passphrase but the loginpass (the same password to log in on the computer)


could the config file be one of these? (files located in /home/name/.ecryptfs/name/.ecryptfs)
.wrappep-passphrase
auto-mount
auto-umount
Private.mnt
Private.sig
wrapped-passphrase



I can't access the directory  /
what permission should the directory / have?
is there a list with the right permissions for all the filesystem directories?

or is it not possible?

---

### Post by cmpcmp on 2010-01-16
I found the solution to mount it here
[https://answers.launchpad.net/ecryptfs/+question/97115](https://answers.launchpad.net/ecryptfs/+question/97115)


now the files are not encrypted anymore.
I see them if i type
```
root@ubuntu:/# cd /home/computer/Private
root@ubuntu:/# ls
```but now I'ld like to copy them to external hard disk.
but what is the exact location of the disk?

---

### Post by cmpcmp on 2010-01-16
If I type in command  'df'

```
root@ubuntu:/# df
Bestandssysteem           1K-blokken Gebruikt Beschikbr Geb% Aangekoppeld op
/dev/sda1             74706268  20827596  50083720  30% /
udev                    383524       292    383232   1% /dev
none                    383524       292    383232   1% /dev/pts
none                    383524       220    383304   1% /dev/shm
none                  74706268  20827596  50083720  30% /var/run
none                  74706268  20827596  50083720  30% /var/lock
none                  74706268  20827596  50083720  30% /lib/init/rw
/home/.ecryptfs/computer/.Private
                      74706268  20827596  50083720  30% /home/computer/Private
```without 'root':
```
ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                    383524     63364    320160  17% /
udev                    383524       292    383232   1% /dev
/dev/sr1                706532    706532         0 100% /cdrom
/dev/loop0              684032    684032         0 100% /rofs
none                    383524       220    383304   1% /dev/shm
tmpfs                   383524        40    383484   1% /tmp
none                    383524        92    383432   1% /var/run
none                    383524         0    383524   0% /var/lock
none                    383524         0    383524   0% /lib/init/rw
/dev/sda1             74706268  20827596  50083720  30% /media/09400b6b-e756-4c31-b801-fa41e7af03bd
/dev/sdb1               501280    138928    362352  28% /media/512 MB
/dev/sda1             74706268  20827596  50083720  30% /mnt
/dev/sdc5              1026104    243004    783100  24% /media/INSTALL
/dev/sdc1             53255440  34768912  18486528  66% /media/C038158338157A1C
```



with 'root':
```
root@ubuntu:# cd /dev/sdc1
bash: cd: /dev/sdc1: Is not a directory
```

it is mounted :  /media/C038158338157A1C
but then it shows : 'File or directory doens't exist'

---

