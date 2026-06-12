---
title: "Help with recovering data"
date: 2010-06-03
forum: General Help
---

### Post by mvalenti on 2010-06-03
Ubuntu 9.10 64bit
Acer Laptop

Using ubuntu 9.10 cd to access laptops hard drive.

foun readme file in /media/disk/mark

opened with openoffice
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 $ ecryptfs-mount-private

So I tried a couple of ways...

ubuntu@ubuntu:~$ cd /media/disk/mark
ubuntu@ubuntu:/media/disk/mark$ ecryptfs-mount-private
ERROR: Encrypted Private is not setup properly
ubuntu@ubuntu:/media/disk/mark$ sudo ecryptfs-mount-private
ERROR: Encrypted Private is not setup properly
ubuntu@ubuntu:/media/disk/mark$ 


What am I doing wrong?

---

### Post by weirdtalk on 2010-06-04
I could use a few more details about what were trying to do.

Are you trying to pull (non-deleted) files off a ubuntu 64bit laptop using a live cd of ubuntu? A different setup?

Is the hard disk encrypted?

The way you are setup will determine what you need to do.

---

### Post by mvalenti on 2010-06-04
My ubuntu 9.10 laptop would not boot up after I had removed cairo dock via package manager. I thought that I would be able to boot with the ubuntu 9.10 cd, and copy my home dir to an external drive. When I mount the internal laptop drive, I see the two files, readme.txt and the encrypted data file. I can not seem to "mount" the encrypted file in order to get at its contents to copy. Thanks for your help!


-Mark

---

### Post by dino99 on 2010-06-04
how to chroot your system from a cd, follow this example:

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)


recovering tools:

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

---

### Post by weirdtalk on 2010-06-04
recovery tools like photorec will not help for an encrypted folder.

I would attempt to chroot and get the computer to boot on it's own first, and if that doesn't work maybe this will help:
[link]("https://help.ubuntu.com/community/EncryptedPrivateDirectory")

I don't have much experience with folder encryption so I don't know how much help I can give.

By the way, what error message do you get while booting?

---

### Post by mvalenti on 2010-06-04
it froze on 
usplash:.... then some text/resolution that I cant recall at the moment...

---

### Post by mvalenti on 2010-06-09
Is there a way to copy the data to a seperate drive in an attempt to later retrieve it? I tried last night with the live CD in the laptop and tried copying the data to an external hard drive but apparently did not have permissions.... I REALLY NEED HELP!!!  Does anyone know anything about retrieving this encrypted data?

-Mark

---

### Post by weirdtalk on 2010-06-09
I found this guide:
[http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/](http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/)

It looks easy-ish. If you still have troubles post how far you got. 

You've got me curious now. I might have to try this in a virtual machine just for fun.

---

### Post by weirdtalk on 2010-06-09
I have tested this method on a vm and it works I will list the step I took for those interested.

I used a ubuntu 10.04 cd, but any live cd/usb should work.

once booted I opened a terminal and ran these commands
```

sudo su
mkdir /media/chroot

```

Then I had to figure out which disk I need to mount (which disk ubuntu is installed on.) You can either use
```
fdisk -l
```
or
```
gparted
```
for me it was on /dev/sda1 so please put you disk in place of sda1 in the following commands.


Next we want to mount this drive & change the root location.
```

mount /dev/sda1 /media/chroot
mount -o bind /dev /media/chroot/dev
mount -o bind /sys /media/chroot/sys
mount -o bind /dev/shm /media/chroot/dev/shm
mount -o bind /proc /media/chroot/proc
chroot /media/chroot

```

then switch to our username (in my case it is "user")
```
su user
```

It will print a warning about not being able to see the encrypted home. Next we load our encrypted home folder.
```
ecryptfs-mount-private
```
It will ask you for your login password. Hopefully you remember it.

Then change to that folder and reveal what is inside.
```
cd /home/user
ls
```

At this point you can copy any data you want out for recovery purposes.

---

### Post by mvalenti on 2010-06-09
Much appreciated! I will try this first thing when I get home and will post the results.

Thanks for your time!

-Mark

---

### Post by mvalenti on 2010-06-09
welp, this is how far I got...

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# mkdir /media/chroot
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x731e75ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5837    46885671   83  Linux
/dev/sda2            5838       30152   195310237+  83  Linux
/dev/sda3           30153       38913    70372732+   5  Extended
/dev/sda5           37698       38913     9767520   82  Linux swap / Solaris
/dev/sda6           30153       37696    60597117   83  Linux

