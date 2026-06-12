---
title: "Change 'Pictures' location from /home to a NAS"
date: 2011-08-22
forum: General Help
---

### Post by Chris Grk-O-Matic on 2011-08-22
I bought an LG NAS for pic's, videos, and music. Is there a way to turn the pictures folder in the NAS into the default location for when I select the Pictures folder in my home directory?  
 
 
Running Ubuntu 10.10 on IBM's: T41, T42, T62

---

### Post by seawolf167 on 2011-08-22
What about something like this:

Make your directories on your NAS device (Pictures, Videos, etc.), move all your current items from those folders (on /home) to their respective folders on the NAS device, then delete the source directories (from /home), and re-create them as sym links which point to your NAS directories

---

### Post by Chris Grk-O-Matic on 2011-08-22
Thanks I think I got the deleting the source directory part. Is that as easy as just *deleting it* (the folder) on all my laptops? 
 
I did a quick search on sym links and by that do you mean like a shortcut? So I'm guessing with my NAS mounted, I should be able to right click on the icon that is on my desktop and make a sym link? Sorry, I'm not at home so I can't tinker but I appreciate your response.
 
 
Chris

---

### Post by seawolf167 on 2011-08-22
It should be.

make destination directory

```
mkdir /path/to/NAS/Pictures
```move items

```
cp -r ~/Pictures /path/to/NAS/Pictures
```delete Pictures on /home

```
rm -rf ~/Pictures
```**be very careful with this command!!**

make sym link to NAS directory

```
cd ~
ln -s /path/to/NAS/Pictures Pictures
```

---

### Post by Chris Grk-O-Matic on 2011-08-22
Thanks I look forward to trying out what you suggested.
 
Will I be able to upload to the NAS via the sym links with a picture managing program like fStop?
 
Best,
Chris

---

### Post by seawolf167 on 2011-08-22
The sym link is essentially just a pointer to another location, you can read more about it [here ]("http://manpages.ubuntu.com/manpages/jaunty/man7/symlink.7.html")or in the man page.

```
man ln
```Anything that is able to (or set to) follow sym links will follow them as if it were actually that folder/file. Some things don't follow sym links though to ensure that it (some program) doesn't take (or parse, backup, etc.) more than it is instructed too (by following into all sorts of possible sym links)

You could always create a "test" link & folder to ensure that anything you use will work (I believe it all should)

---

### Post by Chris Grk-O-Matic on 2011-08-22
I'm missing something here. For the first step, "Make a destination directory," I'm doing:

```
mkdir smb://lg-nas-n2a2.local/volume1_public/Pictures
```but then I'm getting a ```
cannot create directory
```What am I doing wrong here?

---

### Post by seawolf167 on 2011-08-22
Is this an NTFS volume? Do you have permission on that share to modify (rwx)? Are your user/groups set up correctly?

---

### Post by lmarmisa on 2011-08-22
> **Chris Grk-O-Matic said:**
> I'm missing something here. For the first step, "Make a destination directory," I'm doing:

```
mkdir smb://lg-nas-n2a2.local/volume1_public/Pictures
```but then I'm getting a ```
cannot create directory
```What am I doing wrong here?

You should automount the remote NAS folder adding a line to the file **/etc/fstab**. Have you done this?.

---

### Post by Chris Grk-O-Matic on 2011-08-22
> **seawolf167 said:**
> Is this an NTFS volume? Do you have permission on that share to modify (rwx)? Are your user/groups set up correctly?
The volume is set to raid1. I haven't done anything with permissions nor do I know how to approach that. As for Users, I figured I could leave it as admin so I didn't create any users.

So I take it I'm way off?

---

### Post by Chris Grk-O-Matic on 2011-08-22
> **lmarmisa said:**
> You should automount the remote NAS folder adding a line to the file **/etc/fstab**. Have you done this?.
No. Please explain.

---

### Post by lmarmisa on 2011-08-22
Try this procedure for automounting the NAS at startup.

Open a terminal and type:

```

sudo mkdir -p /media/NAS
gksudo gedit /etc/samba/credentials

```

Add two lines to this file:

```

username=NAS_username_here
password=NAS_password_here

```

Save & Quit.

Continue with these commands:

```

sudo chmod 600 /etc/samba/credentials
gksudo gedit /etc/fstab

