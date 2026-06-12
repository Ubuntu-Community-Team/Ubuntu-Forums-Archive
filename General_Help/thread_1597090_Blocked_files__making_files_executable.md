---
title: "Blocked files / making files executable?"
date: 2010-10-14
forum: General Help
---

### Post by anonymousie on 2010-10-14
I just upgraded to 10.10 (everything was working fine in 10.04). I'm very much a newbie, so be gentle.

Here's my problem. I have .jar files that in 10.04 would execute with OpenJDK. Now I get an error message, telling me that it is blocked:

"The file '[path]' is not marked as executable. If this was downloaded or copied from an untrusted source, it may be dangerous to run. For more details, read about the executable bit."

I try to set it as executable like it was before, and it's a no go. My checkmark takes then quickly disappears before my eyes.

Can anyone help me fix this?

---

### Post by Lars_bylund on 2010-10-23
no solution, but got the same problem, also cos of upgrade from 10.04 to 10.10...

Please help.

edit: left click on the .exe file, open with>other applications> then click on the 'use a custom command and type wine.

If the 'remember this application for dos/windows...' box is checked, I guess this will be true to other .exe applications.

Then just press open.

I manage to open .exe files by just klicking on em, but still can not set it as executable in the properties, so there's some kind of bug or something.

the .exe files are read-and-write.

I also did this: (originally posted here: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1500627](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1500627))

Here's what you need to do to revert the  "open with wine windows program loader" to the old defaults.
 	Quote:
 	 	 		 			 				 					Originally Posted by **mc4man** 					 				
 				[I]      	Code:
 	gksu gedit /usr/share/applications/wine.desktop 
In the .desktop look for line Exec= and change to this, save and  close
      	Code:
 	Exec=wine start /unix %f 
[/I]
"

But i dont know how this afected the situation.

However, it did not solve that you cant check the box.

---

### Post by efflandt on 2010-10-23
In a terminal read: **man chmod**
But for system files you have to do that as root (using **sudo**) or **sudo nautilus** (**gksu nautilus** kept throwing errors about gconf_value_free, but seemed to work also)

For example if you cd to that directory then **sudo chmod 755 *.jar**
But if the files have rw-r--r-- permission **sudo chmod +x *.jar** would work as well.

Note that **x** permission on a directory has different meaning than for a file.  For a file it means "execute" permission, but for a directory **x** is required to "access" the directory (in order to list files with ls or anything).  So that is why directories often have 755 permission (drwxr-xr-x).

---

### Post by WorMzy on 2010-10-23
Is this file stored on an NTFS partition? If so you have a choice. You can either copy it to your EXT4 partition, and run it from there (after setting the executable bit), OR you can change the permissions that NTFS partitions mount with.

For the second option, you just need to create an entry in /etc/fstab for the partition. Take a look at this file first, you'll see that there are several columns of information. To know what to put as the information for your NTFS drive, we'll need to know a few things about the partition. Once you have all the information, you can edit fstab by running
```
gksu gedit /etc/fstab
```

[LIST]
[*]Firstly: **which partition is it**?
In this case, this needs to be a device node identifier. e.g. /dev/sda1, a partition UUID, or a partition label. run
```
sudo blkid -c /dev/null
```
and it will tell you all the relevant information about your partitions. Hopefully you can determine from this list which one is the correct partition.

If you use a UUID or Label, you need to declare it as such. e.g. "*[COLOR="Red"]LABEL=Windows[/COLOR]*", "UUID=[COLOR="Red"]*ABCDEFGHIJKLKLMNOP*[/COLOR]".

[*]Next, **where should it be mounted**?
This part is simple: where do you want the partition to be accessible from? Ubuntu mounts partitions in /media by default, so if you want the partition to be mounted there, say so. e.g. "/media/Windows". You will need to manually create this folder since fstab will complain if it's not there, so make sure that the folder isn't being used already, and run ```
sudo mkdir /media/Windows
```

[*]Next, **which filesystem should it be mounted as**?
Since we're mounting an ntfs partition, specify "ntfs" or "ntfs-3g" for this column. As far as I'm aware, there's no difference between these, so don't split hairs deciding which to use.

