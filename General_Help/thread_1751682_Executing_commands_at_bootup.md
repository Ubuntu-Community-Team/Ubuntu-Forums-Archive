---
title: "Executing commands at bootup"
date: 2011-05-06
forum: General Help
---

### Post by drnick79 on 2011-05-06
Hello all,
 
Would anyone venture a guess as to what I am doing incorrectly? :confused:
 
I am trying to get some RAID parameters to change at boot (before login). Per instructions on another site, I edited the rc.local file as below and made sure it was executable.
 
rc.local file:
 
 
```
 
#!/bin/sh -e
 
## rc.local
 
## This script is executed at the end of each multiuser runlevel.
## In order to enable or disable this script just change the execution bits.
## By default this script does nothing.
 
# Tune the RAID5 configuration
 
echo 8192 > /sys/block/md0/md/stripe_cache_size
 
blockdev --setra 4096 /dev/md0
 
exit 0

```
 
 
However, the parameters are not changed when the system restarts. I tried adding a sleep 10 command in the script as I saw someone else suggest, but that didn't work either. I also made a file called raidscript, put the above code in it using a text editor, made sure it was executable, put it in the /etc/init.d folder, and ran the "update-rc.d raidscript defaults" command. Still no luck.
 
I've seem this same question asked in several forums without a definitive answer. Once logged in, if I run these commands in a terminal (with sudo), they will work just fine, but I was hoping to automate it without the need to login.
 
Thanks for any advice- Nick.

---

### Post by drnick79 on 2011-05-08
Well, I found a way that works...
 
This is my /etc/rc.local file that will change these RAID parameters at bootup:
 
```

#!/bin/bash
 
##rc.local
 
su root -c "echo 8192 > /sys/block/md0/md/stripe_cache_size"
 
su root -c "blockdev --setra 4096 /dev/md0"
 
exit 0

```
 
 
Is there a better way to accomplish this? Is the "su root" command generally not used in scripts?
 
Any advice would be appreciated!

---

