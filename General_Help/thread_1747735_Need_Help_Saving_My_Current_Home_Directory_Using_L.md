---
title: "Need Help Saving My Current Home Directory Using Live CD 10.04"
date: 2011-05-03
forum: General Help
---

### Post by bry72 on 2011-05-03
Hey Guys,

So I tried upgrading from 10.04 to 10.10 using the upgrade manager and my computer froze half way through.  I now get an error message that says "“The configuration defaults for GNOME Power Manager have not been  installed correctly. Please contact your computer administrator.”  I go into great detail about this issue on another thread I posted:

[http://ubuntuforums.org/showthread.php?t=1743258](http://ubuntuforums.org/showthread.php?t=1743258)

I tried all the suggestions mention in the above thread but nothing worked.

One suggestion I received was to save my current home directory using the Live CD 10.04 and then reinstall Ubuntu 10.04.

A little bit about my computer:

1.  I have a dual boot system (Ubuntu and Windows XP)
2.  I have a laptop with an 80 GB hard drive.  55 GB are for Windows XP and 25 GB are for Ubuntu 10.04.
3.  I have tried running sudo commands using the live CD but they don't seem to do anything.  I type in the sudo command and it just gives me another prompt.  No error message or anything else.

The main question I have is does saving my home directory save all the files, folders, documents, bookmarks, etc. that are currently on the Ubuntu system?  I made the mistake of not saving these things onto a CD before trying to do the upgrade.  My main concern is to be able to salvage and save this data.  Hopefully saving the home directory does that.

Hopefully someone can give me instructions on how to do this.

---

### Post by Hedgehog1 on 2011-05-03
Greetings!

1st - there is no password for root on the LiveCD/LiveUSB, so no text back on a **sudo** is normal.

Next - you might find copying your documents easier if you use nautilus as root (please use this for emergencies like this only):

```
gksudo nautilus
```

You can copy your documents to your Windows partition, an external hard drive, or a USB stick.

You may find it necessary to mount the partitions manually:

```
sudo mkdir /mnt/windows
sudo mount /dev/sda2 /mnt/windows
```
```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda5 /mnt/ubuntu
```

***The Hedge***

:KS

---

### Post by Rasa1111 on 2011-05-03
As hedge says...

Easiest way usually is to open a terminal, 
and use the first command hedge gave.
```
gksudo nautilus
```then type your password, and a new nautilus window will open (in Root).
Then you can navigate to your files, (click on the file system in nautilus where your files are),  select and copy all files you need, and save them to an external drive or wherever. 

Good luck. <3

---

### Post by bry72 on 2011-05-03
When I use the gksudo nautilus command, what items are being copied from my home directory?  Is the entire 25 GB I have partitioned for Ubuntu 10.04 being copied or is it just the files and such listed under "Places" (e.g. Documents, Downloads, Photos, etc.)

I will have to copy my home directory to my Windows partition as I don't have an external hard drive or USB stick.

What do you mean by mounting the partitions manually?  I know the computer is currently partitioned with 55 GB for Windows XP and 25 GB for Ubuntu 10.04.

Based on your post, these are the steps I need to do:

1.  Boot Live CD and open terminal.
2.  Type in gksudo nautilus.
3.  Type in  sudo mkdir /mnt/windows
4.  Type in sudo mount /dev/sda2 /mnt/windows
[FONT=monospace]5. Type in [/FONT]sudo mkdir /mnt/ubuntu
6.  Type in sudo mount /dev/sda5 /mnt/ubuntu

[FONT=monospace]Doing the above steps will copy my Ubuntu home directory and put it on my Windows partition.  I would then need to pick and choose which files from the Ubuntu home directory that is now saved on the Windows partition and save them onto a CD.  I would then reinstall Ubuntu 10.04, insert the CD with the saved files and save them in the freshly installed Ubuntu 10.04 and I should be back to where I was prior to doing the upgrade.

Is that correct?
[/FONT]

---

### Post by bry72 on 2011-05-03
> **Rasa1111 said:**
> As hedge says...

Easiest way usually is to open a terminal, 
and use the first command hedge gave.
```
gksudo nautilus
```then type your password, and a new nautilus window will open (in Root).
Then you can navigate to your files, (click on the file system in nautilus where your files are),  select and copy all files you need, and save them to an external drive or wherever. 

Good luck. <3

Since I am doing all of this from the Live CD, as I have no way of booting my regular Ubuntu OS, I should leave the password blank, correct?  The Live CD has the username listed as "ubuntu" and I know there is no password for it.

When you say "select and copy all files", will it be a matter of right clicking on a file, saving it to a folder on my desktop and once I have retrieved all the files I want, burn them all to a CD?

Your method seems much simpler than Hedgehog1's but is it possible to take out the Live CD and then burn the files to another CD?  Wouldn't the Live CD have to remain inserted into my disk drive in order for it to run?

If the Live CD does have to remain in my disk drive in order to run, how would I transfer the folder of files I want to save over to my Windows partition?

---

### Post by Hedgehog1 on 2011-05-03
The above steps don't copy anything.  Let me explain each one:

This is nautilus:

[IMG]http://img546.imageshack.us/img546/5255/screenshotnatu.png[/IMG]

Nautilus is the GUI that lets us move and view and copy files.  

Normally, nautilus runs with just the access right you have as a user.

But for emergencies, we sometimes want to run it in 'God Jr.' mode where we can do anything.  That mode is: **root**. Root as also known as **Super User** - and **sudo** means **S**uper **U**ser **DO**

When you want to run a graphical program like nautilus, we have to use the gnome friendly version of **sudo**: **gksudo**.

Hence the command:

```
gksudo nautilus
```

The mount commands allow access to your Ubuntu disk partition and your Windows disk partition.

You may not need to do them manually, but if you do, they will make the windows partition appear as:

**/mnt/windows**

And the Ubuntu partition appear as:

**/mnt/ubuntu**

You will then have to use nautilus to manually copy your files from one partition to the other.

There is no automatic copying in these commands - you are left in complete control at all times.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-03
> **bry72 said:**
> If the Live CD does have to remain in my disk drive in order to run, how would I transfer the folder of files I want to save over to my Windows partition?

After you select 'TRY', Ubuntu is loaded into a 'RAM Disk'.  As long as you don't select 'install', you can then remove the CD and burn one with a backup of your files.

It is more complicated, but do-able.

***The Hedge***

:KS

---

### Post by bry72 on 2011-05-03
So wouldn't I first want to run the sudo mount commands so I can have access to the "real" Ubuntu partition, rather than the info that is on the Live CD?

The reason I ask is that one of the suggestions was to run the Live CD, open a terminal and type "sudo apt-get clean".  This was suppose to clean out the cache and free up disk space as the error message of "“The configuration defaults for GNOME Power Manager have not been  installed correctly. Please contact your computer administrator.” is normally attributed to not having enough disk space.  Then they gave me another command to run to see how much disk space I had.

When I ran the sudo apt-get clean command, nothing happened.  I then ran the command to see how much disk space I had, and it amounted to MB, not GB. It was reading the amount of space from the CD, not from the partition on my hard drive.

So just to make things easier, what would be the exact steps I would need to do in order to get access to the "real" Ubuntu partition using the Live CD, find the files I want to keep, put them in a folder on my desktop and then transfer that folder over to Windows so I can burn those files onto a CD.

---

### Post by Hedgehog1 on 2011-05-03
OK - step by step.

1- boot from the live CD, select 'TRY'.

2- do these five commands in order:

```
sudo mkdir /mnt/windows
sudo mount /dev/sda2 /mnt/windows
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda5 /mnt/ubuntu
gksudo nautilus
```

3- you will see this:
[IMG]http://img546.imageshack.us/img546/5255/screenshotnatu.png[/IMG]

4- Using nautilus - make a new directory in **/mnt/windows** called **savedhome**

5- Using nautilus - copy the files from the **/mnt/ubuntu/home** folder to the **/mnt/windows/savedhome** folder.

I can't think of any way to explain it easier.

***The Hedge***

:KS

p.s. You can run FireFox from the LiveCD and access the Ubuntu Forums if you get stuck.

---

### Post by Rasa1111 on 2011-05-03
> **bry72 said:**
> Since I am doing all of this from the Live CD, as I have no way of booting my regular Ubuntu OS, I should leave the password blank, correct?  The Live CD has the username listed as "ubuntu" and I know there is no password for it.

When you say "select and copy all files", will it be a matter of right clicking on a file, saving it to a folder on my desktop and once I have retrieved all the files I want, burn them all to a CD?

Your method seems much simpler than Hedgehog1's but is it possible to take out the Live CD and then burn the files to another CD?  Wouldn't the Live CD have to remain inserted into my disk drive in order for it to run?

If the Live CD does have to remain in my disk drive in order to run, how would I transfer the folder of files I want to save over to my Windows partition?


Hmm..

Just had a thought I seem to have forgot about.. lol

 If I am correct, (Hedge please stop me if Im wrong)..

You should be able to boot the CD, open nautilus in root, 
then 'mount' (or open) your 55 GB file system,
and also your 25 GB file system,
and copy the files from the 25GB system over to the 55 GB. 

So, If I am not wrong ... (I have done things just like this in the past)
and what I'm thinking would/will work..
Theoretically I would~
~Boot into the live CD 
~open a terminal and put in **gksudo nautilus**
~when nautilus window opened, I would (as you see in screenshot)
Open (or "mount") one of the partitions by right clicking it in the left panel
and choosing "open in new tab" (or new window), doesn't matter. 
Then do the same for the other partition. 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190951&stc=1&d=1304400220[/IMG]

 Once both are mounted/opened, I would create a folder in the 55GB file system, (probably on its desktop where its easy to find temporarily)

Then I would select any of the files I needed to keep from the 25 GB partition window.
> When you say "select and copy all files", will it be a matter of right  clicking on a file, saving it to a folder on my desktop and once I have  retrieved all the files I wantClicking on any file will 'select' it, it can be one file, or a number of files (or all files)
Once "selected" (or highlighted) you can simply right-click, choose 'Copy', and then "paste" those files into another folder (like the one I theoretically made in the 55GB partitions desktop).

So,
"highlight/select' any files, right click and "copy"
then open the new folder where you want them to go, right click in the empty folder, and "paste". 

 *If* I am not mistaken here somewhere,
 The files would then copy over into the folder we made on the windows xp desktop/55GB partition. 
and once finished, all our files would now be there, in their own folder on the windows XP desktop (pretending thats where we made the new folder) once we booted into it. . lol

 I really hope I am not mistaken or have missed something crucial.. lol

Ive gone over it in my head a few times now, and dont see why it wouldnt work...
as Ive done virtually the same thing myself in the past. (without the windows).

Hedge, or anyone else..
Please tell if I am mistaken...

and bry72,
I hope what Ive said will work for you!
but maybe we should wait for a 2nd opinion..:confused: lol

 I don't think it would hurt to try, as long as you know your way around the windows file system enough to be able to create a new folder where you want , to copy files to.

Good luck and please forgive if Ive given bad advice. lol 
Im not very familiar with anything windows these days. :lol: <3

---

### Post by Hedgehog1 on 2011-05-03
Rasa1111's description is the variation without the mount commands.  It should work fine.  I had only added the mount commands because some users had reported issues with mounting external USB drives from nautilus, and had to mount them manually. They were 'just in case'; but got pulled into the step-by-step.

Both roads lead to Rome...

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-03
> **mach12324 said:**
> thanks for your valuable information

With a **hedgehog** and an **astronaut** on the case - there is lots of good info to be had!

Hope it helps you!

***The Hedge***

:KS

---

### Post by Rasa1111 on 2011-05-03
> **Hedge~**Rasa1111's description is the variation without the mount commands.  It should work fine.  

ahh cool! Good to know, thanks! lol
Glad I'm not going *more* nuts. :lol: Thanks! <3

See, my newbness really shows..
instead of a few simple commands I go for the looong graphical way. lol doh! 

I figured there might be some USB issues like you said..
but if he's not using one, and just transfers from one system to the other..
I think it should be ok?

>  					Originally Posted by **mach12324** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10761163#post10761163") 				
 				[I]"thanks for your valuable information"-

[/I]
 			 		 	 	 With a **hedgehog** and an **astronaut** on the case - there is lots of good info to be had!

Hope it helps you!



 haha!! :lol: 

hope it can help mach12324. :)