[*]Next, **what options should it be mounted with**?
This is the most important column in this case, this is where you specify permissions. How you do this isn't immediately obvious, but there's a way, and it's actually rather simple.

This is a comma separated list, so don't use spaces or tabs, or else you'll find that the mount line doesn't work as expected. To specify the permissions, you merely need to declare three things: UID, GID, and umask.
[LIST]
[*]uid=*[COLOR="Red"]####[/COLOR]* specifies which userid should own the files on the partition. e.g. "uid=1000" means that the user with the id "1000" should own the files. You can find out your UID by opening a terminal and running "echo $UID".

[*]gid=*[COLOR="Red"]####[/COLOR]* specified which groupid should own the files on the partition. e.g. "gid=1000" means that the group with the id "1000" should own the files. Finding out groupids is slightly more difficult than finding out your userid because you can belong to several groups at the same time. Now, Ubuntu normally creates a group for every user, with the same ID as the UID, so you can probably use your UID as the GID. However, you can get a list of groups by running, in a terminal, "cat /etc/group". This will display a list with upto four colon-separated fields per line. The lines will contain the following items: name, an encrypted password, the GID, and a list of users in the group. Find the group you want to use, and add it's GID to the options.

[*]umask=*[COLOR="Red"]UGO[/COLOR]* is the most important of the three options; it specifies what the permissions will be for the user, the group, and everyone else. The numbers used here need to be between 0 and 7, anything else will probably cause an error. These numbers are actually an inverse of normal permissions, so while "7" means "read, write, and execute" in normal permission setting, in fstab "7" means "no permissions". Setting "umask=000" will give EVERYONE read, write, and execute permissions. For clarification, the U is the permissions for the user, G is for group, and O is for others.
[/LIST]

You may also add other things to this list. Generally speaking, it's best to start with the "defaults" option. "auto" makes the partition mount automatically when you boot up. Read more here: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

[*]**The final two columns should be "0" and "0"**.
These two columns are only used for Linux filesystems, so setting them to 0 stops any complications from arising.
[/LIST]
A finished fstab line may look like:
```
UUID=ABCDEFGHIJKLKLMNOP /media/Windows ntfs defaults,auto,uid=1000,gid=1000,umask=002 0 0
```
another example:
```
/dev/sdb5 /mnt/Music ntfs-3g defaults,uid=1002,gid=1500,umask=227
```

---

### Post by Lars_bylund on 2010-10-23
[COLOR=Red]Did you even read what I wrote before replying?[/COLOR]
> **Lars_bylund said:**
> no solution, but got the same problem, also cos of upgrade from 10.04 to 10.10...

Please help.
[COLOR=Red]
[COLOR=Red]edit: left click on the .exe file, open with>other applications> then click on the 'use a custom command and type wine.

If the 'remember this application for dos/windows...' box is checked, I guess this will be true to other .exe applications.[/COLOR][/COLOR] [COLOR=Red]

Then just press open.[/COLOR] [COLOR=Red]

I manage to open .exe files by just klicking on em, but still can not set it as executable in the properties, so there's some kind of bug or something.[/COLOR] 

the .exe files are read-and-write.

I also did this: (originally posted here: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1500627](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1500627))

Here's what you need to do to revert the  "open with wine windows program loader" to the old defaults.
     Quote:
                                                                      Originally Posted by **mc4man**                                      
                 [I]          Code:
     gksu gedit /usr/share/applications/wine.desktop 
In the .desktop look for line Exec= and change to this, save and  close
          Code:
     Exec=wine start /unix %f 
[/I]
"

But i dont know how this afected the situation.

However, it did not solve that you cant check the box.

---

### Post by SeijiSensei on 2010-10-24
> **anonymousie said:**
> "The file '[path]' is not marked as executable. If this was downloaded or copied from an untrusted source, it may be dangerous to run. For more details, read about the executable bit."

I'm not up on Java, but is the file listed in '[path]' a .jar?  If so, then "sudo chmod a+x /path/to/file.jar" will mark it as world-executable.

---

