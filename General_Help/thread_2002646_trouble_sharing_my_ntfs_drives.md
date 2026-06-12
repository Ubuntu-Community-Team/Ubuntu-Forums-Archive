---
title: "trouble sharing my ntfs drives"
date: 2012-06-13
forum: General Help
---

### Post by eulu on 2012-06-13
I have two ntfs drives that I auto mount. I set the auto-mount up using [these instructions]("http://it-diary.com/tutorials/how-to-auto-mount-ntfs-partitions-in-ubuntu/")... (adding lines in fstab)

This seems to work fine but wondering if it's preventing me from sharing my drives on the network.

At first I got the following message when trying to share the drives:
[SIZE=1]"'net usershare' returned error 255: net usershare add: cannot share path /media/Data2 as we are restricted to only sharing directories we own. Ask the administrator to add the line "usershare owner only = false" 
    to the [global] section of the smb.conf to allow this."[/SIZE]

So I followed[ these instructions]("http://ubuntuforums.org/showthread.php?t=1691164") to do what was suggested and now I get this message when trying to share the drives: 
[SIZE=1]'net usershare' returned error 255: net usershare add: failed[/SIZE]

  Any ideas what I need to do? I am guessing something about my fstab lines isn't right/complete.. Here's my auto-mount lines in fstab currently: 
[SIZE=1]/dev/sdb1  /media/Data1  ntfs  defaults  0 0
/dev/sdc1  /media/Data2  ntfs  defaults  0 0[/SIZE]

**EDIT:** Upon some searching.. Should I include the part in bold, rather than "defaults"?
/dev/sdb1 /media/Data1 ntfs  **nls=iso8859-1,umask=000**   0  0  

 I didn't try sharing the drives before I added the auto-mount settings  because I just had to reload the OS due to nvidia driver hell..  I am pretty sure I'd be able to share the drives if I take out the auto mounts from fstab..

---

### Post by idoitprone on 2012-06-13
> **eulu said:**
> I have two ntfs drives that I auto mount. I set the auto-mount up using [these instructions]("http://it-diary.com/tutorials/how-to-auto-mount-ntfs-partitions-in-ubuntu/")... (adding lines in fstab)

This seems to work fine but wondering if it's preventing me from sharing my drives on the network.

At first I got the following message when trying to share the drives:
[SIZE=1]"'net usershare' returned error 255: net usershare add: cannot share path /media/Data2 as we are restricted to only sharing directories we own. Ask the administrator to add the line "usershare owner only = false" 
    to the [global] section of the smb.conf to allow this."[/SIZE]

So I followed[ these instructions]("http://ubuntuforums.org/showthread.php?t=1691164") to do what was suggested and now I get this message when trying to share the drives: 
[SIZE=1]'net usershare' returned error 255: net usershare add: failed[/SIZE]

  Any ideas what I need to do? I am guessing something about my fstab lines isn't right/complete.. Here's my auto-mount lines in fstab currently: 
[SIZE=1]/dev/sdb1  /media/Data1  ntfs  defaults  0 0
/dev/sdc1  /media/Data2  ntfs  defaults  0 0[/SIZE]

**EDIT:** Upon some searching.. Should I include the part in bold, rather than "defaults"?
/dev/sdb1 /media/Data1 ntfs  **nls=iso8859-1,umask=000**   0  0  

 I didn't try sharing the drives before I added the auto-mount settings  because I just had to reload the OS due to nvidia driver hell..  I am pretty sure I'd be able to share the drives if I take out the auto mounts from fstab..

you dont really need nls=isp886watever

```
 /dev/sdb1 /media/Data1 ntfs-3g defaults,locale=en_US.utf8   0  0  
```
perhaps change it to this

did you install ntfs-3g?

```
sudo apt-get install ntfs-3g
```

remount the filesystem or reboot because once windows filesystems are mounted, you cannot change the permissions

---

### Post by eulu on 2012-06-13
I tried 
```
/dev/sdb1 /media/Data1 ntfs  nls=iso8859-1,umask=000   0  0
```and your 
```
/dev/sdb1 /media/Data1 ntfs-3g defaults,locale=en_US.utf8   0  0 
```and still get 
```
'net usershare' returned error 255: net usershare add: failed
```
when trying to share the drive

---

