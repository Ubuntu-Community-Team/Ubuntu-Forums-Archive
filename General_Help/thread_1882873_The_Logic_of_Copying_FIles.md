---
title: "The Logic of Copying FIles"
date: 2011-11-18
forum: General Help
---

### Post by katya_sehgal on 2011-11-18
I am unable to copy files between folders in Ubuntu. I downloaded a software onto 'Downloads' and would like to copy this folder to partition I had created. This partition is located at /media.

I read forums on 'chown' and nautilus but was unable to move the folder. Also, is it not possible to move it the regular way. I realise that I can move the folder to documents and even music, which fall under 'Computer'. 

But I cannot move anything to the partition drives under 'Devices'. I get a permission error.

 > There was an error copying the file into /media/0bc7f324-047c-4b72-a7f2-fa81cf6bf300.

Under Show More Details,

> Error opening file '/media/0bc7f324-047c-4b72-a7f2-fa81cf6bf300/Celtx-2.9.1.tar.bz2': Permission denied

Possibilities?

---

### Post by katya_sehgal on 2011-11-18
I am hoping to get a quick reply, so I know it has nothing to do with the partitions I created. 
How do I copy?

---

### Post by mick222 on 2011-11-18
To move the file simply pres alt +F2 in the box that appears type
 gksu nautilus 
type your password then you should be able to drag and drop the file.
Can you access the files already on this partition.

---

### Post by katya_sehgal on 2011-11-18
I am hoping to get a quick reply, so I know it has nothing to do with the partitions I created. 
How do I copy?

---

### Post by katya_sehgal on 2011-11-18
> **mick222 said:**
> To move the file simply pres alt +F2 in the box that appears type
 gksu nautilus 
type your password then you should be able to drag and drop the file.
Can you access the files already on this partition.

I can't access the downloads folder in this mode. I get Home - Desktop only.

---

### Post by Orange_and_Green on 2011-11-18
The command mick222 gave you will let you open a file browser window as the user "root" (think "Administrator"). So what you see is root's Desktop (/root/Desktop).

To find your own home directory, you will have to navigate up the hierarchy twice (first up from /root/Desktop to /root, and then up from /root to /) and then enter the directory "home", and then again the one that matches your username (so if your user is "katya", that would be again / -> /home -> /home/katya). This will lead you to your own home dir and from there you can copy/move files with root (administrator) privileges as long as you keep the nautilus window open.


EDIT: the exact way to navigate "up" in nautilus may also depend on the particular version you are using. If you still have problems, please also specify which Ubuntu version and flavour you are using.

Also please note that the files you are moving will keep their permission settings also in the destination directory. To be able to read/modify them, you will have to set according permissions with chmod and such. Please ask again if you need help on that as well.

---

### Post by carranty on 2011-11-18
> **katya_sehgal said:**
> I can't access the downloads folder in this mode. I get Home - Desktop only.

To get access to your Downloads folder do as mike222 suggests.  This will open nautilus in root's home folder, you need to click 'File System' from the left hand menu (if there isn't a left hand menu press F9), then click on 'home', then the folder named after your user name, then 'Downloads'.  For example on my computer if would be

File System > home > carranty > Downloads

---

### Post by mick222 on 2011-11-18
> **katya_sehgal said:**
> I can't access the downloads folder in this mode. I get Home - Desktop only.
It starts at Home/Desktop click on file system then the home folder then your user name Downloads should be there .
Make sure the partition you are trying to move the file to is mounted look  in disc utility

---

### Post by katya_sehgal on 2011-11-18
Thank you. Is this the normal way to copy files from "Computer" to "Devices"; devices being the partitions I have created?

If not, where am I going wrong?


> **mick222 said:**
> To move the file simply pres alt +F2 in the box that appears type
 gksu nautilus 
type your password then you should be able to drag and drop the file.
Can you access the files already on this partition.

