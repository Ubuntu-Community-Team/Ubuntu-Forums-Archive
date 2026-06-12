---
title: "Can't write to my 2nd and 3rd HD?"
date: 2010-05-20
forum: General Help
---

### Post by tahitiwibble on 2010-05-20
Hi guys,

I have just installed 10.04 onto a brand new HD and cannot access my old drives for lack of permission. I've tried various "sudo chmod 777" combinations to no avail.

Thanks many if you can help me out of this fix.

---

### Post by Crafty Kisses on 2010-05-21
Can I please see the results of?
```
fdisk -l
```

---

### Post by tahitiwibble on 2010-05-21
> **Crafty Kisses said:**
> Can I please see the results of?
```
fdisk -l
```

Oh dear, I don't get any response from the terminal at all with "fdisk -l" :confused:

---

### Post by Sef on 2010-05-21
> Quote:
 	 	 		 			 				 					Originally Posted by **Crafty Kisses** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9335489#post9335489") 				
 				[I]Can I please see the results of?
 	Code:
 	fdisk -l 
[/I]
 			 		 	 	 
Oh dear, I don't get any response from the terminal at all with  "fdisk -l" :confused:

The command is incorrect.   Copy and paste this command:
```

sudo fdisk -l
```

then copy and paste the results here.

---

### Post by nhasian on 2010-05-21
during installation of ubuntu you can specify where to mount the other drives.  i like to mount my secondary drive /dev/sdb1 as /data

my /etc/fstab says:
```

# /data was on /dev/sdb1 during installation
UUID=c1e8abe9-1230-42c1-b125-9015354d0371 /data           ext4    defaults      
```

don't forget to make the directory that your mounting the drive to in a terminal with the command:

```
sudo mkdir /data
```

if you didn't have your other drives connected during the installation of ubuntu you can manually edit your /etc/fstab and add it like mine but change to your UUID.

then once your in ubuntu and can see the directories, all you need to do is change the permissions using the easy gui way by pressing Alt-F2 and entering:

```
gksu nautilus
```

now you can change the owner and group to your username to get access to your data.

---

### Post by ayenack on 2010-05-21
```
sudo mkdir /dev/sda2/drop_box
``` (Where /dev/sda2 is the path to the drive and /drop_box is the name of the folder created.)

Then.

```
sudo chown your_username_here:your_username_here /dev/sda2/drop_box
```

And you should be able to write the folder created.

mkdir = Make Directory (The folder created.)
chown = Change Owner/Ownership (And changing ownership of it.)

---

### Post by tahitiwibble on 2010-05-21
> **Sef said:**
> The command is incorrect.   Copy and paste this command:
```

sudo fdisk -l
```

then copy and paste the results here.

Hello Sef,

Thanks for helping out and for sorting the double thread dilemma.

sda & sdb are the HD's I want to write to.

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc535b5b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2557    20539071   83  Linux
/dev/sda2            9542        9729     1510079+   5  Extended
/dev/sda3            2558        9541    56098980   83  Linux
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux
/dev/sdb2           30402       60801   244188000   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004207c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2554    20514973+  83  Linux
/dev/sdc2            2555       31678   233938530   83  Linux
/dev/sdc3           31679       60801   233930497+  83  Linux
dad@dad-desktop:~$
```

---

### Post by tahitiwibble on 2010-05-21
> **nhasian said:**
> during installation of ubuntu you can specify where to mount the other drives.  i like to mount my secondary drive /dev/sdb1 as /data

my /etc/fstab says:
```