```

Append these two lines at the end of file **fstab**:

```

# NAS
//NAS_name_or_IP_address_here/share_here /media/NAS cifs credentials=/etc/samba/credentials,uid=1000,gid=1000 0 0

```

Save & Quit.

Finally type this command and check if the NAS folder is mounted:

```

sudo mount -a

```

---

### Post by lmarmisa on 2011-08-22
According to your previous post, the actual lines to add to the file **fstab** are:

```

# volume1_public on lg-nas-n2a2
//lg-nas-n2a2.local/volume1_public /media/NAS cifs credentials=/etc/samba/credentials,uid=1000,gid=1000 0 0

```

---

### Post by Chris Grk-O-Matic on 2011-08-22
This is the result:


```
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

---

### Post by lmarmisa on 2011-08-22
> **Chris Grk-O-Matic said:**
> This is the result:


```
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

Ok. Type this command and post the result (do no post the NAS password, change it to xxxxx, for example):

```

sudo mount //lg-nas-n2a2.local/volume1_public /media/NAS -t cifs -o username=NAS_user,password=NAS_password,uid=1000,gid=1000

```

---

### Post by Chris Grk-O-Matic on 2011-08-22
I think I may have gotten this part wrong, correct me if I'm wrong:

When you instructed me to:
```
username=NAS_username_here
password=NAS_password_here
```

I put
```
username=NAS_XXXXX
password=NAS_XXXXX
```

Was I supposed to put this instead?
```
username=XXXXX
password=XXXXX
```

---

### Post by lmarmisa on 2011-08-22
I am referring to the user and password for accessing to the NAT. 

Did you define an user / password for it or are you using the default user **guest** with no password?.

---

### Post by Chris Grk-O-Matic on 2011-08-22
The NAS was left with the default user ID because it would not let me change it but I did change the password. Perhaps I should create a new user?

Thanks

---

### Post by lmarmisa on 2011-08-22
> **Chris Grk-O-Matic said:**
> The NAS was left with the default user ID because it would not let me change it but I did change the password. Perhaps I should create a new user?

Thanks

I think that a new user is not needed at the moment. Please, use those user_ID and password for mounting the remote folder.

But, type this manual command first:

```

sudo mount //lg-nas-n2a2.local/volume1_public /media/NAS -t cifs -o username=NAS_default_user_ID,password=NAS_password,uid=1000,gid=1000