Partition table entries are not in disk order
root@ubuntu:/home/ubuntu# mount /dev/sda1 /media/chroot
root@ubuntu:/home/ubuntu# mount -o bind /dev /media/chroot/dev
root@ubuntu:/home/ubuntu# mount -o bind /sys /media/chroot/sys
root@ubuntu:/home/ubuntu# mount -o bind /dev/shm /media/chroot/dev/shm
root@ubuntu:/home/ubuntu# mount -o bind /proc /media/chroot/proc
root@ubuntu:/home/ubuntu# chroot /media/chroot
root@ubuntu:/# su mark
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

mark@ubuntu:/$ su user
Unknown id: user
mark@ubuntu:/$ su mark
Password: 
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

mark@ubuntu:/$ ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly

---

### Post by weirdtalk on 2010-06-09
ok there are still two things we can try.

The first is from: [http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/](http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/)

he suggests recreated the user WITHOUT recreated the home directory.

I suggest copying the /home/mark to /home/mark~ before trying this. Then follow the steps until chroot. Do the chroot and then 
```
adduser --no-create-home mark
sudo su mark
```

and continue the steps.

if it complains about user already existing make a new user (like mark2) and 'cp /home/mark /home/mark2' before any other steps.

The second thing you can try is from the ubuntu directions:

first you need to recover the passphrase:
```
ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase "login passphrase"
```

then use the directions from "recovering your data manually" [LINK]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering Your Data Manually")

let us know how that goes.

---

### Post by mvalenti on 2010-06-10
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# mkdir /media/chroot
root@ubuntu:/home/ubuntu# mountmount /dev/sda1 /media/chroot
bash: mountmount: command not found
root@ubuntu:/home/ubuntu# mount /dev/sda1 /media/chroot
root@ubuntu:/home/ubuntu# mount -o bind /dev /media/chroot/dev
root@ubuntu:/home/ubuntu# mount -o bind /sys /media/chroot/sys
root@ubuntu:/home/ubuntu# mount -o bind /dev/shm /media/chroot/dev/shm
root@ubuntu:/home/ubuntu# mount -o bind /proc /media/chroot/proc
root@ubuntu:/home/ubuntu# chroot /media/chroot
root@ubuntu:/# adduser --no-create-home mark
adduser: The user `mark' already exists.
root@ubuntu:/# adduser --no-create-home mark2
Adding user `mark2' ...
Adding new group `mark2' (1002) ...
Adding new user `mark2' (1002) with group `mark2' ...
Not creating home directory `/home/mark2'.
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for mark2
Enter the new value, or press ENTER for the default
	Full Name []: 
	Room Number []: 
	Work Phone []: 
	Home Phone []: 
	Other []: 
Is the information correct? [Y/n] 
root@ubuntu:/# sudo su mark2
mark2@ubuntu:/$ ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly


I will try the 2nd method and repost...

---

### Post by mvalenti on 2010-06-10
ubuntu@ubuntu:~$ ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase "login passphrase"
Warning: Using default salt value (undefined in ~/.ecryptfsrc)
Error: Unwrapping passphrase failed [-5]
Info: Check the system log for more information from libecryptfs
ubuntu@ubuntu:~$

---

### Post by mvalenti on 2010-06-10
ubuntu@ubuntu:~$ sudo ecryptfs-add-passphrase --fnek
Passphrase: 
Warning: Using default salt value (undefined in ~/.ecryptfsrc)
Inserted auth tok with sig [493701a8ae5c5778] into the user session keyring
Inserted auth tok with sig [a2bb372be737b465] into the user session keyring
ubuntu@ubuntu:~$ sudo mount -t ecryptfs /home/username/.Private /home/username/Private
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 1
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y
Filname Encryption Key (FNEK) Signature [493701a8ae5c5778]: a2bb372be737b465
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=a2bb372be737b465
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=493701a8ae5c5778
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? y
Aborting mount.
ubuntu@ubuntu:~$

---

### Post by weirdtalk on 2010-06-11
I believe the first method failed, becuase there was no /home/mark2

you have to run
```
sudo mkdir /home/mark2
sudo cp -r /home/mark /home/mark2
```

before running ecryptfs-mount-private

For the second method I see the prefix ubuntu@ubuntu

you need to follow the chroot steps until you login in as mark the prefix will change to mark@ubuntu then it should work

also change sudo mount -t ecryptfs /home/username/.Private /home/username/Private
to
sudo mount -t ecryptfs /home/mark/.Private /home/mark/Private

Let us know.

---

### Post by weirdtalk on 2010-06-11
found another example of someone using the chroot with sucess:
[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/337475](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/337475)

```
 ubuntu@ubuntu$ sudo mount /dev/sda1 /mnt
  ubuntu@ubuntu$ sudo mount -o bind /dev /mnt/dev
  ubuntu@ubuntu$ sudo mount -o bind /proc /mnt/proc
  ubuntu@ubuntu$ sudo mount -o bind /sys /mnt/sys
  ubuntu@ubuntu$ sudo chroot /mnt
  root@ubuntu$ su - kirkland
  kirkland@ubuntu$ ecryptfs-mount-private
  kirkland@ubuntu$ Password:
  kirkland@ubuntu$ cd
  kirkland@ubuntu$ ls -alF
  kirkland@ubuntu$ cat .profile