# /data was on /dev/sdb1 during installation
UUID=c1e8abe9-1230-42c1-b125-9015354d0371 /data           ext4    defaults      
```

don't forget to make the directory that your mounting the drive to in a terminal with the command:

```
sudo mkdir /data
```

if you didn't have your other drives connected during the installation of ubuntu you can manually edit your /etc/fstab and add it like mine but change to your UUID.

then once your in ubuntu and can see the directories, all you need to do is change the permissions using the easy gui way by pressing Alt-F2 and entering:

```
gksu nautilus
```

now you can change the owner and group to your username to get access to your data.

Hi nhasian,

Sorry but all that is just a little too technical for my old brain. I wanted to use the whole drives, do you still have to create the directories as you described?

---

### Post by tahitiwibble on 2010-05-21
> **ayenack said:**
> ```
sudo mkdir /dev/sda2/drop_box
``` (Where /dev/sda2 is the path to the drive and /drop_box is the name of the folder created.)

Then.

```
sudo chown your_username_here:your_username_here /dev/sda2/drop_box
```

And you should be able to write the folder created.

mkdir = Make Directory (The folder created.)
chown = Change Owner/Ownership (And changing ownership of it.)

Hi there ayenack,

I tried to use chown on the drives' /dev/sd?? to no avail. Is the mkdir essential?

---

### Post by ayenack on 2010-05-22
It's best to create a folder on the drive. It'll give you as much space as the free space on the drive so you won't lose any space.

So to do this on drive /dev/sdc1 you'd do this.

```
sudo mkdir /dev/sdc1/drop_box
```

Then this.

```
sudo chown your_username_here:your_username_here /dev/sdc1/drop_box
```

Once you have done that you can right click on the folder you created and allow read/write access to other users by clicking on the Permissions tab. To make sure the changes have taken place log out then in to your account.

Just for some background and to give you a bit more of an understanding of permissions and what not take a look at this.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Also here for changing whole drive and more.

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131) (Be careful though as it's possible to mess up your system and the post is old.)

looks a bit complicated but worth reading through.

---

### Post by tahitiwibble on 2010-05-22
Hi ayenack,

Thank you for the help, I'm grateful to you. Unfortunately as you will see below (or anyone else that might lend a badly needed hand), I didn't get too far. And haven't a clue as to why.
```

dad@dad-desktop:~$ sudo makdir /dev/sdb1/dodgey_partition_1
[sudo] password for dad: 
sudo: makdir: command not found
dad@dad-desktop:~$ sudo mkdir /dev/sdb1/dodgey_partition_1
mkdir: cannot create directory `/dev/sdb1/dodgey_partition_1': Not a directory
dad@dad-desktop:~$ sudo mkdir /dev/sdb1/dodgey_partition_a
mkdir: cannot create directory `/dev/sdb1/dodgey_partition_a': Not a directory
dad@dad-desktop:~$ sudo mkdir /dev/sdb1/dodgey_a
mkdir: cannot create directory `/dev/sdb1/dodgey_a': Not a directory
dad@dad-desktop:~$
```

---

### Post by ayenack on 2010-05-23
I did a typo it should be

mkdir

But I see you must have looked at my earlier post or worked that out for yourself.

It has to be on a directory that exists so make sure that you have the path right. Not to sure what other advice to I can offer because it should work.

---

### Post by ayenack on 2010-05-23
tahitiwibble can you do me a favour and go to Places>Computer and let me know what's listed there?

---

### Post by nhasian on 2010-05-23
no problem, its actually not that hard.  you didnt mention if you had your drives attached or not when you installed Ubuntu?

Please give me the output of the following commands so i can finish helping you mount your drives:

```
cat /etc/fstab
```
```
sudo blkid
``` 

and to answer your question, if you didn't specify where you wanted the drives mounted during installation, then yes you will need to create the directories.  Dont think of the drives as drive letters like in windows.  Think of your entire computer like a tree with branches instead.  You have your root folder which is /.  everything builds off of that.  your drives are in /dev/sda, /dev/sdb, and /dev/sdc.  if your drives have multiple partitions, then its /dev/sda1, /dev/sda2, etc.  So you have Ubuntu installed on your primary partition /dev/sda1.  now you have to tell linux where you want the other two drives to be mounted so you can access your data.  that's why you have to create two directories.  You can mount them as /videos and /music or /500G1, /500G2 or however you like to name them.

> **tahitiwibble said:**
> Hi nhasian,

Sorry but all that is just a little too technical for my old brain. I wanted to use the whole drives, do you still have to create the directories as you described?

---

### Post by oldfred on 2010-05-23
I think you are mixing mkdir with mount:

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

$ sudo mkdir /Data
$ sudo mount /dev/sda5 /Data
where sda5 needs to be your drive, partition
if not known to list partitions
sudo fdisk -l

If you cannot read and write then change the permissions.

$ sudo chmod -R 777 /Data
sudo chown -R fred:fred /Data
where fred should be your login name

---

