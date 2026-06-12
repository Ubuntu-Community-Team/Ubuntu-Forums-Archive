---
title: "issue with tar.gz file"
date: 2010-04-26
forum: General Help
---

### Post by stek_87 on 2010-04-26
Hi!

I am having an issue with a tar.gz archive that I have created myself.

The archive is containing some very large files. (actually it is 3 virtual machines in it)

First I stopped the virtual machines, then i created the archive
sudo tar -xzvf tarfile.tar.gz ./*
(I was standing in the folder where the directories for the virtual machines was).
The tar.gz was 110GB when finished, Everything seemed OK.

Afterwords I sent the file to windows with FTP in binary mode. In windows I tested the archive with 7-zip and it was OK.

Now I have tranfered the file back to linux (also binary mode) and I am extracting the files. Here is the issue.. The first VM got out just fine, the second is still running, at the moment One of the big files in there is 700GB in size (still growing), and it was about 200GB before..(!!)

What is wrong?
Should I just wait and see how big it is going to be? And if it will continue to unpack the 3rd machine afterwords?
(this file is a diskfile that is 2TB inside the vm OS, but it is stored in "thin format" so it has not get that big jet. I'm still concerned that this archive is corrupt some how..

The total uncompressed size was about 300gb for all data before I compressed it.

any one got a clue?

rgds

---

### Post by john newbuntu on 2010-04-26
```
tar -tvf tarfile.tar.gz 
```
should list the individual file sizes in the tarfile.
If it fails or does not finish, try extracting one file at a time from the .gz file.

---

### Post by stek_87 on 2010-04-26
> **john newbuntu said:**
> ```
tar -tvf tarfile.tar.gz 
```
should list the individual file sizes in the tarfile.
If it fails or does not finish, try extracting one file at a time from the .gz file.

thank you for taking time!

I have tried this, but it takes long time (i pressed ctrl+c after ~5 minuses..) How long time should it take to list all ontent of 110GB tar.gz file?
I guess I will try this soon. The file is now over 1TB in size (extracted from the tar.gz). Feels like it loops or something.. Just writing more and more data.. :(
I find it hard to extract one fome at time also, because I do not have the filenames..

---

### Post by colorlessprism on 2010-04-26
im wondering did you forget to comment out the backup itself --exclude=/path/to/backup. is it an option to delete the tarfile and start over? below is an example of my tar script for /home. i use bzip2 to compress my backup instead of gzip. Bzip2 provides a higher compression ratio at the expense of speed. note how you can just substitute the "z" in your command with "j", and change the file name to *.tar.bz2*. really its a matter of preference and with the size your talking about i would stay with gzip. here is my backup script:

tar -cvpjf home`date +"%a%b%d%Y"`.tar.bz2 --exclude=/home/tb64/home`date +"%a%b%d%Y"`.tar.bz2 --exclude=/home/tb64/Documents --exclude=/home/tb64/Music --exclude=/home/tb64/Pictures --exclude=/home/tb64/Videos --exclude=/home/tb64/.wine /home/tb64

To understand what is going on 

**tar** - is the command that creates the archive. It is modified by each letter immediately following, each is explained bellow. 
**`date +"%a%b%d%Y"`**- will insert the current date into the filename
**c** - create a new backup archive. 
**v** - verbose mode, tar will print what it's doing to the screen. 
**p** - preserves the permissions of the files put in the archive for restoration later. 
**j** - compress the backup file with 'bz2' to make it smaller. 
**f <filename>** - specifies where to store the backup, *backup.tar.gz* is the filename used in this example. It will be stored in the current working directory, the one you set when you used the cd command. 
**--exclude=/example/path** - The options following this model instruct tar what directories **NOT** to backup.

---

### Post by john newbuntu on 2010-04-26
Yeah "tar -tvf" should be real quick.  I doubt if some recursion happened as colorlessprism indicated.

---

### Post by stek_87 on 2010-04-26
Yes, that might be the problem!

I was standing in the folder where I created the archive, and typed in: sudo tar -czvf archive.tar.gz ./*

(because I wanted to archive all folders in that folder..)

so.. how do I recover from this??
Can I use the exclude option while decompressing?

I only have this tar.gz file to rely on.. =/

---

### Post by stek_87 on 2010-04-26
> **john newbuntu said:**
> Yeah "tar -tvf" should be real quick.  I doubt if some recursion happened as colorlessprism indicated.

Ok.. So you do not think there is a problem with my command line when creating the archive?

---

### Post by stek_87 on 2010-04-26
The file that should be about 200GB in size is now over 1 TB in size.


Is there any point of waiting for the command to finish, or should I interrupt it?

---

### Post by stek_87 on 2010-04-26
```
user1@server1:/folder1/archive1$ cat content.txt
drwxr-xr-x nobody/nogroup    0 2010-04-25 10:38 ./vm1/
-rwxr-xr-x nobody/nogroup 3364 2010-04-25 10:38 ./vm1/vm1.vmx
-rw------- nobody/nogroup  262 2010-04-25 10:38 ./vm1/vm1.vmxf
-rw------- nobody/nogroup    0 2010-04-01 19:59 ./vm1/vm1.vmsd
-rw------- nobody/nogroup 32227695616 2010-04-25 10:37 ./vm1/vm1-flat.vmdk
-rw------- nobody/nogroup         571 2010-04-14 16:24 ./vm1/vm1.vmdk
-rw------- nobody/nogroup        8684 2010-04-25 10:38 ./vm1/vm1.nvram
-rw------- nobody/nogroup  2563957922 2010-04-25 10:38 ./vm1/vm1-0632a67f.vmss
-rw-r--r-- nobody/nogroup       88185 2010-04-08 07:04 ./vm1/vmware-1.log
-rw-r--r-- nobody/nogroup      152777 2010-04-25 10:38 ./vm1/vmware.log
drwxr-xr-x nobody/nogroup           0 2010-04-25 10:35 ./vm2/
-rw------- nobody/nogroup 2147483648000 2010-04-25 01:45 ./vm2/vm2-flat.vmdk
user1@server1:/folder1/archive1$ jobs
[1]+  Stopped                 sudo zcat archive1.tgz | sudo tar xvf -
[2]-  Running                 sudo tar -tvf archive1.tgz > content.txt &
user1@server1:/folder1/archive1$
```

Think I see light in the end of the tunnel.. It seems like the archive is not corrupted, only the filesizes has been messed up.
interesting is that filesize of vm2-flat.vmdk is the size of the virtual disk presented to this vm. Even tho the actual file before compression was about 200GB.

strange?

---

### Post by john newbuntu on 2010-04-26
I came across this blog that mentions that as you move the vmdk's across different block sizes, even the thinly provisioned ones become thick.  I am fairly new to vmwares and not aware of these issues.  You could try other methods mentioned.

[http://blog.tech4him.com/2010/03/esxi-4-moving-vms-to-new-storage/](http://blog.tech4him.com/2010/03/esxi-4-moving-vms-to-new-storage/)

---

### Post by stek_87 on 2010-04-26
Thank you for your reply!
I'm just happy to know that my archive is not corrupted.. Now I will have to wait a couple of years to unzip a 2TB file from a 110GB tar.gz file :P

rgds

---

