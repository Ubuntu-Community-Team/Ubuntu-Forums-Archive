---
title: "some help with permissions please"
date: 2009-11-29
forum: General Help
---

### Post by homer1234 on 2009-11-29
Hi,

I'm pretty new to linux in general and especially ubuntu and am having difficulty changing permissions on my system with ubuntu:

I'm sure you get alot of the whole "I'm a windows pro and and i don't understand any of this $%$" so I won't bother you with it but I WILL say this; 

please do not reply in "terminal speak" (if possible)
I understand that "terminal is my friend" but I ask you to please respect that I can come to that conclusion on my own; don't try to force it on me.

please do not forward me to another thread (again only if convenient and possible)
if it only takes you 30 seconds longer, please just type out the answer to my question rather than getting me a new thread; I've done research, I've read articles, I'm posting this thread not because I'm lazy, but because I am ASKING for help. 

Don't tell me what I'm doing is a bad idea; I honestly don't care, I just want to do what I want and then i'll worry about the rest later.


now for the question;

I have ubuntu loaded on a harddrive that I used to use for just storage; as such I have most of my music on there (now in a folder called "host" as named by linux).
I want to have FULL PERMISSIONS with that folder and I want to know how to give anyone I WANT full permissions with that folder and any other folder as well.
by full permissions i mean everything; so whoever it is should be able to click on there and delete everything for all i care. 
Oh, and I don't want to have to login to root everytime to get those full permissions (im aware of gksudo nautilus but I don't wanna use it everytime I just want to move a folder in that folder)


Thanks in advance for your help and please bear with me if I've said anything "stupid"

---

### Post by audiomick on 2009-11-29
hallo.
I think one terminal command might be really the quickest way. Bear in mind that I am also just a user that want to "do what I want, and that's all". and not an expert computer administrator.

Having said that, try this.

Start nautilus using

```
gksudo nautilus
```

a right click on the relevant folder will give you access to the properties pop up. The third tab lets you set permissions. As far as I know, if you are a sudo, you can allocate all permissions to anyone.

Whether or not you can grant adequate permissions to achieve what you want is then a function of how you have set up your users and groups. That can't be swindled, that is a function of how the permissions in Linux work, and the system is a good one. You just have to work with it, not against it.

Hope I could help.
Michael

---

### Post by homer1234 on 2009-11-29
Thanks for the response michael,

I did try that already however, right clicking the folder and clicking properties>permissions leaves me even more frustrated;