```

If you are able to mount manually the folder, then we will continue with the automatic procedure.

---

### Post by Chris Grk-O-Matic on 2011-08-23
Hi lmarmisa. Well, after retiring from the forum last night and powering my computer back now, the NAS is mounted on my desktop. I guess that's a good thing. I mean, I don't know why it didn't do that last night before shutting it down.

So I followed your last step and did:
```
sudo mount //lg-nas-n2a2.local/volume1_public /media/NAS -t cifs -o username=XXXXX,password=XXXXXX,uid=1000,gid=1000
```and all that came up was ~$

Is it supposed to do that or was something else expected?

Thanks,
Chris

---

### Post by lmarmisa on 2011-08-23
> **Chris Grk-O-Matic said:**
> Hi lmarmisa. Well, after retiring from the forum last night and powering my computer back now, the NAS is mounted on my desktop. I guess that's a good thing. I mean, I don't know why it didn't do that last night before shutting it down.

So I followed your last step and did:
```
sudo mount //lg-nas-n2a2.local/volume1_public /media/NAS -t cifs -o username=XXXXX,password=XXXXXX,uid=1000,gid=1000
```and all that came up was ~$

Is it supposed to do that or was something else expected?

Thanks,
Chris

Ok. You have mounted manually the remote folder.

Please, check now the contents of the folder **/media/NAS** (this is the mount point). You have to find there the remote files stored in your NAS.

Do you see your files?.

---

### Post by Chris Grk-O-Matic on 2011-08-23
This is what came up in the terminal
```
bash: /media/NAS: is a directory
```I have a folder in there called Pictures and just some other random files I threw in for testing purposes.

Why is it that when I go to Places > Network > LG-NAS-N2A2 there seems to be to volumes? One is volume1_public and the other is service with folders called DLNA, Torrent, iTunes - even though I set it up for RAID1?

---

### Post by lmarmisa on 2011-08-23
> **Chris Grk-O-Matic said:**
> This is what came up in the terminal
```
bash: /media/NAS: is a directory
```I have a folder in there called Pictures and just some other random files I threw in for testing purposes.

Why is it that when I go to Places > Network > LG-NAS-N2A2 there seems to be to volumes? One is volume1_public and the other is service with folders called DLNA, Torrent, iTunes - even though I set it up for RAID1?

Hmmm. Step by step, please.

You have mounted the remote folder **smb://lg-nas-n2a2.local/volume1_public** on the local folder **/media/NAS**. I would like if you could see the contents of the folder **/media/NAS** using Nautilus.

Open **Nautilus** (**Places -> Computer**). Then select **File system -> media -> NAS**. Do you see the files stored in the volume1 folder of your NAS?. Try to create a new file or folder and then remove it.

Please, confirm if the contents are good and if you have permission for creating/removing files and folders in the folder NAS.

Best regards,

Luis

P.S. Did you feel the earthquake?.

---

### Post by Chris Grk-O-Matic on 2011-08-23
Yes I felt it. I was at work in a ten story office building that's right next to Manhattan when it occurred. The effect was so mild that at first I felt woozy, then the feeling wasn't going away and everybody else around me was just as bewildered. We all got up but did not feel the urge to run out of the building but if it got worse I was ready to put my chair through the window and run for it - luckily I'm in the 2nd level. It was creepy and it makes me feel for those who have experienced a lot worse.

So I did like you said and was able to open it in Nautilus and add and delete a file.

---

### Post by lmarmisa on 2011-08-23
Well. A new experience for you. I hope that the earthquake did not cause any damage mainly to persons.

Good news if you have tested that the mount was successful.

Do you wish to move your pictures from your home folder to the folder /media/NAS now?. You can use the cut & paste function of Nautilus for that. I recommend to select the icon Pictures, then cut and paste into the folder /media/NAS.

---

### Post by Chris Grk-O-Matic on 2011-08-23
Thanks a bunch! Will I have to do the same procedure on my other computers as well? Ultimately I'm hoping that we can use an image management program on any computer and it will access the NAS. Also, I will be saving video from ZoneMinder and MythTV to it as well with the goal of viewing on any computer, tablet and my TV via DLNA. I just have to figure out a file structure that makes sense and is easy to navigate.

---

### Post by lmarmisa on 2011-08-23
> **Chris Grk-O-Matic said:**
> Thanks a bunch! Will I have to do the same procedure on my other computers as well? Ultimately I'm hoping that we can use an image management program on any computer and it will access the NAS. Also, I will be saving video from ZoneMinder and MythTV to it as well with the goal of viewing on any computer, tablet and my TV via DLNA. I just have to figure out a file structure that makes sense and is easy to navigate.

I suppose that you have no pictures in your home folder now. They have been moved to /media/NAS/Pictures.

We have to complete the 2 remaining steps:

1) Define a symbolic link from your home directory to the new location of the folder Pictures.

2) Check why the automatic mount procedure did not work.

You ask me if you have to repeat the procedure on your other computer too. And the answer is yes. I do not know if you have you familiar or personal pictures stored in several computers. Try to use the NAS as your picture repository. Select your strategy about how to organize your pictures. In my case, I use the next tree structure:

```

Pictures - Family  --- 2011
         |          |- 2010
         |          |- 2009
         |          ....
         | Hobbies --- Aircraft Photos
                    |.... 

```

Other very important issue: define a strategy for your backups. Your personal pictures and all your personal files are very important. I recommend to make a backup of your NAS repository using rsync or a similar tool.

Could you post the results of these commands?:

```

ls -l ~
ls -l /media/NAS

