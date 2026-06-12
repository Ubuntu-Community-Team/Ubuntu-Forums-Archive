---
title: "apt-get error: &quot;E: Line 1 too long (max 1024)&quot;"
date: 2006-05-28
forum: General Help
---

### Post by chrestomanci on 2006-05-28
(Previously posted to an AMD64 specific forum with no reply)

Hi
 
Apt get on my System has become screwed up somehow. If I run it even just "apt-get -h" I get the above error message. It does not say which file it has a problem with. I get the same error message from apt-cache, apt-cdrom, and apt-config but not apt-key
 
I was editing my /etc/apt/sources.list file before it happened, but I have since restored those files from a backup, and it has not cured the problem.
 
I have also tried reinstalling apt using "dpkg -i" and .deb package downloaded from a Ubuntu mirror?
 
I also tried moving aside the directories in "/var/cache/apt/" and "/var/lib/apt" but that did not cure the problem either.

I have tried greping my system files for 'too long (max 1024)' but not found anything.
 
I have run out of ideas, can anyone think what might be the problem. I have fairly good backups, so if the offending file can be identified, then I can delete & restore it, but I am not ready to re-install my system just yet.
 
Help.

---

### Post by Jussi Kukkonen on 2006-05-28
This error message is about *sources.list*, AFAIK.

Could you please copy-paste commands and their full output -- say *sudo apt-get update*? Maybe /etc/apt/sources.list too?

---

### Post by ifokkema on 2006-05-28
Hi,

interesting problem you have there :)

I've just tried to reproduce your error by adding a long line to my sources.list (350 chars). Running apt-cache show works, but apt-get update returns:
```
E: Line 1 too long in source list /etc/apt/sources.list.
```

Slightly different error... Maybe a long shot, but have you run apt-get update after you placed back your sources.list?

Ivo

---

### Post by chrestomanci on 2006-05-28
[QUOTE=Jussi Kukkonen]This error message is about *sources.list*, AFAIK.

Could you please copy-paste commands and their full output -- say *sudo apt-get update*? Maybe /etc/apt/sources.list too?[/QUOTE]

Here goes:
> root@miranda:~# sudo apt-get update
E: Line 1 too long (max 1024)


As I said, I have restored a working copy of sources.list from a backup, but here it is anyway:
> # CD Rom (not in use)
# deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted

# Local repository.
deb file:///var/mirrors/ubuntu stable  main restricted

# Main ubuntu servers.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

