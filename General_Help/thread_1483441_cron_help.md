---
title: "cron help"
date: 2010-05-14
forum: General Help
---

### Post by mg9189b on 2010-05-14
I am having trouble getting my cron jobs to run. I have tried to simplify it as much as possible for this test. I am using Ubuntu Server 8.04, and the previous admin stripped it down to run only what was needed.
 
I am running as root, and there are no users on the system. All access control is done through PAM code and custom login scripts. We can drop down to a shell that is root from there.
 
So, from here, I have tried to make this as basic as possible.
 
I created a file in /etc/cron.d
```
 
-rw-r--r--  1 root root   65 2010-05-14 12:34 test

```
 
The contentst of this file is:
```
 
* * * * * root /bin/echo 'cron.d ' >> /mike.txt 2>&1

```
 
I would expect this file to add another line every minute to /mike.txt. It does not, ever run though. I have rebooted and tested it as well. I can run "/bin/echo 'cron.d ' >> /mike.txt 2>&1" by itself, and it does what is expected. I have tried adding a PATH setting to the file called test.
 
I have verified that cron is indeed running.
```
 
ps -eaf | grep cron
root      9083     1  0 13:11 ?        00:00:00 /usr/sbin/cron

```
 
I have tried restarting the cron service. The logs look like
```
May 14 13:08:35 sti-spm /usr/sbin/cron[2401]: (CRON) INFO (pidfile fd = 3)
May 14 13:08:35 sti-spm /usr/sbin/cron[2402]: (CRON) STARTUP (fork ok)
May 14 13:08:35 sti-spm /usr/sbin/cron[2402]: (CRON) INFO (Running @reboot jobs)
May 14 13:11:46 sti-spm /usr/sbin/cron[9082]: (CRON) INFO (pidfile fd = 3)
May 14 13:11:46 sti-spm /usr/sbin/cron[9083]: (CRON) STARTUP (fork ok)
May 14 13:11:46 sti-spm /usr/sbin/cron[9083]: (CRON) INFO (Skipping @reboot jobs -- not system startup)
```
 
What am I doing wrong?

---

### Post by Youresorock on 2010-05-14
I have trouble with cron.d, cron.daily, etc.  I always use the crontab program to add jobs instead.

I have read that files in your cron.whatever folders cannot contain '.' I don't know if that's true, but something to try.

---

### Post by gmargo on 2010-05-14
I had no trouble at all; I tried a simpler test though.  I just created the following file in /etc/cron.d/, and it started working; I didn't even have to restart cron. (on 8.04 Hardy.)

```

$ cat /etc/cron.d/miketest
* * * * * root date >> /tmp/miketest.txt 2>/dev/null

```

---

### Post by mg9189b on 2010-05-15
I did get this to work on the main distribution.  But that system was upgraded from prior versions and is my development machine.
 
I cannot get this to work the Server release.
 
I am wondering if there may be a missing package that could cause this to happen.

---

### Post by gmargo on 2010-05-15
That is strange.  You should only need the cron package, although I have anacron installed as well.  These are the versions on my up-to-date 8.04 Hardy:
```

ii  anacron                                      2.3-13ubuntu2.1                              cron-like program that doesn't go by time
ii  cron                                         3.0pl1-100ubuntu2.1                          management of regular background processing

```The file permissions in /etc/cron.d/ shouldn't matter, but how about the directory itself?  Mine shows 755 permissions.
```

$ ls -ld /etc/cron.d
drwxr-xr-x 2 root root 4096 May 14 19:16 /etc/cron.d

```

---

### Post by gmargo on 2010-05-15
I created a new 8.04.4 Hardy server install in a VM, and can confirm that cron is installed (no anacron) and works fine by default.  Perhaps you should try "aptitude reinstall cron".

---

### Post by mg9189b on 2010-05-15
I will give that a try on Tuesday.  Thanks for the advice.

---

### Post by mg9189b on 2010-05-18
Well, nothing works yet.  Any more suggestions?
 
The permissions on /etc/cron.d are the same as yours.
 
I reinstalled cron, and that did not help.
 
