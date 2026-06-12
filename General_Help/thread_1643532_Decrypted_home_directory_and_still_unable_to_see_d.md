---
title: "Decrypted home directory and still unable to see data"
date: 2010-12-12
forum: General Help
---

### Post by COKEDUDE on 2010-12-12
I Decrypted home directory and still unable to see data. 


~ $ sudo mount -t ecryptfs /media/4fa4e92e-3532-48fd-a83d-6ea340a669b6/bob /home/bob
Passphrase:
Select cipher:
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 1
Select key bytes:
 1) 16
 2) 32
 3) 24
Selection [16]: 1
Enable plaintext passthrough (y/n) [n]: y
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [aaaaaaaaaaaaaaaa]: bbbbbbbbbbbbbbbb
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=bbbbbbbbbbbbbbbb
  ecryptfs_passthrough
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=aaaaaaaaaaaaaaaa
Mounted eCryptfs

~ $ sudo ls -alF /home/bob
total 28
drwx------ 5 1000 1000 4096 2010-09-03 20:18 ./
drwxr-xr-x 4 root root 80 2010-12-12 03:30 ../
lrwxrwxrwx 1 1000 1000 56 2010-05-24 05:55 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
-rw------- 1 1000 1000 214 2010-09-03 20:18 .bash_history
drwx------ 3 1000 1000 4096 2010-07-16 03:29 .cache/
lrwxrwxrwx 1 1000 1000 29 2010-05-24 05:55 .ecryptfs -> /home/.ecryptfs/bob/.ecryptfs
-rw------- 1 1000 1000 16 2010-09-03 20:18 .esd_auth
drwx------ 2 1000 1000 4096 2010-11-12 20:00 .gconfd/
lrwxrwxrwx 1 1000 1000 28 2010-05-24 05:55 .Private -> /home/.ecryptfs/bob/.Private
drwx------ 2 1000 1000 4096 2010-11-30 02:18 .pulse/
-rw------- 1 1000 1000 256 2010-09-03 20:18 .pulse-cookie
lrwxrwxrwx 1 1000 1000 52 2010-05-24 05:55 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt

~ $ sudo ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly

