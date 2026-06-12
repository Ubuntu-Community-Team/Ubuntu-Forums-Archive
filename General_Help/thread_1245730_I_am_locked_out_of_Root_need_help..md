---
title: "I am locked out of Root need help."
date: 2009-08-20
forum: General Help
---

### Post by hockey97 on 2009-08-20
Hi, currently I tried to change permissions/groups of my external hard drive. 

I tried to use the  chown -R user / command. Well I wanted to make changes to /media/disk  well what happens their was a keyboard lag and it entered only /  so it changed my root file system to my username. Now when I try to get into root using sudo well I use su I get an error like:

setgid: Operation not permitted

I then tried to use chown -R root /  to change it back to the root user.
The problem is that when I see the folders and dir trying to change it back to root I see permissions errors saying you don't have permission.

how can I get around this? I need to set the root part of the ubuntu system back to root user to be able to use sudo or su and login to root.

any ideas?

---

### Post by llamabr on 2009-08-20
I think you need to learn how to use more commas and periods.  I'm not sure what you did, what you're trying, or what you need.

---

### Post by hockey97 on 2009-08-20
I set the root system files from root to my own user. 

I tried to set the root system files back to root but can't.

I get this error in terminal: setgid: Operation not permitted .

That is when I try to log in as root using su in terminal.

So what I need is to know how I can change the permissions of the root system files located at /  to be back as owner to root instead of my own user.

---

### Post by lswb on 2009-08-20
boot into recovery mode then drop to root shell and make a backup of any inportant data. You can try " chown -R root:root / " from the recovery mode shell which will probably get sudo working in a normal boot, but screw up lots of other things. If you really ran sudo chown -R user on / and it successfully executed, it is probably easiest to reinstall. There are just way too many files and directories that need specific owner and group to work correctly

---

### Post by hockey97 on 2009-08-20
can't I just make changes to the /etc/group ?

I changed the admin in /etc/group from my own user back to root user.

I can't save anything. I have a external hard drive that I can't access it. 

I have my website work on the pc and I can't back it up.

Is their any way I can like save all my server configs and server files so I don't need to config or reconfig my servers like apache,mysql, webmin?

I mean it will take a long time to reconfig and setup those servers again.

---

### Post by hockey97 on 2009-08-20
> **lswb said:**
> boot into recovery mode then drop to root shell and make a backup of any inportant data. You can try " chown -R root:root / " from the recovery mode shell which will probably get sudo working in a normal boot, but screw up lots of other things. If you really ran sudo chown -R user on / and it successfully executed, it is probably easiest to reinstall. There are just way too many files and directories that need specific owner and group to work correctly

I tried it in the recovery console. I still get an error. I still get the same error which is Operation not permitted.

---

### Post by hockey97 on 2009-08-21
Is their any other way?  If I have to reinstall the whole OS. How can I save the server configs and other stuff?

I don't want to reinstall every thing and again setup servers . I have 2 websites that I done 2 years of work on it and never published it yet but planning on soon. 

when I try to boot ubuntu I see it go from the loading screen to terminal showing details. 

It shows like 5 things fail to load due to permissions. 
Then when I try to change those permissions I get a operation denied type error.

however I notice chmod 644 works without any errors/ But it still has my own user name as the owner. 

I personally think the people that made ubuntu should add some type of recover or code to prevent permission changes to root files or system files.

---

### Post by lswb on 2009-08-21
If you have ever made a backup now is the time to use it. You can check the documentation for any programs you have customized and see where the config files are kept, copy them to a safe place, then copy them back after restoring from a backup or reinstalling. You can try searching for another solution, maybe someone else has some other ideas.

---

### Post by hockey97 on 2009-08-21
do you think I can just backup the whole computer?

I have a dual boot. so I am right now using windows xp. 

I can see linux drives with windows xp. My external hard drive was formatted to ex3. The problem is that windows xp when I click on the external hard drive it asks to format it. Should I format it as ntfs?

---

### Post by macunixfan on 2009-08-21
Can you run the LiveCD and mount the drives from there?

---

### Post by hockey97 on 2009-08-21
> **macunixfan said:**
> Can you run the LiveCD and mount the drives from there?

