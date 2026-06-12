---
title: "moving an encrypted /home directroy 10.04  -?&gt; 11.04"
date: 2011-08-05
forum: General Help
---

### Post by SalishSea on 2011-08-05
OK, I've got myself in way over my head this time. 

I did some minor upgrades to my 10.04 box which grew and grew and grew until I'd hosed xorg, and after some unwise choices about uninstalling X11 as a means to rebuild the system I now have a drive I was using for 10.04 that basically doesn't have an O/S any more... don't ask! First class stupid.

Anyhow, I've cracked open a new  drive, installed 11.04 and was planning to mount the old /home/me folder as a symbolic link from 11.04. All that was fine until I remembered that 1) I no longer have an OS on my 10.04 drive and I've encrypted my home folder on the 10.04 machine. That home folder is still intact, but obviously not much use right now.

So, have I just hosed myself completely (as I suspect) hosed myself or is there a way to capture the cleartext data from the encrypted folder and move it into the 11.04 machine, either with rsync, restoring the O/S to the formerly 10.04 drive and restoring the encryptied /home to that drive?

Goal 1) recovery contents of encrypted folder to plaintext, but lacking ability to log into O/S that generated the /home folder

2) move data to 11.04

3) attach the cleartext verison of home to my 11.04 account and get to work.

---

### Post by scorp123 on 2011-08-05
How did you encrypt it? Did you use the built-in mechanism, e.g. during installation you simply clicked on the "Encrypt my /home folder ..." option?

If that's the case:

1. move the content of your old /home over to the new /home. Best tool to use for this would be rsync:
```
rsync -lavx --progress /path/to/old/home /
``` (yes, I want to copy the old "home" folder into /, so it gets attached underneath there as "/home". Reason: there are a few hidden files such as ".ecryptfs" that need to be in the same spot when you try to mount your folder again ...)

Expected result: Your new 11.04 system now has a copy of the encrypted "/home" your 10.04 system had.


2. Make sure you have absolutely the same username and password on your 11.04 as on your old 10.04 ...


3. Login. Expected result: Your /home folder got unlocked.



I did the very same thing when I upgraded from 10.04 to 10.10 and then to 11.04 and now back to 10.10 again ... so I know that this should work for as long as you stick to the same username and same password, the encrypted /home folder should get unlocked because the underlying encryption mechanism is the same and thus ends up generating the same crypto keys when the username + password combo is the same as before.

---

### Post by SalishSea on 2011-08-05
Thank you!

1) Same userid. 2) same password and 3) rsync (but without the l option already underway as a backup.  Will report success soon. Thanks!

---

### Post by SalishSea on 2011-08-05
by:

rsync -lavx --progress /path/to/old/home /

do you means ( and assume old drive is mounted on /dev/sdc1)

rsync -lavx --progress /dev/sdc1/home/rob  /

or

rsync -lavx --progress /dev/sdc1/home/  /

Thanks!

---

### Post by scorp123 on 2011-08-06
EDIT:

Forget the previous version of this posting ... before I assume too many things I should maybe ask this: Was your old /home on a separate mount point, e.g. on a harddrive all by itself? Or did you have it on the same harddrive together with the rest of the OS? The reason I ask .. you're right -- the syntax for "rsync" might need some adjustment.

In my case:

I have /home on a separate mountpoint ... So this is the content underneath /home:

```
> ls -al
total 56
drwxr-xr-x  5 root    root  4096 2011-08-06 10:17 .
drwxr-xr-x 26 root    root  4096 2011-07-26 21:49 ..
drwx------ 96 sysadm  sysadm  24576 2011-08-06 09:38 sysadm
drwxr-xr-x  3 root    root  4096 2011-05-01 23:21 .ecryptfs
drwx------  2 root    root 16384 2011-05-01 22:55 lost+found
lrwxrwxrwx  1 root    root     5 2011-07-26 20:40 root -> /root
```

What's important here is that your empty user folder (empty because it's not mounted) -- here "sysadm" in my example -- and the folder ".ecryptfs" (where your encrypted data is stored) get copied over underneath the new /home ... 

So yeah, you may need to adjust the syntax of that "rsync" command I gave. If you end up with directories such as "/rob" or "/home/home/rob" instead of "/home/rob" then the syntax was obviously wrong ...

---

### Post by SalishSea on 2011-08-08
Hmm,

Thanks for the advice.  rsync is working as it should but things are getting more complicated not less.  After a full rsync I do not get the encrypted drive on my 11.04 device,  

Below is the treeview of my new 11.04 drive /home. It contains both the /home/.ecyrptfs/rob  folder and /home/rob and there are the usual control files and dummy folders in /home/rob which you get when you adduser.  
I don't care about any of these files, of course, I just want the encrypted stuff back.


