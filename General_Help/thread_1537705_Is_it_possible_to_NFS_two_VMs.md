---
title: "Is it possible to NFS two VMs?"
date: 2010-07-24
forum: General Help
---

### Post by nesgodawg on 2010-07-24
Is it possible to NFS two VMs together?

I'm just stuck and have no server in which I can use to mount a drive via NFS and I'd like to give it try, but not able to with my current set up. So if you could guide me as to how to properly do it from scratch that'd be great.

I followed these steps:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by renkinjutsu on 2010-07-24
Yes, it is possible to mount NFS shares in VM OR use your VM's as NFS servers as your VM's would also be assigned IP addresses too.. both are do-able. Also, NFS is fairly easy to setup. Install the NFS packages.

After installing the NFS packages, you should have a file called exports:
```
/etc/exports
```

As root, open up the text file```
gksu gedit /etc/exports
Or you can use vim or nano.. whichever text editor you like
```

There should be examples in the exports file telling you how to share (export) your folders

---

### Post by nesgodawg on 2010-07-24
I'm a complete noob, so here is what it's in my /etc/exports/ folder

> # /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
# /files 192.168.159.0/24(rw,no_root_squash,asynch)


I added the last line.

---

### Post by renkinjutsu on 2010-07-24
First of all, you have a # in the beginning of your line. What that character tells the shell is "Ignore everything after this character on this line" so none of the stuff is actually parsed. So remove the # character from the line that you added.

Also, i'm suspicious about the location of your files folder. People usually do not put folders onto the root filesystem.

The / in the very beginning of a path means "root". Imagine that you're in a folder, and you keep backing out of folders until you're no longer in a folder, you are now in the root filesystem

do this```
ls /files
```to see if the path to your folder is correct.

---

### Post by nesgodawg on 2010-07-24
First of all, thank you so much for helping me out with this.

I took out the # in front of the line and saved it.

I also ran 

> ls /files

and nothing came back. I think I was taking the tutorial too literal. What would you recommend? 

I also got this:

> mount.nfs: mount system call failed
 

When I tried to mount. Thought I feel that is to be expected.

---

### Post by renkinjutsu on 2010-07-24
When you typed in ```
ls /files
```
It was empty because there was a folder at root that had nothing in it. If you didn't have a folder there, it would say something along the lines of "File or directory not found"