### Post by idoitprone on 2012-06-13
> **eulu said:**
> I tried 
```
/dev/sdb1 /media/Data1 ntfs  nls=iso8859-1,umask=000   0  0
```and your 
```
/dev/sdb1 /media/Data1 ntfs-3g defaults,locale=en_US.utf8   0  0 
```and still get 
```
'net usershare' returned error 255: net usershare add: failed
```when trying to share the drive

did you install ntfs-3g

then remount or reboot you computer?

---

### Post by eulu on 2012-06-13
Yes, well actually when I tried to install ntfs 3g it said it was already installed, though I never consciously did so... But yes rebooted after changing the line...

---

### Post by idoitprone on 2012-06-13
> **eulu said:**
> Yes, well actually when I tried to install ntfs 3g it said it was already installed, though I never consciously did so... But yes rebooted after changing the line...

post output of```
 ls -l  /media/Data1
```

---

### Post by eulu on 2012-06-13
```
total 584
drwxrwxrwx 1 root root   4096 Apr 24 12:51 Applications
drwxrwxrwx 1 root root   4096 Mar  8 11:57 Backup
drwxrwxrwx 1 root root   4096 Oct 13  2009 Buzz
drwxrwxrwx 1 root root  12288 Jan 20 16:52 Design
drwxrwxrwx 1 root root   8192 Jun 12 11:53 Downloads
drwxrwxrwx 1 root root  98304 Mar  8 12:03 My Audio
drwxrwxrwx 1 root root   8192 Mar  5 19:09 My Ebooks
drwxrwxrwx 1 root root 286720 Mar  5 19:00 My Music
drwxrwxrwx 1 root root  65536 Mar  5 18:59 My Music 2
drwxrwxrwx 1 root root   4096 Jun 12 14:37 My Pictures
drwxrwxrwx 1 root root      0 Oct 13  2009 My songs
drwxrwxrwx 1 root root   8192 May 28  2011 My Videos
drwxrwxrwx 1 root root   8192 Mar  5 19:10 My Videos 2
drwxrwxrwx 1 root root   4096 May 24 18:00 outlook
drwxrwxrwx 1 root root  40960 Aug 11  2011 photos to print
drwxrwxrwx 1 root root   4096 Oct 15  2009 scans
drwxrwxrwx 1 root root      0 Mar 27 12:55 snaps
drwxrwxrwx 1 root root      0 Aug 24  2011 sync
drwxrwxrwx 1 root root      0 Oct 14  2009 System Volume Information
drwxrwxrwx 1 root root  16384 Dec  6  2011 Todd
drwxrwxrwx 1 root root   4096 Jun 12 20:42 ubuntu
drwxrwxrwx 1 root root   4096 Jul  5  2010 VNC
drwxrwxrwx 1 root root   4096 Nov 12  2011 worship chords
drwxrwxrwx 1 root root   8192 Aug  1  2011 zion
```

---

### Post by idoitprone on 2012-06-13
> **eulu said:**
> ```
total 584
drwxrwxrwx 1 root root   4096 Apr 24 12:51 Applications
drwxrwxrwx 1 root root   4096 Mar  8 11:57 Backup
drwxrwxrwx 1 root root   4096 Oct 13  2009 Buzz
drwxrwxrwx 1 root root  12288 Jan 20 16:52 Design
drwxrwxrwx 1 root root   8192 Jun 12 11:53 Downloads
drwxrwxrwx 1 root root  98304 Mar  8 12:03 My Audio
drwxrwxrwx 1 root root   8192 Mar  5 19:09 My Ebooks
drwxrwxrwx 1 root root 286720 Mar  5 19:00 My Music
drwxrwxrwx 1 root root  65536 Mar  5 18:59 My Music 2
drwxrwxrwx 1 root root   4096 Jun 12 14:37 My Pictures
drwxrwxrwx 1 root root      0 Oct 13  2009 My songs
drwxrwxrwx 1 root root   8192 May 28  2011 My Videos
drwxrwxrwx 1 root root   8192 Mar  5 19:10 My Videos 2
drwxrwxrwx 1 root root   4096 May 24 18:00 outlook
drwxrwxrwx 1 root root  40960 Aug 11  2011 photos to print
drwxrwxrwx 1 root root   4096 Oct 15  2009 scans
drwxrwxrwx 1 root root      0 Mar 27 12:55 snaps
drwxrwxrwx 1 root root      0 Aug 24  2011 sync
drwxrwxrwx 1 root root      0 Oct 14  2009 System Volume Information
drwxrwxrwx 1 root root  16384 Dec  6  2011 Todd
drwxrwxrwx 1 root root   4096 Jun 12 20:42 ubuntu
drwxrwxrwx 1 root root   4096 Jul  5  2010 VNC
drwxrwxrwx 1 root root   4096 Nov 12  2011 worship chords
drwxrwxrwx 1 root root   8192 Aug  1  2011 zion
```