I can only boot into my windows xp drive. I have a dual boot with linux ubuntu.

should I make a new cd  that is a live cd? 

currently I tried making a backup of my computer files. Using windows xp.  Currently I can access a few folders ones that were under my user name and nothing root. 

So I can't make backups of my server configs or any folders that have different usergroups then my own user. So I can backup home folder and a few root folders. 

I found old backups of etc, root and home folders.

I have the installation cd that is all. 

I can download and make a cd that is a live cd and try that.

I never used a live cd. Do you think it will  work?

I will give it a try. Would it matter on the versions? 

my ubuntu is either 8.04 or 8.10 server edition but have desktop installed with it. 

so , should I try the live cd or backup everything first? 

How can I easily backup everything? My external hard drive is formatted to ext3 format but windows xp when you select the drive it asks if I want to format it and I click cancel and it won't load the external hard drive.  Yet when ubuntu was working I can see the drive with gparted and it shows as ext3 file formate but at the time I didn't have the right permissions to tranfer files  to the external hard drive.

what should I do first? do  a backup or just give the live cd a try?

---

### Post by tgeer43 on 2009-08-21
> so , should I try the live cd or backup everything first? 

How can I easily backup everything? My external hard drive is formatted to ext3 format but windows xp when you select the drive it asks if I want to format it and I click cancel and it won't load the external hard drive. Yet when ubuntu was working I can see the drive with gparted and it shows as ext3 file formate but at the time I didn't have the right permissions to tranfer files to the external hard drive.

what should I do first? do  a backup or just give the live cd a try?Speaking from hard earned experience, you should try the following:

- Boot from a Live CD. Any recent version should do.
- Backup your server configs and anything else that's really important to you.' Tar' would be a good way to do this but make sure to use the --same-owner and -p options to preserve file ownerships and permissions (although they might already be messed up). See 'man tar' for more details.
- Reinstall Ubuntu using the same username as the original installation.
- Reinstall your apps then untar the backup tarball, again using the --same-owner and -p options to reestablish your server configs and other important data.

I wish there were a simpler/faster way but once you've screwed up your root ownerships and permissions you're, well... screwed.

In the future keep your backups current and use chown and chmod with _extreme_ _caution_.
> I personally think the people that made ubuntu should add some type of recover or code to prevent permission changes to root files or system files.There *are* safeguards and recovery options in place that are sufficient. You were operating as root when you botched things up. Root does and should have permission to change ownership and permissions of its own files. It's unfair to blame Ubuntu or its coders for your misuse of root powers.

XP is asking to format your ext3 drive because you don't have ext3 filesystem support installed. Google 'Windows ext3 support' if you want to add it. You *could* then do your backups from XP but personally I would go the Live CD route.

Hope this helps,

tgeer

---

### Post by hockey97 on 2009-08-21
> **tgeer43 said:**
> Speaking from hard earned experience, you should try the following:

- Boot from a Live CD. Any recent version should do.
- Backup your server configs and anything else that's really important to you.' Tar' would be a good way to do this but make sure to use the --same-owner and -p options to preserve file ownerships and permissions (although they might already be messed up). See 'man tar' for more details.
- Reinstall Ubuntu using the same username as the original installation.
- Reinstall your apps then untar the backup tarball, again using the --same-owner and -p options to reestablish your server configs and other important data.

I wish there were a simpler/faster way but once you've screwed up your root ownerships and permissions you're, well... screwed.

In the future keep your backups current and use chown and chmod with _extreme_ _caution_.
There *are* safeguards and recovery options in place that are sufficient. You were operating as root when you botched things up. Root does and should have permission to change ownership and permissions of its own files. It's unfair to blame Ubuntu or its coders for your misuse of root powers.

XP is asking to format your ext3 drive because you don't have ext3 filesystem support installed. Google 'Windows ext3 support' if you want to add it. You *could* then do your backups from XP but personally I would go the Live CD route.

Hope this helps,

tgeer

Oh, no I am not blaming the makers of ubuntu. I am just suggesting them in future versions to try and seperate commands that are critical like permissions  or something that can revert to changes made in one day well only those that are critical like permission changes. So after the day those changes were made it will delete the revert data. 