### Post by tahitiwibble on 2010-05-23
> **ayenack said:**
> tahitiwibble can you do me a favour and go to Places>Computer and let me know what's listed there?

Of course :)

[IMG]http://i221.photobucket.com/albums/dd79/wibble_01/Screenshot-ComputerFileBrowser.png[/IMG]

The 2 80 GB HD partitions are my old 9.10 files, the 2 "Dodgey" partitions are on an old HD that a friend gave to me and the "Storage" partition is on the same brand new 500 gig hard drive that houses my lovely new 10.04 system where /home is pointed to and which is my data storage partition for a 10.04/W7 pro dual boot..

---

### Post by tahitiwibble on 2010-05-23
> **nhasian said:**
> no problem, its actually not that hard.  you didnt mention if you had your drives attached or not when you installed Ubuntu?

Please give me the output of the following commands so i can finish helping you mount your drives:

```
cat /etc/fstab
```
```
sudo blkid
``` 

and to answer your question, if you didn't specify where you wanted the drives mounted during installation, then yes you will need to create the directories.  Dont think of the drives as drive letters like in windows.  Think of your entire computer like a tree with branches instead.  You have your root folder which is /.  everything builds off of that.  your drives are in /dev/sda, /dev/sdb, and /dev/sdc.  if your drives have multiple partitions, then its /dev/sda1, /dev/sda2, etc.  So you have Ubuntu installed on your primary partition /dev/sda1.  now you have to tell linux where you want the other two drives to be mounted so you can access your data.  that's why you have to create two directories.  You can mount them as /videos and /music or /500G1, /500G2 or however you like to name them.

I didn't have the other 2 HD's connected when I installed 10.04.


```
dad@dad-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=521e6dba-cf48-4cca-bc6f-71f7e9a21211 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=4e8d8d22-63c7-492f-bc4c-f7a6040bdb79 /home           ext4    defaults        0       2
dad@dad-desktop:~$ 
```

& 

```
dad@dad-desktop:~$ sudo blkid
[sudo] password for dad: 
/dev/sda1: LABEL="Dodgey_HD_1" UUID="0ebc3015-081f-4eed-a04b-089011a4a035" TYPE="ext4" 
/dev/sda2: LABEL="Dodgey_HD_2" UUID="4473e068-102d-48c2-a99f-141999530aa8" TYPE="ext4" 
/dev/sdb1: UUID="521e6dba-cf48-4cca-bc6f-71f7e9a21211" TYPE="ext4" 
/dev/sdb2: UUID="4e8d8d22-63c7-492f-bc4c-f7a6040bdb79" TYPE="ext4" 
/dev/sdb3: LABEL="Storage" UUID="9fb6d50b-499a-4400-bd79-84f136972e09" TYPE="ext4" 
/dev/sdc1: UUID="36f47d0b-6169-45c3-af37-953a2124ae82" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc3: UUID="6baa9a9b-a9e7-4008-aa2d-ba5bb7ce5c28" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="942f7cc7-ea3a-42b2-9a57-f78e586a5cb1" TYPE="swap" 
dad@dad-desktop:~$
```

---

### Post by tahitiwibble on 2010-05-23
> **oldfred said:**
> I think you are mixing mkdir with mount:

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

$ sudo mkdir /Data
$ sudo mount /dev/sda5 /Data
where sda5 needs to be your drive, partition
if not known to list partitions
sudo fdisk -l

If you cannot read and write then change the permissions.

$ sudo chmod -R 777 /Data
sudo chown -R fred:fred /Data
where fred should be your login name

Hey Chick-car-go, thanks for chipping in. I am trying to figure out what you say there. Gimme at least 5 :)

---

### Post by tahitiwibble on 2010-05-23
Some might consider this a waste of a post, but I just wanted to say a **BIG** _thanks_ to you guys. There was a time when my brain could have handled all this OK on it's own, but when you get older things tend to change a bit.

---

### Post by tahitiwibble on 2010-05-26
I'm still lost with this one. :confused: Could someone help me figure things out?

---

### Post by oldfred on 2010-05-26
If you want to permanently mount it you need to edit fstab. You should read the next two links to understand a little about the settings>

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

then you can use this which mostly automates mounting but some of the settings need to be understood.

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)

---

### Post by tahitiwibble on 2010-05-26
Oldfred,