rob@rob-System-Product-Name:/home$ tree -La 2 /home
/home
&#9500;&#9472;&#9472; .directory -> /etc/kubuntu-default-settings/directory-home
&#9500;&#9472;&#9472; .ecryptfs
&#9474;** &#9492;&#9472;&#9472; rob
&#9500;&#9472;&#9472; rob
&#9474;** &#9500;&#9472;&#9472; Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
&#9474;** &#9500;&#9472;&#9472; .adobe
&#9474;** &#9500;&#9472;&#9472; .bash_history
&#9474;** &#9500;&#9472;&#9472; .bash_logout
&#9474;** &#9500;&#9472;&#9472; .bashrc
&#9474;** &#9500;&#9472;&#9472; .cache
&#9474;** &#9500;&#9472;&#9472; .config
&#9474;** &#9500;&#9472;&#9472; .dbus
&#9474;** &#9500;&#9472;&#9472; Desktop
&#9474;** &#9500;&#9472;&#9472; .dmrc
&#9474;** &#9500;&#9472;&#9472; Documents
&#9474;** &#9500;&#9472;&#9472; Downloads
&#9474;** &#9500;&#9472;&#9472; .ecryptfs -> /home/.ecryptfs/rob/.ecryptfs
&#9474;** &#9500;&#9472;&#9472; .esd_auth
&#9474;** &#9500;&#9472;&#9472; .fontconfig
&#9474;** &#9500;&#9472;&#9472; .gconf
&#9474;** &#9500;&#9472;&#9472; .gconfd
&#9474;** &#9500;&#9472;&#9472; .gstreamer-0.10
&#9474;** &#9500;&#9472;&#9472; .gtkrc-2.0-kde4
&#9474;** &#9500;&#9472;&#9472; .kde
&#9474;** &#9500;&#9472;&#9472; .local
&#9474;** &#9500;&#9472;&#9472; .macromedia
&#9474;** &#9500;&#9472;&#9472; .mozilla
&#9474;** &#9500;&#9472;&#9472; Music
&#9474;** &#9500;&#9472;&#9472; Pictures
&#9474;** &#9500;&#9472;&#9472; .Private -> /home/.ecryptfs/rob/.Private
&#9474;** &#9500;&#9472;&#9472; .profile
&#9474;** &#9500;&#9472;&#9472; Public
&#9474;** &#9500;&#9472;&#9472; .pulse
&#9474;** &#9500;&#9472;&#9472; .pulse-cookie
&#9474;** &#9500;&#9472;&#9472; README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt
&#9474;** &#9500;&#9472;&#9472; .sudo_as_admin_successful
&#9474;** &#9500;&#9472;&#9472; Templates
&#9474;** &#9500;&#9472;&#9472; treeview
&#9474;** &#9500;&#9472;&#9472; Videos
&#9474;** &#9500;&#9472;&#9472; .Xauthority
&#9474;** &#9492;&#9472;&#9472; .xsession-errors


So with that not working, I started wondering if I have somehow really screwed this up on the 10.04 side to begin with .

On the 10.04 disk, here is the ls -la for /home/rob where /temmpmountpoint is the location on the 11.04 filestructure where I have mounted the 10.04 drive.

@rob-System-Product-Name:/tempmountpoint/home$ ls -la
total 16
drwxr-xr-x  4 root root 4096 2011-08-05 21:36 .
drwxr-xr-x 23 root root 4096 2011-08-08 12:06 ..
lrwxrwxrwx  1 root root   44 2011-05-15 17:14 .directory -> /etc/kubuntu-default-settings/directory-home
drwxr-xr-x  3 root root 4096 2011-05-15 17:20 .ecryptfs
dr-x------  3 rob  rob  4096 2011-05-16 09:05 rob


So, that looks OK, but no .Private folder which I was expecting.

I went looking and I can find .Private at 

ls -la /tempmountpoint/home/.ecyrptfs/rob/
total 120
drwxr-xr-x   4 rob  rob    4096 2011-05-15 17:20 .
drwxr-xr-x   3 root root   4096 2011-05-15 17:20 ..
drwx------   2 rob  rob    4096 2011-05-15 17:20 .ecryptfs
drwx------ 130 rob  rob  106496 2011-08-02 16:08 .Private
[email]rob@rob-System-Product-Name:/tempmountpoint/home/.ecrypt[/email]fs/rob$ 

which was not where I was expecting it. It might be right, but I was not expecting this...

The folder:  /tempmountpoint/home/.ecryptfs/rob/.ecryptfs

contains: 
total 20
drwx------ 2 rob rob  4096 2011-05-15 17:20 .
drwxr-xr-x 4 rob rob  4096 2011-05-15 17:20 ..
-rw-r--r-- 1 rob rob     0 2011-05-15 17:20 auto-mount
-rw-r--r-- 1 rob rob     0 2011-05-15 17:20 auto-umount
-rw------- 1 rob rob    10 2011-05-15 17:20 Private.mnt
-rw------- 1 rob rob    34 2011-05-15 17:20 Private.sig
-rw------- 1 rob root   48 2011-05-15 17:20 wrapped-passphrase

and .ecryptfs has all of the ENCRYPTFS_FNEK files that you would expect.

My questions:

1) is this the normal setup for .ecryptfs ? 
2) if it is normal, and I have transferred it correctly to the 11.04 /home location, then what might be keeping U11.04 from using the .ecryptfs structure and thus restoring my  10.04 folders?

3) I am thinking that the easiest thing might be to put 10.04 Ubuntu back on the 10.04 drive, and see if I can get it to boot, then rsync to a non-encrypted folder.

Suggestions desperately welcome!

Rob

---

### Post by SalishSea on 2011-08-08
No encryptfsd installed by default with 11.04. Once that was installed, the .ecryptfs file structure was recognized and everything went fine. Thank you so much for your help.

Rob

---

