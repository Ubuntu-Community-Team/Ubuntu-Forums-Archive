---
title: "screwed up my sudoers"
date: 2010-12-07
forum: General Help
---

### Post by dorlow on 2010-12-07
Ok, I'm trying to figure out how to get a script of mine to run without the sudo command and I somehow screwed up something.  I modified the sudoers using the visudo.  I added a line that said...

david ALL=ALL: /home/david/script

Now when I try to run anything sudo, I get this...

```
sudo: /etc/sudoers.d/backup_script is mode 04755, should be 0440
>>> /etc/sudoers.d/README: /etc/sudoers.d/backup_script near line 18 <<<
sudo: parse error in /etc/sudoers.d/README near line 18
sudo: no valid sudoers sources found, quitting
*** glibc detected *** sudo: double free or corruption (!prev): 0x09cac970 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0x19d591]
/lib/tls/i686/cmov/libc.so.6(+0x6cde8)[0x19ede8]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0x1a1ecd]
/lib/tls/i686/cmov/libc.so.6(fclose+0x14a)[0x18daaa]
sudo[0x805791d]
sudo[0x80588b6]
sudo[0x805648e]
sudo[0x805a1f4]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x148bd6]
sudo[0x804a7c1]
======= Memory map: ========
0012e000-00130000 r-xp 00000000 08:01 1442491    /lib/tls/i686/cmov/libdl-2.11.1.so
00130000-00131000 r--p 00001000 08:01 1442491    /lib/tls/i686/cmov/libdl-2.11.1.so
00131000-00132000 rw-p 00002000 08:01 1442491    /lib/tls/i686/cmov/libdl-2.11.1.so
00132000-00285000 r-xp 00000000 08:01 1442488    /lib/tls/i686/cmov/libc-2.11.1.so
00285000-00286000 ---p 00153000 08:01 1442488    /lib/tls/i686/cmov/libc-2.11.1.so
00286000-00288000 r--p 00153000 08:01 1442488    /lib/tls/i686/cmov/libc-2.11.1.so
00288000-00289000 rw-p 00155000 08:01 1442488    /lib/tls/i686/cmov/libc-2.11.1.so
00289000-0028c000 rw-p 00000000 00:00 0 
00357000-00362000 r-xp 00000000 08:01 1310852    /lib/libpam.so.0.82.2
00362000-00363000 r--p 0000a000 08:01 1310852    /lib/libpam.so.0.82.2
00363000-00364000 rw-p 0000b000 08:01 1310852    /lib/libpam.so.0.82.2
00406000-0040f000 r-xp 00000000 08:01 1442490    /lib/tls/i686/cmov/libcrypt-2.11.1.so
0040f000-00410000 r--p 00008000 08:01 1442490    /lib/tls/i686/cmov/libcrypt-2.11.1.so
00410000-00411000 rw-p 00009000 08:01 1442490    /lib/tls/i686/cmov/libcrypt-2.11.1.so
00411000-00438000 rw-p 00000000 00:00 0 
00541000-00547000 r-xp 00000000 08:01 1442495    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00547000-00548000 r--p 00006000 08:01 1442495    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00548000-00549000 rw-p 00007000 08:01 1442495    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
005fc000-00617000 r-xp 00000000 08:01 1310975    /lib/ld-2.11.1.so
00617000-00618000 r--p 0001a000 08:01 1310975    /lib/ld-2.11.1.so
00618000-00619000 rw-p 0001b000 08:01 1310975    /lib/ld-2.11.1.so
00b3d000-00b45000 r-xp 00000000 08:01 1442499    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
00b45000-00b46000 r--p 00007000 08:01 1442499    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
00b46000-00b47000 rw-p 00008000 08:01 1442499    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
00b4f000-00b6c000 r-xp 00000000 08:01 1310803    /lib/libgcc_s.so.1
00b6c000-00b6d000 r--p 0001c000 08:01 1310803    /lib/libgcc_s.so.1
00b6d000-00b6e000 rw-p 0001d000 08:01 1310803    /lib/libgcc_s.so.1
00c3b000-00c45000 r-xp 00000000 08:01 1442497    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00c45000-00c46000 r--p 00009000 08:01 1442497    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00c46000-00c47000 rw-p 0000a000 08:01 1442497    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00dd3000-00de6000 r-xp 00000000 08:01 1442494    /lib/tls/i686/cmov/libnsl-2.11.1.so
00de6000-00de7000 r--p 00012000 08:01 1442494    /lib/tls/i686/cmov/libnsl-2.11.1.so
00de7000-00de8000 rw-p 00013000 08:01 1442494    /lib/tls/i686/cmov/libnsl-2.11.1.so
00de8000-00dea000 rw-p 00000000 00:00 0 
00f9d000-00f9e000 r-xp 00000000 00:00 0          [vdso]
08048000-08066000 r-xp 00000000 08:01 16647206   /usr/bin/sudo
08066000-08067000 r--p 0001d000 08:01 16647206   /usr/bin/sudo
08067000-08068000 rw-p 0001e000 08:01 16647206   /usr/bin/sudo
08068000-0806b000 rw-p 00000000 00:00 0 
09ca7000-09cc8000 rw-p 00000000 00:00 0          [heap]
b7500000-b7521000 rw-p 00000000 00:00 0 
b7521000-b7600000 ---p 00000000 00:00 0 
b7637000-b7676000 r--p 00000000 08:01 16777671   /usr/lib/locale/en_US.utf8/LC_CTYPE
b7676000-b7794000 r--p 00000000 08:01 16777345   /usr/lib/locale/en_US.utf8/LC_COLLATE
b7794000-b7796000 rw-p 00000000 00:00 0 
b779a000-b779b000 r--p 00000000 08:01 16777546   /usr/lib/locale/en_US.utf8/LC_NUMERIC
b779b000-b779c000 r--p 00000000 08:01 16779883   /usr/lib/locale/en_US.utf8/LC_TIME
b779c000-b779d000 r--p 00000000 08:01 16779884   /usr/lib/locale/en_US.utf8/LC_MONETARY
b779d000-b779e000 r--p 00000000 08:01 16779885   /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b779e000-b779f000 r--p 00000000 08:01 16777703   /usr/lib/locale/en_US.utf8/LC_PAPER
b779f000-b77a0000 r--p 00000000 08:01 16777363   /usr/lib/locale/en_US.utf8/LC_NAME
b77a0000-b77a1000 r--p 00000000 08:01 16779886   /usr/lib/locale/en_US.utf8/LC_ADDRESS
b77a1000-b77a2000 r--p 00000000 08:01 16779887   /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b77a2000-b77a3000 r--p 00000000 08:01 16777361   /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b77a3000-b77aa000 r--s 00000000 08:01 16647366   /usr/lib/gconv/gconv-modules.cache
b77aa000-b77ab000 r--p 00000000 08:01 16779888   /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b77ab000-b77ad000 rw-p 00000000 00:00 0 
bfe43000-bfe58000 rw-p 00000000 00:00 0          [stack]
Aborted
david@david-laptop:/etc$ sudo visudo
```