The thing is that even when they're mounted (I can see the HD's in my "Places" menu, and suppose that they mount when I double click on them), I still can't write to them. I have tried to change the permissions as described in my previous posts but that doesn't change things. When I look at permissions for the HD's after I've mounted them to desktop I get the message that 'permissions could not be determined' 

Over to you Squire :)

---

### Post by colin.p on 2010-05-26
You've probably tried this already, but I had the same problem with an internal 250GB disk that I formatted from NTFS to ext4. I followed the thread about using Pysdm (link in previous post to yours) and still got the permissions error until I got to post #22 and tried this, substituting my info, of course:
To fix permission problems:

Code:

sudo chown -R USERNAME:USERNAME /media/MyData
sudo chmod -R 755 /media/MyData

where USERNAME is the name of the user ( as seen in /home/USERNAME )

in my case it was : 

sudo chown -R colin:colin /media/Archive
sudo chmod -R 755 /media/Archive

That fixed it for me once and for all.

Colin

---

### Post by tahitiwibble on 2010-05-26
> **colin.p said:**
> You've probably tried this already, but I had the same problem with an internal 250GB disk that I formatted from NTFS to ext4. I followed the thread about using Pysdm (link in previous post to yours) and still got the permissions error until I got to post #22 and tried this, substituting my info, of course:
To fix permission problems:

Code:

sudo chown -R USERNAME:USERNAME /media/MyData
sudo chmod -R 755 /media/MyData

where USERNAME is the name of the user ( as seen in /home/USERNAME )

in my case it was : 

sudo chown -R colin:colin /media/Archive
sudo chmod -R 755 /media/Archive

That fixed it for me once and for all.

Colin

Hello Colin,

Thanks for the suggestion. I just looked in my "media" folder and the internal HD's only appear after manually mounting them. Should they appear in the folder all the time? or should I mount them and then do "sudo chown" etc?

** edit ** I just read post 22 and will read again,digest and try it out later, I'm optimistic! Thanks Colin. I'll let you know if it works.

---

### Post by colin.p on 2010-05-26
I followed the post I was referring to,the drive was already mounted. I  could see it clearly, but I could not do anything to it. That's when I ran the code that I saw in post 22. Immediately, I was able to write to the drive and after a reboot, just to make sure it auto-mounted, I still could write to it.
I noticed that some tell you to do a "sudo chmod -R 777 /Data", but I did a
"sudo chmod -R 755 /media/Archive", where "media/Archive" is my drive.
Also, I think I read somewhere that the label of secondary hd's are preceded by "/media/".
I know it's somewhat confusing, I'm starting to get a headache myself.

Colin

---

### Post by oldfred on 2010-05-26
As I had in my previous post. IF they are NTFS they do not support linux permissions and ownership, so the only time you set anything on windows partitions is as you mount them. The automount now does not seen to give full rights, so with NTFS you cannot change and are stuck. It really is best to mount via fstab with proper permissions up front.

this is my setting, It has to be your UUID and whatever mount you have created, otherwise it is relatively simple.
```
# Entry for /dev/sda2 :
UUID=2A87EC53669130A9                      /home/fred/shared  ntfs-3g      defaults                             0  0  
```

---

### Post by tahitiwibble on 2010-05-28
> **colin.p said:**
> I followed the post I was referring to,the drive was already mounted. I  could see it clearly, but I could not do anything to it. That's when I ran the code that I saw in post 22. Immediately, I was able to write to the drive and after a reboot, just to make sure it auto-mounted, I still could write to it.
I noticed that some tell you to do a "sudo chmod -R 777 /Data", but I did a
"sudo chmod -R 755 /media/Archive", where "media/Archive" is my drive.
Also, I think I read somewhere that the label of secondary hd's are preceded by "/media/".
I know it's somewhat confusing, I'm starting to get a headache myself.

Colin

It took me a while to get round to it for various reasons (not least of all the fact that this looked to be a daunting task).

EUREKA .......... Colin, you're a blooming genius! a gentleman and a scholar and I'm very grateful to you because it worked like a charm!

I don't know why or how, but it did ...... thanks mate :)

---

### Post by colin.p on 2010-05-28
No worries, glad I could be of some small assistance, even though I had just followed directions that someone had themselves followed.

Colin

---