???????
You should be able to access your drive

there are the correct permissions

Are you sharing it through a samba server?

---

### Post by eulu on 2012-06-13
> **idoitprone said:**
> ???????
Are you sharing it through a samba server?

Not exactly sure what you mean, but I think the answer is yes, since I noticed when I first tried to share that it had me download and install samba.. Is there some other way to do the share?

---

### Post by idoitprone on 2012-06-13
Sorry I miss interpreted you situation

I thought that all you needed was access to your drive,

but it turn out that you needed to be able to alter your samba installation

[https://wiki.archlinux.org/index.php/Samba#Sharing_a_folder_fails](https://wiki.archlinux.org/index.php/Samba#Sharing_a_folder_fails)

i do not have any experience with samba. this is why i miss this common bug which is probably a feature in samba

---

### Post by eulu on 2012-06-13
Followed those steps (thanks).. 

On the drive I have fstab set to:
```
/dev/sdb1 /media/Data1 ntfs-3g defaults,locale=en_US.utf8   0  0

```I get:
> 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.On the drive that I left set in fstab to
```
/dev/sdc1  /media/Data2  ntfs  defaults  0 0
```i still get
```
'net usershare' returned error 255: net usershare add: failed
```

EDIT: I have to go get some sleep but thanks for your input! ;-)

---

### Post by Morbius1 on 2012-06-13
In every single variation of your line in fstab, and I will use the latest as an example:
> /dev/sdc1  /media/Data2  ntfs  defaults  0 0Although not explicitly stated, the owner of the partition is root not you. Usershare ( creating a share from Nautilus ) by default only allows a user to share something he owns.

So to fix that one can do one of 3 things:

** [1] Change the line in fstab to look like this so that you become the owner:**
> /dev/sdc1  /media/Data2  ntfs  defaults,[COLOR=Blue]**uid=1000**[/COLOR]  0 0**[2] Or, and I consider this a bad idea on a multi-user system, add the following line to the [global] section:**
> usershare owner only = false[COLOR=Blue]*Note: the problem you may have had is taking the original error message literally and added the following to the global section with quotes around it:*[/COLOR]
```
"usershare owner only = false" 
```[COLOR=Blue]*That's will be ignored by samba since it's an invalid syntax.*[/COLOR]
**[3] Share it as root since he's the one that owns it:**
```
gksu nautilus
```If [1] and [2] still don't work then there is the possibility that you are not a member of the correct group, so add yourself:
```
sudo gpasswd -a your-user-name sambashare
```Then logoff and  logon again for the group membership to take affect and try it again.

---

### Post by eulu on 2012-06-13
> **Morbius1 said:**
> 
**Change the line in fstab to look like this so that you become the owner:**

I did this and still got a message about permission denied. But I pressed on.

> **Morbius1 said:**
> 
[COLOR=Blue]*Note: the problem you may have had is taking the original error message literally and added the following to the global section with quotes around it:*[/COLOR]

I didn't have quotes in the conf file.. I had only added them here. Bad move on my part as it wasted your time apologies.

> **Morbius1 said:**
> 
**Share it as root since he's the one that owns it:**

This revealed a goof in my process. I actually did this early on in the game, and it seemed to take my shares while in as root, but then because I couldn't see the shares on the network, and when I went into nautilus regularly it didn't show them as shared, I didn't think they were/are shared... Forgot to mention this until now..  

Since I was still getting permission errors, I removed the shares as root* then* I could go back into nautilus and create the shares, *BUT*, I am still not able to access the shares from the network (Windows). I get the prompt to enter username and password but then blank page after that.. (Same thing after restarting samba too)

> **Morbius1 said:**
> 
```
sudo gpasswd -a your-user-name sambashare
```

I went ahead and did this too but same thing... 

I am going to go logoff then try to access the shares again.. EDIT: still no dice

---

### Post by Morbius1 on 2012-06-13
Please post the output of the following commands:
```
testparm -s
``````
net usershare info --long
```

---