Perhaps this helps.  The upgrade script that was run on this machine removed the following packages (are any of these used by cron??):
 
 apt-get --yes purge apparmor apparmor-utils at bash-completion bsdmainutils man-db bzip2 ubuntu-minimal command-not-found-data command-not-found python-gdbm console-setup console-terminus kbd consolekit dbus dbus-x11 cpp cpp-4.3 dmsetup dosfstools eject friendly-recovery libntfs-3g28 libntfs-3g49 fuse-utils ntfs-3g gettext-base pppoeconf screen-profiles gnupg python-gnupginterface ubuntu-keyring update-manager-core python-newt update-notifier-common gpgv groff-base hdparm info installation-report iputils-arping iso-codes laptop-detect libapparmor-perl libapparmor1 libatm1 libck-connector0 libpam-ck-connector libclass-accessor-perl libparse-debianchangelog-perl libcompress-raw-zlib-perl libcompress-zlib-perl libio-compress-zlib-perl libdbus-1-3 libdbus-glib-1-2 python-dbus wpasupplicant libffi5 python-gobject libfont-afm-perl libhtml-format-perl libfribidi0 libfuse2 libgc1c2 w3m libgmp3c2 libmpfr1ldbl libhtml-parser-perl libhtml-tree-perl librpc-xml-perl libwww-perl libxml-parser-perl libxml-sax-expat-perl libxml-simple-perl libhtml-tagset-perl libhtml-template-perl libio-compress-base-perl libio-string-perl libiw29 wireless-tools liblockfile1 lockfile-progs libmailtools-perl libpci3 lshw pciutils libpcsclite1 libpolkit2 libterm-readkey-perl libtimedate-perl liburi-perl libxext6 xauth libxml-namespacesupport-perl libxml-sax-perl libxmuu1 lsb-release python-apt manpages mlocate nano openssl-blacklist patch popularity-contest ppp pppconfig python python-central python-openssl python-pam python-pyopenssl python-serial python-support python-twisted-bin python-twisted-core python-zopeinterface ufw python2.5 python2.5-minimal reiserfsprogs rsync screen sgml-base xml-core shared-mime-info tasksel tasksel-data ubuntu-serverguide uuid-runtime vim libpython2.6 python2.6 x-ttcidfont-conf x11-common xfonts-encodings xfonts-utils xkb-data libfontenc1 libxfont1 snmpd

 apt-get --yes autoremove

---

### Post by mg9189b on 2010-05-18
oh yeah, the cron version running right now is  3.0pl1-105ubuntu1.1

---

### Post by mg9189b on 2010-05-18
What makes this issue more perplexing is that I have multiple servers, and some do work with this example just fine.  All were configured the same way.
 
My development machine works as well, but it is running Karmic.

---

### Post by gmargo on 2010-05-18
> **mg9189b said:**
> Well, nothing works yet.  Any more suggestions?
 
apt-get --yes purge [really long list]   -  WOW!

At the very least:
```

apt-get install ubuntu-minimal ubuntu-standard

```

---

### Post by mg9189b on 2010-05-19
That did not do anything.  It appears that these 2 packages are already installed.

```
root@sti-spm:/etc/cron.d# apt-get install ubuntu-minimal ubuntu-standard
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-minimal is already the newest version.
ubuntu-standard is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by gmargo on 2010-05-19
> **mg9189b said:**
> oh yeah, the cron version running right now is  3.0pl1-105ubuntu1.1

You claimed to be running 8.04 Hardy, but this version of cron is from 9.04 Jaunty. 
[http://packages.ubuntu.com/jaunty/cron](http://packages.ubuntu.com/jaunty/cron)

So perhaps you are really running Jaunty, and need to adjust your /etc/apt/sources.list to point to Jaunty instead of Hardy.

Use "lsb_release -a" to see what your system thinks it is.

---

### Post by mg9189b on 2010-05-19
I am sorry.  I meant 9.04.  I should have just said jaunty.
 
Anyway, I have done some digging and rebuilt a server using the install scripts one line at a time.  I have determined it is not the list of packages, or the removal of them, for when done by themselves, all works fine.  
 
The problem starts when the custom PAM and NSS libraries are used.
 
I was not aware that PAM had any influence on cron jobs, or the root account, but I'm no expert on Unix either.  I am currently looking at the code and configuration files of our PAM code to see if there is anything there I need to do.
 
Any suggestions would be much appreciated.  Is there some kind of option in these config files that I can use to tell PAM and NSS to tell cron to use normal security features?

---

### Post by mg9189b on 2010-05-19
Well, thanks for all you input.  The solution is that I needed to modify /etc/pam.d/cron for sufficient privileges to do whatever it needs to do.
 
Well, not being even remotely familiar with this, I managed to get another user's configuration to work.  I now need to explore this some more to see if this is the security set of settings I really need.  For now though, I have crossed this hurdle.

---

