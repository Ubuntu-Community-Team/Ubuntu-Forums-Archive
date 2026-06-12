---
title: "Trying to transfer files from unbootable vista"
date: 2010-01-02
forum: General Help
---

### Post by peter762033 on 2010-01-02
Hi, im trying to get the files off of my unbootable laptop with ubuntu live cd. The problem i have is that i get into ubuntu then go to the computer option but i dont see the C: drive where my files are stored. How can i make it so i can see the hard drive in the laptop so i can copy my files to an external hard drive?

thanks!

---

### Post by Mark Phelps on 2010-01-02
Once you boot into the LiveCD, use synaptic to install ntfsprogs.  

Then, click on Places and you should see a list of mountable volumes.  Linux doesn't use the "C", "D", drive notation of MS Windows, so you won't see anything by that name; instead, if your "C" drive was 40GB, you'll see something like 40GB drive under Removable Media.

---

### Post by peter762033 on 2010-01-02
Ok then, im booted into the live cd, how do i use synaptic to install ntfsprogs?

thanks for the help!

EDIT: I just found it, scrolled down to ntfsprogs and it has a green box next to it, does this mean its all ready installed?

---

### Post by Ginsu543 on 2010-01-02
I'm not sure I understand what you mean by "go to the computer option," but have you tried looking under "Places" menu? Ubuntu should recognize the hdd in your laptop, although it won't say "C: drive." It should list the name you gave the C: drive. Another option is to look for it under Nautilus, which is the Ubuntu file browsing program. You can find it in the menus under Applications --> System Tools (assuming you are using Karmic live CD). If you don't see it there, you may have to turn the menu item on by first going to System --> Preferences --> Main Menu, clicking on System Tools, and checking on File Browser.

---

### Post by peter762033 on 2010-01-02
I got to the computer menu by going, places > computer. The only drive that is see which could be it is one called OS, but i never named a drive that and it has no writing underneath it saying how large the drive is and i cant access it. Other than that there just one called filesystem. 
If i browsed for it through system tools wouldnt i need to know the drive name? I dont actually know its name as this is second hand and ive never booted into it, and im using the ubuntu live cd not the karmic live cd,

thanks!

---

### Post by OldGrantonian on 2010-01-02
> **peter762033 said:**
> I got to the computer menu by going, places > computer.

Double-click on each partition that you see in Places > Computer

You will be asked to authenticate once.

Open one partition at a time, and eventually you will open the correct partition, containing files that you recognize.
.

---

### Post by peter762033 on 2010-01-02
Ok in the computer screen all i see are 4 drive options, these are,

CD-RW/DVD+RW Drive
OS
USB Drive
Filesystem

Now the obvious 2 are filesystem and OS. When  i go into filesystem its just just stuff to do with linux. When i doublle click on the OS drive it says 

Unable to mount location
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

And then this pops up,

Cannot mount volume.
Unable to mount the volume 'OS'.

And then in the details link it says