:-Dustin
```

The differences being fewer things needed to be mounted and he used 'su - user' instead of 'su user' which I'm not sure makes a difference (the man page suggests it acts like a normal login rather than just switching the user), but is worth trying.

---

### Post by mvalenti on 2010-06-11
Let me give it a go again... getting a lil confused with the last posts... so I printed everything out and will reassemble the posts into a set of steps... ;)  

BTW, my home dir is on a seperate drive than boot... I just thought of that... Not sure if that changes anything tho in how we mount...


-Mark

---

### Post by mvalenti on 2010-06-11
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount -o bind /sys mnt/sys
mount: mount point mnt/sys does not exist
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# su - mark
No directory, logging in with HOME=/
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

mark@ubuntu:/$ ecryptfs-mount-privite
No command 'ecryptfs-mount-privite' found, did you mean:
 Command 'ecryptfs-mount-private' from package 'ecryptfs-utils' (main)
ecryptfs-mount-privite: command not found
mark@ubuntu:/$ 


kirklands method....

---

### Post by beckols on 2010-06-11
> **mvalenti said:**
> 
mark@ubuntu:/$ ecryptfs-mount-privite
No command 'ecryptfs-mount-privite' found, did you mean:
 Command 'ecryptfs-mount-private' from package 'ecryptfs-utils' (main)
ecryptfs-mount-privite: command not found
mark@ubuntu:/$ 


kirklands method....

You spelled "private" wrong.

---

### Post by weirdtalk on 2010-06-11
> **mvalenti said:**
> 
BTW, my home dir is on a seperate drive than boot... I just thought of that... Not sure if that changes anything tho in how we mount...


it does. First mount the root then the /home like so:
```

sudo mount /dev/sda1 /mnt
sudo mount /dev/sda? /mnt/home

```

edit: is that "root" or "boot"? /boot being separate won't make any difference.

---

### Post by mvalenti on 2010-06-11
root, sorry...

at what point in the process do I enter?
sudo mount /dev/sda1 /mnt
sudo mount /dev/sda2 /mnt/home

---

### Post by weirdtalk on 2010-06-11
the first command is the one from the long list of instructions (should be the first of the mounts). the second (sudo mount /dev/sda? /mnt/home) will be right after that, then resume the rest of the instructions.

---

### Post by mvalenti on 2010-06-12
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# mkdir /media/chroot
root@ubuntu:/home/ubuntu# mount /dev/sda1 /media/chroot
root@ubuntu:/home/ubuntu# mount /dev/sda2 /mnt/home
mount: mount point /mnt/home does not exist
root@ubuntu:/home/ubuntu# mount /dev/sda1 /mnt
root@ubuntu:/home/ubuntu# mount /dev/sda2 /mnt/home
root@ubuntu:/home/ubuntu# mount -o bind /dev /media/chroot/dev
root@ubuntu:/home/ubuntu# mount -o bind /sys /media/chroot/sys
root@ubuntu:/home/ubuntu# mount -o bind /dev/shm /media/chroot/proc
root@ubuntu:/home/ubuntu# chroot /media/chroot
root@ubuntu:/# su mark
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

mark@ubuntu:/$ ecryptfs-mount-privite
No command 'ecryptfs-mount-privite' found, did you mean:
 Command 'ecryptfs-mount-private' from package 'ecryptfs-utils' (main)
ecryptfs-mount-privite: command not found
mark@ubuntu:/$

not sure what i'm doing wrong...

---

### Post by weirdtalk on 2010-06-12
> **mvalenti said:**
> 
root@ubuntu:/home/ubuntu# mount /dev/sda1 /media/chroot
root@ubuntu:/home/ubuntu# mount /dev/sda2 /mnt/home
mount: mount point /mnt/home does not exist

not sure what i'm doing wrong...

One problem is that we are mixing guides. (Another is you misspelled "private" in ecryptfs-mount-private.) We set up the root to /media/chroot and then tried to set /home to /mnt/home (there is no /mnt/home) if we are putting things in /media/chroot we need to continue to put them their so the updated commands would be:

```

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# mkdir /media/chroot
root@ubuntu:/home/ubuntu# mount /dev/sda1 /media/chroot
root@ubuntu:/home/ubuntu# mount /dev/sda2 /media/chroot/home
root@ubuntu:/home/ubuntu# mount -o bind /dev /media/chroot/dev
root@ubuntu:/home/ubuntu# mount -o bind /sys /media/chroot/sys
root@ubuntu:/home/ubuntu# mount -o bind /proc /media/chroot/proc
root@ubuntu:/home/ubuntu# chroot /media/chroot
root@ubuntu:/# su - mark
mark@ubuntu:/$ ecryptfs-mount-private
mark@ubuntu:/$ cd /home/mark
mark@ubuntu:/$ ls

