---
title: "Help setting correct permissions on a network shared folder"
date: 2012-06-28
forum: General Help
---

### Post by MrGrumpyArse on 2012-06-28
Hi, I have been using Ubuntu for a couple of years now, and have recently set up a small server running 12.04 64 bit server.

The server has been up and running for a month or so and everything is working fine except for the following issue........

I have created (via a number of tutorials) some user folders which are on a second hard drive which is mounted on the server at boot. (via fstab and uuid)

So, so far I have the following folders (drive mounted at /mnt/sdb1)

mnt/sdb1/mark
mnt/sdb1/claire
mnt/sdb1/lewis
mnt/sdb1/shared

The first 3 folders are exclusively for the individual user to access and store/create documents which only the author has access to.

The shared directory is an anything goes folder where any user with an account and appropriate group membership can read/write/execute any files it contains regardless of the original author.

At least thats how it is intended, the first 3 "private" directories work well and can be accessed by both Windows and Ubuntu without problems.  Their permissions are shown below.

```

drwx------  2 claire claire  4096 Jun 16 20:02 claire
drwx------  2 lewis  lewis   4096 Jun  6 17:02 lewis
drwx------ 67 mark   mark    4096 Jun 16 11:36 mark

```


The shared directory is more problematic,  I have created the user group "trusted" and added the 3 users to it 

```

:~$ groups mark claire lewis
mark : mark adm cdrom sudo dip plugdev lpadmin sambashare trusted
claire : claire trusted
lewis : lewis trusted

```

The shared directory has the following permissions, and if I understand correctly files created within it should be available for any of the 3 users to edit/create/whatever as the users are all members of the group "trusted"
```

drwxrws---  2 root   trusted 4096 Jun 28 09:58 shared

```

But what actually happens is the 3 users can all access the directory, but any files created appear to have different permissions dependant on how they were created. 
I have created 3 files to illustrate what I mean, 
one via ssh using the "touch" command (logged in as "mark"), 
one via nautilus from an Ubuntu 12.04 64 bit laptop(logged in as Mark), and 
one from a laptop running Win7 (logged in as claire)

```

mark@grumpyserver:/mnt/sdb1/shared$ ls -l
total 0
-rwx------ 1 mark   trusted 0 Jun 28 11:50 nautilus_test_file.txt
-rw-rw-r-- 1 mark   trusted 0 Jun 28 11:50 touch_test_file.txt
-rwx------ 1 claire trusted 0 Jun 28 11:51 win7_claire_test_file.text.txt

```

Only the file created using 
```
 touch /mnt/sdb1/shared/touch_test_file.txt
```
is allowing group access.

The default umask is set to 
```

mark@grumpyserver:~$ umask
0002

```

Any ideas where I am going wrong, setting permissions and general server set-up is all new to me so this has been a bit of a "painting by numbers" exercise so its more than likely I am not understanding the process clearly.

Any help much appreciated 

Mark

---

### Post by Morbius1 on 2012-06-28
That's interesting. You will note that the proper permissions are attained when you don't go though Samba. I suppose the proper way to do this is to look at the share definition for the "shared" share. Run the following command and look at the "shared" definition:
```
testparm -s
```It may be that you have a parameter that's trying to force the permissions like a "create mask = 700" in which case just remove it.

[COLOR=Blue]* If all else fails there is another way:*[/COLOR]

Install the following package:
```
sudo apt-get install bindfs
```And then run the following command:
```
sudo bindfs -o group=trusted,perms=0660:ug+D /mnt/sdb1/shared /mnt/sdb1/shared
```That looks like a typo but let me explain: You are going to mount a directory to itself with a set of permissions defined by bindfs. In this case all current and any future files added will have:

Owner = owner of the file that created it.
Group = trusted
Files will have permissions of 660
Subdirectories will have permissions of 770

It's basically doing the same thing as a setgid but it will not allow samba to alter or in any way change the resulting permissions.

If you find the bindfs acceptable then you need to create an upstart job to have this done on boot since the command I gave you will not survive a reboot. You can use this as a model on how to do that:

* Create an upstart job file:
```
gksu gedit /etc/init/bindfs-remounts.conf 
```* With this content:
```
# List of bindfs remounts
description "Bindfs Remounts"

start on stopped mountall

script
  bindfs -o group=trusted,perms=0660:ug+D /mnt/sdb1/shared /mnt/sdb1/shared
end script
```You can test to see if it works before an actual reboot by running:
```
sudo initctl start bindfs-remounts
```