ntfs_attr_pread_i: ntfs_pread failed: input/outpu error failed to read ntfs $bitmap: input/output error ntfs is either inconsistent, or there is a hardware fault, or its a softraid/ fakeraid hardware. In the first case run chkdsk /f on windows then reboot into windows twice. The useage of the /f parameter is very important! if the device is a softraid/ fakeraid then first activate it and mount a different device under the /dev/mapper/directory, (eg./dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details.

So do you think that the OS drive is the drive with my stuff in it? How can i get into it? Or is there a hardware failure of the Hard drive?

Thanks again!

---

### Post by OldGrantonian on 2010-01-02
> **peter762033 said:**
> Ok in the computer screen all i see are 4 drive options, these are,

CD-RW/DVD+RW Drive
OS
USB Drive
Filesystem


To simplify as much as possible, disconnect any external media.

In your case:

•  Remove any CD from the drive
• Remove any USB stick.
• Switch off or remove any external HDD

Applications > Accessories > Terminal

At the prompt, enter:

```

sudo  fdisk  -l

```The last thing is "minus ell", not "minus one"

You will be asked to enter a password.

Post your results here.
.

---

### Post by peter762033 on 2010-01-02
Ok, well i cant remove the cd as ubuntu is running off of it. I put in the promt you said and i got this result, wasnt asked for a password,

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1280    10240000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1280       30402   233916600    7  HPFS/NTFS

Was i supposed to have been asked for a password?

thanks!

---

### Post by OldGrantonian on 2010-01-02
> **peter762033 said:**
> Ok, well i cant remove the cd as ubuntu is running off of it. I put in the promt you said and i got this result, wasnt asked for a password

I'm sorry. I forgot you are operating from a CD. So, no password needed. (And of course, no removal of CD :) )

Type the following into google:

Partition does not end on cylinder boundary

I think you will find results that may  cause you some worry.

Anyway, I'm no expert, but it looks as if /dev/sda3 is your bootable partition (because of the asterisk "*")

I see that you have a Dell Utility partition. Are there recovery facilities on that partition? (Maybe a button on your laptop?)

You will do no harm by looking around some more. None of the following commands are destructive.

First, mount /dev/sda3 and have a look at it:

```

mkdir  /mnt/peter/

mount   -t   ntfs-3g   /dev/sda3    /mnt/peter/  -o  defaults,umask=0

cd  /mnt/peter

ls

```
Now, you should see some directories. Do you recognize any of these?


Now, mount /dev/sda2 and have a look at it:

```

mkdir  /mnt/peter2

mount   -t   ntfs-3g   /dev/sda2    /mnt/peter2/  -o  defaults,umask=0

cd  /mnt/peter2

ls

```BTW:  the techies will tell you that you can mount more than one file system on one mount point, but I'm a coward :)

Now, you should see some directories. Do you recognize any of these?

To be safe (I said I was a coward):

```

umount  /mnt/peter

umount  /mnt/peter2

```

---

### Post by peter762033 on 2010-01-02
Ok, i searched around for the cylinder boundary issue and found this

[http://ubuntuforums.org/archive/index.php/t-1070547.html](http://ubuntuforums.org/archive/index.php/t-1070547.html)

it doesnt look to be a major issue luckily!

I typed in the first lot of command prompts you suggested and got this error,

ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

You suggested that i put 'peter' in the prompt like this,


mkdir  /mnt/peter/

mount   -t   ntfs-3g   /dev/sda3    /mnt/peter/  -o  defaults,umask=0

cd  /mnt/peter

ls
Ive never actually been able to access this laptop as ive been given it from a friend, so i dont know if i should include 'peter' in the promts?

Thanks for helping!

---

### Post by Leppie on 2010-01-02
> **peter762033 said:**
> Ok, i searched around for the cylinder boundary issue and found this

[http://ubuntuforums.org/archive/index.php/t-1070547.html](http://ubuntuforums.org/archive/index.php/t-1070547.html)

it doesnt look to be a major issue luckily!
no, it's not a big problem.


> **peter762033 said:**
> I typed in the first lot of command prompts you suggested and got this error,

ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
do you have a windows cd around? and is windows still usuable on this system or is this the unbootable vista partition?

> **peter762033 said:**
> You suggested that i put 'peter' in the prompt like this,


mkdir  /mnt/peter/

mount   -t   ntfs-3g   /dev/sda3    /mnt/peter/  -o  defaults,umask=0

cd  /mnt/peter

ls
Ive never actually been able to access this laptop as ive been given it from a friend, so i dont know if i should include 'peter' in the promts?

Thanks for helping!
peter is just a mount point (e.g. kind of a label), you could've put something like dell_laptop as well. it doesn't change functionality.
i would actually mount the partitions as read-only for the moment:
```
$sudo mount -t ntfs -r /dev/sdaY /mnt/yourchoice/  ##change /dev/sdaY and /yourchoice to your needs
```

---

### Post by peter762033 on 2010-01-02
I dont have a windows disk, it came pre installed, and i cant boot the system, i just get a blue screen of death. Ive tried safe mode etc and i cant fix it, so the reason im using ubuntu is so i can retrieve my files and reinstall windows. Ofcourse i would rather fix the blue screen problem but i havent been succesfull, does anybody know how to fix this?

I just tried the prompts you gave me and i get this error message

ntfs-3g: Failed to access volume '/dev/sdaY': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.

What does this mean?

thanks!

EDIT: ive heard i may need to install ntfs-config, how do i do this?

---

### Post by Leppie on 2010-01-02
in sdaY you will have to replace Y with the number of the partition you want to browse (that's why i put the comment "##change /dev/sdaY and /yourchoice to your needs" there). this means that for one partition you'll use sda2 and for the other sda3.

---

### Post by Leppie on 2010-01-02
if you really want to restore vista, you could give the [vista recovery cd]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") a try.

---

### Post by Leppie on 2010-01-02
> **peter762033 said:**
> EDIT: ive heard i may need to install ntfs-config, how do i do this?
ntfs-config can be installed like this:
```
$sudo apt-get install ntfs-config
```

however, you don't need ntfs-config.
just replace the sdaY with the partitions you're mounting (in your case sda2 or sda3).

---

### Post by peter762033 on 2010-01-02
Ok, sorry i didnt quite understand. I just closed the terminal and started again, then typed in what you suggested and this is what i got,

ubuntu@ubuntu:~$ $sudo mount -t ntfs -r /dev/sda2 /mnt/peter/
mount: only root can do that

What is root? Can i make it go from root? 

I have tried the recovery cd and it didnt work, it got stuck when it wanted to know where system files where and i couldnt find them, i couldnt enter the C: drive, everytime i double clicked it it just didnt respond and all of the buttons went grey so they were unclickable. Also when i was in the recovery cd it didnt list the C: size and in properties it said 'unknown' for everything, doesnt sound good.
Is it possible that theres a problem with the hard drive?

Thanks!

---

### Post by Leppie on 2010-01-02
> **peter762033 said:**
> Ok, sorry i didnt quite understand.
don't worry ;)

> **peter762033 said:**
> I just closed the terminal and started again, then typed in what you suggested and this is what i got,

ubuntu@ubuntu:~$ $sudo mount -t ntfs -r /dev/sda2 /mnt/peter/
mount: only root can do that
i put the "$" to indicate commands on the command line, it represents your command line prompt (ubuntu@ubuntu:~$). so the command you should type in is:
```
sudo mount -t ntfs -r /dev/sda2 /mnt/peter/
```
the system doesn't understand the command "$sudo", but does understand "sudo" (without the quotes).

> **peter762033 said:**
> What is root? Can i make it go from root? 
Also do i need to install NTFS-config?

Thanks!
root is the main administrator account *nix based systems. you obtain temporary admin rights by using the "sudo" command.

---

### Post by peter762033 on 2010-01-02
Ok, i feel silly lol, i just tried the correct prompt for sda2 and sda3 and these are the results,

ubuntu@ubuntu:~$ sudo mount -t ntfs -r /dev/sda2 /mnt/peter/
fuse: mount failed: Device or resource busy

ubuntu@ubuntu:~$ sudo mount -t ntfs -r /dev/sda3 /mnt/peter/
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Is this normal? Should the drive have mounted? And it says the drive or resource is busy, what could it be doing?

Thanks

---

### Post by peter762033 on 2010-01-02
I just thought i would try changing the prompt to sda1 to see what would happen and i got this,

ubuntu@ubuntu:~$ sudo mount -t ntfs -r /dev/sda1 /mnt/peter/
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

Could this help out?

thanks

---

### Post by Leppie on 2010-01-02
> **peter762033 said:**
> Ok, i feel silly lol
don't, we all have to learn before knowing

> **peter762033 said:**
> i just tried the correct prompt for sda2 and sda3 and these are the results,

ubuntu@ubuntu:~$ sudo mount -t ntfs -r /dev/sda2 /mnt/peter/
fuse: mount failed: Device or resource busy
this means the partition is still mounted. if you want to mount it as read-only, you will have to unmount it first:
```
$sudo umount /dev/sda2
```
you can then mount it as read-only:
```
$sudo mount -t ntfs -r /dev/sda2 /mnt/peter
```

> **peter762033 said:**
> ubuntu@ubuntu:~$ sudo mount -t ntfs -r /dev/sda3 /mnt/peter/
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Is this normal? Should the drive have mounted? And it says the drive or resource is busy, what could it be doing?

Thanks
i think this is because vista crashed, don't worry about that message for the moment.

---

### Post by peter762033 on 2010-01-02
I suppose you are right, we all have to learn!

I just entered the prompts you put up but it didnt say anything after i put them in, should it have said something like, 'mounted'? Here i what it did,

ubuntu@ubuntu:~$ sudo umount /dev/sda2
ubuntu@ubuntu:~$ sudo mount -t ntfs -r /dev/sda2 /mnt/peter
ubuntu@ubuntu:~$ 

I looked in the 'computer' area and its still the same, i dont see the hard drive, should i beable to see it?

Thanks!

---

### Post by Leppie on 2010-01-02
these commands do not produce output unless something goes wrong ;)

you can now access your files using a file manager. look under "Places" in the top bar. if there is no "peter" there, just go to filesystem and then the folder "mnt". the folders you created earlier should be there.

---

### Post by peter762033 on 2010-01-02
oh ok, so i got it right haha. In the places dropdown there is no option 'peter', how do i get to filesystem?

thanks

---

### Post by OldGrantonian on 2010-01-02
> **peter762033 said:**
> In the places dropdown there is no option 'peter', how do i get to filesystem?

I think you need to select "Computer", then "File System"

Then open "mnt", then "peter"
.

---

### Post by peter762033 on 2010-01-02
In the applications, places, system dropdown i dont see filesystem atall, is it supposed to be in one of these dropdowns? Where else could i look?

thanks

---

### Post by Leppie on 2010-01-02
> **OldGrantonian said:**
> I think you need to select "Computer", then "File System"

Then open "mnt", then "peter"
.

sorry, this may be different in my system (i'm using xubuntu) #-o

---

### Post by OldGrantonian on 2010-01-02
> **peter762033 said:**
> In the applications, places, system dropdown i dont see filesystem atall, is it supposed to be in one of these dropdowns? Where else could i look?

thanks

I cheated :)

I edited my post. Sorry.

---

### Post by Leppie on 2010-01-02
> **peter762033 said:**
> In the applications, places, system dropdown i dont see filesystem atall, is it supposed to be in one of these dropdowns? Where else could i look?

thanks

is there "computer"?

---

### Post by koma77 on 2010-01-02
Try the Places menu agan. 

There should be a Computer item there. Click it.

In the window that opens, click on Filesystem.

Click on mnt.

Click on peter.

---

### Post by peter762033 on 2010-01-02
Yep i got it and ive opened up the folders 

mnt > peter > users > default

But when i get into there i see folders such as music, videos etc but they are all empty, at the bottom of the window for every folder it says 0 items 4.7gb free

When i go to this folder,

mnt > peter > users > public

Iget the same story, default and public are the only folders i see in the users folder, shouldnt my files be in here? Everything is empty :s What does this mean?

Thanks!

---

### Post by Leppie on 2010-01-02
> **peter762033 said:**
> Yep i got it and ive opened up the folders 

mnt > peter > users > default

But when i get into there i see folders such as music, videos etc but they are all empty, at the bottom of the window for every folder it says 0 items 4.7gb free

When i go to this folder,

mnt > peter > users > public

Iget the same story, default and public are the only folders i see in the users folder, shouldnt my files be in here? Everything is empty :s What does this mean?

Thanks!
under vista, user data is stored in \user\<username>
have you tried looking under \Documents and Settings\<username> as well?
and how about the other partition?

---

### Post by peter762033 on 2010-01-02
In users i only get default and public not a normal name. 
There is no documents and settings folder in mnt > peter.
To try the other partition do i do the prompts from earlier but with sda3? So they would be,

sudo umount /dev/sda3

sudo mount -t ntfs -r /dev/sda3 /mnt/peter

Shall i try that?

Thanks

---

### Post by peter762033 on 2010-01-02
I thought i would give it a go and i got this result,

ubuntu@ubuntu:~$ sudo umount /dev/sda3
umount: /dev/sda3: not mounted
ubuntu@ubuntu:~$ sudo mount -t ntfs -r /dev/sda3 /mnt/peter
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Same error message as before :s. What else can i try?

thanks

---

### Post by Leppie on 2010-01-02
> **peter762033 said:**
> In users i only get default and public not a normal name. 
There is no documents and settings folder in mnt > peter.
To try the other partition do i do the prompts from earlier but with sda3? So they would be,

sudo umount /dev/sda3

sudo mount -t ntfs -r /dev/sda3 /mnt/peter

Shall i try that?

Thanks
i thought you had peter and peter2...
but this should work as well.

---

### Post by Leppie on 2010-01-02
> **peter762033 said:**
> I thought i would give it a go and i got this result,

ubuntu@ubuntu:~$ sudo umount /dev/sda3
umount: /dev/sda3: not mounted
ubuntu@ubuntu:~$ sudo mount -t ntfs -r /dev/sda3 /mnt/peter
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Same error message as before :s. What else can i try?

thanks
you may want to try downloading some cd image with ntfs tools (especially tools to check and repair ntfs filesystems).

---

### Post by peter762033 on 2010-01-02
Ok il google for some tools now, il let you know how i get on. Do you know of any tools i could use?

Thanks

---

### Post by Leppie on 2010-01-02
> **peter762033 said:**
> Ok il google for some tools now, il let you know how i get on. Do you know of any tools i could use?

Thanks
there's images like [Ultimate Boot CD]("http://www.ultimatebootcd.com/download.html"), Hiren's Boot CD, [Vista Recovery CD]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"), etc.

---

### Post by peter762033 on 2010-01-02
I have a burnt iso of ultimate boot cd i can use, which program on the disk should i use, there are lots to choose from,

Thanks

---

### Post by Leppie on 2010-01-02
> **peter762033 said:**
> I have a burnt iso of ultimate boot cd i can use, which program on the disk should i use, there are lots to choose from,

Thanks

you could also install testdisk:
```
$sudo apt-get install testdisk
```

to run testdisk:
```
$sudo testdisk
```

---

### Post by OldGrantonian on 2010-01-03
The activity seems to have died down.  Maybe it's time for a review :)

Your original post started with the line:
> 
im trying to get the files off of my unbootable laptop
What does "unbootable" mean? Do you get as far as the Dell splash screen? If yes, then it seems that you can press F8 to enter the Dell recovery partition.

Here are two links:
[http://en.community.dell.com/forums/t/19279101.aspx](http://en.community.dell.com/forums/t/19279101.aspx)
[http://en.community.dell.com/forums/t/19254952.aspx](http://en.community.dell.com/forums/t/19254952.aspx)

When you used fdisk, there was a Dell line. Type that line into google, and you will see many results:

/dev/sda1 1 5 40131 de Dell Utility

Here are some comments on repair tools. Remember that, in order to repair your OS or your filesystem, I think these tools must write to disk. So, before any repair, you should try to get your data off the disk to another media. Otherwise, you might damage any data that might be currently recoverable using low-level sector scratchers.

Years ago, GetDataBack was the best tool (maybe it still is). It costs $79, but here's a quote about the demo version:

> 
The demo version allows you to perform the data recovery and to see and verify your recovered files without having the possibility to save
I used the demo version on a friend's Sony Vaio, and verified that 60% of his data was recoverable on the later part of the disk. The FAT, directory, and early files were all zeros. Maybe the disk head was over the early part of the disk when it failed. The collapsing magnetic field writes zeros to that part of the disk.

I then tried various free and open source tools to recover the data, but the damage was too severe, and we only got about 20% of his files.

Eventually, my friend paid $79 and got 60% of his files back. The rest were either garbage or zeros. 

Note that the FAT was damaged, so a single recovered file might contain data from only one sector. So, due to fragmentation, my friend had to search the recovered files and join up non-contiguous bits manually. For Word files, he then had to extract only the text, leaving all the control code stuff. The filenames were simply hex strings, because the directory was also damaged.

BTW: If you find all this depressing, I can assure you that my friend (and his school-age daughter) were delighted with what he got back :)

Remember that data recovery sites are magnets for malware. So make sure you have noScript and WOT installed in your Firefox if you visit such sites. Also, google the site name and look for unfavourable comments.

One final comment. I'm no techie, but I think I've read that If you mount any device that has problems, it might be safer to unmount it before shutting down. I think there was an example on this forum where a user could not use Ubuntu to mount a Windows partition, because Windows failed to unmount the partition during the previous session (a crash?). I think the user had to reboot to Windows, exit gracefully, then reboot to Ubuntu. (Of course, his Windows was bootable, which yours isn't).
.

---

### Post by peter762033 on 2010-01-03
Morning,

Well when i boot up the laptop i do get the dell screen and i can go into the f8 option, so i will give that a go once i have recovered my data (if i can).

With getdataback do i have to put the hard drive into an enclosure and then plug it into my working computer? Or is there an iso version? Are there any recovery tools which are iso so i can run them off of a disk? What were the various freeware options that only recovered 20% of files, were these iso?

When i tried to run test disk in ubuntu it said that E: couldnt find package testdisk, what does this mean?

Thanks for the help, much appreciated!

---

### Post by Leppie on 2010-01-03
does that laptop have internet when using the ubuntu livecd? installing testdisk would require an internet connection.
testdisk is also included on the ultimate boot cd.
alternatively, search for other images like Hiren's Boot CD (it includes getdataback)

---

### Post by peter762033 on 2010-01-03
> **Leppie said:**
> does that laptop have internet when using the ubuntu livecd? installing testdisk would require an internet connection.
testdisk is also included on the ultimate boot cd.
alternatively, search for other images like Hiren's Boot CD (it includes getdataback)

Yep the laptop does have internet connection with ubuntu. Ive just started up test disk through UBCD but how do i test the disk to see if its healthy? Can i download getbackdata as an iso instead of downloading the whole of hirens boot cd?

Thanks

---

### Post by Leppie on 2010-01-03
> **peter762033 said:**
> Yep the laptop does have internet connection with ubuntu. Ive just started up test disk through UBCD but how do i test the disk to see if its healthy? Can i download getbackdata as an iso instead of downloading the whole of hirens boot cd?

Thanks
the testdisk wiki: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
it's for the windows version, but i think it will give you an idea of how it works (and screens are very similar to linux ones).
i don't know about getdataback images. hbcd is only about 200mb.

---

### Post by peter762033 on 2010-01-03
Il look into that. 
I found a link for hirens boot cd, 

[http://www.hirensbootcd.net/](http://www.hirensbootcd.net/)

is this the correct download?

thanks

---

### Post by Leppie on 2010-01-03
i cannot provide any link or instructions as to where and how to obtain the cd. this because of copyright infringements. but the link you posted is the website with info on the contents.

---

### Post by peter762033 on 2010-01-03
Ok, i just burnt the disk and it running, but i cant find the getdataback on the disk, weird.

I had a thought, should i just take the hard drive out, get an enclosure, and plug it into my working computer and transfer the files that way? If i did this are there freeware programs i can use to get the data onto my computer off of the hard drive?

Thanks!

---

### Post by Leppie on 2010-01-03
> **peter762033 said:**
> Ok, i just burnt the disk and it running, but i cant find the getdataback on the disk, weird.
most of these cd's are divided into sections. browse the sections, i think it may be in some section called recovery or partitioning (tools).

i don't really see why putting the drive in an enclosure would make things easier.

---

### Post by peter762033 on 2010-01-03
I looked into recovery and partitioning tools but its not there.
Well if i were to put it in an enclosure and then plug that into my working computer so i can use recovery software running off of my computer, wouldnt that make it eaiser, then i could run getbackdata. Heres a video of what i mean,

[http://www.youtube.com/watch?v=KsyBrjqPAmo&feature=related](http://www.youtube.com/watch?v=KsyBrjqPAmo&feature=related)

Could this work? 

Thanks

---

### Post by impact on 2010-01-03
> **peter762033 said:**
> Ok, i just burnt the disk and it running, but i cant find the getdataback on the disk, weird.

I had a thought, should i just take the hard drive out, get an enclosure, and plug it into my working computer and transfer the files that way? If i did this are there freeware programs i can use to get the data onto my computer off of the hard drive?

Thanks!

> One final comment. I'm no techie, but I think I've read that If you mount any device that has problems, it might be safer to unmount it before shutting down. I think there was an example on this forum where a user could not use Ubuntu to mount a Windows partition, because Windows failed to unmount the partition during the previous session (a crash?). I think the user had to reboot to Windows, exit gracefully, then reboot to Ubuntu. (Of course, his Windows was bootable, which yours isn't).



This. I once had a drive like that. It was ntfs-formatted external drive and Ubuntu refused to mount it, saying that the drive contents was inconsistent. I had to connect the drive to a Windows (Vista in my case) machine, which could mount and repair the filesystem automagically and then safely unmount it. Afterwards, the drive could be connected to Ubuntu without problems.

---

### Post by peter762033 on 2010-01-03
Ok then, so basically i need to take the hard drive out and get an enclosure? Do you think that the method on the youtube video i posted would work too?

thanks

---

### Post by Leppie on 2010-01-03
just get a good enclosure, i always prefer those with metal casings.

---

### Post by peter762033 on 2010-01-03
Well i just went out and they only had ones for IDE drives not SATA grrrr, how do i find out which one my drive is?. Is the enclosure option my only option? Are there any other pieces of software i can use? Id like to use hirens cd but i cant see the getdataback option, i only see what are in these screenshots,

[http://www.hirensbootcd.net/screenshots.html](http://www.hirensbootcd.net/screenshots.html)

Thanks

---

### Post by peter762033 on 2010-01-03
> **OldGrantonian said:**
> The activity seems to have died down.  Maybe it's time for a review :)

Your original post started with the line:
What does "unbootable" mean? Do you get as far as the Dell splash screen? If yes, then it seems that you can press F8 to enter the Dell recovery partition.

Here are two links:
[http://en.community.dell.com/forums/t/19279101.aspx](http://en.community.dell.com/forums/t/19279101.aspx)
[http://en.community.dell.com/forums/t/19254952.aspx](http://en.community.dell.com/forums/t/19254952.aspx)


.

I just tried the F8 on boot up and followed the instruction on that guide but i select the 'Repair your computer' option and the windows scroll bar comes up then i get a blue screen with error STOP: 0X000000F4, so i guess i cant use this to restore it back to factory settings. Will i need a vista disk to restore the computer once i get my files back?

Thanks

---

### Post by Leppie on 2010-01-03
> **peter762033 said:**
> Id like to use hirens cd but i cant see the getdataback option, i only see what are in these screenshots,

[http://www.hirensbootcd.net/screenshots.html](http://www.hirensbootcd.net/screenshots.html)

Thanks

getdataback is there in the screenshots as well. it's a windows app, so it's under the windows apps. i merely mentioned it's on hbcd as you were talking about it. there's several other tools available on that image.

---

### Post by peter762033 on 2010-01-03
Ok ive got it fixed finally, it wasnt a hard drive fault or anything in the end. I downloaded this vista recovery cd

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

and it scanned for problems and fixed them, now its allfixed! Finally!

I would just like to thank everyone who has helped me out with this, appreciate the help,

Cheers

---

### Post by Leppie on 2010-01-03
> **peter762033 said:**
> Ok ive got it fixed finally, it wasnt a hard drive fault or anything in the end. I downloaded this vista recovery cd

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

and it scanned for problems and fixed them, now its allfixed! Finally!

I would just like to thank everyone who has helped me out with this, appreciate the help,

Cheers

i believe that's what i suggested in post #15...

---

### Post by peter762033 on 2010-01-03
yea i did try it then but with no luck, i was only trying to do system restore then which wouldnt work. Well atleast its fixed now,

Thanks

---

### Post by Leppie on 2010-01-03
> **peter762033 said:**
> yea i did try it then but with no luck, i was only trying to do system restore then which wouldnt work. Well atleast its fixed now,

Thanks

well, glad you got your files back.
you really should give linux a try, it's much more reliable than windows. if you need help setting up your system for side by side installation, just give a shout here at the forum (or pm me if you prefer).

---