```

If they look good, I will send you the command for creating the symbolic link.

---

### Post by Chris Grk-O-Matic on 2011-08-24
On this computer I actually didn't have any pictures in the home folder, but here are the results you asked for:

```
rosarie@rosarie-ThinkPad-T41:~$ ls -l ~
total 36
drwxr-xr-x 2 rosarie rosarie 4096 2011-07-21 19:53 Desktop
drwxr-xr-x 2 rosarie rosarie 4096 2011-06-05 16:43 Documents
drwxr-xr-x 2 rosarie rosarie 4096 2011-07-21 20:53 Downloads
-rw-r--r-- 1 rosarie rosarie  179 2011-04-18 11:30 examples.desktop
drwxr-xr-x 2 rosarie rosarie 4096 2011-04-18 11:36 Music
drwxr-xr-x 4 rosarie rosarie 4096 2011-08-21 19:43 Pictures
drwxr-xr-x 2 rosarie rosarie 4096 2011-04-18 11:36 Public
drwxr-xr-x 2 rosarie rosarie 4096 2011-04-18 11:36 Templates
drwxr-xr-x 3 rosarie rosarie 4096 2011-06-01 21:53 Videos
```

```
rosarie@rosarie-ThinkPad-T41:~$ ls -l /media/NAS
total 0
drwxr-xr-x 1 rosarie rosarie 0 2011-08-23 22:13 DLNA
drwxr-xr-x 1 rosarie rosarie 0 2011-08-23 21:21 MythTV
drwxr-xr-x 1 rosarie rosarie 0 2011-08-23 21:18 Pictures
drwxr-xr-x 1 rosarie rosarie 0 2011-08-23 22:07 TEST
drwxr-xr-x 1 rosarie rosarie 0 2011-08-23 21:21 WebCam
```

---

### Post by lmarmisa on 2011-08-24
Thanks.

Please type these commands:

```

cd ~
mv Pictures Pictures.old
ln -s /media/NAS/Pictures Pictures

```

Now, you will be able to access your pictures in the folder ~/Pictures ( /home/rosarie/Pictures ). But your pictures are really stored in your NAS.

In relation with the automatic mount procedure I did not pay my attention to your [post #16]("http://ubuntuforums.org/showpost.php?p=11177573&postcount=16"). I think that you are right and this is the mistake you typed.

---

### Post by Chris Grk-O-Matic on 2011-08-24
Awesome. Thank you for taking the time to help me out with this.

So for example, ~/Documents, I would do the same procedure except substitute the word Pictures for Documents in the code? I'm going to have to get back to you on this once I'm comfortable with what we just did, but I think I would like to split ~/Documents into to subdirectories, one in my wife's name and one in mine. And same with Video, one subdirectory for MythTV and another for Webcam. This seems to make sense in theory.

From the terminal output from before, what does this mean?
```
drwxr-xr-x 2 rosarie rosarie 4096
```

---

### Post by lmarmisa on 2011-08-24
> **Chris Grk-O-Matic said:**
> Awesome. Thank you for taking the time to help me out with this.

So for example, ~/Documents, I would do the same procedure except substitute the word Pictures for Documents in the code?


You do not need to repeat the complete procedure. The procedure for automounting the NAS folder at startup ([post #12]("http://ubuntuforums.org/showpost.php?p=11177449&postcount=12")) has not to be repeated. BTW, is that problem solved?.

After startup, all the shared contents of the NAS are in **/media/NAS**. Move your documents to the appropriate folder you want, for example, to **/media/NAS/Documents**.

Finally, type these commands:

```

cd ~
mv Documents Documents.old
ln -s /media/NAS/Documents Documents

```

I have defined two folders **Pictures.old** and **Documents.old**. Feel free to remove them if you are sure they are empty.

> 
 I'm going to have to get back to you on this once I'm comfortable with what we just did, but I think I would like to split ~/Documents into to subdirectories, one in my wife's name and one in mine. And same with Video, one subdirectory for MythTV and another for Webcam. This seems to make sense in theory.

From the terminal output from before, what does this mean?
```
drwxr-xr-x 2 rosarie rosarie 4096
```

In relation with your last question, rosarie is the owner of the file. She is really the owner of the file inside your computer not in the NAS (but this detail is too tech). d means directory, r read permission, w write permission, x execute permission. The global meaning of the string **drwxr-xr-x**: directory; the owner has permissions for r, w and x; group for r and x; and other for r and x. 4096 is the size of the file (or the inode size in the case of a directory). 2 is the number of links pointing to it. All this stuff is very important for geeks. ;)

---

### Post by Chris Grk-O-Matic on 2011-08-24
> **lmarmisa said:**
> You do not need to repeat the complete procedure. The procedure for automounting the NAS folder at startup ([post #12]("http://ubuntuforums.org/showpost.php?p=11177449&postcount=12")) has not to be repeated. BTW, is that problem solved?
Yes it's solved. But I do have to do the automount procedure on my other pc's correct?

---

### Post by lmarmisa on 2011-08-24
> **Chris Grk-O-Matic said:**
> Yes it's solved. But I do have to do the automount procedure on my other pc's correct?

Yes, this is correct.

---

### Post by lmarmisa on 2011-08-24
If you have several PCs, maybe you will wish to give read-only permissions to some users or some PCs.

This can be made in several ways. I recommend to define a new user in your NAS with read only privileges. Then, if you wish to mount your NAS folder in read-only mode, use this alternative user and its password in the file **/etc/samba/credentials**. Very easy.

---

### Post by Chris Grk-O-Matic on 2011-08-26
Okay I think I did a bad thing.

While moving on from a successful PC#1 to making a futile attempt of doing the same thing to PC#2, I have gotten stuck again, perhaps due to not following your directions correctly. Particularly the one where you said I do not have to repeat step#12.  But I did it on PC#2 because automounting seemed logical to me (how else would the NAS automount, right?). 

This is what I got:
  	 	 	 	p { margin-bottom: 0.08in; }```