I can't change the owner of the folder from root to anything else; the folder access for root, is create and delete files but file access is ---
also, i can't change the group of the folder either
-changing folder access makes it look like everything is working but it just goes back to what it was; (i can click the list arrow and change "access files" under others for folder access but it just goes back to access files and i can't change the file access permissions for ANY feild.

I also tried to create a "share" under sharing but that just led me to a dead end.

---

### Post by audiomick on 2009-11-29
I don't know if I can solve this, but it is worth a try

who owns the folder now?

can you show me the full path to it, and it's permissions?

---

### Post by homer1234 on 2009-11-29
> **audiomick said:**
> I don't know if I can solve this, but it is worth a try

who owns the folder now?

can you show me the full path to it, and it's permissions?


name of folder: host

location: /
volume: unknown
owner: root
folder access: create and delete files
file access: ---

group: root
folder access: access files
file access: ---

others
folder access: access files
file access: ---

share
<share this folder is checked>
share name: host
<allow others to create and delete files in this folder is checked>


is that all of the info you need?

EDIT: this is all by looking at properties while in gksudo nautilus

---

### Post by audiomick on 2009-11-29
I think so.
I have to get my big fat book out. Could take a while...

---

### Post by audiomick on 2009-11-29
Hi, I'm back.

There is a "step up" from sudo. The command is

```
sudo su
```

you will be asked for your password.

The difference is that sudo is a routine that lets a "normal" user do stuff that normally the root has to do. The "sudo su" command makes you into root, the super user. The command means, if you like, "let me be the super user"

Be careful with this. When you have entered this command, you are god in that terminal until you close the terminal, i.e. you can shoot down your computer, and nobody will argue.

I have read a few times recently that there are some things that "sudo" doesn't enable, but "sudo su" does.

I also know from experience that the ownership and rights of files and folders created by root (in your case the installer) can be frustratingly hard to change.

So, do the sudo su command, then do

```
nautilus
```

Then try the right click on the folder again.

I'll wait for your answer. If it doesn't work, I'll do some more thinking.

---

### Post by capscrew on 2009-11-29
> **homer1234 said:**
> name of folder: host

location: /
volume: unknown
owner: root
folder access: create and delete files
file access: ---

group: root
folder access: access files
file access: ---

others
folder access: access files
file access: ---

share
<share this folder is checked>
share name: host
<allow others to create and delete files in this folder is checked>


is that all of the info you need?

EDIT: this is all by looking at properties while in gksudo nautilus

Just a guess on my part, but I don't believe you will be successful in *sharing * the root directory (e.g. /) or in changing the permissions.  This is analogous to windows share $C

I would use gksudo (Alt-F2) and create a directory under / (i.e /host).  Then you can set the ownership and permissions you want.  This is the directory (folder) you should share.  When you browse it will be this folder you will see.

I use this on my system and the folder I created is /smb.  I actually use sub-directories.  You could create folders such as: /smb/music and /smb/video.  Then you can share those separately.

---

### Post by Leppie on 2009-11-29
I think the easiest thing to do is create a group for this shared folder (or all shared folders if you wish) in the "Users and Groups" applet you can find in the main menu (I have Xubuntu, but I think it's System>Administration>Users and Groups). Click the keychain button in between "Help" and "Close" at the bottom of the dialogue and then click on the "Manage Groups" button. The groups list will appear. Click the "Add Group" button and make sure the group id > 1003. Choose a name for the group like myshares (or whatever name you'd prefer). Then select the people you would like to be part of this group from the list (add yourself as well ;)). Click the ok button and close the "Users and Groups" applet.
Now open a terminal and execute the following command:
```
$sudo chown -R root:myshares /host/    
```

Root is still the owner of the folder, but the myshares group members have permission to change things. If you want to make your normal user account the owner of the folder, change root:myshares to your account name. Like this you don't have to create an extra group for this.

If you open up nautilus,and check the folder permissions you will see that you can now change to read and write for the folder.

Hope this helps

---

### Post by homer1234 on 2009-11-29
nope, sorry, but it did the same thing.


EDIT: sorry could have been more clear on that, the sudo su didn't work. i'll try the other recommendations now

---

### Post by homer1234 on 2009-11-29
> **Leppie said:**
> I think the easiest thing to do is create a group for this shared folder (or all shared folders if you wish) in the "Users and Groups" applet you can find in the main menu (I have Xubuntu, but I think it's System>Administration>Users and Groups). Click the keychain button in between "Help" and "Close" at the bottom of the dialogue and then click on the "Manage Groups" button. The groups list will appear. Click the "Add Group" button and make sure the group id > 1003. Choose a name for the group like myshares (or whatever name you'd prefer). Then select the people you would like to be part of this group from the list (add yourself as well ;)). Click the ok button and close the "Users and Groups" applet.
Now open a terminal and execute the following command:
```
$sudo chown -R root:myshares /host/    
```Root is still the owner of the folder, but the myshares group members have permission to change things. If you want to make your normal user account the owner of the folder, change root:myshares to your account name. Like this you don't have to create an extra group for this.

If you open up nautilus,and check the folder permissions you will see that you can now change to read and write for the folder.

Hope this helps

EDIT: 
i did that but it just cycled through everything in the folder with responses saying "operation not permitted"

might I add, that is quite possibly the most frustrating thing I have ever had to deal with; my OWN computer telling me "no you can't do this. sorry." lol

---