---

### Post by bry72 on 2011-05-03
I just tried using my 10.04 Live CD.  I should point out before I give you my results that this CD takes forever to boot and it does not give a "Try" and "Install" screen.  It just goes straight into "Try" and has an icon on the desktop to "Install Ubuntu 10.04".  I downloaded Ubuntu 10.04 from the ubuntu website and burned the CD myself.  This is not an official Ubuntu 10.04 CD.

Anyway, here is what happened.  I typed in the first command line and it gave me a prompt.  I typed in the second command line and accidentally forgot to put a space between /sda2 /mnt/windows.  It gave me an error message of:
 
"mount: can't find /dev/sda2/mnt/windows in /etc/fstab or etc/mtab"

I figured since I made an error, I would exit out of the terminal and open the terminal again.  When I put in the first command line, it gave me this:

  "mkdir: cannot create directory '/mnt/windows': Files exists."
 
I continued with the rest of the command lines and when I put in gksudo nautilus, I got this:

"Nautilus share-message:  Called "net usershare info" but it failed: 'net share' returned error 255:  net usershare: cannot open usershare directory /var/lib/samba/usershares.  Error no such file or directory.  Please ask your system administrator to enable user sharing."

It did open the nautilus screen but as suspected it only gave me the files from the Live CD.  Only 22 items and 166 MB.