> **Orange_and_Green said:**
> The command mick222 gave you will let you open a file browser window as the user "root" (think "Administrator"). So what you see is root's Desktop (/root/Desktop).

To find your own home directory, you will have to navigate up the hierarchy twice (first up from /root/Desktop to /root, and then up from /root to /) and then enter the directory "home", and then again the one that matches your username (so if your user is "katya", that would be again / -> /home -> /home/katya). This will lead you to your own home dir and from there you can copy/move files with root (administrator) privileges as long as you keep the nautilus window open.


EDIT: the exact way to navigate "up" in nautilus may also depend on the particular version you are using. If you still have problems, please also specify which Ubuntu version and flavour you are using.

Also please note that the files you are moving will keep their permission settings also in the destination directory. To be able to read/modify them, you will have to set according permissions with chmod and such. Please ask again if you need help on that as well.

> **carranty said:**
> To get access to your Downloads folder do as mike222 suggests.  This will open nautilus in root's home folder, you need to click 'File System' from the left hand menu (if there isn't a left hand menu press F9), then click on 'home', then the folder named after your user name, then 'Downloads'.  For example on my computer if would be

File System > home > carranty > Downloads

> **mick222 said:**
> It starts at Home/Desktop click on file system then the home folder then your user name Downloads should be there .
Make sure the partition you are trying to move the file to is mounted look  in disc utility

---

### Post by Orange_and_Green on 2011-11-18
I think the "normal way" would be to define the partitions in /etc/fstab with user access, or alternatively create (with the gksu nautilus window) a directory in the partition, right-click, select "Properties", and change the access options so that your user owns it. Then you do not need gksu nautilus to read/write, just your normal file browser.

---

### Post by carranty on 2011-11-18
> **katya_sehgal said:**
> Thank you. Is this the normal way to copy files from "Computer" to "Devices"; devices being the partitions I have created?

If not, where am I going wrong?

There are many different ways of copying files in Linux, I'd say the "normal" way is just whichever method you find easiest.

---

### Post by katya_sehgal on 2011-11-18
> **Orange_and_Green said:**
> I think the "normal way" would be to define the partitions in /etc/fstab with user access, or alternatively create (with the gksu nautilus window) a directory in the partition, right-click, select "Properties", and change the access options so that your user owns it. Then you do not need gksu nautilus to read/write, just your normal file browser.

I got a bit about fstab from links like these.

```
http://knowledgelayer.softlayer.com/questions/194/What+is+the+%7B47%7Detc%7B47%7Dfstab+file%3F
```

I would like to use he normal file browser - as you call it. How do I change the settings? Otherwise I will have to use nautilus every time.

---

### Post by Orange_and_Green on 2011-11-18
Just to clarify - nautilus *is* what I call the "normal file browser". When you click, for example, on a folder on your desktop, or on the "Home" icon, you open a new nautilus window browsing that particular location.

The command "gksu nautilus" opens a window for just the same program, but with root privileges. This window can access also those places and copy those files that your user account (and thus, any nautilus window opened by your user without extra permissions) does not have the rights to access and modify.

Having said that, if the partitions you created are supposed to be permanent, I would suggest that you should configure their access settings so that even the nautilus windows that you open without root credentials can access them. This, as I said, can be done in two ways.