It's just a suggestion. I googled around and found many fourms and post of others doing similar stuff. 

I am just suggesting they should create something in future versions that will allow us to get back to a working copy. 

just giving a suggestion and not blaming them. It's still a better os then windows. It's just that when things go wrong like getting locked out or some other problem. It takes a long time to recover. I mean I can easily just reinstall ubuntu and lose all data but the programs and all other stuff I done it took  a long time to set them up properly.

I am right now using a live cd sending this post currently. 

the problem is that I have a dual boot system. with this live cd I can't find the root of my system only  the root of the live cd system.

I only can see any extended hard drives/particians.

so I can't copy server info and other stuff. Is their some special way to mount the hard drive to view the root or all content on it. 

I got one that shows my windows xp drive but that drive has my root linux system files. 
Then I got a extended partician which has my user folder but it's different it's not the same and shows the folders are empty.

---

### Post by tgeer43 on 2009-08-21
Okay - take a deep breath and say after me, "I *CAN* do this". :wink:

Ubuntu cannot automount your drives when booting from the Live CD because there are no entries for them in it's /etc/fstab file. However, you can mount them manually. Here's how to do it:

First you'll need to know what the drive specifier for your drive is. After booting the Live CD, open up a terminal and type the command:
```
sudo fdisk -l
```This will list all of the drives connected to your system. Mine looks like this:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006c4a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19065   153139581   83  Linux
/dev/sda2           19066       19457     3148740   82  Linux swap / Solaris

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b199367

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1
```With the information given by fdisk find the drive that you are wanting to work with. The specifier that you are looking for will be something like 'hda1' or 'sdb3' or something similar. It's up to you to determine which one is the correct drive.

Next type:
```
sudo mkdir /mnt/mydisk
sudo mount /dev/hda1 /mnt/mydisk
```Substituting your drive specifier for 'hda1' in my example. Now your drive is mounted and accessible. You should now see it in the 'Places' menu as well as in the nautilus window when you select 'Computer' from the 'Places' menu. Additionally, you can see the contents of your drive by using nautilus to browse to the /mnt/mydisk directory.

That's it! Now go back and follow the directions in my previous post. If you need detailed instructions on backing up your data prior to reinstallation then post back here and I will do my best to help you.

Good luck,

tgeer

---

### Post by hockey97 on 2009-08-22
> **tgeer43 said:**
> Okay - take a deep breath and say after me, "I *CAN* do this". :wink:

Ubuntu cannot automount your drives when booting from the Live CD because there are no entries for them in it's /etc/fstab file. However, you can mount them manually. Here's how to do it:

First you'll need to know what the drive specifier for your drive is. After booting the Live CD, open up a terminal and type the command:
```
sudo fdisk -l
```This will list all of the drives connected to your system. Mine looks like this:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006c4a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19065   153139581   83  Linux
/dev/sda2           19066       19457     3148740   82  Linux swap / Solaris

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b199367

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1
```With the information given by fdisk find the drive that you are wanting to work with. The specifier that you are looking for will be something like 'hda1' or 'sdb3' or something similar. It's up to you to determine which one is the correct drive.

Next type:
```
sudo mkdir /mnt/mydisk
sudo mount /dev/hda1 /mnt/mydisk
```Substituting your drive specifier for 'hda1' in my example. Now your drive is mounted and accessible. You should now see it in the 'Places' menu as well as in the nautilus window when you select 'Computer' from the 'Places' menu. Additionally, you can see the contents of your drive by using nautilus to browse to the /mnt/mydisk directory.

That's it! Now go back and follow the directions in my previous post. If you need detailed instructions on backing up your data prior to reinstallation then post back here and I will do my best to help you.

Good luck,

tgeer

I followed what you said and I got my external hard drive mounted. 

Now the problem is that it has no writeing permissions. It's at read only. 

How do I change this?

---

### Post by HiImTye on 2009-08-22
if you made *yourself* the owner of the files then you should be able to change them back without using sudo, in theory

try using nautilus and then right clicking one of the folders, going to permissions, changing the owner back to root

edit: make sure to apply permissions to child folders as well

---