# Mplayer
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb [http://si.archive.ubuntu.com/ubuntu](http://si.archive.ubuntu.com/ubuntu) breezy multiverse




Thanks very much for looking, but I fear this will be a hard problem. I think apt-get is failing very soon after it starts up.

Using ldd, I have found that the four apt-* tools that failed all use the same libaries, but apt-key is staticaly linked. 

> root@miranda:~# ldd /usr/bin/apt-get
        libapt-pkg-libc6.3-6.so.3.10 => /usr/lib/libapt-pkg-libc6.3-6.so.3.10 (0x00002aaaaabc3000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00002aaaaad97000)
        libm.so.6 => /lib/libm.so.6 (0x00002aaaaafa0000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00002aaaab126000)
        libc.so.6 => /lib/libc.so.6 (0x00002aaaab233000)
        /lib64/ld-linux-x86-64.so.2 (0x00002aaaaaaab000)


---

### Post by chrestomanci on 2006-05-28
Perhaps I could compile apt-get from source, and run it using a debugger to find out what file it is trying to open. Any idea how do do that without apt working? Which debugger would be easyest to use, as I have only debugged C-Programs on windows before?

---

### Post by Jussi Kukkonen on 2006-05-28
It seems I was wrong -- if sources.list buffer is too long the error message is what ifokkema says... Your case is probably something else, like you suspected.

Now, apt probably only reads files from /etc/apt/ (and maybe  /var/lib/apt), maybe you should take a look at  files in there and see if there really are long lines?

---

### Post by Jussi Kukkonen on 2006-05-28
[QUOTE=Jussi Kukkonen]
Now, apt probably only reads files from /etc/apt/ (and maybe  /var/lib/apt), maybe you should take a look at  files in there and see if there really are long lines?[/QUOTE]

Well, I decided to take advantage of the freedom we have, and checked the source... According to it your error message is printed when reading the config file -- */etc/apt/apt.conf* I suppose, maybe also stuff in */etc/apt/ap.conf.d/*.

---

### Post by chrestomanci on 2006-05-29
Thanks Jussi Kukkonen

What had happened was that the /etc/apt/apt.conf file had been replaced with an empty directory. When I deleted the directory, and put an empy file in it's place everything worked again.

Do you think it would be a good idea to report the issue as a bug against apt. Would that bug report go to Ubuntu or to Debian?

Thanks again for your help.

---

### Post by ntsibane on 2007-05-31
I have had the same problem for about a week now, but never got around to try to clear it. 

I have just tried your fix but it doesn't work for me. I even tried copying "/usr/share/doc/apt/examples/apt.conf" to "/etc/apt/apt.conf" it still does not work.

---

### Post by ifokkema on 2007-06-01
Hi!
What did you do last, before the error started turning up?
Just to verify - could you run these commands, and post the output, please?
```
ls -lah /etc/apt/
ls -lah /etc/apt/apt.conf.d/
```
Ivo

---

### Post by ntsibane on 2007-06-05
I don't remember what I had just done, the error came up when I tried to install, I hadn't installed anything on my system for over month.

Here is the output

> ntsibane@ntsibane-laptop:~$ ls -lah /etc/apt/
total 44K
drwxr-xr-x   4 root root 4.0K 2007-05-31 15:52 .
drwxr-xr-x 122 root root 8.0K 2007-06-04 23:02 ..
-rw-r--r--   1 root root  496 2007-05-31 16:10 apt.conf
drwxr-xr-x   2 root root 4.0K 2007-05-31 20:38 apt.conf.d
-rw-------   1 root root    0 2006-10-25 15:27 secring.gpg
-rw-r--r--   1 root root 1.8K 2007-05-10 11:01 sources.list
-rw-r--r--   1 root root 1.6K 2007-04-12 08:26 sources.list~
drwxr-xr-x   2 root root 4.0K 2007-03-15 08:14 sources.list.d
-rw-------   1 root root 1.2K 2006-10-25 15:27 trustdb.gpg
-rw-r--r--   1 root root 2.4K 2006-10-25 15:27 trusted.gpg
-rw-r--r--   1 root root 2.4K 2006-10-25 15:27 trusted.gpg~
ntsibane@ntsibane-laptop:~$ ls -lah /etc/apt/apt.conf.d/
total 352K
drwxr-xr-x 2 root root 4.0K 2007-05-31 20:38 .
drwxr-xr-x 4 root root 4.0K 2007-05-31 15:52 ..
-rw-r--r-- 1 root root  138 2006-09-28 01:44 01ubuntu
-rw-r--r-- 1 root root   80 2006-09-11 23:19 05aptitude
-rw-r--r-- 1 root root  129 2007-05-23 07:51 10periodic
-rw-r--r-- 1 root root   85 2006-04-02 10:33 20archive
-rw-r--r-- 1 root root  223 2006-06-27 14:54 50unattended-upgrades
-rw-r--r-- 1 root root  181 2007-05-31 20:38 70debconf
-rw-r--r-- 1 root root  160 2005-07-14 12:38 90zope-common
-rw-r--r-- 1 root root  116 2006-04-02 10:33 99update-notifier
-rw------- 1 root root 392K 2007-05-28 04:59 core

Ntsibane

---

### Post by ifokkema on 2007-06-06
Hi,

I noticed this file... /etc/apt/apt.conf.d/core... it's been modified quite recently... can you view the file? Does it look like a settings file? What happens, if you temporarly move it out of the /etc/apt directory tree?

---

### Post by ntsibane on 2007-06-07
I can't view the file, its not a text file. I moved the file and it works.

Thank you,
Ntsibane

---

### Post by ifokkema on 2007-06-09
Great! Glad to hear that fixed things.

---