### Post by audiomick on 2009-11-29
Hallo again.
Sorry my suggestion didn't work. I'm off to bed now, it's nearly 2.30 a.m. here...
Please make a final post if you get this sorted out. I am going to subscribe to the thread, and would really like to know what the solution was.
Good luck,
Michael

---

### Post by homer1234 on 2009-11-29
> **audiomick said:**
> Hallo again.
Sorry my suggestion didn't work. I'm off to bed now, it's nearly 2.30 a.m. here...
Please make a final post if you get this sorted out. I am going to subscribe to the thread, and would really like to know what the solution was.
Good luck,
Michael


ok, enjoy your sleep and thank you very much for all your help; I will definitely post and say if this is sorted out

see ya!

---

### Post by Leppie on 2009-11-29
Is this by any change a windoze partition?
If so, what is the fstab entry to mount it?

---

### Post by fluffman86 on 2009-11-29
If you did a Wubi install, then navigating to /host is really only pointing you to your C: drive in Windows.  That's partitioned as NTFS, and Linux permissions don't tend to stick there.  At least, I've never had any luck with that.

Maybe you could try doing a full install.  Also try these commands from terminal (even though you don't want to. :P  It's just the only way I know to do it.)  
```
sudo chown -R username:username /host
sudo chmod -R 755 /host
```
That's the best way to set the permissions if you're the only username set up in Ubuntu.  If you want to add more users, then add a group "share" in System > Admin > Users and Groups, add everyone you want to the "share" group then run:
```
sudo chown -R username:share /host
sudo chmod -R 775 /host
```
Just an FYI: chmod is used to change permissions, -R means recursive (to get all the folders inside of /host).  The first number is owner, second is group, third is everyone else.  A value of 4 means read, 2 means write, and 1 means execute (which is necessary to list the files a lot of times).  Add them together to get the permissions you want.

---

### Post by homer1234 on 2009-11-29
> **fluffman86 said:**
> If you did a Wubi install, then navigating to /host is really only pointing you to your C: drive in Windows.  That's partitioned as NTFS, and Linux permissions don't tend to stick there.  At least, I've never had any luck with that.

Maybe you could try doing a full install.  Also try these commands from terminal (even though you don't want to. :P  It's just the only way I know to do it.)  
[code]sudo chown -R username:username /host
sudo chmod -R 755 /host[code]
That's the best way to set the permissions if you're the only username set up in Ubuntu.  If you want to add more users, then add a group "share" in System > Admin > Users and Groups, add everyone you want to the "share" group then run:
[code]sudo chown -R username:share /host
sudo chmod -R 775 /host[code]
Just an FYI: chmod is used to change permissions, -R means recursive (to get all the folders inside of /host).  The first number is owner, second is group, third is everyone else.  A value of 4 means read, 2 means write, and 1 means execute (which is necessary to list the files a lot of times).  Add them together to get the permissions you want.



ok, lotta things to reply to ^_^

this folder is actually NOT a windows partition
here is a map of what i have on my computer right now

Harddrive A: windows partition; has windows XP but nothing else i care about and I have been able to access all files in there just fine

Harddrive B: a secondary harddrive that i used to use just for storage; i installed ubuntu onto this drive so everything on the level of the OS is labeled under "host" when im in ubuntu

Harddrive C: an external drive with a whole bunch- o -files- again i can access everything here just fine


I tried doing all of those commands already but it just cycles through all of the items in that folder and tells me "no! you cant do that!"
(operation not permitted :P)

right now i just logged on to xp and am moving all of the music in the harddrive to the C drive and hopefully ill be able to access it from ubuntu from there... 



Also, I thought i DID install ubuntu fully on my machine... how do I know for sure?

---

### Post by Leppie on 2009-11-29
> **homer1234 said:**
> Also, I thought i DID install ubuntu fully on my machine... how do I know for sure?
Do you get the GRUB menu when booting?

