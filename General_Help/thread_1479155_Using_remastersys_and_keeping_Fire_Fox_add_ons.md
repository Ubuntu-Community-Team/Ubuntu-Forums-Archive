---
title: "Using remastersys and keeping Fire Fox add ons?"
date: 2010-05-10
forum: General Help
---

### Post by CharlotteThe57th on 2010-05-10
Does anyone have a method to make sure my Fire Fox add-ons are kept when I make a custom Live CD using remastersys :confused:

I want to make sure my custom Live CD already has add-ons that don't need re-installation, such as AdBlockPlus and FireGPG, I want to share the custom Live CD and some of the prospective users are technic phobics! 

There must be a simple way to achieve this, such as restricting add-on file permissions so they can't be removed during remastersys Live CD process.

Cheers
Charlotte

---

### Post by Fenris_rising on 2010-05-10
Hi There

Hope I get this right, I did the same a while ago, just add the mozilla folder to the 'skel' folder. When you use remastersys the skel folder is copied and the info therein zapped back into place when you use the disk.

regards

Fenris

---

### Post by CharlotteThe57th on 2010-05-11
Cheers for this, could you explain further.

I have located the skel folder but it is a read only root folder, so I am not sure how to use it.

If I put all of the Mozilla folder inside this skel folder how does this ensure that when I start Fire Fox the add-ons will work and not need to be reinstalled?

> **Fenris_rising said:**
> Hi There

Hope I get this right, I did the same a while ago, just add the mozilla folder to the 'skel' folder. When you use remastersys the skel folder is copied and the info therein zapped back into place when you use the disk.

regards

Fenris

---

### Post by warfacegod on 2010-05-11
To write to root folders, you need to be root. Hit Alt+F2 and type gksudo nautilus in the text box, hit Enter. After you enter your password, a new file browser will open with root privileges.

Use caution when root. You can do serious damage to the OS as root.

---

### Post by CharlotteThe57th on 2010-05-11
Cheers, very useful tip.

Can you recommend how to ensure documents/files I place in my desktop also get included in the livecd iso?

It looks like I need to download a copy of an Ubuntu guide, so I can get the most out of your help.

> **warfacegod said:**
> To write to root folders, you need to be root. Hit Alt+F2 and type gksudo nautilus in the text box, hit Enter. After you enter your password, a new file browser will open with root privileges.

Use caution when root. You can do serious damage to the OS as root.

---

### Post by warfacegod on 2010-05-11
Can't help you there. I've only just started playing with remastersys myself. I would imagine that, if its in the Desktop folder, it will be part of the .iso.

---