ibm@ibm-laptop:~$ sudo mkdir -p /media/NAS  
 [sudo] password for ibm:  
 ibm@ibm-laptop:~$ gksudo gedit /etc/samba/credentials  
 ibm@ibm-laptop:~$ sudo chmod 600 /etc/samba/credentials  
 ibm@ibm-laptop:~$ gksudo gedit /etc/fstab  
 ibm@ibm-laptop:~$ sudo mount -a  
 mount: wrong fs type, bad option, bad superblock on //lg-nas-n2a2.local/volume1_public,  
        missing codepage or helper program, or other error  
        (for several filesystems (e.g. nfs, cifs) you might  
        need a /sbin/mount.<type> helper program)  
        In some cases useful info is found in syslog - try  
        dmesg | tail  or so  
 

 ibm@ibm-laptop:~$  

```

Was I not supposed to do the fstab?

---

### Post by lmarmisa on 2011-08-27
> **Chris Grk-O-Matic said:**
> Okay I think I did a bad thing.

While moving on from a successful PC#1 to making a futile attempt of doing the same thing to PC#2, I have gotten stuck again, perhaps due to not following your directions correctly. Particularly the one where you said I do not have to repeat step#12.  But I did it on PC#2 because automounting seemed logical to me (how else would the NAS automount, right?). 

This is what I got:
  	 	 	 	p { margin-bottom: 0.08in; }```
ibm@ibm-laptop:~$ sudo mkdir -p /media/NAS  
 [sudo] password for ibm:  
 ibm@ibm-laptop:~$ gksudo gedit /etc/samba/credentials  
 ibm@ibm-laptop:~$ sudo chmod 600 /etc/samba/credentials  
 ibm@ibm-laptop:~$ gksudo gedit /etc/fstab  
 ibm@ibm-laptop:~$ sudo mount -a  
 mount: wrong fs type, bad option, bad superblock on //lg-nas-n2a2.local/volume1_public,  
        missing codepage or helper program, or other error  
        (for several filesystems (e.g. nfs, cifs) you might  
        need a /sbin/mount.<type> helper program)  
        In some cases useful info is found in syslog - try  
        dmesg | tail  or so  
 

 ibm@ibm-laptop:~$  

```

Was I not supposed to do the fstab?

Maybe the problem is due because the package **samba** is not installed. Type this command for installing it:

```

sudo apt-get install samba

```

Then try again this command:

```

sudo mount -a

```

If the problem is not solved, plz post the result of this command:

```

cat /etc/fstab

