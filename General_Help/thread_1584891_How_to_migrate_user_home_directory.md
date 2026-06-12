---
title: "How to migrate user home directory"
date: 2010-09-29
forum: General Help
---

### Post by satimis on 2010-09-29
Hi folks,

Ubuntu 10.04 64 bit

I ran following command to change username;

# usermod -c "Real name" -l new_username old_username

but forgot adding -m option to move the contents of the old home directory to the new home directory.

Therefore;
# ls /home
old_user_directory

Please advise how to fix it.  /home is on partition /dev/sda3 NOT on root directory

TIA

B.R.
satimis

---

### Post by Old *ix Geek on 2010-09-29
```
cd /home
sudo mv old_user_directory new_user_directory
```
should do it. *IF* you should end up with any permissions issues or other problems, post again.

---

### Post by satimis on 2010-09-29
> **Old *ix Geek said:**
> ```
cd /home
sudo mv old_user_directory new_user_directory
```
should do it. *IF* you should end up with any permissions issues or other problems, post again.

Hi,

Thanks for your advice.

$ sudo mv old_user satimis
No complaint

$ ls -al satimis/```

total 172
drwxr-xr-x 29 satimis old-user 4096 2010-09-30 07:22 .
drwxr-xr-x  4 root    root          4096 2010-09-30 07:48 ..
-rw-------  1 satimis old_user  255 2010-09-30 06:33 .bash_history
-rw-r--r--  1 satimis old_user  220 2010-09-29 23:24 .bash_logout
.....
.....

```

$ sudo chown satimis:satimis satimis```

chown: invalid group: `satimis:satimis'

```

Please advise how to fix it

TIA

B.R.
satimis

---

### Post by Old *ix Geek on 2010-09-29
> **satimis said:**
> $ sudo chown satimis:satimis satimis```

chown: invalid group: `satimis:satimis'
```

```
sudo groupadd satimis
``` will add the new group, then reissuing the previous command should work.

---

### Post by satimis on 2010-09-29
> **Old *ix Geek said:**
> ```
sudo groupadd satimis
``` will add the new group, then reissuing the previous command should work.

$ sudo groupadd satimis
$ sudo satimis:satimis /home/satimis
without complaint.

Reboot PC

satimis can login but desktop doesn't start.

Warning:-
```

Could not update ICE authority file /home/old_user/.ICEauthority
[close]

There is a problem with configuration server(/usr/lib/libcof2-4/gconf-sanity-check-2 exited with status 256)
[close]

Nautilus could not create following required folders:/home/old_user Desktop, /home/old_user/.nautilus
[OK]


```

B.R.
satimis

---

### Post by Old *ix Geek on 2010-09-29
> **satimis said:**
> $ sudo groupadd satimis
$ sudo satimis:satimis /home/satimis
without complaint.

Reboot PC

satimis can login but desktop doesn't start.It's probably just permission problems. Try:
```
sudo chown -R satimis /home/satimis
sudo chgrp -R satimis /home/satimis
sudo chmod -R [depends on what you want--you can do "777" if you don't care about other users accessing your files] /home/satimis 
```
> Warning:-
```
Could not update ICE authority file /home/old_user/.ICEauthority
[close]

There is a problem with configuration server(/usr/lib/libcof2-4/gconf-sanity-check-2 exited with status 256)
[close]

Nautilus could not create following required folders:/home/old_user Desktop, /home/old_user/.nautilus
[OK]
```I've [**[color="blue"]written about this[/color]**](http://ubuntuforums.org/showpost.php?p=9753876&postcount=2) before, but the circumstances were different.

This isn't an elegant way to fix it, but it should work: Add the old user back; then make sure its permissions are recursively set as above, only with the correct username and group, obviously. Restart. See what happens.

---

### Post by satimis on 2010-09-29
> **Old *ix Geek said:**
> It's probably just permission problems. Try:
```
sudo chown -R satimis /home/satimis
sudo chgrp -R satimis /home/satimis
sudo chmod -R [depends on what you want--you can do "777" if you don't care about other users accessing your files] /home/satimis 
```
I've [**[color="blue"]written about this[/color]**](http://ubuntuforums.org/showpost.php?p=9753876&postcount=2) before, but the circumstances were different.

This isn't an elegant way to fix it, but it should work: Add the old user back; then make sure its permissions are recursively set as above, only with the correct username and group, obviously. Restart. See what happens.

Hi,

I have to login as root

# chown -R satimis /home/satimis
# chgrp -R satimis /home/satimis
# chmod -R satimis /home/satimis

all went through without complaint.

Problem still remains satimis' desktop can't start

Edit:

Can't I completely delete this user including all relevant files?  Then I'll recreate a new one.  This is a freshly installed PC.  No files on satimis/old_user's home directory.

satimis

---

### Post by satimis on 2010-09-29
Hi folks,

Problem solved as follow:

Login as root

# userdel -r satimis
# rm -rf /home/satimis
# adduser satimis

That is all

B.R.
satimis

---