### Post by hockey97 on 2009-08-22
> **HiImTye said:**
> if you made *yourself* the owner of the files then you should be able to change them back without using sudo, in theory

try using nautilus and then right clicking one of the folders, going to permissions, changing the owner back to root

edit: make sure to apply permissions to child folders as well


Ya I tried that. When I try swtiching the owner back to root I would get a nice error saying operation denied. In the system logs it shows permission denied should be 644. 

This is what I see.  I  also tried the live cd way. I can make the changes without the errors. But the only thing is that I can't transfer files to my expertnal hard drive  due to permissions. 

I don't think I have write access to external hard drive. 

I followed the instructions 2 posts above. I mounted the external hard drive properly. by making a folder in the mnt folder and running the mount commant in terminal.  I can access the external hard drive and read it but I don't have any writing permission. 

how would I enable writing permissions using a command in terminal? 


I also notice when I try to do a normal boot. I see about 5 fails  and those modules failed do to permission problems. 

I was thinking if I can write down those modules or directory. I can then write permissions to those areas to atleast gety my system bootable. 

currently I can't boot into my own system due to some modules that is in the booting process dosen't have the right permissions.


Thanks for all the input. In most google searches that I found most of the people that were in the same situation or similar situation ended up backing up files if they could and reinstalling ubuntu. 

If I have to reinstall  should I install that latest version? cause I have currently 8.10 


right now my concern is backing up everything. I did made backups but my external hard drive couldn't mount on my system. So I loaded my windows xp and reformat my hard drive. Then got in ubuntu and reformat it to ext3. 
Then I had no access to the mounted external hard drive. So I then tried to write permissions since I saw the external drive owner to be root and wanted  it to be changed to my user. Instead not seeing whats on the monitor I typed in the directory location of the media/disk etc. Yet it only registered the / and so I wrote the permission to the whole system or atlest the root part of the system.

well I thank you for all the help. I will keep posting here if I have any more questions  on backing the stuff up which I will.

---

### Post by hockey97 on 2009-08-22
Ok, so far whats preventing me from booting into my system is that I get an error saying  that the home folder needs to have user rights of the user your logging in as. Then it says that it must have a chmod of 644 permissions. 

I booted into the recovery boot and typed in as root to change home folder permissions to user and chmod it to 644. I still get the same error after that. 

I also get another errory saying that I don't have proper rights to file $home/.dmrc file  which said that it's preventing to start the session and language. 

I think if I can get the proper permissions to that file. I think I can boot into the system.

does anyone know where this file resides/located at?  and what permissions it should have?

---

### Post by AmerNewbieInDE on 2009-08-22
hmm, sounds like you may of copied files from another disk....i did the same so..

actually... you are in the same place i was, but my system changed on it own.. i could not run sudo su or gksudo. run a live cd, copy/backup what you need off your linux partition and reinstall....i found little help here, just alot of try this and try that. dont get me wrong, it is all helpful, but could not get the permissions back.

---

### Post by AmerNewbieInDE on 2009-08-22
> **hockey97 said:**
> Ok, so far whats preventing me from booting into my system is that I get an error saying that the home folder needs to have user rights of the user your logging in as. Then it says that it must have a chmod of 644 permissions. 

I booted into the recovery boot and typed in as root to change home folder permissions to user and chmod it to 644. I still get the same error after that. 

I also get another errory saying that I don't have proper rights to file $home/.dmrc file which said that it's preventing to start the session and language. 

I think if I can get the proper permissions to that file. I think I can boot into the system.

does anyone know where this file resides/located at?  and what permissions it should have?

the file is in /home/user... but hidden use ctrl+h to see it

look here....