```

Best regards,

Luis

---

### Post by Chris Grk-O-Matic on 2011-08-27
Okay I just installed Samba and then:
```
ibm@ibm-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7fe8e9a0-47f4-4bdd-abd3-9cf8a2a74677 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=20a3bd1c-e778-426a-a0bf-93378fd24703 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# volume1_public on lg-nas-n2a2
//lg-nas-n2a2.local/volume1_public /media/NAS cifs credentials=/etc/samba/credentials,uid=1000,gid=1000 0 0
ibm@ibm-laptop:~$ 
```

Thanks Luis,
Chris

---

### Post by Morbius1 on 2011-08-27
Excuse the intrusion but there is a good chance that this error:
> ibm@ibm-laptop:~$ sudo mount -a  
 mount: wrong fs type, bad option, bad superblock on //lg-nas-n2a2.local/volume1_public,  
        missing codepage or helper program, or other error  
        (for several filesystems (e.g. nfs, cifs) you might  
        need a /sbin/mount.<type> helper program)  
        In some cases useful info is found in syslog - try  
        dmesg | tail  or so  Is due to a package not being installed:
```
sudo apt-get install cifs-utils
```Or on an older Ubuntu install:
```
sudo apt-get install smbfs
```

---

### Post by Chris Grk-O-Matic on 2011-08-27
Thanks it worked! What was the problem?

Now when I go to /home/ibm/pictures is there a way that the folder can open up with Dolpin as opposed to, err, I think it's called Nautilus?  I have Dolphin installed.

---

### Post by lmarmisa on 2011-08-28
> **Chris Grk-O-Matic said:**
> Thanks it worked! What was the problem?

Now when I go to /home/ibm/pictures is there a way that the folder can open up with Dolpin as opposed to, err, I think it's called Nautilus?  I have Dolphin installed.

Hi Chris,

According to your comments I believe that the Linux distro that you have installed on your second computer is not exactly Ubuntu. I think that you are running Kubuntu or other KDE distro. This could explain why the default file manager is Dolphin. This reason would explain the need of additional packages for mounting the remote folder using CIFS/Samba too.

Please, check if Dolphin is able to see the files located at /home/NAS/Pictures.

Best regards,

Luis

P.S. I wish that the damages produced by Irene are small.

---

### Post by Chris Grk-O-Matic on 2011-08-29
I am running Ubuntu but I downloaded Dolphin a while ago because I like the layout. My NAS is displayed in Dolphin and it works well. I'm just wondering if Dolphin can pop up as the default instead of Nautilus.
&#12288;
We got a lot of rain and strong winds but thankfully that's about it for where I live. Some places that are not to far away from me had far worse damage. I learned recently that with northern hemisphere hurricanes, the windiest part is always to the east of the eye of the storm. Which would explain why suburbs in New York such as Queens looked really bad as per what I saw on the news. But thanks for the consideration.
&#12288;
What a week eh?!

---

### Post by lmarmisa on 2011-08-30
> **Chris Grk-O-Matic said:**
> I am running Ubuntu but I downloaded Dolphin a while ago because I like the layout. My NAS is displayed in Dolphin and it works well. I'm just wondering if Dolphin can pop up as the default instead of Nautilus.
&#12288;
We got a lot of rain and strong winds but thankfully that's about it for where I live. Some places that are not to far away from me had far worse damage. I learned recently that with northern hemisphere hurricanes, the windiest part is always to the east of the eye of the storm. Which would explain why suburbs in New York such as Queens looked really bad as per what I saw on the news. But thanks for the consideration.
&#12288;
What a week eh?!

Yes, your week was not too good. I hope that the damages will be repaired soon and everything back to normal. :-D

In relation with Dolphin, I have found this link that could help you:

[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

---

### Post by TheValk on 2011-09-06
I hope sufficient time has past to excuse me hi-jacking a thread.

I have the same model NAS and I found this thread helped me set up auto-login just fine.

One problem has shown up though.  If I login through the network to the NAS I can upload from the PC to the NAS at around 19.5MB/sec.
However, if I use the procedure here to auto-login my upload is around 6.8MB/sec, a huge drop.

I am on Lucid with the NAS and the PC on a gigabit LAN through a gigabit switch.

Any thoughts anyone?

---

### Post by Morbius1 on 2011-09-06
Then don't use this method use the "network" method - just automate it.

When you go through "Network" you are using this command:
```
gvfs-mount smb://server/share
```You can use Gigolo which uses the exact same method to access the remote share but has an "auto-mount" feature:
[http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

---

### Post by TheValk on 2011-09-07
> **Morbius1 said:**
> Then don't use this method use the "network" method - just automate it.

When you go through "Network" you are using this command:
```
gvfs-mount smb://server/share
```You can use Gigolo which uses the exact same method to access the remote share but has an "auto-mount" feature:
[http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

Thanks for that.  I'll give it a go.

OK, installed Gigolo and set up an auto-mount.

Works a treat.  Now uploading at 18MB/sec, (limited by the USB drive source).

Many thanks.

---