The easy way is not to change etc/fstab (there's a possibility to cause further malfunctions if you modify this file carelessly), but instead to invoke nautilus once with root privileges (gksu nautilus), navigate to the partition, create a new directory, then right-click, go to "Properties", "Permisssions", and set yourself (and not root) as the owner of the folder. It's also explained [here]("https://help.ubuntu.com/11.04/ubuntu-help/nautilus-file-properties-permissions.html"). From then on, you can access the folder with your "regular" nautilus windows and read/write files. I would recommend this for a new user.

The fstab thing is, IMHO, something more geared towards a more experienced user. If you decide to do this, please first make a backup of your current /etc/fstab file.

[This page]("https://help.ubuntu.com/community/Fstab") explains the format of fstab in detail. If you follow this method, you can specify the keywords "user,exec,rw" in the "options" tab for the partitions you want.

To give you exact indications on what to change in fstab, I would first need you to post your /etc/fstab file as it is right now, and which partitions you want to modify.

---

### Post by katya_sehgal on 2011-11-18
> **Orange_and_Green said:**
> Just to clarify - nautilus *is* what I call the "normal file browser". When you click, for example, on a folder on your desktop, or on the "Home" icon, you open a new nautilus window browsing that particular location.

The command "gksu nautilus" opens a window for just the same program, but with root privileges. This window can access also those places and copy those files that your user account (and thus, any nautilus window opened by your user without extra permissions) does not have the rights to access and modify.

Having said that, if the partitions you created are supposed to be permanent, I would suggest that you should configure their access settings so that even the nautilus windows that you open without root credentials can access them. This, as I said, can be done in two ways.

The easy way is not to change etc/fstab (there's a possibility to cause further malfunctions if you modify this file carelessly), but instead to invoke nautilus once with root privileges (gksu nautilus), navigate to the partition, create a new directory, then right-click, go to "Properties", "Permisssions", and set yourself (and not root) as the owner of the folder. It's also explained [here]("https://help.ubuntu.com/11.04/ubuntu-help/nautilus-file-properties-permissions.html"). From then on, you can access the folder with your "regular" nautilus windows and read/write files. I would recommend this for a new user.

The fstab thing is, IMHO, something more geared towards a more experienced user. If you decide to do this, please first make a backup of your current /etc/fstab file.

[This page]("https://help.ubuntu.com/community/Fstab") explains the format of fstab in detail. If you follow this method, you can specify the keywords "user,exec,rw" in the "options" tab for the partitions you want.

I was playing with fstab just when I read your post.
Shall follow your routine and revert. Leaving fstab for now.

May I request you to have a look at the partitions and point out errors? At this stage I can still delete them.


/dev/sda3   ext4     Mounted on /media/Primary Emergenc     uuid: 0dd42e6b-31f6-4642-a086-5a6c8112a1e4


/dev/sda6   ext4     Mounted on /media/0bc7f324-047c-4b72-a7f2-fa81cf6bf300         uuid: 0bc7f324-047c-4b72-a7f2-fa81cf6bf300

I plan to further divide sda6 (logical) into smaller sections should the need arise. This is in the case one drive ever gets corrupted. 

Your inputs.

---

### Post by Orange_and_Green on 2011-11-18
Thank you for your info katya_sehgal.

What you have posted is a *part* of the entries for two of your partitions.

"/dev/sda3 ext4 Mounted on /media/Primary Emergenc" and "/dev/sda6 ext4 Mounted on /media/0bc7f324-047c-4b72-a7f2-fa81cf6bf300" look like comments to me, do they have a "#" in front of them? If yes, every line that starts with a "#" is a comment and does not affect the system's behaviour.

the normal syntax for fstab is:
<UUID> <mount point> <type> <options> <dump> <pass>.

The values are separated by blank spaces or, more commonly, by <TAB>s.

Let me guess. The first uncommented line in your fstab could read something like

```
UUID=0dd42e6b-31f6-4642-a086-5a6c8112a1e4 /media/Primary\ Emergenc ext4 auto 0 2
```

The first value is the UUID. It's just an identifier (think "name") that is assigned to a partition when you format it. Meaning, the partition "/dev/sda3" is called "0dd42e6b-31f6-4642-a086-5a6c8112a1e4". In fact, you could substitute "UUID=0dd42e6b-31f6-4642-a086-5a6c8112a1e4" with "/dev/sda3" and it would work just as well.

The second value is the directory that the partition mounts to. In linux, blank spaces in directory names are a bit tricky (although supported), that's why you should have the "\ " in between. EDIT: as an alternative, quotes("/media/Primary Emergenc" *might* work as well, not sure though).

The third value is the file system type. It depends on what you chose to format the partition to. It could be ext3, ext4, fat32, ntfs, or several other things. **Only as an example**, I chose ext4.

The next values are the options. This is how the partitions are told to "behave" when they are mounted. What goes best in here also depends on the type of the file system; however, as a general rule, putting "user" in the options would let ordinary users mount the partition even without having root privileges.

The next two numbers ... well, let's ignore them for now, I don't think you need them right now :P

Now, it's important that you didn't change the entries for any partitions that have "/", "/home", "/etc" "/var", "/usr" (not all are always present, "/" is always there, and often "/home" too), as the mount point (second value). If you did - don't panic, I can help you fix this, and there's always the possibility to repair a broken fstab with the live CD. Anyway, feel free to play around with the other partitions, it's a great way to learn the different options.

---

### Post by katya_sehgal on 2011-11-18
I hope this doesn't take too much of your time. I am good while learning. I could not find the # tag...

> "/dev/sda6 ext4 Mounted on /media/0bc7f324-047c-4b72-a7f2-fa81cf6bf300" look like comments to me, do they have a "#" in front of them? If yes, every line that starts with a "#" is a comment and does not affect the system's behaviour.


From what I have gathered thus far,
using: 
cat /etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=20b6158d-83c3-4609-8759-ab21b18bd0c5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a3f90b10-9c8c-4df4-8e92-accdf4272266 none            swap    sw              0       0

```

Or is there another command to gather the data?

> The third value is the file system type. It depends on what you chose to format the partition to. It could be ext3, ext4, fat32, ntfs, or several other things. Only as an example, I chose ext4.


I too chose ext4 since I read it is the latest in use by Ubuntu members (or Linux members). I do not recall the name of the website.

I did not get this info:

> The next values are the options. This is how the partitions are told to "behave" when they are mounted. What goes best in here also depends on the type of the file system; however, as a general rule, putting "user" in the options would let ordinary users mount the partition even without having root privileges.



so I went for:
sudo blkid
and got...


```
/dev/sda1: UUID="20b6158d-83c3-4609-8759-ab21b18bd0c5" TYPE="ext4" 
/dev/sda3: LABEL="Primary Emergenc" UUID="0dd42e6b-31f6-4642-a086-5a6c8112a1e4" TYPE="ext4" 
/dev/sda5: UUID="a3f90b10-9c8c-4df4-8e92-accdf4272266" TYPE="swap" 
/dev/sda6: UUID="0bc7f324-047c-4b72-a7f2-fa81cf6bf300" TYPE="ext4" 
anil@anil-Inspiron-1420:~$ 
```


but I didn't see the 'options' part.

> Now, it's important that you didn't change the entries for any partitions that have "/", "/home", "/etc" "/var", "/usr" (not all are always present, "/" is always there, and often "/home" too), as the mount point (second value). If you did - don't panic, I can help you fix this, and there's always the possibility to repair a broken fstab with the live CD. Anyway, feel free to play around with the other partitions, it's a great way to learn the different options.

I did not change any "/" functions. 
With the information I have provided, are you able to ascertain the correctness of partitions? 
If they are incorrect, then
This would be a good time to make changes :-)
Not much data in the laptop. I am itching to put in data, but only after I can command copying functions.

Thank You Orange_and_Green

---

### Post by Orange_and_Green on 2011-11-18
Hi,

as far as I can tell, the entries are correct.
If you want, I'll comment the file you posted more in depth.


The first 7 lines all start with a "#" character, right? So this part is a comment, it is intended for humans to read it, not for the machine:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

```

The first (non-comment) line is

```
proc            /proc           proc    nodev,noexec,nosuid 0       0

```

This is a virtual path, so you do not need to worry about it. Please leave it untouched.

Then, you have another commented line,

```
# / was on /dev/sda1 during installation

```

and then, the entry that specifies your root partition:
```
UUID=20b6158d-83c3-4609-8759-ab21b18bd0c5 /               ext4    errors=remount-ro 0       1

```

Let's read the entry value by value (each value is separated by either a blank space or a TAB):

"UUID=20b6158d-83c3-4609-8759-ab21b18bd0c5": This is the identifier ("name") of the partition you have on /dev/sda1. As I said before, you could in theory replace this with /dev/sda1, the result would be the same.

"/": this is the mount point of this partition. It basically means that this partition is mounted at the top level of the file system, there is no directory containing this partition. If you are familiar with Windows or DOS, think of "/" as "C:\"

"ext4": this is the type of file system, it's the way that the data is coded onto the hard drive. ext4 is the latest in the ext family and is usually the default for Linux systems. If you use Windows or DOS, you may be familiar with other file systems like ntfs or fat32, for example. Anyway, this is fine.

"errors=remount-ro" is the value for the "option" tab. Only one option is specified, so the other ones are at default. errors=remount-ro is an option that means that, if the computer tries to mount /dev/sda1 at boot and fails, it will try to mount it at least as read-only ("ro").

The next values are "0" and "1". At the moment, ignore these.

So, taken as a whole, this line means, "take the partition /dev/sda1 (whose UUID is 20b6158d-83c3-4609-8759-ab21b18bd0c5), and mount it at muont point /, using ext4, with default options and failsafe read-only mount".

Then there's another comment, and then the entry for the swap partition. Your swap partition has UUID a3f90b10-9c8c-4df4-8e92-accdf4272266, is, of course, of type swap, and does not have a mount point because you're not really meant to see it. Basically, think of it as a disk space that the computer uses as a substitute when it runs low on memory.

That said, I would suggest you should first backup this working version of fstab just in case, and then, if you want to try, add the following lines to it:

```

/dev/sda3 /home/anil/FirstExtraPartition ext4 user,rw,exec 0 2

/dev/sda6 /home/anil/SecondExtraPartition ext4 user,rw,exec 0 2


```

This should mount your additional partitions inside your home folder (of course, feel free to change "FirstExtraPartition" and "SecondExtraPartition" with anything you like), with "user, read-write, and execution privileges".

Then save and reboot.

---

### Post by katya_sehgal on 2011-11-18
> **Orange_and_Green said:**
> Hi,

as far as I can tell, the entries are correct.
If you want, I'll comment the file you posted more in depth.


The first 7 lines all start with a "#" character, right? So this part is a comment, it is intended for humans to read it, not for the machine:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

```

The first (non-comment) line is

```
proc            /proc           proc    nodev,noexec,nosuid 0       0

```

This is a virtual path, so you do not need to worry about it.

Then, you have another commented line,

```
# / was on /dev/sda1 during installation

```

and then, the entry that specifies your root partition:
```
UUID=20b6158d-83c3-4609-8759-ab21b18bd0c5 /               ext4    errors=remount-ro 0       1

```

Let's read the entry value by value (each value is separated by either a blank space or a TAB):

"UUID=20b6158d-83c3-4609-8759-ab21b18bd0c5": This is the identifier ("name") of the partition you have on /dev/sda1. As I said before, you could in theory replace this with /dev/sda1, the result would be the same.

"/": this is the mount point of this partition. It basically means that this partition is mounted at the top level of the file system, there is no directory containing this partition. If you are familiar with Windows or DOS, think of "/" as "C:\"

"ext4": this is the type of file system, it's the way that the data is coded onto the hard drive. ext4 is the latest in the ext family and is usually the default for Linux systems. If you use Windows or DOS, you may be familiar with other file systems like ntfs or fat32, for example. Anyway, this is fine.

"errors=remount-ro" is the value for the "option" tab. Only one option is specified, so the other ones are at default. errors=remount-ro is an option that means that, if the computer tries to mount /dev/sda1 at boot and fails, it will try to mount it at least as read-only ("ro").

The next values are "0" and "1". At the moment, ignore these.

So, taken as a whole, this line means, "take the partition /dev/sda1 (whose UUID is 20b6158d-83c3-4609-8759-ab21b18bd0c5), and mount it at muont point /, using ext4, with default options and failsafe read-only mount".

Then there's another comment, and then the entry for the swap partition. Your swap partition has UUID a3f90b10-9c8c-4df4-8e92-accdf4272266, is, of course, of type swap, and does not have a mount point because you're not really meant to see it. Basically, think of it as a disk space that the computer uses as a substitute when it runs low on memory.

That said, I would suggest you should first backup this working version of fstab just in case, and then, if you want to try, add the following lines to it:

```

/dev/sda3 /home/anil/FirstExtraPartition ext4 user,rw,exec 0 2

/dev/sda6 /home/anil/SecondExtraPartition ext4 user,rw,exec 0 2


```

This should mount your additional partitions inside your home folder (of course, feel free to change "FirstExtraPartition" and "SecondExtraPartition" with anything you like), with "user, read-write, and execution privileges".

Then save and reboot.


This sounds wonderful. Literacy is a good thing. 
Shall employ your formula for mounting additional partitions inside home folder, and then search how to create directories (mkdir). Then create one in the additional drive and load my software there. 

I shall revert and tell you the details. You are kind.

---

### Post by Orange_and_Green on 2011-11-18
Keeping my fingers crossed LOL

I'm going home now, I'll be offline for some time, but I'll check again on this thread later. Good luck and congratulations on your will to learn, this is really the most important thing.

---

### Post by katya_sehgal on 2011-11-18
> **Orange_and_Green said:**
> Keeping my fingers crossed LOL

I'm going home now, I'll be offline for some time, but I'll check again on this thread later. Good luck and congratulations on your will to learn, this is really the most important thing.


I named them PrimaryEmergency (Primary) and ExtendedHQ (Logical). They show in the HOME folder.

They have a 'lock' drawn over them. While attempting to copy a file into them, for example:

```
The folder "005PainsathLakhKiDakait" cannot be copied because you do not have permissions to create it in the destination.
```

In Properties tab, I see that 'root' is the owner. I'll wait then and not add any program or  copy files.
Look forward to some interaction tomorrow (or whenever you are back).

---

### Post by Orange_and_Green on 2011-11-18
Hi there, I'm back:) It's my 30th birthday today and I've been celebrating until now :guitar:

Anyway, congratulations, you're almost done!
Now, you have to set up the permissions for the mount point.

open up a terminal and type:
```
gksu nautilus /home/anil
``` (it's the last time, promise;)), 

This should take you to your home folder, with root privileges. Now, right-click on PrimaryEmergency, select Properties, then Permissions. Set "anil" as both the owner and the owner group. Do the same thing for ExtendedHQ.

Now the lock should have disappeared and you can copy/paste your files easily. Also, the changes should persist even after shutting down/rebooting.

Have lots of fun with Ubuntu,

O&G

---

### Post by katya_sehgal on 2011-11-19
> **Orange_and_Green said:**
> Hi there, I'm back:) It's my 30th birthday today and I've been celebrating until now :guitar:

Anyway, congratulations, you're almost done!
Now, you have to set up the permissions for the mount point.

open up a terminal and type:
```
gksu nautilus /home/anil
``` (it's the last time, promise;)), 

This should take you to your home folder, with root privileges. Now, right-click on PrimaryEmergency, select Properties, then Permissions. Set "anil" as both the owner and the owner group. Do the same thing for ExtendedHQ.

Now the lock should have disappeared and you can copy/paste your files easily. Also, the changes should persist even after shutting down/rebooting.

Have lots of fun with Ubuntu,

O&G

It's good that I finish learning on your birthday so we can now party together. [violin, piano sonata graphic]

I can now copy the files. It has been fun learning. And I look forward to more complications :-)

Shall mark thread as solved after posting a summary of events here.

Cheers. 
And happy birthday, Orange and Green.

---

### Post by katya_sehgal on 2011-11-22
Marking as solved. Shall post summary once I am back.

---