---

### Post by bab1 on 2012-06-28
> **MrGrumpyArse said:**
> ...Any ideas where I am going wrong, setting permissions and general server set-up is all new to me so this has been a bit of a "painting by numbers" exercise so its more than likely I am not understanding the process clearly.

The *umask* value is an environment variable. As such it can be changed by various apps.  You will need (and can) set it is the SSH  (SFTP) conf file and you can set the dir and file masks in the Samba share and in the system via PAM_*umask*.  Or you can use the mount bind that Morbius1 has suggested.  They all set the *umask* variable in one way or the other.

[COLOR="Blue"]**Edit:** A quick edit dredged [**_[COLOR="Red"]this[/COLOR]_**]("http://serverfault.com/questions/231717/how-to-get-full-control-of-umask-pam-permissions") up.  It appears to explain how/where to set all the umasks values.  READ THE COMMENTS TOO![/COLOR]

---

### Post by MrGrumpyArse on 2012-06-28
Thank you for your replies 

Morbius1 I think you have hit the nail on head with your first suggestion, when I ran 
```
testparm -s
```
It showed
```

[1tb_drive]
	comment = ubuntu server file share
	path = /mnt/sdb1/
	valid users = mark, claire, lewis
	read only = No
	create mask = 0700

```

And now it comes flooding back!  I remember setting that section, in my samba config when I first set up the server.  At a point when I had even less idea of what I was doing than I do now :-)

It was from a tutorial, but I believe I changed the mask to 0700 for some misguided reason.....

I shall remove the mask and report back shortly

Thanks again

Mark

---

### Post by MrGrumpyArse on 2012-06-29
Ok, well there is some progress......

I have removed the  "mask = 0700" from the servers /etc/samba/smb.conf 

I have set the umask in /etc/pam.d/login to 0007, which if I understand should give rwx rwx --- .

but running "umask" from the terminal still shows "0002", which again if I understand should give rwx rwx r-- .  which wouldnt particularly be an issue but it does show that the umask in /etc/pam.d/login is not being applied/respected.

I then set the umask in /etc/login.defs to 0007.

Now when I run "umask" from terminal it shows "0007" 

However now when I create files I get the below results
```

-rwxr----- 1 mark   trusted 0 Jun 29 11:55 nautilus_test_file.txt
-rw-rw---- 1 mark   trusted 0 Jun 29 11:56 touch_test_file.txt
-rwxr----- 1 claire trusted 0 Jun 29 11:57 win7_test_file.txt

```

So there appears still to be inconsistencies, 

the 2 files created via samba show rwx r-- ---
the file created via ssh show      rw- rw- ---

I don't understand why the files have different permissions? or where the the files created via samba are getting their permissions from?

Any thoughts

cheers

Mark

---

### Post by Morbius1 on 2012-06-29
[COLOR=Blue]*As a side note*[/COLOR]: It's for reasons like this that I started to use bindfs. The resulting permissions on the "remounted" folder are immutable - just as if the folder was on an ntfs partition - so all this umask and create mask stuff is ignored. 

Anyway, In retrospect I probably went too far when I said to just remove the "create mask" line from smb.conf. Change the value to 770, restart samba, and see if it gets you closer. Samba is interfering with the default umask so a 770 might get you closer.

---

### Post by MrGrumpyArse on 2012-06-29
Thanks again for your reply,

Interestingly I was just playing with setting the following in /etc/samba/smb.conf

```
create mask = 0770
```

and after a little more reading 

```
directory mask = 0770
```

These 2 combined with setting umask in /etc/pam.d/login & /etc/login.defs  to 0007 seems to produce something like the consistent results I am after.

Here are my test results below

```

drwxrws--- 2 mark   trusted 4096 Jun 29 13:23 nautilus_test_dir
drwxrws--- 2 mark   trusted 4096 Jun 29 13:25 ssh_test_dir
drwxrws--- 2 claire trusted 4096 Jun 29 13:27 win7_test_dir

-rwxrw---- 1 mark   trusted    0 Jun 29 13:23 nautilus_test_doc.txt
-rw-rw---- 1 mark   trusted    0 Jun 29 13:25 ssh_test_doc.txt
-rwxrw---- 1 claire trusted    0 Jun 29 13:27 win7_test_doc.txt

```

I think its time to use these settings for a while and see how things work out.

As for bindfs, I have made a note of that and will use that route if this one proves beyond me....

Many Thanks

Mark

I will mark this thread as solved after a little more testing :-)

---

