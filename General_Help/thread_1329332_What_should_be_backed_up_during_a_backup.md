---
title: "What should be backed up during a backup?"
date: 2009-11-17
forum: General Help
---

### Post by Radissthor on 2009-11-17
Hello everyone,

I happened to install the 64 bit version of Jaunty and now I want to change back to the 32 bit one. For that I understand I have to reinstall the OS and for that I want to backup my 'System information' so that all my configurations stick. This means from wallpaper to sound options and packages, to firefox configuration and OOo packs, etc... 

So, the question is: What folders should be backed up? The 'Simple Backup' software has as default the /var/, /Home/, /usr/local/ and /etc/ folder. And leaves out the /media/, /var/cache/, /var/spool/ and /var/tmp/ folders.  Is this enough to keep all my configurations? Is there something that's not needed or that's missing?

Thanks in advanced for your comments and help.

---

### Post by Giblet5 on 2009-11-17
Open a terminal window (Applications -> Accessories -> Terminal) and enter (select/copy the command, then click on the terminal window and hit Shift-Ins):

```
sudo dpkg -l | awk '{ print $2 }' | sed -e '1,5d' > $HOME/packages.txt
```

Now, use tar to backup /home (assumes that you have an NTFS or ext2/3/4 drive mounted at /media/USBdrive - substitute what you DO have, but remember that FAT32 filesystems can't create files larger than 4G...):

```
sudo tar -cvzPf /media/USBdrive/backup.tar.gz /home /etc/passwd /etc/shadow /etc/group /etc/sudoers /etc/X11
```

That will take awhile.

When done, verify the backup via ```
sudo tar tzf /media/USBdrive/backup.tar.gz
```

Reinstall.

Update your system via ```
sudo apt-get update
sudo apt-get upgrade
```

You'll need to reboot when that's done.

Log in. Bring up a terminal window and run:
```
cd /
sudo tar xzvf /media/USBdrive/backup.tar.gz
```

When it completes, paste these commands into the terminal window:

```
for i in `cat $HOME/packages.txt`
do
    clear
    echo "Installing package $i"
    sudo apt-get install $i -yq
done
```

That will install all of the packages you had installed before. You'll get warnings on the packages that are already installed by default, that's OK.

When it completes (and it will take awhile), log off, then log in. Everything should be as it was.

---

### Post by Radissthor on 2009-11-17
> **Giblet5 said:**
> 
Now, use tar to backup /home (assumes that you have an NTFS or ext2/3/4 drive mounted at /media/USBdrive - substitute what you DO have, but remember that FAT32 filesystems can't create files larger than 4G...):

```
sudo tar -cvzPf /media/USBdrive/backup.tar.gz /home
```

(...)

That will install all of the packages you had installed before. You'll get warnings on the packages that are already installed by default, that's OK.

When it completes (and it will take awhile), log off, then log in. Everything should be as it was.

Thanks for the complete advice! I have a question. I have a 200Gb External drive that is recognized as SWISNIFE 1 by Ubuntu. So what exact line should I substitute in the first command above?

Another, more general question. What does the process you have described do? Is it like a back up using the terminal or something?

---

### Post by Giblet5 on 2009-11-17
> **Radissthor said:**
> Thanks for the complete advice! I have a question. I have a 200Gb External drive that is recognized as SWISNIFE 1 by Ubuntu. So what exact line should I substitute in the first command above?

Another, more general question. What does the process you have described do? Is it like a back up using the terminal or something?


You're no doubt familiar with the term "tip of the iceberg"...

On Windows, the GUI interface is the iceberg and the command-line interface is the tip. There's not much one can do from the Windows command prompt.

On any Linux system, the GUI is the tip and the command-line is the iceberg.


The instructions I provided use commands that are documented in the manual that you might not know you have, because there is no gui interface for them. A gui isn't even possible because they can be used so many ways - either by themselves - or in combination with other commands.

Example manual pages: ```
man tar
man awk
man dpkg
man apt-get
...
```


The tar command line I provided will create a backup archive (compressed) that can exactly reproduce the entire /home directory, subdirectories, files, and links, plus the user config files in /etc (user names, passwords, groups, etc).

Oh yeah...

I don't/can't know where that drive of yours will mount. You control that.

Just remember that if it's a FAT32 filesystem (aka FAT aka vfat), it won't store files more than 4G in size. (It's a 32-bit filesystem = 2³² = 4G) You can format it for whatever you want, but if you intend to use it with Windows, I'd format it as NTFS. If you're not using it with Windows, I'd format it as ext3.

---

### Post by fluffman86 on 2009-11-17
Go to Places > SWISNIFE 1, and in the window that opens up, click the little pencil or paper or something to the left of the location bar near the top.

You should see something like /media/SWISNIFE1

If there are no spaces in the name, then change /media/USBdrive/backup.tar.gz above to /media/SWISNIFE1.backup.tar.gz

Note that Linux is CASE SENSITIVE.  Meaning swisnife1 is not SWISNIFE1 or SwIsNiFe1...they are ALL DIFFERENT.

Also, the command line cannot handle spaces.  So if your drive is mounted at /media/SWISNIFE 1, then you need to change /media/USBdrive/backup.tar.gz to /media/SWISNIFE\ 1/backup.tar.gz  Note the backslash there.  It's used to "esape" or ignore the space before the 1.

And as for Giblet's process:

1. Run the command dpkg, and list the output. (that's a lower case L in his command).  Then, he uses a program called sed to strip out uneccessary information about the packages, and directs it with ">" to a file call packages.txt in your home directory.  That final part in needed because otherwise it would just show up in your terminal.

2. Next, he uses tar, the Tape Archiver, to essentially compress (like a zip or rar file in Windows) into a single file (backup.tar.gz) all of the information that's at /home, /etc/passwd, etc...  Then he verifies the information with the next command.

3. You reinstall the system, but that's not the most up-to-date stuff.  So you use apt-get to update your package list and connect to the internet to see what's new and available now, then upgrade all of the listed packages.  Some of these will include a kernel update, which means you have to reboot.

4. Now that everything's up-to-date, you need to find your archive that you made.  Again, we use the program tar to e*X*tract, from a *Z*ipped up *F*ile, and be *V*erbose (tell us what's happening) about it.

5. Finally, that's just a simple script that says
read each line of packages.txt in your home directory
then sudo apt-get install [the contents of each line]
and -yq means Yes, I want to really do that, and do it quietly without asking a bunch of questions.

If you open of that file, you'd see it says something like
vlc
gedit
gnome-terminal
...etc., etc.,...
So you want to use apt-get as a super doer to install vlc.
Then again with gedit
and so on.

Edit: now that I've read Giblet's next post, it's important to note that everything he told you to do actually *CAN* be done from the GUI...it's just much harder.  So for example if you right click on your home folder in nautilus, you can click "compress" and I believe synaptic has an option of saving all of your markings in there to transfer to another computer.

---

### Post by Radissthor on 2009-11-17
> **Giblet5 said:**
> 

I don't/can't know where that drive of yours will mount. You control that.

Just remember that if it's a FAT32 filesystem (aka FAT aka vfat), it won't store files more than 4G in size. (It's a 32-bit filesystem = 2³² = 4G) You can format it for whatever you want, but if you intend to use it with Windows, I'd format it as NTFS. If you're not using it with Windows, I'd format it as ext3.

Many thanks for the detailed explanation. I don't intend to use Windows. I have only one partition with Ubuntu on it. 
I'm afraid I didn't get your specifications of FAT32 and NTFS. What do those words refer to? And what does it mean that I cannot copy files larger than 4 GB? Does that mean only single files or folder? I don'0t think I have one file that is heavier than 4 GB, but I sure have some folders (discographies for example) that are sure larger than that.

---

### Post by fluffman86 on 2009-11-17
Once you run the tar command above, it turns ALL of your folders and files into ONE single file.  This means that if you have more than 4 GB of data, it won't fit on a normal thumbdrive.

You see, every disk, whether it's a CD or a DVD or a thumbdrive or a Hard Disk Drive, all store information using what's called a filesystem.  It's, well, the system or method it uses for storing files.

FAT32 is one of the most common filesystems because it's been around for a long time.  It works really well on thumbdrives, which only recently started getting over 4GB.  Unfortunately, even if you have a 32GB thumbdrive, it can only hold individual files up to 4GB, not a single 32GB file.

That's why NTFS was invented...it doesn't have that problem.  Unfortunately, it only really works well on larger drives because even if you store a 1 byte file on NTFS, it still takes up like 4,096 bytes, because of the system that NTFS uses to store the file as well as permissions for the file, etc.

Anyway, if you're just using this drive to back up linux, then the best thing to do would be to install gparted with:

sudo apt-get install gparted

And use that to erase the data on your swisnife and convert the filesystem from fat32 to ext3 or ext4 - a fast linux filesystem...which, unfortunately, windows can't read. :P

---

### Post by Giblet5 on 2009-11-17
When you buy a USB disk drive eg, Western Digital MyBook drives, they come formatted as FAT32.

FAT32 is a Windows 98 file system that is very limited. (Can't store file ownership, permissions or 2/3 of timestamps. Files can be no larger than 4GB, etc)

NTFS is the file system that modern Windows systems use. It is very limited as well, but files can be Really Big.

Linux uses ext2/3/4, or any number of other types, and they are extremely useful. Windows can't read any of those however.

You should install gparted if you haven't already (see Synaptic Package Manager). Run gparted and format that external drive as "ext3". Give it a label like "External", then it will mount as /media/External.

---

### Post by Radissthor on 2009-11-17
> **Giblet5 said:**
> When you buy a USB disk drive eg, Western Digital MyBook drives, they come formatted as FAT32.

FAT32 is a Windows 98 file system that is very limited. (Can't store file ownership, permissions or 2/3 of timestamps. Files can be no larger than 4GB, etc)

NTFS is the file system that modern Windows systems use. It is very limited as well, but files can be Really Big.

Linux uses ext2/3/4, or any number of other types, and they are extremely useful. Windows can't read any of those however.

You should install gparted if you haven't already (see Synaptic Package Manager). Run gparted and format that external drive as "ext3". Give it a label like "External", then it will mount as /media/External.

But would that disable my thumbdrive from being read by windows computers forever? I don't use Windows, but I reckon I may have to pass some files to a Windows machine sometime in the future. 

So if I have to format the thumbdrive as NTFS or FAT32, would I be able to save only 4 GB of my information?

I'm sorry for all the questions and I appreciate your patience. I've alway been told that the stupidest question is that which is not asked...:)

BTW: I'm not trying to upgrade to 9.10 or anything like that, just to change from 64 to 32 bit version. Will running the update upgrade commands do that? I didn't get the part in which I change from 64 to 32...

---

### Post by Giblet5 on 2009-11-17
FAT32 is limited to 4GB, aka 4000MB.

NTFS is not limited in this way.

Format it as NTFS and you can write (almost) any size file and Windows systems can read it.

Open a terminal window and enter the following command:

```
sudo du -sm /home
```

That will display the size of /home in megabytes (MB). An 8G thumb drive can store about 8000MB. The tar command I suggested will compress everything by about half.

So, if the du command above says /home is 10000MB, it should fit on an 8000MB thumbdrive using the command line I suggested.

If the du command says /home is 5000MB or less, you can get away with leaving the thumbdrive formatted as FAT32 because the backup file will be about half of that 5000MB.

If the du command says that /home is 50000MB, that thumbdrive can't hold it all, no matter how you format it.

---

### Post by Radissthor on 2009-11-17
I typed the 'sudo tar' command and the last few lines were:

/home/hernan/.wine/drive_c/Program Files/Roland/Virtual Sound Canvas DXi/HELP/index_ew.htm
/home/hernan/.wine/drive_c/Program Files/Roland/Virtual Sound Canvas DXi/HELP/trouble_ew.htm
/home/hernan/.wine/drive_c/Program Files/Roland/Virtual Sound Canvas DXi/RVI01Dx.dll
/home/hernan/.wine/drive_c/Program Files/Roland/Virtual Sound Canvas DXi/CWDXPX1.dll
/home/hernan/.wine/drive_c/Program Files/Roland/Virtual Sound Canvas DXi/RVI01.dat

gzip: stdout: File too large


When I typed the 'sudo du -sm /home' It replied:

hernan@Inspiron1525:~$ sudo du -sm /home
[sudo] password for hernan: 
du: cannot access `/home/hernan/.gvfs': Permission denied

I tried typing from root, but I got the same message.

I repeat the question of when exactly am I installing the 32 bit version over the 64 bit I have now...

EDIT: The 'backup.tar.gz' that was copied into my thumbdrive weighs exactly 4 GBs, so I'm guessing not all was copied...

---

### Post by Giblet5 on 2009-11-17
You will get that error message, yes, but it will also display the size of /home (it takes a few minutes to add up the sizes of the thousands of files you have accumulated).

You stopped the command before it was done, so all you got was the error message (a message which is to be expected).

Try again, except don't stop it this time: ```
sudo du -sm /home
```

The 'gzip: File too large' error is either because you left the thumbdrive formatted as FAT32 and you tried to exceed the 4GB file size limit that I have already mentioned quite a few times, OR the thumbdrive is too small to hold all of the data, even with compression.

My home directory is 422GB. There is no thumb drive made that can hold it. My wife's home directory is twice that size.

I use a Western Digital MyBook drive for backups. It holds 1TB and sells at Sam's Club for $99. I formatted it as one ext3 filesystem.


You have to complete a backup before you reinstall. Otherwise, you will lose all of your settings and data.

Do the backup. Verify it. Then reinstall.

If the data just won't fit on the thumb drive, get a bigger drive, or delete all of the stuff you don't need, and try the backup again.

---

### Post by Radissthor on 2009-11-17
I run the command again. This is what I got:

du: cannot access `/home/hernan/.gvfs': Permission denied
25850	/home


My laptop hardrive is 80GB and my thumbdrive is 200GB, so it cannot be a problem of the thumbdrive being too small. If I change to ext 3 or whatever number, I won't be able to use the thumbdrive in a Windows Computer, which is something I may want to do someday. How can I go about this?ty

---

### Post by Giblet5 on 2009-11-17
> **Radissthor said:**
> I run the command again. This is what I got:

du: cannot access `/home/hernan/.gvfs': Permission denied
25850	/home


My laptop hardrive is 80GB and my thumbdrive is 200GB, so it cannot be a problem of the thumbdrive being too small. If I change to ext 3 or whatever number, I won't be able to use the thumbdrive in a Windows Computer, which is something I may want to do someday. How can I go about this?ty

Unmount the USB drive (bring up Places -> Home and right-click the device. Select unmount.)

Use gparted - like I said before - to make that drive NTFS - like I also said before.

Mount the new NTFS partition. Follow the backup directions.

---

### Post by Radissthor on 2009-11-17
Ok So I downloaded and run gparted. I identified my thumbdrive, but I don't know how to change it from FAT32 to NTFS. There isn't an easily avialable option at hand at least.

---

### Post by Giblet5 on 2009-11-17
> **Radissthor said:**
> Ok So I downloaded and run gparted. I identified my thumbdrive, but I don't know how to change it from FAT32 to NTFS. There isn't an easily avialable option at hand at least.

Exit gparted.

Open a terminal window and enter ```
sudo gparted
```

When the interface is done scanning your disks, select the USB drive from the dropdown menu in the upper-right corner.

Right-click the FAT32 (or vfat, or fat, or whatever FAT it's called) and select "Format to -> NTFS".

When it's done, right-click the ntfs volume and select "Label". Set it to something useful like "External".

That will make it automount as /media/External which is a lot easier than some device's names.

When it's formatted and labeled, and mounted where it belongs, exit gparted and run the backup.

---

### Post by Radissthor on 2009-11-17
The format to option is grayed and cannot be used. The only options available are unmount, amnage flags and information. All other options are grayed.

---

### Post by Giblet5 on 2009-11-17
You have to unmount it before you can format it.

---

### Post by Radissthor on 2009-11-18
> **Giblet5 said:**
> You have to unmount it before you can format it.

Ok I did that. Launched gparted from terminal with the sudo code and then mounted the thumbdrive. Clicked refresh and was able to select the 'format to' menu. 

The problem is that the only available options are ext2/3/4, fat 16/32, linux-swap and reiserfs. The NTFS option is grayed and cannot be chosen.

---

### Post by beast2k on 2009-11-19
Great post, somebody should sticky this.

---

### Post by Giblet5 on 2009-11-19
Then I recommend reformatting 32GB of the USB drive as ext3. Leave the rest of the drive as FAT32.

Your /home directory is just over 25GB and, with compression (the -z flag to tar), the backup will use around 14GB.

You can still access this from Windows, but you'll have to install [this Windows driver]("http://ext2fsd.sourceforge.net/projects/projects.htm") first. Bonus: you'll be able to access your Ubuntu home directory from Windows...


I would like to hear an explanation of why you can't format the drive as NTFS. Does anybody know why that would happen?

I can do it here, on a primary partition, of a USB stick or a 320GB USB drive.

---

### Post by Radissthor on 2009-11-19
Ok.... so I connected my thumbdrive to my laptop and open gparted. After it recognized the drive, I clicked on Device and I chose "Create Partition Table". A message appeared that a default msdos partition would be created and all data would be erased. I wanted to cancel it, but accidentaly accepted and now... My drive is not recognized by gparted =( 
I unmounted and mounted again, but nothing... It doesn't appear on the desktop or in the Places Menu. What can I do? =(

EDIT: Ok, now the thumbdrive is recognized but it is no longer called SWISNIFE1, but unallocated. When I right-click it, I have no option available except 'New' and 'Information'.

---

### Post by Giblet5 on 2009-11-20
Well, your option now is "New".

Create a 32GB ext3 partition. Label it Backups.

Use the rest as FAT32. Label it SWISKNIFE1.

Do your backups on /media/Backups.

---

### Post by Radissthor on 2009-11-20
Ok, I'm a bit confused with gparted interface. How do I choose the size of the partition? What is the MiB number that sould be devboted to the ext3 partition and how do I create the FAT32 partition afterwards?

I've attached what I'm seeing now in gparted. Thanks for the help! :)

EDIT: Ok, I think I've figured that 350000 means a partition of 35 GB. Am I correct?
**My question  now is what type of partition do I choose? Extended, primary or logical partition? (logical cannot be chosen BTW, it's grayed)...**

---

### Post by Giblet5 on 2009-11-20
35,000 MiB = 35G

---

### Post by Radissthor on 2009-11-20
And what type of Partition do I have to choose?

---

### Post by Giblet5 on 2009-11-20
See post #23 above.

---

### Post by Radissthor on 2009-11-20
> **Giblet5 said:**
> Well, your option now is "New".

Create a 32GB ext3 partition. Label it Backups.

Use the rest as FAT32. Label it SWISKNIFE1.

Do your backups on /media/Backups.

My options are Primary and Extended. Logical is also present but cannot be chosen. Which should I choose?

---

### Post by Giblet5 on 2009-11-20
> **Radissthor said:**
> My options are Primary and Extended. Logical is also present but cannot be chosen. Which should I choose?

Primary for both.

Extended is useful if you have a monster 2TB drive and want to install every release of Ubuntu on one disk drive. Your drive isn't that big and you're not trying to set up dozens of partitions.

---

### Post by Radissthor on 2009-11-20
I did a successful partition and then proceeded to do the back up and then to confirm it as indicated in the first posts. These are the last lines of the backup command and then there's the output for the 
command: 

 ```
sudo tar tzf /media/USBdrive/backup.tar.gz
``` 


```
/etc/X11/ja_JP.UTF-8/app-defaults/
/etc/X11/ja_JP.UTF-8/app-defaults/TiMidity
tar: Error exit delayed from previous errors
hernan@Inspiron1525:~$ sudo tar tzf /media/USBdrive/backup.tar.gz
[sudo] password for hernan: 
tar: /media/USBdrive/backup.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
hernan@Inspiron1525:~$ 

```

So is it Ok for me to reinstall?? 

Another strange thing... I cannot see the FAT32 partition in Ubuntu. This is weird because the whole disk was, supposedly, formated as FAT32 and it could be accessed, but now only the ext3 partition is shown in the interface.

Edit: I unmounted and mounted back. Now both partitions are available. The ext3 Backups partition has two folders. One, named 'back.tar.gz' weighs 23.6 GB and the other folder is called 'lost+found' and it has like a mail symbol on it. **Do you think the backup was completed successfully? **

---

### Post by Sin@Sin-Sacrifice on 2009-11-20
> **fluffman86 said:**
> Go to Places > SWISNIFE 1, and in the window that opens up, click the little pencil or paper or something to the left of the location bar near the top.

You should see something like /media/SWISNIFE1

If there are no spaces in the name, then change /media/USBdrive/backup.tar.gz above to /media/SWISNIFE1.backup.tar.gz

Note that Linux is CASE SENSITIVE.  Meaning swisnife1 is not SWISNIFE1 or SwIsNiFe1...they are ALL DIFFERENT.

Also, the command line cannot handle spaces.  So if your drive is mounted at /media/SWISNIFE 1, then you need to change /media/USBdrive/backup.tar.gz to /media/SWISNIFE\ 1/backup.tar.gz  Note the backslash there.  It's used to "esape" or ignore the space before the 1.

And as for Giblet's process:

1. Run the command dpkg, and list the output. (that's a lower case L in his command).  Then, he uses a program called sed to strip out uneccessary information about the packages, and directs it with ">" to a file call packages.txt in your home directory.  That final part in needed because otherwise it would just show up in your terminal.

2. Next, he uses tar, the Tape Archiver, to essentially compress (like a zip or rar file in Windows) into a single file (backup.tar.gz) all of the information that's at /home, /etc/passwd, etc...  Then he verifies the information with the next command.

3. You reinstall the system, but that's not the most up-to-date stuff.  So you use apt-get to update your package list and connect to the internet to see what's new and available now, then upgrade all of the listed packages.  Some of these will include a kernel update, which means you have to reboot.

4. Now that everything's up-to-date, you need to find your archive that you made.  Again, we use the program tar to e*X*tract, from a *Z*ipped up *F*ile, and be *V*erbose (tell us what's happening) about it.

5. Finally, that's just a simple script that says
read each line of packages.txt in your home directory
then sudo apt-get install [the contents of each line]
and -yq means Yes, I want to really do that, and do it quietly without asking a bunch of questions.

If you open of that file, you'd see it says something like
vlc
gedit
gnome-terminal
...etc., etc.,...
So you want to use apt-get as a super doer to install vlc.
Then again with gedit
and so on.

Edit: now that I've read Giblet's next post, it's important to note that everything he told you to do actually *CAN* be done from the GUI...it's just much harder.  So for example if you right click on your home folder in nautilus, you can click "compress" and I believe synaptic has an option of saving all of your markings in there to transfer to another computer.

HA!! awesome explanation... reading that was much more enjoyable than a man page. You should write man pages. Call them fluffman pages. And I agree about this being a sticky.

---

### Post by Giblet5 on 2009-11-23
> **Radissthor said:**
> Edit: I unmounted and mounted back. Now both partitions are available. The ext3 Backups partition has two folders. One, named 'back.tar.gz' weighs 23.6 GB and the other folder is called 'lost+found' and it has like a mail symbol on it. **Do you think the backup was completed successfully? **

Yes, I do, but you can (and should) test it too.

```
tar tzf back.tar.gz
``` will open it. Or, you can just double-click the file from the filemager and browse the files and folders.

"lost+found" is always created on a linux or unix filesystem. That is where orphaned files get placed when you have minor filesystem corruption and fsck has fixed it. (It's for maintenance)

---

### Post by Radissthor on 2009-11-23
Thanks for replying! I thought the thread had died :D

The files in the backup are Home, which has the folders I can see in the GUI and some others that I didn't know where there, and the etc folder, which has the X11 folder and some loose files. I think eveything's in there, so I'm going to proceed to do the reinstall. I'll post back my results here. Thanks for the help!!

---

### Post by Radissthor on 2009-11-23
OK, I did everything and there's good news and bad (hopefully, easily fixed) news:

GOOD:
I run all the commands of the first Giblet5 post and everytrhing went OK. All my folders, configurations, plugins, etc..All was there, even my desktop background!!! So thanks a lot Giblet. 
This was truly helpful information! :)

BAD:
I cannot connect to internet. I can access my university's wireless signal and it says I'm connected at a 100%, but when I open Firefox it takes frever to load until it calls for an 'Addressed not found' error. I rebooted like 5 times but the problem persists. Any idea on what may be causing this problem?

Thanks again for the helP! :P And I hope this last little problem can be solved... It's the only thing missing!

---

### Post by Radissthor on 2009-11-23
Well, I finally worked out the problem. 

I had to run 

```
gksudo gedit /etc/network/interfaces
```

and I found the lines were:

```
auto lo 
iface lo inet loopback
```

So I edited the file according to an advice I received some time ago in the forum when my wireless was messed up by configuring a PPPoE connection. This is how it looks now:

```
auto lo 
iface lo inet loopback


#auto dsl-provider 
#iface dsl-provider inet ppp
#pre-up /sbin/ifconfig/eth1 up # line maintained by pppoeconf

#auto eth1
#iface eth1 inet manual
```

Then I rebooted and now wireless works like a charm. Everything is up and running so I guess that'll be all. Thanks a lot for all the help and, mostly, for all the patience you all had with me. Special thanks go to Giblet5 for all the excellent advices. 

Cheerios :D

PS: I laughed so hard whith Giblet5's edit reason on post #32 I think I now have a six-pack in my stomach, hahahaha!!! XD

---

