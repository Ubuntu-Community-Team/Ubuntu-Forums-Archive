---
title: "Activating a Partition"
date: 2011-05-10
forum: General Help
---

### Post by rsnow on 2011-05-10
I hope I am saying this correctly. What I want to do is use a partition other than the one the OS is installed on for my data files. Before I installed 10.10 I set up a separate partition for this purpose and formatted it as ext 4. It shows under Places as a "131GB Filesystem". It contains a folder called "lost+found.

When I try to set up folders/directories to use for data using Ctrl+Shift+n nothing happens. The File menu does not have the option to create new directories. I cannot drag and drop anything onto it. The properties shows root as the owner.

Can someone tell me how to make the partition usable or direct me to where the instructions might be? After going through 400+ pages of a book on using the command line, I haven't found anything to deal with this.

---

### Post by ~Plue on 2011-05-10
Use chown on the mount point (replace 'username' and ' /media/data' accordingly)
```
sudo chown username:  /media/data/
```

---

### Post by MDguy on 2011-05-10
First open a terminal, and run 
```
sudo fdisk -l
```Find the device (/dev/sdX) that corresponds to the partition you created to store data, and then run
```
sudo mount /dev/sd[COLOR=Red]X[/COLOR] /mnt
``` (replace X with the partition number of your data partition).
then run:
```
sudo chown <yourusername> -R /mnt/*
```After doing that, you should be able to go to Places->131GB Filesystem and add/modify files.

---

### Post by rsnow on 2011-05-11
Thanks for the response. I did the following and here are the results.

sudo fdisk -l
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6395    51366813+  83  Linux
/dev/sda2           42631       43778     9212929    5  Extended
/dev/sda3            6396       22339   128070180   83  Linux
/dev/sda5           42631       43778     9212928   82  Linux swap / Solaris

Partition table entries are not in disk order

sudo mount /dev/sda3 /mnt
mount: /dev/sda3 already mounted or /mnt busy
mount: according to mtab, /dev/sda3 is already mounted on /mnt

sudo chown myusername -R /mnt/*

Now, when I right click on the 131 GB Filesystem icon and look at permissions I find the following - The permissions of "bc23afa-7d5d-4c2e-aa69-b790dee82ad5" could not be determined.

So, what I did changed the permissions message from saying the owner is root to the above statement. It looks like it almost worked.

---

### Post by wildmanne39 on 2011-05-11
> **rsnow said:**
> Thanks for the response. I did the following and here are the results.

sudo fdisk -l
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6395    51366813+  83  Linux
/dev/sda2           42631       43778     9212929    5  Extended
/dev/sda3            6396       22339   128070180   83  Linux
/dev/sda5           42631       43778     9212928   82  Linux swap / Solaris

Partition table entries are not in disk order

sudo mount /dev/sda3 /mnt
mount: /dev/sda3 already mounted or /mnt busy
mount: according to mtab, /dev/sda3 is already mounted on /mnt

sudo chown myusername -R /mnt/*

Now, when I right click on the 131 GB Filesystem icon and look at permissions I find the following - The permissions of "bc23afa-7d5d-4c2e-aa69-b790dee82ad5" could not be determined.

So, what I did changed the permissions message from saying the owner is root to the above statement. It looks like it almost worked.

Hi, is one of those partitions the one you are trying to use, or did you set it up on another drive?:D

---

### Post by MDguy on 2011-05-11
now try:
```
sudo chmod a+rw -R /mnt/*
```
Then try to open the "131 GB Filesystem" icon and place a file in it.

---

### Post by oldfred on 2011-05-11
This is how I do it. I make a mount point /mnt/data.

echo $USER
sudo mkdir /mnt/data
sudo chown -R $USER:$USER /mnt/data
sudo chmod -R 766 /mnt/data
sudo blkid
#Edit fstab with your UUID:
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext3         auto,users,rw,relatime               0  2 
#Verify entry is ok, if no errors it is:
sudo mount -a
#from home so default location of link is in $HOME
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music

---

### Post by rsnow on 2011-05-11
MDguy - I did sudo chmod a+rw -R /mnt/* 
then tried to place a text file into 131 GB Filesystem - result below

There was an error copying the file into /media/bc23afa5-7d5d-4c2e-aa69-b790dee82ad5.

---

### Post by rsnow on 2011-05-11
oldfred - If I try your method, should I substitute location bc23afa-7d5d-4c2e-aa69-b790dee82ad5 in place of the a55e6335-616f-4b10-9923-e963559f2b05 shown in your UUID=? 

UUID=a55e6335-616f-4b10-9923-e963559f2b05 /mnt/data ext3 auto,users,rw,relatime 0 2

---

### Post by oldfred on 2011-05-12
Yes it has to be your UUID.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by rsnow on 2011-05-12
oldfred - Success! At least mostly. I read the links you provided and I am beginning to understand a little better about mounting and file systems. I followed your instructions and I can now store data in that partition. However, there are still a couple of mysteries (to me). When I typed  mv Music oldMusic I wound up with oldMusic in my Home folder but there was no Music folder in the other partition. I was able to create a Music folder there and transfer(copy) my music files there. When I check the properties of the partition icon it still says they cannot be determined. I am also wondering if I should be able to change the name of the icon representing the partition? If so, how? Right clicking the icon shows the 'rename' option not active. It is a minor thing but something I would like to do.

Thanks for your help.

---

### Post by oldfred on 2011-05-12
It worked a bit easier for me as I had copied all the folders from an older  /home into /data. So I had Music, Videos, etc  as folders - I now have 13 or 14 folders in /data that I auto mount into /home. But the folder has to exist in /data to be able to link that folder back to /home.

I first used the commands I posted to link each folder. Since I was doing the same for both my desktop & laptop & installing the beta/rc/final several times I found it repetitive. So I just listed history, copied to a bash file and run that for every reinstall.

After doing each folder a few times I found this, one line for all folders:
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
#Or link all with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

I have not found the icon locations, or I found so many I am not sure which ones it uses.

---

### Post by rsnow on 2011-05-13
Well thanks again. I am not going to try and get too deep into things just yet. I have a ton of work to do just getting all my music stuff straightened out so I will concentrate on that for now.

I am quite happy with my setup now and although it has taken me a few years I am getting more comfortable with Linux(Ubuntu) each day.

---