I then logged out and logged back in and opened the terminal.  This is what I got after I typed in the first command line:

ubuntu@ubuntu:~$ sudo mkdir /mnt/windows
mkdir: cannot create directory `/mnt/windows': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt windows
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount.

I have an official Ubuntu 10.10 installation disk that I am going to use in "try" mode and see what happens.  If that doesn't work, I will try and download Ubuntu 10.04 again and burn a new CD to see if that helps.

---

### Post by bry72 on 2011-05-03
I just tried the official Ubuntu 10.10 Live CD.  When I clicked the "try" mode, it took me to a blank screen with a mouse pointer.  I waited 5 minutes but it did not take me to the desktop screen.

Tomorrow, I will try and download Ubuntu 10.04 again and burn another CD.

If that doesn't work, I am wondering if there is a way to do this from the Windows XP side.  Meaning, is there a way to transfer the home directory of Ubuntu over to Windows while using Windows XP.

---

### Post by Rasa1111 on 2011-05-03
Do you have a flash drive that you can run Ubuntu from?
It is* much* faster and less 'problem prone' than CD's in my experience. 
Just learned this a few months ago myself. lol
A handful of times Ive had CD's fail constantly, but the same thing on a USB drive goes flawlessly. 
Maybe worth a shot?

Im not sure if you can access the Ubuntu side from XP..
But for some reason I do think ive read about it around here before.

Sorry i cant be more help. :???:

---

### Post by bry72 on 2011-05-03
Rasa1111,

I booted the Live CD 10.04, opened the terminal and typed in "gksudo nautilus".  The screen then went blank for a short period of time and then gave me a login screen.  I typed in "ubuntu" as the username and just hit enter for the password (did not enter any letters).  It accepted this and took me back to the desktop screen.  I then opened the terminal again and typed in "gksudo nautilus".  It gave me this error message:

"Nautilus share-message:  Called "net usershare info" but it failed:  'net share' returned error 255:  net usershare: cannot open usershare  directory /var/lib/samba/usershares.  Error no such file or directory.   Please ask your system administrator to enable user sharing."

Just as before, it did open the nautilus screen but it only gave me the files from the Live CD.  Only 22 items and 166 MB.  It did not list any of my partitions in the left hand panel.

Perhaps someone knows of a way to transfer the files from Ubuntu into Windows while working in Windows XP?

---

### Post by Rasa1111 on 2011-05-03
Man, I don't know whats going on over there. :???:

 I just found this though...[http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html](http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html)
I wonder if it can help you?

also this~ [http://www.fs-driver.org/](http://www.fs-driver.org/)

For accessing your Ubuntu files from Windows., 

Still looking though.....

---

### Post by bry72 on 2011-05-04
> **Rasa1111 said:**
> Man, I don't know whats going on over there. :???:

 I just found this though...[http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html](http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html)
I wonder if it can help you?

also this~ [http://www.fs-driver.org/](http://www.fs-driver.org/)

For accessing your Ubuntu files from Windows., 

Still looking though.....

Rasa1111, you did it!  The website link you provided to ubuntugeek.com  has four programs you can run.  I tried Ext2 and explore2fs but neither  worked.  I wasn't going to bother with the other two because they say  they only read files, not write.  However, I wanted to see if anything  was still on the Ubuntu partition so I installed and ran Disk Internals Linux Reader.

I was able to see all the files on the Ubuntu partition.  Then I noticed in the bottom left hand corner under "File and Folder Tasks", it had "Add to recovery list" and "Recover the selected items".  So I added some files but figured when I hit "Recover the selected items" it was going to give me a message saying, "You can only read files, not write."

BUT, it took me to a wizard asking me where I wanted to save my files on the Windows XP side and it worked!

The only glitch I found was when I went into the .mozilla folder and saved the "Bookmarks.html" file.  When I opened it up, it does not have any of my bookmarks at all.  There is another folder called "bookmarkbackups" but the files in there have an extension name of .json, not .html.  I tried opening one but no program would open it.

I'll have to dig through the folders some more because I do want to find the bookmarks.html file.

Other than that, I am VERY happy!  Finally figured out a way to save my files thanks to you.  :D

I downloaded the Ubuntu Rescue Remix ISO and I might try it just to see if it can put the partition back to how it was.  If not, no biggie as I have the files I want and I can just do a reinstall of 10.04.

Thanks again, Rasa1111, for taking the time to find those websites.  I really appreciate it.

---

### Post by Rasa1111 on 2011-05-04
Good news! :D Woohoo! 

You're most welcome bry!

Very glad it helped! :D

I'm unsure of how to work out that bookmarks thing. 
I havent even used firefox regularly for about a year. 

Maybe...
Our friend Loving Linux (Firefox pro!) , would be able to help if you asked him?
[http://ubuntuforums.org/member.php?u=649167](http://ubuntuforums.org/member.php?u=649167)

Im happy it worked out for you man! 
Nothing better than when things work how we need them to! 
Especially after everything else fails!  lol :)

<3

---

### Post by lovinglinux on 2011-05-04
The bookmarks.html file is no longer used since Firefox 3, that's why it is almost empty. Although you can export/import bookmarks as html files, your bookmarks are stored in the places.sqlite database file. Just copy that and you are ready to go.

If your places.sqlite file became corrupted, you can restore a backup using those json files. Don't need to open them. Just go to the bookmark manager, then select the "Import and Backup" menu and click the latest date in the backup list or open a json file.

You might also want to copy *signons.sqlite* and *key3.db* that store your passwords and encryption key.

Let me know if you need anything else from Firefox that I point to the file you need to copy.

---

### Post by bry72 on 2011-05-04
> **lovinglinux said:**
> The bookmarks.html file is no longer used since Firefox 3, that's why it is almost empty. Although you can export/import bookmarks as html files, your bookmarks are stored in the places.sqlite database file. Just copy that and you are ready to go.

If your places.sqlite file became corrupted, you can restore a backup using those json files. Don't need to open them. Just go to the bookmark manager, then select the "Import and Backup" menu and click the latest date in the backup list or open a json file.

You might also want to copy *signons.sqlite* and *key3.db* that store your passwords and encryption key.

Let me know if you need anything else from Firefox that I point to the file you need to copy.

Lovinglinux, I responded to you in a private message but I'll go ahead and post it here so others can read what worked for me and what didn't.

I tried opening the *places.sqlite* file using:
Import and Back>Restore> Choose File> and changed the file type  from JSON to "All Files" and opened places.sqlite.  It gave me an error  message of "Unsupported File Type".

However, I used the same path as above to open the most recent *.json*  file and it restored all of my bookmarks.  Thanks for your help!

In regards to *signons.sqlite*, I never save passwords in Firefox so I don't think I need that file.  Would what I need the *key3.db* encryption key for?

Is there a file in the .mozilla folder that has all the add-on's and add-on settings that I can save and add back on to Firefox?

I don't think I'm going to bother with the Rescue Remix ISO CD unless someone thinks there is a chance it could restore the Ubuntu partition.  Since I was able to save the files I needed from the Ubuntu partition, I think reinstalling 10.04 would be the easier way to go.

Before I do the re-installation, should there be any other files or folders that you guys feel I should look into?  I looked at and saved files from the following folders located in the "home directory":

1.  .mozilla folder to retrieve bookmarks.
2.  Documents folder
3.  Download folder
4.  Desktop folder
5.  Pictures folder

---

### Post by Rasa1111 on 2011-05-04
2 for 2! alright! :D lol

Thanks L.L.! <3

I would just do a fresh install also.

 Unless there are some settings that you want saved from some of your apps/programs, or config. files..
You shouldnt need to have to copy anything except for your own personal files you want.
Which seems like you're squared away on. 

 When you go to the contents of your home folder. and press **Ctrl H **(in Ubuntu, not sure about windows), a bunch of hidden files will become visible. 
Most of these are folders for different apps, configuration files and settings you've saved.

 Unless there is something you really worked a long time on getting 'just right', 
such as a conky configuration, and conky folder, or whatever else,
You probably don't need to bother. 

But you might want to check out the hidden files anyway, just in case there's something you might want? lol

Good luck. 

:)

---

### Post by lovinglinux on 2011-05-04
> **bry72 said:**
> I tried opening the *places.sqlite* file using:
Import and Back>Restore> Choose File> and changed the file type  from JSON to "All Files" and opened places.sqlite.  It gave me an error  message of "Unsupported File Type".

The places.sqlite cannot be imported through the backup menu. All you need is to place that file inside the new profile folder. However you don't need to do that now, because you have already restored the bookmarks. Additionally, you cannot open sqlite files without a database reader.

> **bry72 said:**
> However, I used the same path as above to open the most recent *.json*  file and it restored all of my bookmarks.  Thanks for your help!

You are welcome. That is the correct procedure.

The backup feature of Firefox bookmark manager can only import/export json or html. You can also add opml support with a third party extension. But sqlite no. 

> **bry72 said:**
> In regards to *signons.sqlite*, I never save passwords in Firefox so I don't think I need that file.  Would what I need the *key3.db* encryption key for?

If you use a Master Password to protect the passwords saved by Firefox, then you cannot open the passwords database unless you have an encryption key. The key3.db file stores that key. If your key3.db file becomes corrupted, then you cannot open your passwords anymore. 

You do not need it if you do not save passwords in Firefox.

> **bry72 said:**
> Is there a file in the .mozilla folder that has all the add-on's and add-on settings that I can save and add back on to Firefox?

Yes. Inside your profile folder there is a folder named "extensions".

Have you tried to copy the entire ~/.mozilla folder? If your profile is not corrupted, then you can simply transfer the ~/.mozilla folder to a new machine or installation.

> **bry72 said:**
> I don't think I'm going to bother with the Rescue Remix ISO CD unless someone thinks there is a chance it could restore the Ubuntu partition.  Since I was able to save the files I needed from the Ubuntu partition, I think reinstalling 10.04 would be the easier way to go.

If you have the files you need, then re-installing from fresh is the best option. I never do upgrades, only clean installs.

Make sure you create a separate partition for home, so whenever you need to reinstall the system, you don1t need to mess with personal files and configuration, as long as you don't format the home partition.

> **bry72 said:**
> L

Before I do the re-installation, should there be any other files or folders that you guys feel I should look into?  I looked at and saved files from the following folders located in the "home directory":

1.  .mozilla folder to retrieve bookmarks.
2.  Documents folder
3.  Download folder
4.  Desktop folder
5.  Pictures folder

Assuming there is nothing corrupted in your user directory, you could copy everything starting with a dot, since they are configuration folder and files.

---

### Post by bry72 on 2011-05-06
What a nightmare!  So I tried installing 10.04 using a CD and I messed up somehow when it came to reinstalling over the old 10.04.  When I rebooted, I no longer had a grub menu.  It only gave me a prompt of "grub rescue".  I couldn't get into Windows so I tried installing the official 10.10 CD.  It gave me an error message regarding something about the CD drive.  I tried again with the 10.04 CD and no luck.

I ended up wiping my whole hard drive, reinstalling Windows and then downloading 10.04.  Instead of wasting my time burning it to a CD, I took Rasa1111's advice and bought a USB flash drive.  I installed 10.04 onto it.

Then I tried using the boot menu to boot from "Removable Devices".  No luck.  Must be because I have an older computer.  I did some research and found a program called "Plop Boot Manager".  Link is here:

[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

I used the instructions for burning the ISO to a CD.

 I then rebooted my computer with the Plop CD in the drive and the USB drive in one of the slots.  I selected the CD drive from the boot menu and the Plop menu came up.  I selected USB and ......it worked!

Holy cow, I can't believe how ridiculous this whole ordeal was.  All because I tried upgrading from the upgrade manager.    :icon_frown:

My advice to anyone reading this thread is to do what Rasa1111 recommends.  Instead of trying to use the upgrade manager to upgrade from one version to the next, simply download the new version from the ubuntu website, burn it to a USB flash drive and install it that way.

A lot of people have problems installing from a CD, especially if you burned it yourself.  It has something to do with the speed in which it is written to the CD.  Even the official 10.10 CD didn't work for me and that came straight from Ubuntu!

If your computer is older and you can't get it to boot from the USB drive, use the plop software (link above).

Hope this thread helps anyone who has a dual boot system with Windows and has their Ubuntu OS crash on them.  Now you have the means to retrieve files from Ubuntu while in Windows, an easier way to reinstall Ubuntu using a USB flash drive and the Plop software to help if you have an older computer that doesn't boot from a USB.

After almost a week of dealing with this, I can now officially say this thread is SOLVED.  :guitar:

---

### Post by Rasa1111 on 2011-05-07
Hi bry!

haha!  

 Well Im glad you got it worked out in the end!
it sounds like you did very well with what was thrown at you! 
Good job. Congrats :)

I have never heard of 'plop', but sure could have used it a few times! lol
Nice find!
I might have to check that out on my desktop that also wont boot from USB.

Welcome to one of the 'fun' parts that is breaking and fixing your system! :lol:  lol

Feels good to have it worked out though eh? 

Good to hear! thanks for the update. :)
Have fun man. <3

---

### Post by manofstee1 on 2011-07-18
Can someone help me with this issue. I need to know how to transfer my files to and external hard drive. Any help would be greatly appreciated.

---