The / filesystem is generally not somewhere you want to have your shared files because i think by default, Ubuntu partitions the drive so that / has less storage space. It's a good idea to move the folder /files to /home/files using:```
mv /files /home
``` or rename it to something else AND move it to the /home directory; example: ```
mv /files /home/shared
```

right now, the folder is owned by the user "root" which is essentially the admin user of the system. If you type into the terminal ```
ls -ld /home/files
(or ls -ld /home/shared if you ended up renaming the folder)
```
you will probably see something containing "root:root". That means it's owned by the user root and belongs to group root.

Since the folder is owned by root, you, as a regular user will not be able to put files into there without first typing in a password for 'sudo' all the time in the terminal, which is annoying. So do this:```
sudo chown yourusername:yourusername /home/files (or whatever you renamed it to)
```


substitute yourusername for your own username. If you're unsure about what your username is, you can type ```
whoami
```
into the terminal..

You can also do something like:```
chown $(whoami):$(whoami) /home/blahblahblahh...
```

Now, remember to reflect the change in your /etc/exports file
change /files to whatever it is now ( /home/shared (?))

Now, for NFS to re-export everything in the /etc/exports file```
sudo exportfs -r
```

---

### Post by nesgodawg on 2010-07-24
> kevin@kevin-desktop:/$ sudo exportfs -r
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.159.0/24:/home/shared".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x


Should I try to remount now or what does this mean?

> kevin@kevin-desktop:/$ sudo mount 192.168.159.144:/home/shared home/shared
mount.nfs: mount system call failed


---

### Post by nesgodawg on 2010-07-24
Continued playing around and still can't get it to work properly.

---

### Post by drdos2006 on 2010-07-24
I did a search on 'HOWTO' + 'NFS' and came up with this.
[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)

Here is a copy of my /etc/exports file.
/////////////
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/media/sdb1/sdb1-sharedfiles	192.168.0.2/24(async,no_root_squash,rw)
/media/sdc1/sdc1-sharedfiles	192.168.0.2/24(async,no_root_squash,rw)
/media/sdd1/sdd1-sharedfiles	192.168.0.2/24(async,no_root_squash,rw)
//////////////////
I can now mount these harddrives on my destop by running this script form my machine and log directly onto the external harddrives. (Like Windows has with drive mapping ).
////////////////////////////////////
# !/bin/bash
# Must install server and client NFS programs first
sudo mkdir /media/sdb1-sharedfiles
sudo mkdir /media/sdc1-sharedfiles
sudo mkdir /media/sdd1-sharedfiles

sudo mount 192.168.0.111:/media/sdb1/sdb1-sharedfiles  /media/sdb1-sharedfiles
sudo mount 192.168.0.111:/media/sdc1/sdc1-sharedfiles  /media/sdc1-sharedfiles
sudo mount 192.168.0.111:/media/sdd1/sdd1-sharedfiles  /media/sdd1-sharedfiles
///////////////////////////////
I called the script MountServerShares.sh and run it from the terminal with:
sudo bash /home/MountServerShares.sh

regards

---

### Post by nesgodawg on 2010-07-24
Another attempt: another fail

> kevin@kevin-desktop:/$ sudo vim /etc/exports
[sudo] password for kevin: 
kevin@kevin-desktop:/$ sudo mkdir /media/sdb1-sharedfiles
kevin@kevin-desktop:/$ sudo mkdir /media/sdc1-sharedfiles
kevin@kevin-desktop:/$ sudo mkdir /media/sdd1-sharedfiles
kevin@kevin-desktop:/$ sudo mount 192.168.0.111:/media/sdb1/sdb1-sharedfiles /media/sdb1-sharedfiles
mount.nfs: mount system call failed
kevin@kevin-desktop:/$ sudo mount 192.168.159.144:/media/sdb1/sdb1-sharedfiles /media/sdb1-sharedfiles
mount.nfs: mount system call failed


---

### Post by drdos2006 on 2010-07-24
Were you able to install the Server Side files on one VM as per the the HOWTO ?

regards

---

### Post by nesgodawg on 2010-07-25
What are the server sides? I think I'm missing those?

---

### Post by drdos2006 on 2010-07-25
One machine needs to be the server, the other machine needs to be the client. 
Go through the HOWTO link I supplied.
I have just backed up all my files using the HOWTO and copied to my DVD backups using it. All from my machine.

regards

---

### Post by drdos2006 on 2010-07-25
I did some tests for you and it appears that one of your VM needs to be a server, the second VM a client.
regards

---

### Post by nesgodawg on 2010-07-25
Would I use samba for that or should I got with creating an ESXi server? If that is the case, I do have a ESXi server set up.

---

### Post by drdos2006 on 2010-07-25
It appears to me that Samba on both VMs would allow you to access shared on each VM and is probably the easier path to follow.
Just install Samba on each VM and share the folders.

regards

---

### Post by nesgodawg on 2010-07-25
But wouldn't this take it into CIFS territory over NFS?

---

### Post by drdos2006 on 2010-07-25
Then just follow the HOWTO link I gave and install the server side files on the ESX server and the client files on your second machine.

regards

---

### Post by nesgodawg on 2010-07-25
step by step with logistical modification to work on my system. Still no go.

---

### Post by renkinjutsu on 2010-07-26
please post your exports file (with the CODE tags). We'll have a look over it

---

### Post by nesgodawg on 2010-07-28
Here you go:

> # /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
/shared/music 192.168.1.0/24(rw,no_root_squash,async) 

---

### Post by nesgodawg on 2010-07-31
Did I miss something? What else do you guys need from me?

---