[http://ubuntuforums.org/showthread.php?t=1247266](http://ubuntuforums.org/showthread.php?t=1247266)

---

### Post by hockey97 on 2009-08-23
> **AmerNewbieInDE said:**
> the file is in /home/user... but hidden use ctrl+h to see it

look here....

[http://ubuntuforums.org/showthread.php?t=1247266](http://ubuntuforums.org/showthread.php?t=1247266)

I tried those. Just now and it didn't work. I still got the errors.  

I then found if that didn't work to try doing chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo 

they said that if it prompts you wrong permission 4755 should be 0440 then they said to do this: chmod 0440 /etc/sudoers.

so I did all that. Now I can't even boot to my ubuntu login screen anymore. 

after the loading screen it goes to a terminal looking screen. I see like 5 things that fail.

one was /skbin/klogd  all fails errors were due to permission problems.

I don't remeber the rest but know they weren't important to boot the system.

If I can boot into the system it would be eaiser to make the changes.


Is their any logs I should look at and post here to help anyone assist me?

I think it would be smart to start looking at some logs to see whats wrong.

---

### Post by hockey97 on 2009-08-23
Ok, I looked in /var/logs  and in messages log file I found this.

```
dhcdbd: dbus_svc_init failed: org.freedesktop.DBus.Error.NoReply Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

That is the only thing I am seeing that is an error in the logs. The other stuff is like restart messages. 

This is what I found so far. Is their a particular log I should be looking at to finding out why I can't get to my ubuntu login screen?

---

### Post by lswb on 2009-08-23
With all the chmod and chown you have done it is quite possible that programs no longer have correct permissions/owners to be able to write to the logs. I don't think you can get it any worse than it is now, so you might consider this:

Boot from live CD, open a terminal and mount the hard drive, say to /mnt/disk, and then chmod -R 777 /mnt/disk from the live CD environment. Lets say your trashed partition is recognized as /dev/sda1, then

sudo mount -t ext3 /dev/sda1 /mnt/disk
sudo chmod -R 777 /mnt/disk

This will result in a completely insecure system where anybody can run or access any thing, but maybe it will at least let you copy your config files and other data files you want to save.

Plug in your external hard drive or a usb drive and let the live CD automount it, then copy your config and data files to the external drive. Afterwards do a reinstall to the hard drive. Install the packages you need, and copy the config and data files from the removable disk. Make sure to set appropriate ownership and permissions for the copied files, you may need to check documention or see how the various packages set up their default configs.

IMHO it will take less time and be more reliable than trying to restore correct permissions and ownerships to the existing installation.

After you have everything working again, use your removable drive to make a complete backup of the working system, "just in case!" Good luck!

---

### Post by hockey97 on 2009-08-23
Does anyone know what is user id 999 or group id is 999? 

I save some errors saying that user id 999 dosen't exist anymore. This is the reason the gnome and mysql are failing.

---

### Post by joshuntu on 2009-08-23
I am kind of having a similar problem, i ran a command (sorry cant remember it) that locked a certain folder like some of the root folders and now i can't delete it, is there a strong terminal command that can delete a folder even if it has a little lock hovering obove it??

---

### Post by hockey97 on 2009-08-23
> **joshuntu said:**
> I am kind of having a similar problem, i ran a command (sorry cant remember it) that locked a certain folder like some of the root folders and now i can't delete it, is there a strong terminal command that can delete a folder even if it has a little lock hovering obove it??

that lock means that you don't have the permission to access it. 

you need to use chmod  commands or chown to change the permissions. 

that's all I can say.

---

### Post by hockey97 on 2009-08-25
would anyone know of the files that ubuntu needs to boot to get the destop loaded. 

Or atleast gnome display manager permissions it needs. I am currently googling for the right permissions so far I was told to chwon it to root:root and give it a 644 permission. I done this with no new results.

currently. I can't backup the files to my external hd. I can back the files up on my windows partician but I won't have enough room to store it on my internal hard drives.

well I will look into this. 

Maybe down the road. If I have spare time. I will try to make a recover application with permissions in mind that's if noone beats me to it first I guess.

---

### Post by keforex on 2009-08-26
Isn't it easier to edit the sudoers file? Someone here explained how to do this, gotta do a search.


EDIT:

Here ya go: [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by hockey97 on 2009-08-27
Thanks for the information. I found out the permission was wrong. 

I just changed everything to permission 777. I know it's unsecure but I want a system that can at least boot. I will later on try and find the proper permissions.

Right now the only thing stopping me is that I get a error with Xsession.

I got an error saying: cannot execute /etc/gdm/Xsession default [6263]

this is the only error preventing me from booting into my sysetm graphically.

I then get another error window saying that your sesssion lasted 10 min and that it logged me out. If I didn't log myself out then it could be hardware problems. etc

I then get handed a error log and it shows something along the lines like:

child class: /etc/gdm/Xsession  cannot run due to internal error.

that is about it. I then googled /etc/gdm/Xsession and found a few other websites having others that had the same problem.

I was told to change the permissions of /temp/   and gconfd and also .Xauthority  they claim that .Xauthority is located in my home/users folder.

I tried looking for it in my home user folder.

Does anyone know how to fix it?

---

### Post by lswb on 2009-08-27
Well, I guess I can say "I told you so" and point out that if you had copied your config and data files, reinstalled, and reconfigured your applications, you would have been done with it a few days ago!

---

### Post by hockey97 on 2009-08-29
> **lswb said:**
> Well, I guess I can say "I told you so" and point out that if you had copied your config and data files, reinstalled, and reconfigured your applications, you would have been done with it a few days ago!

I can't back it up to my external hard drive. 

I can only make backups to my windows xp partician. Yet I don't have enough room to spare for the backup to my xp partician.

I just need to get etc/gdm/Xsessions to work properly then I can boot into my system graphically.

---

### Post by hockey97 on 2009-08-29
From the errors I am getting is that the Xsession has no permissio to be excuted. How do you give the permission for a file to be runned?

any commandes?

---

### Post by gsocker on 2009-08-29
You edit those permission bits. You have been using the numeric version(octal base). 
There are also text version which may be easier for you to use.
There are three categories: user, group, and other.
Each has read, write, and execute permissions. 
The "text" equivalent of chmod 777 is
```
chmod u=rwx,g=rwx,o=rwx
```
or
```
chmod a=rwx
```
"u": user
"g": group
"o": other
"a": "all" - combines the about three.
"=" sets permissions to the ones given.
"+" adds the permissions specified.
"-" removes the permissions specified.
"r" is read, "w" is write, and "x" is execute.
Note that directories use the "execute" bit as the "can user view contents of directory bit?"
There are also setuid, setgid, and sticky bits, each of which does different things.

If you have an external hard drive, you should be able to back up to it as long as the live cd can mount it.
Since the permissions on your original install are screwed up, you will definitely need to be root to copy the files off.

I second the reinstall method. There are too many files in /etc and /var that need the **correct** user,group, and permissions set for system programs to work, without compromising the security of the system.

---

### Post by hockey97 on 2009-08-30
> **gsocker said:**
> You edit those permission bits. You have been using the numeric version(octal base). 
There are also text version which may be easier for you to use.
There are three categories: user, group, and other.
Each has read, write, and execute permissions. 
The "text" equivalent of chmod 777 is
```
chmod u=rwx,g=rwx,o=rwx
```
or
```
chmod a=rwx
```
"u": user
"g": group
"o": other
"a": "all" - combines the about three.
"=" sets permissions to the ones given.
"+" adds the permissions specified.
"-" removes the permissions specified.
"r" is read, "w" is write, and "x" is execute.
Note that directories use the "execute" bit as the "can user view contents of directory bit?"
There are also setuid, setgid, and sticky bits, each of which does different things.

If you have an external hard drive, you should be able to back up to it as long as the live cd can mount it.
Since the permissions on your original install are screwed up, you will definitely need to be root to copy the files off.

I second the reinstall method. There are too many files in /etc and /var that need the **correct** user,group, and permissions set for system programs to work, without compromising the security of the system.


Ok, I will reinstall. I just want to make sure I backup the right files. 

I currently have 2 years of work of my website. 

I want to backup all servers even webmin.  I want to backup nvidia installation or config .

I remeber I had a very hard time installing nvidia drivers.

Right now. I can  use the live cd and mount my external hard drive.

when I start to copy things over some files don't have proper permissions for the root user to copy those files.

Is their a way I can change all permissiosn to 777 so I can access them all to back them up?


I am thinking to backup everything I have. Just so that I won't forget any files that I needed or something.

---

### Post by hockey97 on 2009-08-30
My external hard drive is a ntfs file system. 

I have to have it as ntfs because I am in college and some up coming assignments I have to save it on a usb device to upload the assignment to the computer to give a presentation type stuff.

So I would really like to keep the file system to a windows system since my colleges uses windows xp. 

I would like to know if I need to do anything special in order for me to backup my stuff on this external hard drive?

I am using the live cd. My old ubuntu system I did installed a module that will allow ubuntu to read windows file systems.

I googled around and found some forums talking about that you have to manually mount the ntfs external hard drive in terminal to make it work properly.

So far I can mount the drive sometimes. I sometimes get a error on Dbus and other times I get errors saying cannot mount. The their is other times where it mounts but when I transfer the files from my linux partician to the external drive some files have errors saying you don't have permission to access this file. Their is a bunch of files that have this error. 

I want to back up everything the reason for this is so that when I do a reinsatll I will for sure have the backup files I need. 

So do you think I have to do anything special to get a ntfs external to mount or work properly?

---

### Post by gsocker on 2009-08-30
OK, so you are running the Live CD and mounting both the external and internal drives, then trying to copy as the livecd user?
Ignoring the GUI, both can be mounted from the command line. This completely bypasses hal/dbus, solving that problem.
Since the default live cd user is not root, you will have permission problems on some files.
Become root, and the permission problems will go away.

To mount the external hard drive from the command line:
Plug it in.
Open Terminal.
Run "sudo -i". The live cd does not require a password for sudo.

Run "dmesg"
Look at the last couple of lines. 
You should see something similiar to this:
```
scsi10 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 10
usb-storage: waiting for device to settle before scanning
scsi 10:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9339 PQ: 0 ANSI: 0
sd 10:0:0:0: [sdd] Attached SCSI removable disk
sd 10:0:0:0: Attached scsi generic sg7 type 0
usb-storage: device scan complete
sd 10:0:0:0: [sdd] 31776768 512-byte hardware sectors: (16.2 GB/15.1 GiB)
sd 10:0:0:0: [sdd] Write Protect is off
sd 10:0:0:0: [sdd] Mode Sense: 03 00 00 00
sd 10:0:0:0: [sdd] Assuming drive cache: write through
sd 10:0:0:0: [sdd] 31776768 512-byte hardware sectors: (16.2 GB/15.1 GiB)
sd 10:0:0:0: [sdd] Write Protect is off
sd 10:0:0:0: [sdd] Mode Sense: 03 00 00 00
sd 10:0:0:0: [sdd] Assuming drive cache: write through
 **sdd: sdd1**

```The last line(the one in bold) tells you what device the disk's partition will show up as, in this case sdd1.
Create a mount point for the external drive, for example, "/media/backup": 
```
mkdir /media/backup
```Mount the external drive, using the device listed in the dmesg output:
```
mount -t ntfs-3g /dev/your_device_here  /media/backup
```This assumes the external drive is USB.
Firewire will not have the "USB Mass Storage" lines, but is otherwise identical.

From your message, it seems only the external drive is giving you problems when mounting.
You should now be able to copy anything.
If you still have problems, please post the exact error messages.

To unmount the external drive before you reboot, run 
```
umount /media/backup
```

---

### Post by hockey97 on 2009-09-01
Ok, I am able to now backup files the problem now is that I still don't have certain permissions for certain files.

Also not all gets covied over. When I check the backup on my external hd I find some folders empty. 

I notice after I did the backup. I booted into windows and at the boot screen windows started a chkdsk /f to my external hard drive and deleted 1,000 files due to finding it was cruppted. 

When windows booted. I saw errors saying that my external hard drive is cruppted please run chkdsk /f.  Then the external drive would disconnect. I then turn the external hard drive off and then turn it back on. Randomly sometimes it will work and other times I get ether a crupption error or a permission error. 

When it behaves I can see the folders and do see most of the folders have files in them. 



Currently I only care for backup up my server config files  and my website work.

I also would like to backup my nvidia files. The reason was that it was a pain in the butt to get nvidia working on my computer. I used nivida drivers.

I would like to backup php config or installation and same with webmin.

---

### Post by hockey97 on 2009-09-04
I am using the live cd. I  still do get problems mounting the external hard drive. 

This time I decided to screenshot the error. So here is the screen shot of the error.

here is the image: 

[IMG]http://i32.tinypic.com/2rzxap4.jpg[/IMG]



That is when I am using live cd.

---