I feel like I'm stuck in a catch 22.  I can't modify the file's permission because I need to do a sudo chmod and change the permissions, but I can't do that, because as soon as I type any command with sudo, I get what is above.

---

### Post by matt_symes on 2010-12-07
Hi

Try to fix it from the recovery console (at boot time from grub menu) by dropping into a root shell.

Kind regards

---

### Post by CharlesA on 2010-12-07
The sudoers file isn't really meant for running scripts as root (without sudo).

[This]("https://help.ubuntu.com/community/RootSudo") might be worth a read.

---

### Post by matt_symes on 2010-12-07
Hi

+1 CharlesA.

Tell us what your script is trying to achieve and we may be able to suggest the best method to invoke your script.

Kind regards

---

### Post by garvinrick4 on 2010-12-07
Run a live CD and get into root in Nautilus and copy and paste the virgin copy over to your
install that is messed up and save. Add any lines that you want. Matter of fact here is one.

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

---

### Post by dorlow on 2010-12-08
I fixed it yesterday by running the live cd.  I figured out what I did wrong though.  I put my script in the /etc/sudoers.d folder.  It was trying to read it as a source file or something like that.  I was thinking at that moment when I dropped the script in that folder that everything in that folder was a trusted folder and maybe it wouldn't prompt for the sudo password for files in that folder... I was wrong.

Does anyone know how I can run this script without supplying the password?  I've seen so many people post about it and I can't find a straight post on how to do it.  I see everyone says you need to add the user to the sudoers... but not one post I've come across has explained how to do it.  I've screwed up my system once trying to figure it out, so I hope someone will please just spell it out in plain english as if I'm a complete dummy.

Here's a script I call "backup_script"

sudo tar -z --create \
         --file=/media/Backup/$(date +%y%m%d)_$(date +%H%M%S)_Desktop_Backup.tgz \
         --listed-incremental=/var/log/usr.snar \
         /home/david/Desktop/

This is just one excerpt of the file.  I have about 10 lines like this backing up different folders.  Everytime I run it, I have to type sudo backup_script and it asks me for a password.  I can't figure out how to make it a trusted script file so then I could just use cron to schedule it and it won't prompt for a password.

---

### Post by CharlesA on 2010-12-08
Hi dorlow,

I copied the above post to [your other thread]("http://ubuntuforums.org/showthread.php?t=1640432") and edited out the bit about sudo.

That way you can get help with your script, since it seems you solved your sudo problem.

---

### Post by dorlow on 2010-12-08
I swear, this sudo thing was never meant to be... CharlesA, when I click your link, it goes to a post I didn't start, doesn't have anything to do with sudoing, or ever comment in. Please, someone just tell me how to do it! I just checked my other posts and don't see any posts from you in it.
 
This is how every other post I've found on the internet is... everyone is so vague just figuring everyone else knows it all.  I don't.  I wouldn't be asking if I knew.  I need someone to spell it out.  Please just tell me how to do it.

---

### Post by CharlesA on 2010-12-08
Ah sorry about that. I mixed up some numbers.

Your thread is here: [http://ubuntuforums.org/showthread.php?t=1640432](http://ubuntuforums.org/showthread.php?t=1640432)

If you need to run it in cron as root, you'd need to run add it to root's crontab like so:

```
sudo crontab -e
```

---

### Post by dorlow on 2010-12-08
.

---