> **homer1234 said:**
> right now i just logged on to xp and am moving all of the music in the harddrive to the C drive and hopefully ill be able to access it from ubuntu from there...
The files you are trying to access are on a windoze partition (fat or ntfs), as windows can only access a couple of different filesystems. Since you do not have write access to this partition and since you're using windoze xp, I suspect it is a ntfs partition. To gain full control over your ntfs partitions install ntfs-3g like this:
```
$sudo apt-get install ntfs-3g
```

Or go to System>Administration>Synaptic and search for ntfs-3g and install.

Once ntfs-3g is installed open your fstab in an editor:
```
$sudo gedit /etc/fstab
```

Find the line that refers to /host, it should look something like this:
```
UUID=1E5A005C5A003357	/host	ntfs ro
```

Change it to make it look like this:
```
UUID=1E5A005C5A003357	/host	ntfs-3g rw
```

In a terminal execute these commands:
```
$sudo umount /host  ##unmount the partition with your music files
$sudo mount -a  ##mount all the partitions listed in /etc/fstab
```

If you open nautilus and check the permissions, you should find that you have complete control now.

Hope this helps.

---

### Post by homer1234 on 2009-11-29
> **Leppie said:**
> Do you get the GRUB menu when booting?


The files you are trying to access are on a windoze partition (fat or ntfs), as windows can only access a couple of different filesystems. Since you do not have write access to this partition and since you're using windoze xp, I suspect it is a ntfs partition. To gain full control over your ntfs partitions install ntfs-3g like this:
```
$sudo apt-get install ntfs-3g
```Or go to System>Administration>Synaptic and search for ntfs-3g and install.

Once ntfs-3g is installed open your fstab in an editor:
```
$sudo gedit /etc/fstab
```Find the line that refers to /host, it should look something like this:
```
UUID=1E5A005C5A003357    /host    ntfs ro
```Change it to make it look like this:
```
UUID=1E5A005C5A003357    /host    ntfs-3g rw
```In a terminal execute these commands:
```
$sudo umount /host  ##unmount the partition with your music files
$sudo mount -a  ##mount all the partitions listed in /etc/fstab
```If you open nautilus and check the permissions, you should find that you have complete control now.

Hope this helps.


yes i do see the GRUB menu when booting

im trying the other things right now; will post an edit with results.

---

### Post by Leppie on 2009-11-29
If you cannot find the /host entry, please post the entire contents of your /etc/fstab file.

---

### Post by homer1234 on 2009-11-29
> **homer1234 said:**
> yes i do see the GRUB menu when booting

im trying the other things right now; will post an edit with results.


ok so i opened the fstab but I don't see anything like that line you referred to;

i've got one line that says

/host/ubuntu/disks/root.disk /              ext4           loop,errors=remmount-ro 0        1


nothing that says UUID though..

---

### Post by Leppie on 2009-11-29
> **homer1234 said:**
> yes i do see the GRUB menu when booting


if you do see GRUB when booting, i suppose you have a full install.

---

### Post by homer1234 on 2009-11-29
> **Leppie said:**
> If you cannot find the /host entry, please post the entire contents of your /etc/fstab file.


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/home.disk /home           ext4    loop            0       2
/host/ubuntu/disks/usr.disk /usr            ext4    loop            0       2
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Leppie on 2009-11-29
what is the complete path to the concerning folder?

The /host/ubuntu/disks/ paths indicate a Wubi installation.

---

### Post by homer1234 on 2009-11-29
> **Leppie said:**
> what is the complete path to the concerning folder?


/host


to open it i go to my computer; filesystem then host

---

### Post by Leppie on 2009-11-29
Could you also please post your /etc/mtab file?

And the output of the following command:
```
$sudo fdisk -l
```

---

### Post by wilee-nilee on 2009-11-29
> **homer1234 said:**
> Hi,

I'm pretty new to linux in general and especially ubuntu and am having difficulty changing permissions on my system with ubuntu:

I'm sure you get alot of the whole "I'm a windows pro and and i don't understand any of this $%$" so I won't bother you with it but I WILL say this; 

please do not reply in "terminal speak" (if possible)
I understand that "terminal is my friend" but I ask you to please respect that I can come to that conclusion on my own; don't try to force it on me.

