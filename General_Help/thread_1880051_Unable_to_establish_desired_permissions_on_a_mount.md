---
title: "Unable to establish desired permissions on a mounted share"
date: 2011-11-12
forum: General Help
---

### Post by petersfreeman on 2011-11-12
**Background**

As well as two routers, a switch, hub, wireless access points and a smart TV box, our home LAN consists of a printer and two desktops and two laptops all running Ubuntu 11.10.

On all four computers (two desktops and two laptops), I have created user accounts for all biological family members and established a group called "family" of which all members of our biological family are members.  I have set each UserID with "family" as its "Main Group" (Users and Groups/Advanced Settings).  This means that any family member can use any computer as they will have a home folder on all four computers so they can sit down at any desktop or take either of the two laptops when traveling.

In the ~/.profile file, I have set umask as such:
```
umask 0007
```
so the result is that created files and directories on all computers show up as:
```
-rw-rw---- 1 <owner> family    0 2011-11-11 12:32 Temp
drwxrwx--- 3 <owner> family 4096 2011-11-12 10:22 Test1

```
with <owner> being the UserID of the person who created the file/directory and all files in all home folders will have the group "family" with read and write access and no access whatsoever for any non-family member.

So far so good...

One of the desktops (let's name it MAIN) has two USB drives connected to it, one is a 2TB and the other is 1TB in size. 

I labeled the USB drives and they are mounted simply by plugging them in.
  
The larger drive is used to store media and the smaller drive is a backup of our household files.

Each user backs up their files onto the 1TB drives (let's label it OURFILES attached to desktop MAIN.

After plugging in the USB cables, the drives show up on the desktop of MAIN and in Nautilus running on MAIN and also in MAIN's /media/ folder, e.g. /media/OURFILES/

OURFILES has a folder for each of the users and a folder for pictures so it looks like this:
```
OURFILES
   /bill/
   /timmy/
   /susan/
   /katy/
   /Pictures/
```
The bash script that I wrote to do the backup is identical on all machines and uses rsync with rsh and ssh to copy new and updated files to OURFILES so that all files in ~/Documents/ go to the respective OURFILES/$USER folder.  

It also copies pictures from the ~/Pictures/ folder into OURFILES/Pictures so that our family pictures, no mater who takes them, or on what machine or in whosoever's home folder, end up all together in the OURFILES/Pictures.  

The script has been used and evolving over the years, gaining sophistication, however it has had a nagging number of permissions problems. I set about to properly structure everything and examine my system from end to end.

**Testing**

First I tested file and directory creation in the home folder of each machine of each user and the correct permissions have been applied to the folders (drwxrwx---) and to the files (-rw-rw----)

All good.

Now I tested each user on the desktop MAIN in creating folders and files on the 1TB USB drive OURFILES.  The permissions are also correct.

I now made the two USB drives shareable by right clicking on the folder in /media/  (for example /media/OURFILES), choosing "Properties" then "Share" tab, checking "Share this folder" and creating a share name of OURFILES.  I checked "Allow others to create and delete files in this folder" making sure that "Guest Access" is not checked.

From one of the laptops, I connected to the share by using Nautilus (Go/Network/MAIN/OURFILES).  It connected but 
in the list view (extra columns) shows the "owner" "group" and "permissions" as "unknown".  I tested creating a folder and a file on this shared drive and found that the permissions bestowed upon this newly created folder and file was:
```
-r-xr-x--- 1 <owner> family    0 2011-11-11 12:32 Temp2
drwxr-xr-x 3 <owner> family 4096 2011-11-12 10:22 Test2

```
Not what I wanted...

Next I used fstab to mount the shares with these entries after creating folders in /media/ and creating a credentials file in /root/ :
```
//MAIN/OURFILES /media/OURFILES cifs user,auto,iocharset=utf8,uid=<userid>,gid=family,credentials=/root/.credentials,file_mode=0660,dir_mode=0770 0 0
//MAIN/OURMEDIA /media/OURFILES cifs user,auto,iocharset=utf8,uid=<userid>,gid=family,credentials=/root/.credentials,file_mode=0660,dir_mode=0770 0 0
```

I can navigate the share from a laptop but when I try to create a file or folder, I get "Error creating directory: Permission denied"

I tried changing the file_mode and dir_mode in fstab to different number but it does not seem to affect it.

I am obviously not understanding something here.

Please help.

Thank you,

Peter

---

### Post by Cyclane on 2011-11-12
What does it say when you use mkdir with verbose output?

```
mkdir -v test_dir
```

---

### Post by petersfreeman on 2011-11-13
Hi Cyclane,

I'm just rebuilding MAIN, however I'll try it in the morning and let you know.  Thanks for the tip.

Cheers,

Peter

---

### Post by Cyclane on 2011-11-13
I've never tried the verbose output of mkdir, so I don't know what to expect of it. So when you're done could you show the output of 'ls -l /media/' and I recommend adding the option rw to fstab. (read-write). Also why does fstab contain the option user, i presume standard users can't read the credentials file? (although this is unrelated to the problem you're experiencing)

And by the way you mention that it doesn't work when you use a USB disk, can I safely assume it works when u use one of your internal disks (when you use any other folder on your system)

---

### Post by fixerdave on 2011-11-13
There is something called a sticky bit that makes sure group permissions stick with newly created stuff.  Here's the info I have recorded on it... not mine, but a cut/paste from a long-ago search of basically the same problem.  I DO NOT recommend you just cut/paste this into a commandline, but from your post it sounds like the info will help you figure out what's going wrong.


random info follows:

find share -type d -exec sudo chmod 2770 '{}' \;   does only directories
find share -type f -exec sudo chmod 0660 '{}' \;    does only files

SGID sticky bit (the 2 of 2770) makes the GID stick for any new files or folders made, thus ensuring group access to the files.  Do NOT set this on the file, only on directories.  Files should never have any sticky bits set, and there is no reason to have execute either.

---

### Post by Cyclane on 2011-11-14
It's called a SGID not a sticky bit. I happened to explain the difference a few minutes ago: [http://ubuntuforums.org/showpost.php?p=11454827&postcount=5](http://ubuntuforums.org/showpost.php?p=11454827&postcount=5)

---

### Post by petersfreeman on 2011-11-21
Hi Cyclane and Fixerdave,

Server MAIN blew up bad, so it has been a while since I have had a chance to look at this problem.  I have rebuilt MAIN using Kubuntu and am looking at this problem again.  I'll look at the SGID for the directories.  I assume that if I were to set the SGID for the foot folder, sublevel folders would inherit the SGID.  I'll look at it tomorrow.

Cheers,

Peter

---

### Post by Cyclane on 2011-11-22
Newly created files/dirs inherit this permission yes

---