I have read all 4 of these guides with no luck. 
[http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/](http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/)
[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html#comment-form](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html#comment-form)
[http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/](http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/)
[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

---

### Post by bodhi.zazen on 2010-12-12
run that last command without sudo

```
ecryptfs-mount-private
```

The cd ls

```
cd
ls
```

---

### Post by COKEDUDE on 2010-12-13
> **bodhi.zazen said:**
> run that last command without sudo

```
ecryptfs-mount-private
```

The cd ls

```
cd
ls
```

I tried it both ways with no luck :(. 

```
~ $ ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly
```

```
~ $ sudo ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly
```


What are you trying to say with cd and ls?

---

### Post by bodhi.zazen on 2010-12-13
How did you set up the home directory ? It seems it is on a removable media ?

---

### Post by COKEDUDE on 2010-12-13
> **bodhi.zazen said:**
> How did you set up the home directory ? It seems it is on a removable media ?

When I installed Linux there was a option for "Require my password for login and to decrypt my home folder." I selected that option.

[IMG]http://i255.photobucket.com/albums/hh133/COKEDUDEUSF/ENCRYPTED_SETUP.png[/IMG]

---

### Post by bodhi.zazen on 2010-12-14
How are you logging on to the machine ? 

I do not understand:

1. what does "media/4fa4e92e-3532-48fd-a83d-6ea340a669b6/bob" have to do with "/home/bob" ?

2. what data exactly is not decrypted when you log in ?

---

### Post by COKEDUDE on 2010-12-14
How are you logging on to the machine ? 
From a Live CD. 

media/4fa4e92e-3532-48fd-a83d-6ea340a669b6/bob
That is the location of the partition and home directory that I am trying to open. 

/home/bob
This is where I am trying to mount media/4fa4e92e-3532-48fd-a83d-6ea340a669b6/bob. Since it is encrypted I have to mount it. 

what data exactly is not decrypted when you log in ?
My whole bob directory is encrypted. I am trying to view it from a live cd so I am not really logging in.

---

### Post by bodhi.zazen on 2010-12-14
From a live CD it is dfiierent.

use :

[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

From your first post I do not see that you ever did a chroot ...

---

### Post by COKEDUDE on 2010-12-14
> **bodhi.zazen said:**
> From a live CD it is dfiierent.

use :

[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

From your first post I do not see that you ever did a chroot ...

That guide does not work. I have tried it MANY MANY times. It is obvious this command will not work. 

```
root@ubuntu$ su - kirkland
```

This is a live cd so the user kirkland will not exist. 
```
~ $ su - kirkland
Unknown id: kirkland

```

It also has this problem. 
```
kirkland@ubuntu$ ecryptfs-mount-private
```

```
~ $ ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly

```

That problem is even after I created the user kirkland.

---

### Post by bodhi.zazen on 2010-12-14
You have to change "kirkland" to the user name on the installation you are trying to decrypt.

"kirkland" was just an example.

This command is run within the chroot.

---

### Post by COKEDUDE on 2010-12-14
> **bodhi.zazen said:**
> You have to change "kirkland" to the user name on the installation you are trying to decrypt.

"kirkland" was just an example.

This command is run within the chroot.

I know. bob is the name I used. I still get the same errors if I use bob. 

```
~ $ su - bob
Unknown id: bob

```

---

### Post by bodhi.zazen on 2010-12-14
> **COKEDUDE said:**
> I know. bob is the name I used. I still get the same errors if I use bob. 

```
~ $ su - bob
Unknown id: bob

```

Either you have the wrong user or have not set up the chroot.

> ubuntu@ubuntu$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu$ sudo mount -o bind /dev/shm /mnt/dev/shm
ubuntu@ubuntu$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu$ sudo chroot /mnt

after setting up the chroot you suco chroot.

You need to mount all your partitions in /mnt, do you have a separate /home ? separate /boot ?

Mount your root partition in /mnt , then mount your home partition in /mnt/home , then set up the chroot, then chroot, then su - bob

---

### Post by COKEDUDE on 2010-12-14
> **bodhi.zazen said:**
> **Either you have the wrong user or have not set up the chroot.**



after setting up the chroot you suco chroot.

You need to mount all your partitions in /mnt, do you have a separate /home ? separate /boot ?

Mount your root partition in /mnt , then mount your home partition in /mnt/home , then set up the chroot, then chroot, then su - bob

??. Live cd's have no user's on them except for the live session user. 

Here's all the output. 

```
mint@mint ~ $ sudo mount /dev/sda1 /mnt
mint@mint ~ $ sudo mount -o bind /dev /mnt/dev
mint@mint ~ $ sudo mount -o bind /dev/shm /mnt/dev/shm
mint@mint ~ $ sudo mount -o bind /proc /mnt/proc
mint@mint ~ $ sudo mount -o bind /sys /mnt/sys
mint@mint ~ $ sudo chroot /mnt


mint / # su - bob
No directory, logging in with HOME=/


bob@mint / $ ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly
bob@mint / $ 

```

---

### Post by bodhi.zazen on 2010-12-14
You are performing a somewhat technical operation and I am not sure how much or little of what you are doing you understand.

You are using a live cd to "chroot" into your old system and decrypt your old home directory. When you chroot you "CHange ROOT" or change the root directory for the shell so /mnt (/dev/sda1) is not /

This means in the chroot, you are using /etc/passwd NOT from the live CD, but rather from /mnt/etc/passwd

so the user "bob" exists not on the live cd, bob exists on the partition you are trying to decrypt. Clear as mud ?

If , when you are done, read up on chroot.

At any rate, the problem is one of setting your ENVIRONMENT , namely $HOME.

I still think your partitions / chroot is not properly configured. Is /dev/sda1 your root partition or /home partition ? do you have a separate /home partition ?

The "su -" command should be getting information from /mnt/etc/passwd (your root partition).

What happened to your installation that you are needing to "recover" from ?

---

### Post by bodhi.zazen on 2010-12-15
Perhaps a demo ?

/me boots a live CD ...

> 
# Set up chroot :
# Note my install (both home and /) on sda3

ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /dev/shm/ /mnt/dev/shm
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys

# As you say, there is no "bodhi" on the live CD:
ubuntu@ubuntu:~$ id bodhi
id: bodhi: No such user

# But after we chroot ...
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# id bodhi
uid=1000(bodhi) gid=1000(bodhi) groups=1000(bodhi),4(adm),20(dialout),24(cdrom),46(plugdev),111(lpadmin),119(admin),122(sambashare)

# See bodhi exists in the chroot, understand now ?


# su to bodhi 
root@ubuntu:/# su - bodhi
keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

# But home is encrypted ...

bodhi@ubuntu:~$ ls
Access-Your-Private-Data.desktop  README.txt

# Decrypt home
bodhi@ubuntu:~$ ecryptfs-mount-private 
Enter your login passphrase:
Inserted auth tok with sig [b0d08471978769db] into the user session keyring

INFO: Your private directory has been mounted.
INFO: To see this change in your current shell:
  cd /home/bodhi

# We will not see the data until we cd into the decrypted home
# read the README.txt =)
bodhi@ubuntu:~$ ls
Access-Your-Private-Data.desktop  README.txt

# so cd ...
bodhi@ubuntu:~$ cd

# Now we can see the decrypted data ...
bodhi@ubuntu:~$ ls
bin  Desktop	Downloads	  Music     Public     Videos
bzr  Documents	examples.desktop  Pictures  Templates  zen

We can access the data, as root, from the live CD (gksu nautilus) at

/mnt/home/bodhi

---

### Post by COKEDUDE on 2010-12-15
> **bodhi.zazen said:**
> You are performing a somewhat technical operation and **I am not sure how much or little of what you are doing you understand.**

You are using a live cd to "chroot" into your old system and decrypt your old home directory. When you chroot you "CHange ROOT" or change the root directory for the shell so /mnt (/dev/sda1) is not /

This means in the chroot, you are using /etc/passwd NOT from the live CD, but rather from /mnt/etc/passwd

so the user "bob" exists not on the live cd, bob exists on the partition you are trying to decrypt. Clear as mud ?

If , when you are done, read up on chroot.

At any rate, the problem is one of setting your ENVIRONMENT , namely $HOME.

**I still think your partitions / chroot is not properly configured. Is /dev/sda1 your root partition or /home partition ? do you have a separate /home partition ?**

The "su -" command should be getting information from /mnt/etc/passwd (your root partition).

**What happened to your installation that you are needing to "recover" from ?**

Not very much about chroot. The man pages are very vague for someone that has never used chroot before. 

I split up / partition and /home partition. 

```
~ $ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c8b89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1245     9999360   83  Linux
/dev/sda2            1246        5478    33998849    5  Extended
/dev/sda3   *        5479       12161    53681197+   7  HPFS/NTFS
/dev/sda5            1246        1743     3998720   82  Linux swap / Solaris
/dev/sda6            1744        5478    29999104   83  Linux

```

This article was quite hard to find. I finally found it from googling "Linux which partition is home installed on"
[http://www.linuxclues.com/articles/02.htm](http://www.linuxclues.com/articles/02.htm)

If I was a betting man I would say / partition is installed on **/dev/sda1** and /home partition is installed on **/dev/sda6**. 

```
~ $ df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  1.6G  152M  1.5G  10% /
none                  1.6G  280K  1.6G   1% /dev
/dev/sr0              700M  700M     0 100% /cdrom
/dev/loop0            682M  682M     0 100% /rofs
none                  1.6G  728K  1.6G   1% /dev/shm
tmpfs                 1.6G  304K  1.6G   1% /tmp
none                  1.6G   92K  1.6G   1% /var/run
none                  1.6G     0  1.6G   0% /var/lock
/dev/sda3              52G   32G   21G  61% /media/D07C698F7C697160
/dev/sda6              29G  9.4G   18G  35% /media/4fa4e92e-3532-48fd-a83d-6ea340a669b6
/dev/sda1             9.4G  4.2G  4.9G  47% /media/4fb33fae-d738-405d-8ba1-bc1ede832411

```

So because of this I thank I am correct in choosing to mount **/dev/sda1**. I will try **/dev/sda6** just because I am curious. 

I deleted some VERY important files.

---

### Post by COKEDUDE on 2010-12-15
No luck with **dev/sda6**. 


```
mint@mint ~ $ sudo mount /dev/sda6 /mnt
mint@mint ~ $ sudo mount -o bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
mint@mint ~ $ sudo mount -o bind /dev/shm /mnt/dev/shm
mount: mount point /mnt/dev/shm does not exist
mint@mint ~ $ sudo mount -o bind /proc /mnt/proc
mount: mount point /mnt/proc does not exist
mint@mint ~ $ sudo mount -o bind /sys /mnt/sys
mount: mount point /mnt/sys does not exist
mint@mint ~ $ sudo chroot /mnt
chroot: failed to run command `/bin/bash': No such file or directory

```

---

### Post by bodhi.zazen on 2010-12-15
Mount them and see what is in them.

ls /media/4fa4e92e-3532-48fd-a83d-6ea340a669b6
ls /media/4fb33fae-d738-405d-8ba1-bc1ede832411

One you sort it out, mount them in the proper location (for your chroot).

1. Unmount them from /media/4fa4e92e-3532-48fd-a83d-6ea340a669b6 and /media/4fb33fae-d738-405d-8ba1-bc1ede832411

2. mount your root partition in /mnt and then your home partition in /mnt/home

assuming sda1 is root and sda6 is home ..

```
sudo mount /dev/sda1 /mnt
sudo mount /dev/sda6 /mnt/home
```

Then set up your chroot

```
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /dev/shm/ /mnt/dev/shm
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /sys /mnt/sys
```

Then chroot

```
sudo chroot /mnt /bin/bash
```

and su to bob

```
su - u bob
```

Then decrypt home.

If the partitions are wrong, mount sda6 at /mnt and sda1 at /mnt/home and try again.

---

### Post by COKEDUDE on 2010-12-16
IT WORKED :D :mrgreen: =D>. 

```
mint@mint ~ $ ls /media/4fa4e92e-3532-48fd-a83d-6ea340a669b6
bob  joe  lost+found  Recycled  RECYCLER
mint@mint ~ $ ls /media/4fb33fae-d738-405d-8ba1-bc1ede832411
bin   home        media       opt       root     sys  vmlinuz
boot  initrd.img  mnt         proc      sbin     tmp
dev   lib         OldHome     Recycled  selinux  usr
etc   lost+found  OldPrivate  RECYCLER  srv      var
mint@mint ~ $ umount /media/4fa4e92e-3532-48fd-a83d-6ea340a669b6
mint@mint ~ $ umount /media/4fb33fae-d738-405d-8ba1-bc1ede832411
mint@mint ~ $ sudo mount /dev/sda1 /mnt
mint@mint ~ $ sudo mount /dev/sda6 /mnt/home
mint@mint ~ $ sudo mount -o bind /dev /mnt/dev
mint@mint ~ $ sudo mount -o bind /dev/shm/ /mnt/dev/shm
mint@mint ~ $ sudo mount -o bind /proc /mnt/proc
mint@mint ~ $ sudo mount -o bind /sys /mnt/sys
mint@mint ~ $ sudo chroot /mnt /bin/bash
 _______________________________________
( Many changes of mind and mood; do not )
( hesitate too long.                    )
 ---------------------------------------
  o
   o
       ___  
     {~._.~}
      ( Y )
     ()~*~()   
     (_)-(_)   
mint / # su - u bob
Unknown id: u
mint / # su - bob
keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'
 _________________________________________
( "I don't think you have to go through   )
( the process of reconfiguring X as I did )
( - that was partly because the           )
( frustration made me brain dead."        )
(                                         )
( Husse Apr 5 2007                        )
 -----------------------------------------
  o
   o
       ___  
     {~._.~}
      ( Y )
     ()~*~()   
     (_)-(_)   
bob@mint ~ $ ecryptfs-mount-private
Enter your login passphrase:
Error: Unwrapping passphrase and inserting into the user session keyring failed [-5]
Info: Check the system log for more information from libecryptfs
ERROR: Your passphrase is incorrect
Enter your login passphrase:
Error: Unwrapping passphrase and inserting into the user session keyring failed [-5]
Info: Check the system log for more information from libecryptfs
ERROR: Your passphrase is incorrect
Enter your login passphrase:
Inserted auth tok with sig [3bacfa4dde6b90dd] into the user session keyring

INFO: Your private directory has been mounted.
INFO: To see this change in your current shell:
  cd /home/bob

bob@mint ~ $ ls -alF
total 32
drwx------ 5 bob  bob  4096 2010-09-03 16:18 ./
drwxr-xr-x 8 root root 4096 2010-08-21 18:16 ../
lrwxrwxrwx 1 bob  bob    56 2010-05-24 01:55 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
-rw------- 1 bob  bob   214 2010-09-03 16:18 .bash_history
drwx------ 3 bob  bob  4096 2010-07-15 23:29 .cache/
lrwxrwxrwx 1 bob  bob    29 2010-05-24 01:55 .ecryptfs -> /home/.ecryptfs/bob/.ecryptfs/
-rw------- 1 bob  bob    16 2010-09-03 16:18 .esd_auth
drwx------ 2 bob  bob  4096 2010-11-12 15:00 .gconfd/
lrwxrwxrwx 1 bob  bob    28 2010-05-24 01:55 .Private -> /home/.ecryptfs/bob/.Private/
drwx------ 2 bob  bob  4096 2010-11-29 21:18 .pulse/
-rw------- 1 bob  bob   256 2010-09-03 16:18 .pulse-cookie
lrwxrwxrwx 1 bob  bob    52 2010-05-24 01:55 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt
bob@mint ~ $ pwd
/home/bob
bob@mint ~ $ cd /home/bob
bob@mint ~ $ ls -alF
total 16672
drwx------ 92 bob  bob    28672 2010-12-09 01:12 ./
drwxr-xr-x  8 root root    4096 2010-08-21 18:16 ../
-rw-r--r--  1 bob  bob    88038 2010-08-31 02:43 20 group list.txt
-rwxr-xr-x  1 bob  bob      191 2010-10-28 15:34 .xprofile*
bob@mint ~ $ pwd
/home/bob
bob@mint ~ $ Nautilus
No command 'Nautilus' found, did you mean:
 Command 'nautilus' from package 'nautilus' (main)
Nautilus: command not found
bob@mint ~ $ nautilus
No protocol specified
Could not parse arguments: Cannot open display: 
bob@mint ~ $ nautilus
No protocol specified
Could not parse arguments: Cannot open display: 

```

Why can I not open nautilus? Why does my **.xprofile** have a ***** next to it?

---

### Post by bodhi.zazen on 2010-12-16
> **COKEDUDE said:**
> IT WORKED :D :mrgreen: =D>. 

```
mint@mint ~ $ ls /media/4fa4e92e-3532-48fd-a83d-6ea340a669b6
bob  joe  lost+found  Recycled  RECYCLER
mint@mint ~ $ ls /media/4fb33fae-d738-405d-8ba1-bc1ede832411
bin   home        media       opt       root     sys  vmlinuz
boot  initrd.img  mnt         proc      sbin     tmp
dev   lib         OldHome     Recycled  selinux  usr
etc   lost+found  OldPrivate  RECYCLER  srv      var
mint@mint ~ $ umount /media/4fa4e92e-3532-48fd-a83d-6ea340a669b6
mint@mint ~ $ umount /media/4fb33fae-d738-405d-8ba1-bc1ede832411
mint@mint ~ $ sudo mount /dev/sda1 /mnt
mint@mint ~ $ sudo mount /dev/sda6 /mnt/home
mint@mint ~ $ sudo mount -o bind /dev /mnt/dev
mint@mint ~ $ sudo mount -o bind /dev/shm/ /mnt/dev/shm
mint@mint ~ $ sudo mount -o bind /proc /mnt/proc
mint@mint ~ $ sudo mount -o bind /sys /mnt/sys
mint@mint ~ $ sudo chroot /mnt /bin/bash
 _______________________________________
( Many changes of mind and mood; do not )
( hesitate too long.                    )
 ---------------------------------------
  o
   o
       ___  
     {~._.~}
      ( Y )
     ()~*~()   
     (_)-(_)   
mint / # su - u bob
Unknown id: u
mint / # su - bob
keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'
 _________________________________________
( "I don't think you have to go through   )
( the process of reconfiguring X as I did )
( - that was partly because the           )
( frustration made me brain dead."        )
(                                         )
( Husse Apr 5 2007                        )
 -----------------------------------------
  o
   o
       ___  
     {~._.~}
      ( Y )
     ()~*~()   
     (_)-(_)   
bob@mint ~ $ ecryptfs-mount-private
Enter your login passphrase:
Error: Unwrapping passphrase and inserting into the user session keyring failed [-5]
Info: Check the system log for more information from libecryptfs
ERROR: Your passphrase is incorrect
Enter your login passphrase:
Error: Unwrapping passphrase and inserting into the user session keyring failed [-5]
Info: Check the system log for more information from libecryptfs
ERROR: Your passphrase is incorrect
Enter your login passphrase:
Inserted auth tok with sig [3bacfa4dde6b90dd] into the user session keyring

INFO: Your private directory has been mounted.
INFO: To see this change in your current shell:
  cd /home/bob

bob@mint ~ $ ls -alF
total 32
drwx------ 5 bob  bob  4096 2010-09-03 16:18 ./
drwxr-xr-x 8 root root 4096 2010-08-21 18:16 ../
lrwxrwxrwx 1 bob  bob    56 2010-05-24 01:55 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
-rw------- 1 bob  bob   214 2010-09-03 16:18 .bash_history
drwx------ 3 bob  bob  4096 2010-07-15 23:29 .cache/
lrwxrwxrwx 1 bob  bob    29 2010-05-24 01:55 .ecryptfs -> /home/.ecryptfs/bob/.ecryptfs/
-rw------- 1 bob  bob    16 2010-09-03 16:18 .esd_auth
drwx------ 2 bob  bob  4096 2010-11-12 15:00 .gconfd/
lrwxrwxrwx 1 bob  bob    28 2010-05-24 01:55 .Private -> /home/.ecryptfs/bob/.Private/
drwx------ 2 bob  bob  4096 2010-11-29 21:18 .pulse/
-rw------- 1 bob  bob   256 2010-09-03 16:18 .pulse-cookie
lrwxrwxrwx 1 bob  bob    52 2010-05-24 01:55 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt
bob@mint ~ $ pwd
/home/bob
bob@mint ~ $ cd /home/bob
bob@mint ~ $ ls -alF
total 16672
drwx------ 92 bob  bob    28672 2010-12-09 01:12 ./
drwxr-xr-x  8 root root    4096 2010-08-21 18:16 ../
-rw-r--r--  1 bob  bob    88038 2010-08-31 02:43 20 group list.txt
-rwxr-xr-x  1 bob  bob      191 2010-10-28 15:34 .xprofile*
bob@mint ~ $ pwd
/home/bob
bob@mint ~ $ Nautilus
No command 'Nautilus' found, did you mean:
 Command 'nautilus' from package 'nautilus' (main)
Nautilus: command not found
bob@mint ~ $ nautilus
No protocol specified
Could not parse arguments: Cannot open display: 
bob@mint ~ $ nautilus
No protocol specified
Could not parse arguments: Cannot open display: 

```

Why can I not open nautilus? Why does my **.xprofile** have a ***** next to it?

To access the data, do not exit the chroot

Open a new terminal and run nautilus as root

```
gksu nautilus
```and browse to /mnt/home/bob

copy / back up the files to an alternate location or flash drive =)

You can not run graphical applications directly from the chroot, you would need to connect to the chroot via a VNC or ssh -X.

Again, when you are done, read up on a chroot.

---

### Post by COKEDUDE on 2010-12-16
Why does my **.xprofile** have a ***** next to it?


Why does mounting it this way allow me to decrypt my home directory? How am I able to mount at **/mnt/home**? I never created that folder. 
```
sudo mount /dev/sda1 /mnt
sudo mount /dev/sda6 /mnt/home
```

---

### Post by bodhi.zazen on 2010-12-16
> **COKEDUDE said:**
> Why does my **.xprofile** have a ***** next to it?[/code]

I have no idea =)

```
Why does mounting it this way allow me to decrypt my home directory? How am I able to mount at **/mnt/home**? I never created that folder. 
[CODE]sudo mount /dev/sda1 /mnt
sudo mount /dev/sda6 /mnt/home
```

Because the /home directory exists in the root ( / ) directory on /dev/sda1 , look in fstab, how else would home mount when you boot ?

chroot is a fun albeit geeky tool =)

[http://en.wikipedia.org/wiki/Chroot](http://en.wikipedia.org/wiki/Chroot)
[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

---

### Post by COKEDUDE on 2010-12-23
I wrote a guide on this so I hope this will help other people. 

[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory)

---