please do not forward me to another thread (again only if convenient and possible)
if it only takes you 30 seconds longer, please just type out the answer to my question rather than getting me a new thread; I've done research, I've read articles, I'm posting this thread not because I'm lazy, but because I am ASKING for help. 

Don't tell me what I'm doing is a bad idea; I honestly don't care, I just want to do what I want and then i'll worry about the rest later.


now for the question;

I have ubuntu loaded on a harddrive that I used to use for just storage; as such I have most of my music on there (now in a folder called "host" as named by linux).
I want to have FULL PERMISSIONS with that folder and I want to know how to give anyone I WANT full permissions with that folder and any other folder as well.
by full permissions i mean everything; so whoever it is should be able to click on there and delete everything for all i care. 
Oh, and I don't want to have to login to root everytime to get those full permissions (im aware of gksudo nautilus but I don't wanna use it everytime I just want to move a folder in that folder)


Thanks in advance for your help and please bear with me if I've said anything "stupid"

If you do not want to learn how to run a Linux system just say so. All of these limitations you pre-suppose will keep you from learning. Permissions are different in a Linux system they are set up to be temporary; like you would use the administrative portion of a MS set up when you should do the basic use in a limited account. In a MS environment you switch users or log off limited then log in administrative to make system wide changes

This limitation scenario makes it difficult to help you as is seen by just trying to see if you have a full install. It seems that your trying to come at Linux from a MS point of view not understanding the vulnerabilities that this may cause and why the limitations are there to keep a robust safety system in place.

I suspect none of this will help you realize this mind set, as you wouldn't have started with the limitations in the first place if you were willing to work to understand.

---

### Post by homer1234 on 2009-11-29
> **wilee-nilee said:**
> If you do not want to learn how to run a Linux system just say so. All of these limitations you pre-suppose will keep you from learning. Permissions are different in a Linux system they are set up to be temporary; like you would use the administrative portion of a MS set up when you should do the basic use in a limited account. In a MS environment you switch users or log off limited then log in administrative to make sytem wide changes

This limitation scenario makes it difficult to help you as is seen by just trying to see if you have a a wubi install or dual boot. It seems that your trying to come at Linux from a MS point of view not understanding the vulnerabilities that this may cause and why the limitations are there to keep a robust safety system in place.

I suspect none of this will help you realize this mind set, as you wouldn't have started with the limitations in the first place if you were willing to work to understand.


I am absolutely willing to learn this mind set and how to use linux;
the "limitations" I put forward were to simply help ME understand the solution better;