### Post by eulu on 2012-06-13
```
testparm -s
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

---

### Post by eulu on 2012-06-13
```
net usershare info --long
```

[Data2]
path=/media/Data2
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Data1]
path=/media/Data1
comment=
usershare_acl=Everyone:F,
guest_ok=y

---

### Post by Morbius1 on 2012-06-13
Well, your smb.conf file is textbook correct except you do not have [COLOR=Blue]**userhsare owner only = false**[/COLOR] added to the file. 

But it doesn't matter since you must have shared the the partitions as root:
> [Data2]
path=/media/Data2
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Data1]
path=/media/Data1
comment=
usershare_acl=Everyone:F,
guest_ok=y     The output of "ls -l /media/Data1" is consistent with what you want to do so there doesn't seem to be an issue with this.

If you run the following command from the Ubuntu box you should get a list of the shares:
```
smbtree
``` And from the same box if you run this command you should get access to the shares:
```
nautilus smb://host-name
```Change "host-name" to whatever your machine name is.

As far as getting prompted for a username and password from the Windows box that shouldn't happen - unless of course you have the same username on both boxes but created a samba password on the Ubuntu box that's different from the Windows login user's password. 

What version of Ubuntu are you using?

---

### Post by eulu on 2012-06-13
> **Morbius1 said:**
> Well, your smb.conf file is textbook correct except you do not have [COLOR=Blue]**userhsare owner only = false**[/COLOR] added to the file. 

Yeah I have tried it both ways...

> **Morbius1 said:**
> If you run the following command from the Ubuntu box you should get a list of the shares:

Yeah that looks ok, although it doesn't specifically show the drive shares, just the host name.. Not sure if it should show the drive shares

> **Morbius1 said:**
> And from the same box if you run this command you should get access to the shares:
```
nautilus smb://host-name
```

 I tried this and the only thing that came up was $print

> **Morbius1 said:**
> As far as getting prompted for a username and password from the Windows box that shouldn't happen - unless of course you have the same username on both boxes but created a samba password on the Ubuntu box that's different from the Windows login user's password. 

This is exactly the case.. You're a smart cookie.. :-)

(FYI - I had it set up like this before I reloaded my Ubuntun OS and it worked fine.. The difference is that I used a ntfs utility last time to auto-mount the drives.. It was a pain of a different order and I didn't feel confident I could remember how to configure it again, which is why I tried a different way to auto-mount the drives this time..)

> **Morbius1 said:**
> What version of Ubuntu are you using?

12.04 64bit

---

### Post by Morbius1 on 2012-06-13
If you run smbtree [COLOR=Blue]and it outputs no errors [/COLOR]but shows the host but no shares and when you run "nautilus smb://host-name" and all it shows is $print then I'll be honest with you, I don't know what to make of it.

My first thought was that samba wasn't running but that's probably not it. You might want to make sure though:
```
sudo service smbd status
```If it's not running than start it:
```
sudo service smbd start
```Anyway I'm at a loss at the moment.

[COLOR=Blue]**EDIT**[/COLOR]: I suppose it's possible that Data1 and Data2 aren't really mounted. Run the following command to see if these 2 partitions are really mounted:
```
mount
```

---

### Post by eulu on 2012-06-13
Samba is running per that command.
Mount results:
> /dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
[B]/dev/sdb1 on /media/Data1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1 on /media/Data2 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)[/B]
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/user/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=user)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
/dev/sde1 on /media/8GB type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)

That part about the default permissions is what I keep wondering about.. I really wish I had thought to make a copy of my fstab before I reinstalled the OS..

---

### Post by Morbius1 on 2012-06-13
The output of mount for those drives is just the way it should be. Everything about your configuration is just the way it should be.

I have no idea why smbtree dos not show the shares. And I don't know why smb://... does not list the shares.

All the usual suspects in this type of problem ( firewall getting in the way, host name longer than 15 characters, etc... ) would have produced errors when you ran those commands so ....

---

### Post by eulu on 2012-06-16
I tried installing Storage Device Manager (pysdm) and redoing my auto-mounts with this, (since I used this last time and was able to share the drives)..  I just set it to defaults though and it's still the same status after redoing it..

---

### Post by grevedan on 2012-09-03
I see this issue on fresh installs of ubuntu 12.04 64-bit.  Add a user to sambashare, try to share a directory in nautilus


'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

---

### Post by grevedan on 2012-09-03
Forget nautilus, just use the real samba tools...they worked for me where nautilus doesn't. Just browse for the directory, set "visible", and quit

[http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba/](http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba/)

---