```

---

### Post by mvalenti on 2010-06-14
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# mkdir /media/chroot
root@ubuntu:/home/ubuntu# mount /dev/sda1 /media/chroot
root@ubuntu:/home/ubuntu# mount /dev/sda2 /media/chroot/home
root@ubuntu:/home/ubuntu# mount -o bind /dev /media/chroot/dev
root@ubuntu:/home/ubuntu# mount -o bind /sys /media/chroot/sys
root@ubuntu:/home/ubuntu# mount -o bind /proc /media/chroot/proc
root@ubuntu:/home/ubuntu# chroot /media/chroot
root@ubuntu:/# su - mark
open: Permission denied
Error locking counterTo run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

mark@ubuntu:~$ ecryptfs-mount-private
Enter your login passphrase:
Error: Unwrapping passphrase and inserting into the user session keyring failed [-5]
Info: Check the system log for more information from libecryptfs
ERROR: Your passphrase is incorrect
Enter your login passphrase:
Inserted auth tok with sig [e075a2f0363f678c] into the user session keyring
open: Permission denied
Error locking countermark@ubuntu:~$ ^C
mark@ubuntu:~$ 


tried every password I know...

---

### Post by weirdtalk on 2010-06-14
after doing a fast google I came across [THIS]("https://bugs.launchpad.net/ecryptfs/+bug/573518") which leads leads me to believe that we do need to mount shm so try this set of commands:

```

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# mkdir /media/chroot
root@ubuntu:/home/ubuntu# mount /dev/sda1 /media/chroot
root@ubuntu:/home/ubuntu# mount /dev/sda2 /media/chroot/home
root@ubuntu:/home/ubuntu# mount -o bind /dev /media/chroot/dev
root@ubuntu:/home/ubuntu# mount -o bind /sys /media/chroot/sys
root@ubuntu:/home/ubuntu# mount -o bind /proc /media/chroot/proc
root@ubuntu:/home/ubuntu# mount -o bind /dev/shm /media/chroot/dev/shm
root@ubuntu:/home/ubuntu# chroot /media/chroot
root@ubuntu:/# su - mark
mark@ubuntu:/$ ecryptfs-mount-private
mark@ubuntu:/$ cd /home/mark
mark@ubuntu:/$ ls

```

the difference is the added "mount -o bind /dev/shm /media/chroot/dev/shm"

---

### Post by mvalenti on 2010-06-14
Omfg!!! It worked!!!!!! Thank you soooooooo much!!!!!!

---

### Post by mvalenti on 2010-06-14
Got almost everything copied without a hitch except for .thunderbird and .mozilla (firefox)  says "permission denied"

I am doing this thru the gui...

---

### Post by weirdtalk on 2010-06-14
most likely permissions, right click and set or do a sudo cp thru cli.

---

### Post by mvalenti on 2010-06-15
Much appreciated, I ended up using sudo nautilus... Thanks again for your help!

---

### Post by Ex_Machina on 2011-01-23
> **weirdtalk said:**
> I have tested this method on a vm and it works I will list the step I took for those interested.

I used a ubuntu 10.04 cd, but any live cd/usb should work.

once booted I opened a terminal and ran these commands
```

sudo su
mkdir /media/chroot

```

Then I had to figure out which disk I need to mount (which disk ubuntu is installed on.) You can either use
```
fdisk -l
```
or
```
gparted
```
for me it was on /dev/sda1 so please put you disk in place of sda1 in the following commands.


You saved my box, Thank you.

---