### Post by warfacegod on 2010-05-11
Ubuntu users guide: [http://ubuntuforums.org/showthread.php?t=1052065]("http://ubuntuforums.org/showthread.php?t=1052065")

---

### Post by CharlotteThe57th on 2010-05-11
Cheers when I make a custom iso with remastersys anything I have placed on the Desktop vanishes, I am trying to keep certain how-to documents on the desktop and short-cuts to new software, with a view to helping newbies  more easily usecustom LiveCD and not be daunted by a system they are unfamiliar with.


> **warfacegod said:**
> Can't help you there. I've only just started playing with remastersys myself. I would imagine that, if its in the Desktop folder, it will be part of the .iso.

---

### Post by ezsit on 2010-05-11
> I am trying to keep certain how-to documents on the desktop and short-cuts to new software

I did this a while ago, so my memory might not be 100%, but I:

(requires root) 
1. created a folder in /opt, something like: /opt/docs and 

(requires root)
2. copied all my documents I wanted on the desktop in that folder (it was only several pdfs and such). 

3. I then created links on the desktop to the files located in the /opt/docs folder. 

(requires root)
4. Lastly, I copied the /home/username/Desktop folder to the /etc/skel folder, 

and made my remastersys dist mode remaster. The desktop icons all appeared on the desktop and when clicked on, opened the files from /opt/docs just like they were supposed to do.

Creating /opt/docs folder requires root, copying docs into the folder requires root, copying the /home/username/Desktop folder into /etc/skel requires root. Creating the links on the desktop does not require root. I have always used the terminal to do my root required jobs like copying files and creating folders, so forgive me not knowing how to do so within Nautilus.

---

### Post by warfacegod on 2010-05-11
Don't worry about it ezsit, I covered root file browsing with Nautilus in post #4.

---

### Post by CharlotteThe57th on 2010-05-16
Thanks, I gave suggestions 1. and 2. ago, but I am getting stuck/trapped by my 'Windows' mind-set and cannot work out suggestions 3. and 4. 

Not wishing to appear to dumb I can't quite figure out how to create links from the "desktop to the files located in the /opt/docs folder."  and then how to do suggestion 4.

I also want items inside the new LiveCD Desktop persistent folder to be read-and-write enabled.

I am using Nautilus to undertake this, a the command line is a bit too far for me to sort out.

Any help appreciated, as I am sure many newbies would like to do similar tasks.


> **ezsit said:**
> I did this a while ago, so my memory might not be 100%, but I:

(requires root) 
1. created a folder in /opt, something like: /opt/docs and 

(requires root)
2. copied all my documents I wanted on the desktop in that folder (it was only several pdfs and such). 

3. I then created links on the desktop to the files located in the /opt/docs folder. 

(requires root)
4. Lastly, I copied the /home/username/Desktop folder to the /etc/skel folder, 

and made my remastersys dist mode remaster. The desktop icons all appeared on the desktop and when clicked on, opened the files from /opt/docs just like they were supposed to do.

Creating /opt/docs folder requires root, copying docs into the folder requires root, copying the /home/username/Desktop folder into /etc/skel requires root. Creating the links on the desktop does not require root. I have always used the terminal to do my root required jobs like copying files and creating folders, so forgive me not knowing how to do so within Nautilus.

---

### Post by Oasu4g on 2010-05-16
I believe Remastersys gives you the option to do just what you're trying to accomplish.

Have you tried Backup complete system including User Data?

---

### Post by CharlotteThe57th on 2010-05-16
I will give that a try, maybe remastersys, could also give a Dist option that includes all user data, as I am using a fresh install, adding some Fire Fox add-ons and putting things on the desktop etc. But does this make a new iso suitable to be used as a Distro/LiveCD, when using the complete the backup option and one that does not need my use **my** password for anyone to log in?

---

### Post by Oasu4g on 2010-05-16
Probably not, but I don't know. Let us know if that option in Remastersys does what you want it to. I've been wondering if it really works, but have never been able to find an excuse to try it yet.

---

### Post by CharlotteThe57th on 2010-05-17
The Backup LiveCd, including the settings and documents option requires a **password** to log-on, so that's a non starter :(

It would seem Remastersys should have an option for fresh Ubuntu install's, so the new user can just use it to customize apps like Fire Fox and place items and links on the Desktop etc, purely done with the view of creating a LiveCd Dist for friends. 

Otherwise just making a LiveCd Dist for friends without retaining any Settings, Desktop or Apps customization could be achieved via Ubuntu Custom Kit, which usefully does not require a complete install to work, as it creates a customized LiveCd directly from an iso. I have tried out UCK, but it is too limited for my purposes, as it cannot do anything in relation to settings or keeping Desktop items etc.

Remastersys is a great package, but there must be many people who could benefit from creating a LiveCd Dist, that includes Documents and Settings and crucially **no** password should be required to log on to this type of Live Cd creation. Call it Back-Up lite!

> **A. Tim said:**
> Probably not, but I don't know. Let us know if that option in Remastersys does what you want it to. I've been wondering if it really works, but have never been able to find an excuse to try it yet.

---

### Post by qwerty2009 on 2010-05-17
of-coarse it needs you to enter your password for root privileges, how els do you expect it to copy the root folders?

---

### Post by CharlotteThe57th on 2010-05-17
It requires the user's password to use the created LiveCd when using the backup option. 

When using the Dist for friends option, no password is needed to run the LiveCd, but this does not include the documents and settings like the backup iso LiveCd version.

For me to make a really useful LiveCd for friends,that needs no password to log-on, with absolutely no intention to install.

I need a straight forward way create the LiveCd that retains FireFox add-ons and Desktop items and links, not one that means such would need to be added every time the LiveCd is run, which is impractical and beyond the patience and ability of friends.

> **qwerty2009 said:**
> of-coarse it needs you to enter your password for root privileges, how els do you expect it to copy the root folders?

---

### Post by CharlotteThe57th on 2010-05-19
I have managed to create live cd/usb that retains all the settings and  desktop items, my placing things in the skel folder. 

My earlier errors seem to stem from not accessing my username folder  under root as well as with root access to the skel folder.

Thanks to all who helped me learn this solution to what I hope will be a  powerful tool in sharing my custom iso's with others.

The guide on [http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys) was  particularly helpful and all those who gave tips on this forum:

[http://ubuntuforums.org/showthread.php?t=1487500](http://ubuntuforums.org/showthread.php?t=1487500)
[http://ubuntuforums.org/showthread.php?t=1479155](http://ubuntuforums.org/showthread.php?t=1479155)

Of course one has to thank the developer of Remastersys for creating  something that newbies like me can work with.

---

### Post by Fragadelic on 2010-05-26
You can use backup mode quite easily to do what you want but any new user created won't have the same info as the /etc/skel folder is the user skeleton folder.

If you use backup mode, just clear the user password and set the system to autologin.  It will then work exactly like the normal live dist mode.

Setting user defaults either in the global gconf database or in /etc/skel is the way to set system wide defaults.  Just be careful not to have anything user specific in /etc/skel or have any actual user folders mentioned by name as they will cause the live user creation to fail.

Stay away from putting any wine folders there too since they will prevent the live scripts from creating the live user during bootup.

The bottom line is that remastersys is a tool that simply makes a live system of your install.  If you have your system setup properly for dist mode, when you run remastersys in dist mode it will give you exactly what you expect.  If it isn't what you expected then your system isn't setup properly.

After making any global gconf changes or /etc/skel additions,etc, create a new user and login as that user to ensure everything is as you expect it.  If it isn't, remove the user, make your changes and make a new user to test with.

Once you are done with testing, ensure that all the temp users are removed from the system before you make the remaster.

Due to the vast amount of different combinations in desktops and app choices it isn't reasonable to expect remastersys or any other single app to prepare your system for dist mode.  It is up to you and I guarantee that you will learn a lot about how the apps all work together and how you can make them behave however you want to in the process.

It is also for this reason that I normally only provide dist mode support on my forum for a donation.  It ensures I will stay motivated enough to continue working on it and ensures me that you are serious enough to learn.

I've been using linux since 1996 and have been creating and helping out with distributions since 2003 and while I'm not an expert by any means I have enough knowledge to help most folks out with dist mode.

The odd time when someone such as the original poster of this thread is nice enough to ask me very politely in a PM I will also help.  My apologies for not replying sooner as things have been quite busy with a couple of my other projects lately.

---

### Post by Fragadelic on 2010-05-26
You can also install firefox extensions and themes globally from the command line but it isn't really documented.

as root run the following commands:

To become root "sudo su" put in your user password and you will be root.

For a global theme:

firefox -install-global-theme theme-file-you-downloaded.jar

And yes that is only a single - before install.

For extensions like adblock or whatever:

firefox -install-global-extension extension-you-downloaded.xpi

There is one major caveat though.  A large number of extensions and themes were not written with being made global defaults in mind so they may fail as they do not have all that is required to be setup as a global default.

Just delete the folder for the bad extensions and remove the .mozilla user folders afterwards but remember that this will remove everything so only do testing with a test user setup.

---

### Post by philinux on 2010-05-26
> **Fragadelic said:**
> You can use backup mode quite easily to do what you want but any new user created won't have the same info as the /etc/skel folder is the user skeleton folder.

If you use backup mode, just clear the user password and set the system to autologin.  It will then work exactly like the normal live dist mode.

I'm using virtual box with peppermint installed. Both modes work fine. Great job by the way.

How do I clear the user password?

---

### Post by Fragadelic on 2010-05-26
become root:
sudo su

then delete the password:
passwd -d username

That will delete the password for "username"

---

### Post by philinux on 2010-05-26
> **Fragadelic said:**
> become root:
sudo su

then delete the password:
passwd -d username

That will delete the password for "username"

Cheers I was just looking at man passwd lol.

---

### Post by Fragadelic on 2010-05-26
This is ok for a live system but you will want to set a password back after you remaster.  Also remember that this passwordless user will also be present on the system you install from the livecd.

---

### Post by Fragadelic on 2010-05-26
If you use dist mode then you don't have to worry about any of this as the live user is created during bootup of the live system.

---

### Post by philinux on 2010-05-26
ah 2 things the dist mode stops for a username and password. Had to use custom for user and hit enter. Also at boot up it stops after the peter anvin bit with the message boot.. You have to hit enter to proceed.

---

### Post by Fragadelic on 2010-05-26
That's because the syslinux package in Ubuntu is modified to ignore the "prompt 0" option.  The gfxboot stuff they put in it apparently needs "prompt 1" so they just hardcoded it in to ensure their nice boot graphics work.

As soon as you press enter it will give you the menu.  If it really bugs you, just pin the syslinux package and download the original source, compile and install it and then it won't stop at the boot: prompt.

---

### Post by philinux on 2010-05-26
I can live with that. What about needing to put custom as a username with dist mode. Cheers.

---

### Post by Fragadelic on 2010-05-26
You shouldn't need "custom" as the username but there are a bunch of names they will not let you use.

What name are you trying to use?

---

### Post by philinux on 2010-05-26
I just got a vanilla peppermint instal. Used the dist option and it stops unexpectedly with a gmd login. Google a bit and found the user custom would work. Is it a bug.
Or should i have setup auto login

---

### Post by Fragadelic on 2010-05-26
With the new ubuntu 10.04, you have to make sure the custom gdm conf file is empty.

---

### Post by philinux on 2010-05-26
> **Fragadelic said:**
> With the new ubuntu 10.04, you have to make sure the custom gdm conf file is empty.

Ah righto which file is that? I'm making a livecd for daughter with broadcom drivers installed. And a couple other apps.

---

### Post by Fragadelic on 2010-05-26
Remove /etc/gdm/custom.conf or move it somewhere else then put it back after you remaster.

---

### Post by philinux on 2010-05-26
Thanks a bunch. Glad you all sorted too I followed your thread in the cafe.

---

### Post by Fragadelic on 2010-05-26
Yes its a lot of fun when the hosting provider gets hacked and refuses to admit it or do anything about it.

Got the domain as well but to smooth things out I just brought back the old site so folks wouldn't have to go changing their repo info and everything.

---

### Post by philinux on 2010-05-27
> **Fragadelic said:**
> Remove /etc/gdm/custom.conf or move it somewhere else then put it back after you remaster.

This file does not exist :confused:

---

### Post by Fragadelic on 2010-05-27
It will only show up if you made some login manager changes as that is where it puts them.  Its ok if they don't exist.  That just means you didn't make any changes to gdm.

---

### Post by philinux on 2010-05-27
Pffft my fault I'm using peppermint so it's lxdm

I've set lxdm to auto login and I've tested it works.

---

### Post by Fragadelic on 2010-05-27
Casper will only setup gdm or kdm for autologin unless the mint folks have made changes to casper and included lxdm in it.

---

### Post by philinux on 2010-05-27
> **Fragadelic said:**
> Casper will only setup gdm or kdm for autologin unless the mint folks have made changes to casper and included lxdm in it.

Aha, so if I install gdm to peppermint and sort out auto login I'm good to go.

---

### Post by Fragadelic on 2010-05-27
Just install it and you should be good to go.  Autologin will automatically be setup by casper during live boot for dist mode.  For backup mode it will be however you have it on the main system.

---

### Post by philinux on 2010-05-27
> **Fragadelic said:**
> Just install it and you should be good to go.  Autologin will automatically be setup by casper during live boot for dist mode.  For backup mode it will be however you have it on the main system.

Installed GDM and setup auto login, tested and it works.
Using Backup mode, moved /etc/gdm/custom.conf to custom.conf.back and it still stops at GDM login screen. Any ideas?

---

### Post by Fragadelic on 2010-05-27
Backup mode will be whatever it is on the main system.  Don't remove anything.

If you have autologin setup on the main system it should work the same on the backup iso.

---

### Post by philinux on 2010-05-28
Right I'm getting confused.

Backup mode is what is needed.

I've gone back to a snapshot of peppermint before I started messing about.

So first thing is to replace lxdm with gdm.

Do I still remove password, setup auto login, but not remove the .conf file?

If I remove the password wont the ability to use sudo vanish from the installation?

Cheers.

---

### Post by guvnr on 2010-05-28
> **Fragadelic said:**
> You can also install firefox extensions and themes globally from the command line but it isn't really documented.

as root run the following commands:

To become root "sudo su" put in your user password and you will be root.

For a global theme:

firefox -install-global-theme theme-file-you-downloaded.jar

And yes that is only a single - before install.

For extensions like adblock or whatever:

firefox -install-global-extension extension-you-downloaded.xpi

There is one major caveat though.  A large number of extensions and themes were not written with being made global defaults in mind so they may fail as they do not have all that is required to be setup as a global default.

Just delete the folder for the bad extensions and remove the .mozilla user folders afterwards but remember that this will remove everything so only do testing with a test user setup.

nice tip, just what I was after, thank you Fragadelic

---

### Post by Fragadelic on 2010-05-28
> **philinux said:**
> Right I'm getting confused.

Backup mode is what is needed.

I've gone back to a snapshot of peppermint before I started messing about.

So first thing is to replace lxdm with gdm.

Do I still remove password, setup auto login, but not remove the .conf file?

If I remove the password wont the ability to use sudo vanish from the installation?

Cheers.

For backup mode you shouldn't need to do anything to the system.  The points I mentioned were for dist mode.  In backup mode I make casper bypass the user creation stage which sets up gdm/kdm and the live user.

You will login the same as on the installed system and everything else should be the same.

---

### Post by philinux on 2010-05-28
> **Fragadelic said:**
> For backup mode you shouldn't need to do anything to the system.  The points I mentioned were for dist mode.  In backup mode I make casper bypass the user creation stage which sets up gdm/kdm and the live user.

You will login the same as on the installed system and everything else should be the same.

Yep as you say. I installed gdm to peppermint, set it to autologin and did not clear the password and the new livecd works as I expected. No user input is needed. Goes straight to Desktop.

So for dist mode on a customised ubuntu install, extra packages installed only,  what is needed to get the behaviour of a normal livecd.

---

### Post by Fragadelic on 2010-05-28
Should be nothing as long as you don't change gdm or set autologin.  Casper for some reason has problems with this.

As long as gdm is normal and you don't put too much in /etc/skel it should work.  The live user on a dist mode setup has their home folder created entirely in RAM with aufs.  This is why there are issues with adding stuff like .wine folders to /etc/skel.

Within remastersys I have /etc and /var copied to a temp area where I apply some changes to the original files preparing them for the squashfs file.  For dist mode I strip out all the user info from /etc/passwd and /etc/group thus leaving the real ones on the system intact.  This is also why remastersys temp folder cannot be on a windows filesystem.  vfat and ntfs do not hold user permissions properly and they end up with a problem on the sudoers file.  That seems to be the only one that has permissions problems.  I've been trying to figure out a reliable way of checking but haven't found anything I like yet.  I also toyed with creating a temp filesystem for these and then loopmounting it but that adds another layer of complexity and I want to keep it simple.

---

### Post by philinux on 2010-05-28
> **Fragadelic said:**
> Should be nothing as long as you don't change gdm or set autologin.  Casper for some reason has problems with this.

As long as gdm is normal and you don't put too much in /etc/skel it should work.  The live user on a dist mode setup has their home folder created entirely in RAM with aufs.  This is why there are issues with adding stuff like .wine folders to /etc/skel.

Within remastersys I have /etc and /var copied to a temp area where I apply some changes to the original files preparing them for the squashfs file.  For dist mode I strip out all the user info from /etc/passwd and /etc/group thus leaving the real ones on the system intact.  This is also why remastersys temp folder cannot be on a windows filesystem.  vfat and ntfs do not hold user permissions properly and they end up with a problem on the sudoers file.  That seems to be the only one that has permissions problems.  I've been trying to figure out a reliable way of checking but haven't found anything I like yet.  I also toyed with creating a temp filesystem for these and then loopmounting it but that adds another layer of complexity and I want to keep it simple.

Clear thanks. I got confused with the comments earlier about removing password from install.

---

### Post by .Guest. on 2011-05-24
What is the maximum size of the /etc/skel folder, that can be saved, from the current OS, to the new LiveCD?

Does anybody have experience with the dialog box that states something similar to, "The file is too large for ISO9660(?), try again?"

Thanks.

---

### Post by Fragadelic on 2011-05-24
> **.Guest. said:**
> What is the maximum size of the /etc/skel folder, that can be saved, from the current OS, to the new LiveCD?

Does anybody have experience with the dialog box that states something similar to, "The file is too large for ISO9660(?), try again?"

Thanks.

The limit for /etc/skel is determined by the amount of ram the PC/Laptop is running since everything for the live user has to be loaded into ram.  The live users home folder is held entirely in ram.

---

### Post by linuxinstalledfromhdd on 2011-05-24
It's sounds like you have too many packages installed and it is running out of space to fit a 4.7Gb disc image.   I love remastersys, but you are limited to a certain size of disc when you create it.  It can be trial and error in the beginning.

---

### Post by .Guest. on 2011-05-26
-> Newbie asking basic questions. <- 

Logged into root using

"gksudo f4".

Open file browser --> Copied wanted folders to 

"/etc/skel"

as root. Then saved those files using

"sudo chown -R root:root /etc/skel"

Failed several tries to create the .iso file, using remastersys, second (2nd on list) option,

"Make a Distributable copy to share with friends - both cdfs and .iso will be created" 

After remastersys runs, the error message similar to, 

"The file size is too large for [iso 9960] image. Please try again."

Are the saved files that remastersys be burned onto the disk image stored in 

"remastersys/remastersys/dummysys/etc" ?

and 

"remastersys/remastersys/dummysys/var/lib" ?

If so, can unwanted files be deleted from that folder, to reduce the final image file size?

Only want to save about 5 or 6 applications for the new .iso, but when looked in 

"remastersys/remastersys/dummysys/etc"

there are more files than were saved in

"/etc/skel".

There is the entire "Home" folder, or ALL of the application of the "Home" folder.

Can the un-wanted folders and files from 

"remastersys/remastersys/dummysys/etc"

be purged from that folder, to reuce the final .iso folder, so it can fit into the .iso image format?

What is the maximum size that an .iso formatted image can be? 4.7GB? 

How can a user check the final .iso to be burned, before initiating remastersys, to make sure that the total size is burnable in the .iso format?

Thanks.

---

### Post by Fragadelic on 2011-05-26
The limit for an iso is dictated by genisoimage which actually has a limit of 4GB per file in the iso. Since the filesystem.squashfs is one single containing the entire live system, it must be smaller than 4GB. This limit has nothing to do with remastersys as many people wrongly think.

If it is saving the /home folder then you are running backup mode instead of dist mode.

Since remastersys creates the filesystem.squashfs from your installed system, there are several things that must be changed or the live will fail to boot.  This is why all of /etc and /var are placed in /home/remastersys/remastersys/dummysys and then I remove certain files and change others from there.

---

### Post by .Guest. on 2011-05-27
> **Fragadelic said:**
> The limit for an iso is dictated by genisoimage which actually has a limit of 4GB per file in the iso. Since the filesystem.squashfs is one single containing the entire live system, it must be smaller than 4GB. This limit has nothing to do with remastersys as many people wrongly think.

If it is saving the /home folder then you are running backup mode instead of dist mode.

Since remastersys creates the filesystem.squashfs from your installed system, there are several things that must be changed or the live will fail to boot.  This is why all of /etc and /var are placed in /home/remastersys/remastersys/dummysys and then I remove certain files and change others from there.
Thank you for your reply.

Tried on several occasions to create .iso using remastersys, option#2,

"Make a Distributable copy to share with friends - both cdfs and iso will be created"

The error message returned, after the process,

"The compressed filesystem is larger than the iso9660 specification allows for a single file. You must try to reduce the amount of data you are backing up and try again."

The same error message appears in the remastersys.log file.

Checked the properties of the "dummysys" folder in "remastersys/remastersys". It is around

"280MB".

Checked the properties of ISOTMP. It is around

"8.4GB".

Which folder needs to be reduced?

How to check, before running the program, if the data that is being formatted to iso, is larger than iso capability?

What is being done incorrectly?

Thanks.

---

### Post by Fragadelic on 2011-05-27
You can't check before since everything will compress differently with mksquashfs.

Most binary type files will compress very little which means if you are trying to include a lot of games with binary data files this is your problem.

You can use synaptic to check how much space each program takes by enabling the view tab for the size property.  If you click on the column headings in synaptic it will sort ascending and descending each time you click on it.

---