Please keep in mind that before every request I put in IF POSSIBLE 
I plan to understand this but at the same time I can't be expected to so all in one sitting right from the get go especially when I'm trying to do something to listen to music while reading articles on how to use linux!
(see the circular logic there? can you tell I'm a java programmer :P)
Anyways, I apologize if I came off as insistent or stubborn.


Also, I'm working on getting the info requested right now; I was in the middle of an uninstall and reinstall when i saw your post

---

### Post by ed-koala on 2009-11-29
Homer, let me ask a couple of questions that I think will help sort all this out, and see if I'm understanding this right..

You are running a fresh Ubuntu install, not an install from Windows using wubi...

You want anyone to create/delete files in your directory now owned by root. Does this include allowing anyone to delete your Ubuntu system files, thereby making your PC a brick?  Or is it just things like music, data, and things of that nature?

I'm not sure Ubuntu is going to let you change / permission from root, BUT you CAN get most files so that anyone can create/delete, but it'll take a small amount of organizing is all.

Let me know exactly which you are looking for pls.

---

### Post by wilee-nilee on 2009-11-29
If you are already a programmer then you will learn this stuff fast I suspect. I know very little really but I had the advantage of starting with Linux so when my friends have problems with their MS setups it is like playing pong in helping them, in comparison to a open source set up.

---

### Post by fluffman86 on 2009-11-29
edit /etc/fstab and add this line:

/host /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0

Then create a folder in /media called "windows" and reboot.  You'll now find the files you want under /media/windows instead of /host.

---

### Post by homer1234 on 2009-11-29
> **ed-koala said:**
> Homer, let me ask a couple of questions that I think will help sort all this out, and see if I'm understanding this right..

You are running a fresh Ubuntu install, not an install from Windows using wubi...

You want anyone to create/delete files in your directory now owned by root. Does this include allowing anyone to delete your Ubuntu system files, thereby making your PC a brick?  Or is it just things like music, data, and things of that nature?

I'm not sure Ubuntu is going to let you change / permission from root, BUT you CAN get most files so that anyone can create/delete, but it'll take a small amount of organizing is all.

Let me know exactly which you are looking for pls.

I think it might install from windows using wubi; but again I could be wrong.

I created the ISO file of ubuntu, burned it onto a dvd, inserted the dvd, and told it to reboot the system; in the menu that asked me if I want to install it within windows I said full installation.
does that answer that question? If not what I'm doing right now is uninstalling ubuntu using the wuubi uninstall file in xp and am going to reinstall it again using a new dvd



now for what I want It's just music and data and things of that nature.
I know better than to mess with system files like that or to make them available for other people to touch- I mean It'd be nice to UNDERSTAND HOW I would do that If I wanted, but as of right now, I just have a folder [host] that has all of my personal data (music, movies, documents, etc...) that I can only look at.
I can't move the folder, i cant add stuff to it, i cant delete stuff from it...
It's a folder under "root" arrest :D

---

### Post by fluffman86 on 2009-11-29
reposting this because I was too slow editing a previous post:
edit /etc/fstab and add this line:

/host /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0

Then create a folder in /media called "windows" and reboot.  You'll now find the files you want under /media/windows instead of /host.

---

### Post by ed-koala on 2009-11-29
Ok, I know nothing about Wubi, sorry. That may be part of the problem, I can't know.

Under a normal install making your data stuff changable by all is very easy :)

---

### Post by audiomick on 2009-11-30
Hi Homer.
It's turned into a bit of an epic, hasn't it?
I hope your re-install is going well.

I haven't looked at wubi at all, but I'm guessing that that is how you had installed. If you are now doing a classic dual boot installation, I think you will be happier with the result.

I will still keep an eye on this thread, so if you have other questions, e.g. partitioning or what have you, please ask.

Michael

---

### Post by Leppie on 2009-11-30
> **homer1234 said:**
> I think it might install from windows using wubi; but again I could be wrong.

I created the ISO file of ubuntu, burned it onto a dvd, inserted the dvd, and told it to reboot the system; in the menu that asked me if I want to install it within windows I said full installation.
does that answer that question? If not what I'm doing right now is uninstalling ubuntu using the wuubi uninstall file in xp and am going to reinstall it again using a new dvd

Wubi should do a complete install, but within a windoze partition. So it uses an amount of free space of your ntfs (windows xp) partition to assign as an ext4 (linux) partition. Also, instead of using GRUB, it will use the nt boot loader to choose between windoze and linux boot.

---

### Post by homer1234 on 2009-12-01
issue resolved :)

so, here's a rundown of what happened and what caused the issue;

Turns out, my computer has a problem with the optical drive so when I attempted to install ubuntu the first time on my system, it wasn't really a full install, but it wasn't a wubi install either.
so, I had an adventure with reinstalling ubuntu, complete with some very scary kernel cache misses, harddrive partitioning, and the terrifying prospect of having to make the decision of rewriting boot sectors vs. reformatting my hard drive.

Finally, I was able to get rid of all traces of the half install as well as the second failed reinstall and I installed ubuntu using an old flash drive I had.

The result?
everything is working PERFECTLY. 
And to add to it all, this even fixed some issues I had with not being able to re-size my swap memory, and even to install some plug-ins that I couldn't before.

Anyways, thank you everyone for all of your help!

---

### Post by Leppie on 2009-12-01
good to hear all is working fine now :)
well, at least now you know the optical drive needs replacing.

---

