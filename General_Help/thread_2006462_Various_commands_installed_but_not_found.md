---
title: "Various commands installed but not found?"
date: 2012-06-19
forum: General Help
---

### Post by forquare on 2012-06-19
Good morning all,

I have a box here where with some commands I get a message saying that the command isn't installed.  However when I try to install them it says that they are installed...

Three commands I've found like this are: passwd, shutdown, reboot.

```

$ passwd
The program 'passwd' is currently not installed.  You can install it by typing:
sudo apt-get install passwd
$ sudo apt-get install passwd
Reading package lists... Done
Building dependency tree
Reading state information... Done
passwd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ sudo passwd
sudo: passwd: command not found

```

Various logs are missing also.

Reinstalling, unfortunatly, isn't an option I'm willing to consider at this point.  Using a backup also isn't an option as the person who set this up didn't backup any configuration, only general data...

EDIT:
I've also tried resetting my password through the GUI, but the 'Change' button is disabled...

Many thanks for any help,
Ben

---

### Post by deathadder on 2012-06-19
The passwd command is under /usr/bin so it sounds like your PATH variable has been reset. You can check your PATH using:
```
echo $PATH
```
On my Xubuntu machine it's set to:
```
$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```
If you're missing /usr/bin for example, you can update your PATH temporarily by using:
```
$ export PATH=$PATH:/usr/bin
```
That will append /usr/bin to your PATH. If that works, there's loads of threads etc around about making your PATH permanent. But that being said, if you want to make the change for your user you can put it in ~/.bashrc, for the system you can add it to /etc/environment.

In your ~/.bashrc you need to place the full export command, if you're editing /etc/environment I believe you can just update the variable like so:
```
PATH="${PATH}:/usr/bin:~/bin:/another/path"
```

---

### Post by forquare on 2012-06-19
Many thanks for your reply, deathadder.

My $PATH is as follows:
```
$ echo $PATH
/home/server/perl5/perlbrew/bin:/home/server/perl5/perlbrew/perls/perl-5.15.9/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

Also to note:
```
$ /usr/bin/passwd
-bash: /usr/bin/passwd: No such file or directory
```

---

### Post by drmrgd on 2012-06-19
I would have thought it was that your $PATH was mucked up too.  The passwd command should be in /usr/bin/, and shutdown and reboot are in /sbin on my system.  Maybe for some strange reason yours isn't.  Can you run:

```
which passwd
```

That should confirm that the command is in /usr/bin on your system.

---

### Post by deathadder on 2012-06-19
Have you changed any permissions on your system recently? What are the permissions on /usr/bin and the passwd command? If you can't find passwd using the which command then it isn't in your PATH. You can find it by using the find command:
```
find / -iname 'passwd'
```
It should look like this:
```
$ ls -l /usr/
total 184
drwxr-xr-x   2 root root 61440 Jun 19 08:25 bin
<snip>
$ ls -l /usr/bin/passwd 
-rwsr-xr-x 1 root root 42824 Apr  9 03:32 /usr/bin/passwd
```

---

### Post by deathadder on 2012-06-19
Can you post the output of the mount command too, it could be that your /usr is mounted but doesn't have the exec flag set.

---

### Post by forquare on 2012-06-19
Many thanks for your responses.

```
$ which passwd
$ which shutdown
$ which reboot
$
```

```
ls -ld /usr/bin
drwxr-xr-x 2 root root 60K Jun 19 08:21 /usr/bin/
```

```
$ find / -iname 'passwd'
/usr/share/lintian/overrides/passwd
/usr/share/doc/passwd
find: ‘/run/udisks’: Permission denied
find: ‘/run/lightdm’: Permission denied
find: ‘/run/cups/certs’: Permission denied
find: ‘/var/log/cups’: Permission denied
find: ‘/var/log/samba/cores’: Permission denied
find: ‘/var/log/lightdm’: Permission denied
find: ‘/var/spool/cups’: Permission denied
find: ‘/var/spool/mqueue’: Permission denied
find: ‘/var/spool/cron/crontabs’: Permission denied
find: ‘/var/spool/cron/atjobs’: Permission denied
find: ‘/var/spool/cron/atspool’: Permission denied
find: ‘/var/spool/mqueue-client’: Permission denied
find: ‘/var/cache/lightdm/dmrc’: Permission denied
find: ‘/var/cache/system-tools-backends/backup’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/lib/ejabberd’: Permission denied
find: ‘/var/lib/gdm’: Permission denied
find: ‘/var/lib/lightdm’: Permission denied
find: ‘/var/lib/polkit-1’: Permission denied
find: ‘/var/lib/sendmail’: Permission denied
find: ‘/var/lib/php5’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/var/lib/sudo’: Permission denied
find: ‘/var/backups/ejabberd-2011-11-23T08:34:16.Y5Nb5E’: Permission denied
find: ‘/sys/kernel/debug’: Permission denied
/etc/passwd
find: ‘/etc/cups/ssl’: Permission denied
/etc/pam.d/passwd
find: ‘/etc/ejabberd’: Permission denied
find: ‘/etc/chatscripts’: Permission denied
find: ‘/etc/ppp/peers’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
/etc/cron.daily/passwd
find: ‘/opt/foldingathome/1/work’: Permission denied
find: ‘/lost+found’: Permission denied
find: ‘/root’: Permission denied
find: ‘/tmp/fah’: Permission denied
find: ‘/tmp/.esd-119’: Permission denied
find: ‘/tmp/pulse-PKdhtXMmr18n’: Permission denied
find: ‘/tmp/pulse-JERREyDrCvCs’: Permission denied
find: ‘/proc/tty/driver’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/2/task/2/fd’: Permission denied
find: ‘/proc/2/task/2/fdinfo’: Permission denied
find: ‘/proc/2/task/2/ns’: Permission denied
find: ‘/proc/2/fd’: Permission denied
find: ‘/proc/2/fdinfo’: Permission denied
find: ‘/proc/2/ns’: Permission denied
find: ‘/proc/3/task/3/fd’: Permission denied
find: ‘/proc/3/task/3/fdinfo’: Permission denied
find: ‘/proc/3/task/3/ns’: Permission denied
find: ‘/proc/3/fd’: Permission denied
find: ‘/proc/3/fdinfo’: Permission denied
find: ‘/proc/3/ns’: Permission denied
find: ‘/proc/6/task/6/fd’: Permission denied
find: ‘/proc/6/task/6/fdinfo’: Permission denied
find: ‘/proc/6/task/6/ns’: Permission denied
find: ‘/proc/6/fd’: Permission denied
find: ‘/proc/6/fdinfo’: Permission denied
find: ‘/proc/6/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
find: ‘/proc/8/task/8/fd’: Permission denied
find: ‘/proc/8/task/8/fdinfo’: Permission denied
find: ‘/proc/8/task/8/ns’: Permission denied
find: ‘/proc/8/fd’: Permission denied
find: ‘/proc/8/fdinfo’: Permission denied
find: ‘/proc/8/ns’: Permission denied
find: ‘/proc/10/task/10/fd’: Permission denied
find: ‘/proc/10/task/10/fdinfo’: Permission denied
find: ‘/proc/10/task/10/ns’: Permission denied
find: ‘/proc/10/fd’: Permission denied
find: ‘/proc/10/fdinfo’: Permission denied
find: ‘/proc/10/ns’: Permission denied
find: ‘/proc/12/task/12/fd’: Permission denied
find: ‘/proc/12/task/12/fdinfo’: Permission denied
find: ‘/proc/12/task/12/ns’: Permission denied
find: ‘/proc/12/fd’: Permission denied
find: ‘/proc/12/fdinfo’: Permission denied
find: ‘/proc/12/ns’: Permission denied
find: ‘/proc/13/task/13/fd’: Permission denied
find: ‘/proc/13/task/13/fdinfo’: Permission denied
find: ‘/proc/13/task/13/ns’: Permission denied
find: ‘/proc/13/fd’: Permission denied
find: ‘/proc/13/fdinfo’: Permission denied
find: ‘/proc/13/ns’: Permission denied
find: ‘/proc/14/task/14/fd’: Permission denied
find: ‘/proc/14/task/14/fdinfo’: Permission denied
find: ‘/proc/14/task/14/ns’: Permission denied
find: ‘/proc/14/fd’: Permission denied
find: ‘/proc/14/fdinfo’: Permission denied
find: ‘/proc/14/ns’: Permission denied
find: ‘/proc/15/task/15/fd’: Permission denied
find: ‘/proc/15/task/15/fdinfo’: Permission denied
find: ‘/proc/15/task/15/ns’: Permission denied
find: ‘/proc/15/fd’: Permission denied
find: ‘/proc/15/fdinfo’: Permission denied
find: ‘/proc/15/ns’: Permission denied
find: ‘/proc/16/task/16/fd’: Permission denied
find: ‘/proc/16/task/16/fdinfo’: Permission denied
find: ‘/proc/16/task/16/ns’: Permission denied
find: ‘/proc/16/fd’: Permission denied
find: ‘/proc/16/fdinfo’: Permission denied
find: ‘/proc/16/ns’: Permission denied
find: ‘/proc/18/task/18/fd’: Permission denied
find: ‘/proc/18/task/18/fdinfo’: Permission denied
find: ‘/proc/18/task/18/ns’: Permission denied
find: ‘/proc/18/fd’: Permission denied
find: ‘/proc/18/fdinfo’: Permission denied
find: ‘/proc/18/ns’: Permission denied
find: ‘/proc/19/task/19/fd’: Permission denied
find: ‘/proc/19/task/19/fdinfo’: Permission denied
find: ‘/proc/19/task/19/ns’: Permission denied
find: ‘/proc/19/fd’: Permission denied
find: ‘/proc/19/fdinfo’: Permission denied
find: ‘/proc/19/ns’: Permission denied
find: ‘/proc/20/task/20/fd’: Permission denied
find: ‘/proc/20/task/20/fdinfo’: Permission denied
find: ‘/proc/20/task/20/ns’: Permission denied
find: ‘/proc/20/fd’: Permission denied
find: ‘/proc/20/fdinfo’: Permission denied
find: ‘/proc/20/ns’: Permission denied
find: ‘/proc/21/task/21/fd’: Permission denied
find: ‘/proc/21/task/21/fdinfo’: Permission denied
find: ‘/proc/21/task/21/ns’: Permission denied
find: ‘/proc/21/fd’: Permission denied
find: ‘/proc/21/fdinfo’: Permission denied
find: ‘/proc/21/ns’: Permission denied
find: ‘/proc/22/task/22/fd’: Permission denied
find: ‘/proc/22/task/22/fdinfo’: Permission denied
find: ‘/proc/22/task/22/ns’: Permission denied
find: ‘/proc/22/fd’: Permission denied
find: ‘/proc/22/fdinfo’: Permission denied
find: ‘/proc/22/ns’: Permission denied
find: ‘/proc/23/task/23/fd’: Permission denied
find: ‘/proc/23/task/23/fdinfo’: Permission denied
find: ‘/proc/23/task/23/ns’: Permission denied
find: ‘/proc/23/fd’: Permission denied
find: ‘/proc/23/fdinfo’: Permission denied
find: ‘/proc/23/ns’: Permission denied
find: ‘/proc/24/task/24/fd’: Permission denied
find: ‘/proc/24/task/24/fdinfo’: Permission denied
find: ‘/proc/24/task/24/ns’: Permission denied
find: ‘/proc/24/fd’: Permission denied
find: ‘/proc/24/fdinfo’: Permission denied
find: ‘/proc/24/ns’: Permission denied
find: ‘/proc/26/task/26/fd’: Permission denied
find: ‘/proc/26/task/26/fdinfo’: Permission denied
find: ‘/proc/26/task/26/ns’: Permission denied
find: ‘/proc/26/fd’: Permission denied
find: ‘/proc/26/fdinfo’: Permission denied
find: ‘/proc/26/ns’: Permission denied
find: ‘/proc/27/task/27/fd’: Permission denied
find: ‘/proc/27/task/27/fdinfo’: Permission denied
find: ‘/proc/27/task/27/ns’: Permission denied
find: ‘/proc/27/fd’: Permission denied
find: ‘/proc/27/fdinfo’: Permission denied
find: ‘/proc/27/ns’: Permission denied
find: ‘/proc/28/task/28/fd’: Permission denied
find: ‘/proc/28/task/28/fdinfo’: Permission denied
find: ‘/proc/28/task/28/ns’: Permission denied
find: ‘/proc/28/fd’: Permission denied
find: ‘/proc/28/fdinfo’: Permission denied
find: ‘/proc/28/ns’: Permission denied
find: ‘/proc/29/task/29/fd’: Permission denied
find: ‘/proc/29/task/29/fdinfo’: Permission denied
find: ‘/proc/29/task/29/ns’: Permission denied
find: ‘/proc/29/fd’: Permission denied
find: ‘/proc/29/fdinfo’: Permission denied
find: ‘/proc/29/ns’: Permission denied
find: ‘/proc/30/task/30/fd’: Permission denied
find: ‘/proc/30/task/30/fdinfo’: Permission denied
find: ‘/proc/30/task/30/ns’: Permission denied
find: ‘/proc/30/fd’: Permission denied
find: ‘/proc/30/fdinfo’: Permission denied
find: ‘/proc/30/ns’: Permission denied
find: ‘/proc/31/task/31/fd’: Permission denied
find: ‘/proc/31/task/31/fdinfo’: Permission denied
find: ‘/proc/31/task/31/ns’: Permission denied
find: ‘/proc/31/fd’: Permission denied
find: ‘/proc/31/fdinfo’: Permission denied
find: ‘/proc/31/ns’: Permission denied
find: ‘/proc/39/task/39/fd’: Permission denied
find: ‘/proc/39/task/39/fdinfo’: Permission denied
find: ‘/proc/39/task/39/ns’: Permission denied
find: ‘/proc/39/fd’: Permission denied
find: ‘/proc/39/fdinfo’: Permission denied
find: ‘/proc/39/ns’: Permission denied
find: ‘/proc/41/task/41/fd’: Permission denied
find: ‘/proc/41/task/41/fdinfo’: Permission denied
find: ‘/proc/41/task/41/ns’: Permission denied
find: ‘/proc/41/fd’: Permission denied
find: ‘/proc/41/fdinfo’: Permission denied
find: ‘/proc/41/ns’: Permission denied
find: ‘/proc/42/task/42/fd’: Permission denied
find: ‘/proc/42/task/42/fdinfo’: Permission denied
find: ‘/proc/42/task/42/ns’: Permission denied
find: ‘/proc/42/fd’: Permission denied
find: ‘/proc/42/fdinfo’: Permission denied
find: ‘/proc/42/ns’: Permission denied
find: ‘/proc/43/task/43/fd’: Permission denied
find: ‘/proc/43/task/43/fdinfo’: Permission denied
find: ‘/proc/43/task/43/ns’: Permission denied
find: ‘/proc/43/fd’: Permission denied
find: ‘/proc/43/fdinfo’: Permission denied
find: ‘/proc/43/ns’: Permission denied
find: ‘/proc/44/task/44/fd’: Permission denied
find: ‘/proc/44/task/44/fdinfo’: Permission denied
find: ‘/proc/44/task/44/ns’: Permission denied
find: ‘/proc/44/fd’: Permission denied
find: ‘/proc/44/fdinfo’: Permission denied
find: ‘/proc/44/ns’: Permission denied
find: ‘/proc/47/task/47/fd’: Permission denied
find: ‘/proc/47/task/47/fdinfo’: Permission denied
find: ‘/proc/47/task/47/ns’: Permission denied
find: ‘/proc/47/fd’: Permission denied
find: ‘/proc/47/fdinfo’: Permission denied
find: ‘/proc/47/ns’: Permission denied
find: ‘/proc/48/task/48/fd’: Permission denied
find: ‘/proc/48/task/48/fdinfo’: Permission denied
find: ‘/proc/48/task/48/ns’: Permission denied
find: ‘/proc/48/fd’: Permission denied
find: ‘/proc/48/fdinfo’: Permission denied
find: ‘/proc/48/ns’: Permission denied
find: ‘/proc/49/task/49/fd’: Permission denied
find: ‘/proc/49/task/49/fdinfo’: Permission denied
find: ‘/proc/49/task/49/ns’: Permission denied
find: ‘/proc/49/fd’: Permission denied
find: ‘/proc/49/fdinfo’: Permission denied
find: ‘/proc/49/ns’: Permission denied
find: ‘/proc/50/task/50/fd’: Permission denied
find: ‘/proc/50/task/50/fdinfo’: Permission denied
find: ‘/proc/50/task/50/ns’: Permission denied
find: ‘/proc/50/fd’: Permission denied
find: ‘/proc/50/fdinfo’: Permission denied
find: ‘/proc/50/ns’: Permission denied
find: ‘/proc/70/task/70/fd’: Permission denied
find: ‘/proc/70/task/70/fdinfo’: Permission denied
find: ‘/proc/70/task/70/ns’: Permission denied
find: ‘/proc/70/fd’: Permission denied
find: ‘/proc/70/fdinfo’: Permission denied
find: ‘/proc/70/ns’: Permission denied
find: ‘/proc/71/task/71/fd’: Permission denied
find: ‘/proc/71/task/71/fdinfo’: Permission denied
find: ‘/proc/71/task/71/ns’: Permission denied
find: ‘/proc/71/fd’: Permission denied
find: ‘/proc/71/fdinfo’: Permission denied
find: ‘/proc/71/ns’: Permission denied
find: ‘/proc/199/task/199/fd’: Permission denied
find: ‘/proc/199/task/199/fdinfo’: Permission denied
find: ‘/proc/199/task/199/ns’: Permission denied
find: ‘/proc/199/fd’: Permission denied
find: ‘/proc/199/fdinfo’: Permission denied
find: ‘/proc/199/ns’: Permission denied
find: ‘/proc/244/task/244/fd’: Permission denied
find: ‘/proc/244/task/244/fdinfo’: Permission denied
find: ‘/proc/244/task/244/ns’: Permission denied
find: ‘/proc/244/fd’: Permission denied
find: ‘/proc/244/fdinfo’: Permission denied
find: ‘/proc/244/ns’: Permission denied
find: ‘/proc/245/task/245/fd’: Permission denied
find: ‘/proc/245/task/245/fdinfo’: Permission denied
find: ‘/proc/245/task/245/ns’: Permission denied
find: ‘/proc/245/fd’: Permission denied
find: ‘/proc/245/fdinfo’: Permission denied
find: ‘/proc/245/ns’: Permission denied
find: ‘/proc/404/task/404/fd’: Permission denied
find: ‘/proc/404/task/404/fdinfo’: Permission denied
find: ‘/proc/404/task/404/ns’: Permission denied
find: ‘/proc/404/fd’: Permission denied
find: ‘/proc/404/fdinfo’: Permission denied
find: ‘/proc/404/ns’: Permission denied
find: ‘/proc/411/task/411/fd’: Permission denied
find: ‘/proc/411/task/411/fdinfo’: Permission denied
find: ‘/proc/411/task/411/ns’: Permission denied
find: ‘/proc/411/fd’: Permission denied
find: ‘/proc/411/fdinfo’: Permission denied
find: ‘/proc/411/ns’: Permission denied
find: ‘/proc/418/task/418/fd’: Permission denied
find: ‘/proc/418/task/418/fdinfo’: Permission denied
find: ‘/proc/418/task/418/ns’: Permission denied
find: ‘/proc/418/fd’: Permission denied
find: ‘/proc/418/fdinfo’: Permission denied
find: ‘/proc/418/ns’: Permission denied
find: ‘/proc/610/task/610/fd’: Permission denied
find: ‘/proc/610/task/610/fdinfo’: Permission denied
find: ‘/proc/610/task/610/ns’: Permission denied
find: ‘/proc/610/fd’: Permission denied
find: ‘/proc/610/fdinfo’: Permission denied
find: ‘/proc/610/ns’: Permission denied
find: ‘/proc/666/task/666/fd’: Permission denied
find: ‘/proc/666/task/666/fdinfo’: Permission denied
find: ‘/proc/666/task/666/ns’: Permission denied
find: ‘/proc/666/fd’: Permission denied
find: ‘/proc/666/fdinfo’: Permission denied
find: ‘/proc/666/ns’: Permission denied
find: ‘/proc/667/task/667/fd’: Permission denied
find: ‘/proc/667/task/667/fdinfo’: Permission denied
find: ‘/proc/667/task/667/ns’: Permission denied
find: ‘/proc/667/fd’: Permission denied
find: ‘/proc/667/fdinfo’: Permission denied
find: ‘/proc/667/ns’: Permission denied
find: ‘/proc/730/task/730/fd’: Permission denied
find: ‘/proc/730/task/730/fdinfo’: Permission denied
find: ‘/proc/730/task/730/ns’: Permission denied
find: ‘/proc/730/fd’: Permission denied
find: ‘/proc/730/fdinfo’: Permission denied
find: ‘/proc/730/ns’: Permission denied
find: ‘/proc/731/task/731/fd’: Permission denied
find: ‘/proc/731/task/731/fdinfo’: Permission denied
find: ‘/proc/731/task/731/ns’: Permission denied
find: ‘/proc/731/fd’: Permission denied
find: ‘/proc/731/fdinfo’: Permission denied
find: ‘/proc/731/ns’: Permission denied
find: ‘/proc/773/task/773/fd’: Permission denied
find: ‘/proc/773/task/773/fdinfo’: Permission denied
find: ‘/proc/773/task/773/ns’: Permission denied
find: ‘/proc/773/fd’: Permission denied
find: ‘/proc/773/fdinfo’: Permission denied
find: ‘/proc/773/ns’: Permission denied
find: ‘/proc/775/task/775/fd’: Permission denied
find: ‘/proc/775/task/775/fdinfo’: Permission denied
find: ‘/proc/775/task/775/ns’: Permission denied
find: ‘/proc/775/fd’: Permission denied
find: ‘/proc/775/fdinfo’: Permission denied
find: ‘/proc/775/ns’: Permission denied
find: ‘/proc/796/task/796/fd’: Permission denied
find: ‘/proc/796/task/796/fdinfo’: Permission denied
find: ‘/proc/796/task/796/ns’: Permission denied
find: ‘/proc/796/fd’: Permission denied
find: ‘/proc/796/fdinfo’: Permission denied
find: ‘/proc/796/ns’: Permission denied
find: ‘/proc/805/task/805/fd’: Permission denied
find: ‘/proc/805/task/805/fdinfo’: Permission denied
find: ‘/proc/805/task/805/ns’: Permission denied
find: ‘/proc/805/fd’: Permission denied
find: ‘/proc/805/fdinfo’: Permission denied
find: ‘/proc/805/ns’: Permission denied
find: ‘/proc/807/task/807/fd’: Permission denied
find: ‘/proc/807/task/807/fdinfo’: Permission denied
find: ‘/proc/807/task/807/ns’: Permission denied
find: ‘/proc/807/fd’: Permission denied
find: ‘/proc/807/fdinfo’: Permission denied
find: ‘/proc/807/ns’: Permission denied
find: ‘/proc/818/task/818/fd’: Permission denied
find: ‘/proc/818/task/818/fdinfo’: Permission denied
find: ‘/proc/818/task/818/ns’: Permission denied
find: ‘/proc/818/task/822/fd’: Permission denied
find: ‘/proc/818/task/822/fdinfo’: Permission denied
find: ‘/proc/818/task/822/ns’: Permission denied
find: ‘/proc/818/task/823/fd’: Permission denied
find: ‘/proc/818/task/823/fdinfo’: Permission denied
find: ‘/proc/818/task/823/ns’: Permission denied
find: ‘/proc/818/task/824/fd’: Permission denied
find: ‘/proc/818/task/824/fdinfo’: Permission denied
find: ‘/proc/818/task/824/ns’: Permission denied
find: ‘/proc/818/fd’: Permission denied
find: ‘/proc/818/fdinfo’: Permission denied
find: ‘/proc/818/ns’: Permission denied
find: ‘/proc/819/task/819/fd’: Permission denied
find: ‘/proc/819/task/819/fdinfo’: Permission denied
find: ‘/proc/819/task/819/ns’: Permission denied
find: ‘/proc/819/fd’: Permission denied
find: ‘/proc/819/fdinfo’: Permission denied
find: ‘/proc/819/ns’: Permission denied
find: ‘/proc/826/task/826/fd’: Permission denied
find: ‘/proc/826/task/826/fdinfo’: Permission denied
find: ‘/proc/826/task/826/ns’: Permission denied
find: ‘/proc/826/fd’: Permission denied
find: ‘/proc/826/fdinfo’: Permission denied
find: ‘/proc/826/ns’: Permission denied
find: ‘/proc/855/task/855/fd’: Permission denied
find: ‘/proc/855/task/855/fdinfo’: Permission denied
find: ‘/proc/855/task/855/ns’: Permission denied
find: ‘/proc/855/fd’: Permission denied
find: ‘/proc/855/fdinfo’: Permission denied
find: ‘/proc/855/ns’: Permission denied
find: ‘/proc/876/task/876/fd’: Permission denied
find: ‘/proc/876/task/876/fdinfo’: Permission denied
find: ‘/proc/876/task/876/ns’: Permission denied
find: ‘/proc/876/fd’: Permission denied
find: ‘/proc/876/fdinfo’: Permission denied
find: ‘/proc/876/ns’: Permission denied
find: ‘/proc/891/task/891/fd’: Permission denied
find: ‘/proc/891/task/891/fdinfo’: Permission denied
find: ‘/proc/891/task/891/ns’: Permission denied
find: ‘/proc/891/fd’: Permission denied
find: ‘/proc/891/fdinfo’: Permission denied
find: ‘/proc/891/ns’: Permission denied
find: ‘/proc/892/task/892/fd’: Permission denied
find: ‘/proc/892/task/892/fdinfo’: Permission denied
find: ‘/proc/892/task/892/ns’: Permission denied
find: ‘/proc/892/fd’: Permission denied
find: ‘/proc/892/fdinfo’: Permission denied
find: ‘/proc/892/ns’: Permission denied
find: ‘/proc/894/task/894/fd’: Permission denied
find: ‘/proc/894/task/894/fdinfo’: Permission denied
find: ‘/proc/894/task/894/ns’: Permission denied
find: ‘/proc/894/fd’: Permission denied
find: ‘/proc/894/fdinfo’: Permission denied
find: ‘/proc/894/ns’: Permission denied
find: ‘/proc/899/task/899/fd’: Permission denied
find: ‘/proc/899/task/899/fdinfo’: Permission denied
find: ‘/proc/899/task/899/ns’: Permission denied
find: ‘/proc/899/fd’: Permission denied
find: ‘/proc/899/fdinfo’: Permission denied
find: ‘/proc/899/ns’: Permission denied
find: ‘/proc/930/task/930/fd’: Permission denied
find: ‘/proc/930/task/930/fdinfo’: Permission denied
find: ‘/proc/930/task/930/ns’: Permission denied
find: ‘/proc/930/fd’: Permission denied
find: ‘/proc/930/fdinfo’: Permission denied
find: ‘/proc/930/ns’: Permission denied
find: ‘/proc/932/task/932/fd’: Permission denied
find: ‘/proc/932/task/932/fdinfo’: Permission denied
find: ‘/proc/932/task/932/ns’: Permission denied
find: ‘/proc/932/task/954/fd’: Permission denied
find: ‘/proc/932/task/954/fdinfo’: Permission denied
find: ‘/proc/932/task/954/ns’: Permission denied
find: ‘/proc/932/task/1210/fd’: Permission denied
find: ‘/proc/932/task/1210/fdinfo’: Permission denied
find: ‘/proc/932/task/1210/ns’: Permission denied
find: ‘/proc/932/fd’: Permission denied
find: ‘/proc/932/fdinfo’: Permission denied
find: ‘/proc/932/ns’: Permission denied
find: ‘/proc/934/task/934/fd’: Permission denied
find: ‘/proc/934/task/934/fdinfo’: Permission denied
find: ‘/proc/934/task/934/ns’: Permission denied
find: ‘/proc/934/task/961/fd’: Permission denied
find: ‘/proc/934/task/961/fdinfo’: Permission denied
find: ‘/proc/934/task/961/ns’: Permission denied
find: ‘/proc/934/task/1449/fd’: Permission denied
find: ‘/proc/934/task/1449/fdinfo’: Permission denied
find: ‘/proc/934/task/1449/ns’: Permission denied
find: ‘/proc/934/fd’: Permission denied
find: ‘/proc/934/fdinfo’: Permission denied
find: ‘/proc/934/ns’: Permission denied
find: ‘/proc/956/task/956/fd’: Permission denied
find: ‘/proc/956/task/956/fdinfo’: Permission denied
find: ‘/proc/956/task/956/ns’: Permission denied
find: ‘/proc/956/task/958/fd’: Permission denied
find: ‘/proc/956/task/958/fdinfo’: Permission denied
find: ‘/proc/956/task/958/ns’: Permission denied
find: ‘/proc/956/fd’: Permission denied
find: ‘/proc/956/fdinfo’: Permission denied
find: ‘/proc/956/ns’: Permission denied
find: ‘/proc/971/task/971/fd’: Permission denied
find: ‘/proc/971/task/971/fdinfo’: Permission denied
find: ‘/proc/971/task/971/ns’: Permission denied
find: ‘/proc/971/fd’: Permission denied
find: ‘/proc/971/fdinfo’: Permission denied
find: ‘/proc/971/ns’: Permission denied
find: ‘/proc/976/task/976/fd’: Permission denied
find: ‘/proc/976/task/976/fdinfo’: Permission denied
find: ‘/proc/976/task/976/ns’: Permission denied
find: ‘/proc/976/fd’: Permission denied
find: ‘/proc/976/fdinfo’: Permission denied
find: ‘/proc/976/ns’: Permission denied
find: ‘/proc/992/task/992/fd’: Permission denied
find: ‘/proc/992/task/992/fdinfo’: Permission denied
find: ‘/proc/992/task/992/ns’: Permission denied
find: ‘/proc/992/fd’: Permission denied
find: ‘/proc/992/fdinfo’: Permission denied
find: ‘/proc/992/ns’: Permission denied
find: ‘/proc/993/task/993/fd’: Permission denied
find: ‘/proc/993/task/993/fdinfo’: Permission denied
find: ‘/proc/993/task/993/ns’: Permission denied
find: ‘/proc/993/fd’: Permission denied
find: ‘/proc/993/fdinfo’: Permission denied
find: ‘/proc/993/ns’: Permission denied
find: ‘/proc/996/task/996/fd’: Permission denied
find: ‘/proc/996/task/996/fdinfo’: Permission denied
find: ‘/proc/996/task/996/ns’: Permission denied
find: ‘/proc/996/fd’: Permission denied
find: ‘/proc/996/fdinfo’: Permission denied
find: ‘/proc/996/ns’: Permission denied
find: ‘/proc/1093/task/1093/fd’: Permission denied
find: ‘/proc/1093/task/1093/fdinfo’: Permission denied
find: ‘/proc/1093/task/1093/ns’: Permission denied
find: ‘/proc/1093/fd’: Permission denied
find: ‘/proc/1093/fdinfo’: Permission denied
find: ‘/proc/1093/ns’: Permission denied
find: ‘/proc/1122/task/1122/fd’: Permission denied
find: ‘/proc/1122/task/1122/fdinfo’: Permission denied
find: ‘/proc/1122/task/1122/ns’: Permission denied
find: ‘/proc/1122/fd’: Permission denied
find: ‘/proc/1122/fdinfo’: Permission denied
find: ‘/proc/1122/ns’: Permission denied
find: ‘/proc/1123/task/1123/fd’: Permission denied
find: ‘/proc/1123/task/1123/fdinfo’: Permission denied
find: ‘/proc/1123/task/1123/ns’: Permission denied
find: ‘/proc/1123/fd’: Permission denied
find: ‘/proc/1123/fdinfo’: Permission denied
find: ‘/proc/1123/ns’: Permission denied
find: ‘/proc/1124/task/1124/fd’: Permission denied
find: ‘/proc/1124/task/1124/fdinfo’: Permission denied
find: ‘/proc/1124/task/1124/ns’: Permission denied
find: ‘/proc/1124/task/1308/fd’: Permission denied
find: ‘/proc/1124/task/1308/fdinfo’: Permission denied
find: ‘/proc/1124/task/1308/ns’: Permission denied
find: ‘/proc/1124/task/1309/fd’: Permission denied
find: ‘/proc/1124/task/1309/fdinfo’: Permission denied
find: ‘/proc/1124/task/1309/ns’: Permission denied
find: ‘/proc/1124/task/1310/fd’: Permission denied
find: ‘/proc/1124/task/1310/fdinfo’: Permission denied
find: ‘/proc/1124/task/1310/ns’: Permission denied
find: ‘/proc/1124/task/1311/fd’: Permission denied
find: ‘/proc/1124/task/1311/fdinfo’: Permission denied
find: ‘/proc/1124/task/1311/ns’: Permission denied
find: ‘/proc/1124/task/1312/fd’: Permission denied
find: ‘/proc/1124/task/1312/fdinfo’: Permission denied
find: ‘/proc/1124/task/1312/ns’: Permission denied
find: ‘/proc/1124/task/1313/fd’: Permission denied
find: ‘/proc/1124/task/1313/fdinfo’: Permission denied
find: ‘/proc/1124/task/1313/ns’: Permission denied
find: ‘/proc/1124/task/1314/fd’: Permission denied
find: ‘/proc/1124/task/1314/fdinfo’: Permission denied
find: ‘/proc/1124/task/1314/ns’: Permission denied
find: ‘/proc/1124/task/1315/fd’: Permission denied
find: ‘/proc/1124/task/1315/fdinfo’: Permission denied
find: ‘/proc/1124/task/1315/ns’: Permission denied
find: ‘/proc/1124/task/1316/fd’: Permission denied
find: ‘/proc/1124/task/1316/fdinfo’: Permission denied
find: ‘/proc/1124/task/1316/ns’: Permission denied
find: ‘/proc/1124/task/1317/fd’: Permission denied
find: ‘/proc/1124/task/1317/fdinfo’: Permission denied
find: ‘/proc/1124/task/1317/ns’: Permission denied
find: ‘/proc/1124/task/1445/fd’: Permission denied
find: ‘/proc/1124/task/1445/fdinfo’: Permission denied
find: ‘/proc/1124/task/1445/ns’: Permission denied
find: ‘/proc/1124/task/1446/fd’: Permission denied
find: ‘/proc/1124/task/1446/fdinfo’: Permission denied
find: ‘/proc/1124/task/1446/ns’: Permission denied
find: ‘/proc/1124/task/1447/fd’: Permission denied
find: ‘/proc/1124/task/1447/fdinfo’: Permission denied
find: ‘/proc/1124/task/1447/ns’: Permission denied
find: ‘/proc/1124/task/1448/fd’: Permission denied
find: ‘/proc/1124/task/1448/fdinfo’: Permission denied
find: ‘/proc/1124/task/1448/ns’: Permission denied
find: ‘/proc/1124/task/1466/fd’: Permission denied
find: ‘/proc/1124/task/1466/fdinfo’: Permission denied
find: ‘/proc/1124/task/1466/ns’: Permission denied
find: ‘/proc/1124/task/1535/fd’: Permission denied
find: ‘/proc/1124/task/1535/fdinfo’: Permission denied
find: ‘/proc/1124/task/1535/ns’: Permission denied
find: ‘/proc/1124/fd’: Permission denied
find: ‘/proc/1124/fdinfo’: Permission denied
find: ‘/proc/1124/ns’: Permission denied
find: ‘/proc/1126/task/1126/fd’: Permission denied
find: ‘/proc/1126/task/1126/fdinfo’: Permission denied
find: ‘/proc/1126/task/1126/ns’: Permission denied
find: ‘/proc/1126/fd’: Permission denied
find: ‘/proc/1126/fdinfo’: Permission denied
find: ‘/proc/1126/ns’: Permission denied
find: ‘/proc/1127/task/1127/fd’: Permission denied
find: ‘/proc/1127/task/1127/fdinfo’: Permission denied
find: ‘/proc/1127/task/1127/ns’: Permission denied
find: ‘/proc/1127/fd’: Permission denied
find: ‘/proc/1127/fdinfo’: Permission denied
find: ‘/proc/1127/ns’: Permission denied
find: ‘/proc/1128/task/1128/fd’: Permission denied
find: ‘/proc/1128/task/1128/fdinfo’: Permission denied
find: ‘/proc/1128/task/1128/ns’: Permission denied
find: ‘/proc/1128/fd’: Permission denied
find: ‘/proc/1128/fdinfo’: Permission denied
find: ‘/proc/1128/ns’: Permission denied
find: ‘/proc/1129/task/1129/fd’: Permission denied
find: ‘/proc/1129/task/1129/fdinfo’: Permission denied
find: ‘/proc/1129/task/1129/ns’: Permission denied
find: ‘/proc/1129/task/1229/fd’: Permission denied
find: ‘/proc/1129/task/1229/fdinfo’: Permission denied
find: ‘/proc/1129/task/1229/ns’: Permission denied
find: ‘/proc/1129/task/1321/fd’: Permission denied
find: ‘/proc/1129/task/1321/fdinfo’: Permission denied
find: ‘/proc/1129/task/1321/ns’: Permission denied
find: ‘/proc/1129/fd’: Permission denied
find: ‘/proc/1129/fdinfo’: Permission denied
find: ‘/proc/1129/ns’: Permission denied
find: ‘/proc/1147/task/1147/fd’: Permission denied
find: ‘/proc/1147/task/1147/fdinfo’: Permission denied
find: ‘/proc/1147/task/1147/ns’: Permission denied
find: ‘/proc/1147/task/1149/fd’: Permission denied
find: ‘/proc/1147/task/1149/fdinfo’: Permission denied
find: ‘/proc/1147/task/1149/ns’: Permission denied
find: ‘/proc/1147/fd’: Permission denied
find: ‘/proc/1147/fdinfo’: Permission denied
find: ‘/proc/1147/ns’: Permission denied
find: ‘/proc/1155/task/1155/fd’: Permission denied
find: ‘/proc/1155/task/1155/fdinfo’: Permission denied
find: ‘/proc/1155/task/1155/ns’: Permission denied
find: ‘/proc/1155/fd’: Permission denied
find: ‘/proc/1155/fdinfo’: Permission denied
find: ‘/proc/1155/ns’: Permission denied
find: ‘/proc/1156/task/1156/fd’: Permission denied
find: ‘/proc/1156/task/1156/fdinfo’: Permission denied
find: ‘/proc/1156/task/1156/ns’: Permission denied
find: ‘/proc/1156/fd’: Permission denied
find: ‘/proc/1156/fdinfo’: Permission denied
find: ‘/proc/1156/ns’: Permission denied
find: ‘/proc/1158/task/1158/fd’: Permission denied
find: ‘/proc/1158/task/1158/fdinfo’: Permission denied
find: ‘/proc/1158/task/1158/ns’: Permission denied
find: ‘/proc/1158/fd’: Permission denied
find: ‘/proc/1158/fdinfo’: Permission denied
find: ‘/proc/1158/ns’: Permission denied
find: ‘/proc/1195/task/1195/fd’: Permission denied
find: ‘/proc/1195/task/1195/fdinfo’: Permission denied
find: ‘/proc/1195/task/1195/ns’: Permission denied
find: ‘/proc/1195/fd’: Permission denied
find: ‘/proc/1195/fdinfo’: Permission denied
find: ‘/proc/1195/ns’: Permission denied
find: ‘/proc/1285/task/1285/fd’: Permission denied
find: ‘/proc/1285/task/1285/fdinfo’: Permission denied
find: ‘/proc/1285/task/1285/ns’: Permission denied
find: ‘/proc/1285/fd’: Permission denied
find: ‘/proc/1285/fdinfo’: Permission denied
find: ‘/proc/1285/ns’: Permission denied
find: ‘/proc/1286/task/1286/fd’: Permission denied
find: ‘/proc/1286/task/1286/fdinfo’: Permission denied
find: ‘/proc/1286/task/1286/ns’: Permission denied
find: ‘/proc/1286/fd’: Permission denied
find: ‘/proc/1286/fdinfo’: Permission denied
find: ‘/proc/1286/ns’: Permission denied
find: ‘/proc/1287/task/1287/fd’: Permission denied
find: ‘/proc/1287/task/1287/fdinfo’: Permission denied
find: ‘/proc/1287/task/1287/ns’: Permission denied
find: ‘/proc/1287/fd’: Permission denied
find: ‘/proc/1287/fdinfo’: Permission denied
find: ‘/proc/1287/ns’: Permission denied
find: ‘/proc/1288/task/1288/fd’: Permission denied
find: ‘/proc/1288/task/1288/fdinfo’: Permission denied
find: ‘/proc/1288/task/1288/ns’: Permission denied
find: ‘/proc/1288/fd’: Permission denied
find: ‘/proc/1288/fdinfo’: Permission denied
find: ‘/proc/1288/ns’: Permission denied
find: ‘/proc/1289/task/1289/fd’: Permission denied
find: ‘/proc/1289/task/1289/fdinfo’: Permission denied
find: ‘/proc/1289/task/1289/ns’: Permission denied
find: ‘/proc/1289/fd’: Permission denied
find: ‘/proc/1289/fdinfo’: Permission denied
find: ‘/proc/1289/ns’: Permission denied
find: ‘/proc/1290/task/1290/fd’: Permission denied
find: ‘/proc/1290/task/1290/fdinfo’: Permission denied
find: ‘/proc/1290/task/1290/ns’: Permission denied
find: ‘/proc/1290/fd’: Permission denied
find: ‘/proc/1290/fdinfo’: Permission denied
find: ‘/proc/1290/ns’: Permission denied
find: ‘/proc/1291/task/1291/fd’: Permission denied
find: ‘/proc/1291/task/1291/fdinfo’: Permission denied
find: ‘/proc/1291/task/1291/ns’: Permission denied
find: ‘/proc/1291/fd’: Permission denied
find: ‘/proc/1291/fdinfo’: Permission denied
find: ‘/proc/1291/ns’: Permission denied
find: ‘/proc/1292/task/1292/fd’: Permission denied
find: ‘/proc/1292/task/1292/fdinfo’: Permission denied
find: ‘/proc/1292/task/1292/ns’: Permission denied
find: ‘/proc/1292/fd’: Permission denied
find: ‘/proc/1292/fdinfo’: Permission denied
find: ‘/proc/1292/ns’: Permission denied
find: ‘/proc/1293/task/1293/fd’: Permission denied
find: ‘/proc/1293/task/1293/fdinfo’: Permission denied
find: ‘/proc/1293/task/1293/ns’: Permission denied
find: ‘/proc/1293/fd’: Permission denied
find: ‘/proc/1293/fdinfo’: Permission denied
find: ‘/proc/1293/ns’: Permission denied
find: ‘/proc/1294/task/1294/fd’: Permission denied
find: ‘/proc/1294/task/1294/fdinfo’: Permission denied
find: ‘/proc/1294/task/1294/ns’: Permission denied
find: ‘/proc/1294/fd’: Permission denied
find: ‘/proc/1294/fdinfo’: Permission denied
find: ‘/proc/1294/ns’: Permission denied
find: ‘/proc/1295/task/1295/fd’: Permission denied
find: ‘/proc/1295/task/1295/fdinfo’: Permission denied
find: ‘/proc/1295/task/1295/ns’: Permission denied
find: ‘/proc/1295/fd’: Permission denied
find: ‘/proc/1295/fdinfo’: Permission denied
find: ‘/proc/1295/ns’: Permission denied
find: ‘/proc/1320/task/1320/fd’: Permission denied
find: ‘/proc/1320/task/1320/fdinfo’: Permission denied
find: ‘/proc/1320/task/1320/ns’: Permission denied
find: ‘/proc/1320/fd’: Permission denied
find: ‘/proc/1320/fdinfo’: Permission denied
find: ‘/proc/1320/ns’: Permission denied
find: ‘/proc/1333/task/1333/fd’: Permission denied
find: ‘/proc/1333/task/1333/fdinfo’: Permission denied
find: ‘/proc/1333/task/1333/ns’: Permission denied
find: ‘/proc/1333/fd’: Permission denied
find: ‘/proc/1333/fdinfo’: Permission denied
find: ‘/proc/1333/ns’: Permission denied
find: ‘/proc/1497/task/1497/fd’: Permission denied
find: ‘/proc/1497/task/1497/fdinfo’: Permission denied
find: ‘/proc/1497/task/1497/ns’: Permission denied
find: ‘/proc/1497/fd’: Permission denied
find: ‘/proc/1497/fdinfo’: Permission denied
find: ‘/proc/1497/ns’: Permission denied
find: ‘/proc/1574/task/1574/fd’: Permission denied
find: ‘/proc/1574/task/1574/fdinfo’: Permission denied
find: ‘/proc/1574/task/1574/ns’: Permission denied
find: ‘/proc/1574/fd’: Permission denied
find: ‘/proc/1574/fdinfo’: Permission denied
find: ‘/proc/1574/ns’: Permission denied
find: ‘/proc/1656/task/1656/fd’: Permission denied
find: ‘/proc/1656/task/1656/fdinfo’: Permission denied
find: ‘/proc/1656/task/1656/ns’: Permission denied
find: ‘/proc/1656/task/1665/fd’: Permission denied
find: ‘/proc/1656/task/1665/fdinfo’: Permission denied
find: ‘/proc/1656/task/1665/ns’: Permission denied
find: ‘/proc/1656/fd’: Permission denied
find: ‘/proc/1656/fdinfo’: Permission denied
find: ‘/proc/1656/ns’: Permission denied
find: ‘/proc/1790/task/1790/fd’: Permission denied
find: ‘/proc/1790/task/1790/fdinfo’: Permission denied
find: ‘/proc/1790/task/1790/ns’: Permission denied
find: ‘/proc/1790/task/1820/fd’: Permission denied
find: ‘/proc/1790/task/1820/fdinfo’: Permission denied
find: ‘/proc/1790/task/1820/ns’: Permission denied
find: ‘/proc/1790/task/1826/fd’: Permission denied
find: ‘/proc/1790/task/1826/fdinfo’: Permission denied
find: ‘/proc/1790/task/1826/ns’: Permission denied
find: ‘/proc/1790/task/1827/fd’: Permission denied
find: ‘/proc/1790/task/1827/fdinfo’: Permission denied
find: ‘/proc/1790/task/1827/ns’: Permission denied
find: ‘/proc/1790/task/1828/fd’: Permission denied
find: ‘/proc/1790/task/1828/fdinfo’: Permission denied
find: ‘/proc/1790/task/1828/ns’: Permission denied
find: ‘/proc/1790/task/1829/fd’: Permission denied
find: ‘/proc/1790/task/1829/fdinfo’: Permission denied
find: ‘/proc/1790/task/1829/ns’: Permission denied
find: ‘/proc/1790/task/1830/fd’: Permission denied
find: ‘/proc/1790/task/1830/fdinfo’: Permission denied
find: ‘/proc/1790/task/1830/ns’: Permission denied
find: ‘/proc/1790/task/1831/fd’: Permission denied
find: ‘/proc/1790/task/1831/fdinfo’: Permission denied
find: ‘/proc/1790/task/1831/ns’: Permission denied
find: ‘/proc/1790/task/1832/fd’: Permission denied
find: ‘/proc/1790/task/1832/fdinfo’: Permission denied
find: ‘/proc/1790/task/1832/ns’: Permission denied
find: ‘/proc/1790/task/1833/fd’: Permission denied
find: ‘/proc/1790/task/1833/fdinfo’: Permission denied
find: ‘/proc/1790/task/1833/ns’: Permission denied
find: ‘/proc/1790/task/1834/fd’: Permission denied
find: ‘/proc/1790/task/1834/fdinfo’: Permission denied
find: ‘/proc/1790/task/1834/ns’: Permission denied
find: ‘/proc/1790/task/1835/fd’: Permission denied
find: ‘/proc/1790/task/1835/fdinfo’: Permission denied
find: ‘/proc/1790/task/1835/ns’: Permission denied
find: ‘/proc/1790/task/1836/fd’: Permission denied
find: ‘/proc/1790/task/1836/fdinfo’: Permission denied
find: ‘/proc/1790/task/1836/ns’: Permission denied
find: ‘/proc/1790/task/1837/fd’: Permission denied
find: ‘/proc/1790/task/1837/fdinfo’: Permission denied
find: ‘/proc/1790/task/1837/ns’: Permission denied
find: ‘/proc/1790/task/1838/fd’: Permission denied
find: ‘/proc/1790/task/1838/fdinfo’: Permission denied
find: ‘/proc/1790/task/1838/ns’: Permission denied
find: ‘/proc/1790/task/1839/fd’: Permission denied
find: ‘/proc/1790/task/1839/fdinfo’: Permission denied
find: ‘/proc/1790/task/1839/ns’: Permission denied
find: ‘/proc/1790/task/1840/fd’: Permission denied
find: ‘/proc/1790/task/1840/fdinfo’: Permission denied
find: ‘/proc/1790/task/1840/ns’: Permission denied
find: ‘/proc/1790/task/1841/fd’: Permission denied
find: ‘/proc/1790/task/1841/fdinfo’: Permission denied
find: ‘/proc/1790/task/1841/ns’: Permission denied
find: ‘/proc/1790/task/1842/fd’: Permission denied
find: ‘/proc/1790/task/1842/fdinfo’: Permission denied
find: ‘/proc/1790/task/1842/ns’: Permission denied
find: ‘/proc/1790/task/1843/fd’: Permission denied
find: ‘/proc/1790/task/1843/fdinfo’: Permission denied
find: ‘/proc/1790/task/1843/ns’: Permission denied
find: ‘/proc/1790/task/1844/fd’: Permission denied
find: ‘/proc/1790/task/1844/fdinfo’: Permission denied
find: ‘/proc/1790/task/1844/ns’: Permission denied
find: ‘/proc/1790/task/1845/fd’: Permission denied
find: ‘/proc/1790/task/1845/fdinfo’: Permission denied
find: ‘/proc/1790/task/1845/ns’: Permission denied
find: ‘/proc/1790/task/1846/fd’: Permission denied
find: ‘/proc/1790/task/1846/fdinfo’: Permission denied
find: ‘/proc/1790/task/1846/ns’: Permission denied
find: ‘/proc/1790/task/1847/fd’: Permission denied
find: ‘/proc/1790/task/1847/fdinfo’: Permission denied
find: ‘/proc/1790/task/1847/ns’: Permission denied
find: ‘/proc/1790/task/1848/fd’: Permission denied
find: ‘/proc/1790/task/1848/fdinfo’: Permission denied
find: ‘/proc/1790/task/1848/ns’: Permission denied
find: ‘/proc/1790/task/1849/fd’: Permission denied
find: ‘/proc/1790/task/1849/fdinfo’: Permission denied
find: ‘/proc/1790/task/1849/ns’: Permission denied
find: ‘/proc/1790/task/1850/fd’: Permission denied
find: ‘/proc/1790/task/1850/fdinfo’: Permission denied
find: ‘/proc/1790/task/1850/ns’: Permission denied
find: ‘/proc/1790/task/1851/fd’: Permission denied
find: ‘/proc/1790/task/1851/fdinfo’: Permission denied
find: ‘/proc/1790/task/1851/ns’: Permission denied
find: ‘/proc/1790/task/1852/fd’: Permission denied
find: ‘/proc/1790/task/1852/fdinfo’: Permission denied
find: ‘/proc/1790/task/1852/ns’: Permission denied
find: ‘/proc/1790/task/1853/fd’: Permission denied
find: ‘/proc/1790/task/1853/fdinfo’: Permission denied
find: ‘/proc/1790/task/1853/ns’: Permission denied
find: ‘/proc/1790/task/1854/fd’: Permission denied
find: ‘/proc/1790/task/1854/fdinfo’: Permission denied
find: ‘/proc/1790/task/1854/ns’: Permission denied
find: ‘/proc/1790/task/1855/fd’: Permission denied
find: ‘/proc/1790/task/1855/fdinfo’: Permission denied
find: ‘/proc/1790/task/1855/ns’: Permission denied
find: ‘/proc/1790/task/1856/fd’: Permission denied
find: ‘/proc/1790/task/1856/fdinfo’: Permission denied
find: ‘/proc/1790/task/1856/ns’: Permission denied
find: ‘/proc/1790/task/1857/fd’: Permission denied
find: ‘/proc/1790/task/1857/fdinfo’: Permission denied
find: ‘/proc/1790/task/1857/ns’: Permission denied
find: ‘/proc/1790/task/1858/fd’: Permission denied
find: ‘/proc/1790/task/1858/fdinfo’: Permission denied
find: ‘/proc/1790/task/1858/ns’: Permission denied
find: ‘/proc/1790/task/1859/fd’: Permission denied
find: ‘/proc/1790/task/1859/fdinfo’: Permission denied
find: ‘/proc/1790/task/1859/ns’: Permission denied
find: ‘/proc/1790/task/1860/fd’: Permission denied
find: ‘/proc/1790/task/1860/fdinfo’: Permission denied
find: ‘/proc/1790/task/1860/ns’: Permission denied
find: ‘/proc/1790/task/1861/fd’: Permission denied
find: ‘/proc/1790/task/1861/fdinfo’: Permission denied
find: ‘/proc/1790/task/1861/ns’: Permission denied
find: ‘/proc/1790/task/1862/fd’: Permission denied
find: ‘/proc/1790/task/1862/fdinfo’: Permission denied
find: ‘/proc/1790/task/1862/ns’: Permission denied
find: ‘/proc/1790/task/1863/fd’: Permission denied
find: ‘/proc/1790/task/1863/fdinfo’: Permission denied
find: ‘/proc/1790/task/1863/ns’: Permission denied
find: ‘/proc/1790/task/1864/fd’: Permission denied
find: ‘/proc/1790/task/1864/fdinfo’: Permission denied
find: ‘/proc/1790/task/1864/ns’: Permission denied
find: ‘/proc/1790/task/1865/fd’: Permission denied
find: ‘/proc/1790/task/1865/fdinfo’: Permission denied
find: ‘/proc/1790/task/1865/ns’: Permission denied
find: ‘/proc/1790/task/1866/fd’: Permission denied
find: ‘/proc/1790/task/1866/fdinfo’: Permission denied
find: ‘/proc/1790/task/1866/ns’: Permission denied
find: ‘/proc/1790/task/1867/fd’: Permission denied
find: ‘/proc/1790/task/1867/fdinfo’: Permission denied
find: ‘/proc/1790/task/1867/ns’: Permission denied
find: ‘/proc/1790/task/1868/fd’: Permission denied
find: ‘/proc/1790/task/1868/fdinfo’: Permission denied
find: ‘/proc/1790/task/1868/ns’: Permission denied
find: ‘/proc/1790/task/1869/fd’: Permission denied
find: ‘/proc/1790/task/1869/fdinfo’: Permission denied
find: ‘/proc/1790/task/1869/ns’: Permission denied
find: ‘/proc/1790/task/1870/fd’: Permission denied
find: ‘/proc/1790/task/1870/fdinfo’: Permission denied
find: ‘/proc/1790/task/1870/ns’: Permission denied
find: ‘/proc/1790/task/1871/fd’: Permission denied
find: ‘/proc/1790/task/1871/fdinfo’: Permission denied
find: ‘/proc/1790/task/1871/ns’: Permission denied
find: ‘/proc/1790/task/1872/fd’: Permission denied
find: ‘/proc/1790/task/1872/fdinfo’: Permission denied
find: ‘/proc/1790/task/1872/ns’: Permission denied
find: ‘/proc/1790/task/1873/fd’: Permission denied
find: ‘/proc/1790/task/1873/fdinfo’: Permission denied
find: ‘/proc/1790/task/1873/ns’: Permission denied
find: ‘/proc/1790/task/1874/fd’: Permission denied
find: ‘/proc/1790/task/1874/fdinfo’: Permission denied
find: ‘/proc/1790/task/1874/ns’: Permission denied
find: ‘/proc/1790/task/1875/fd’: Permission denied
find: ‘/proc/1790/task/1875/fdinfo’: Permission denied
find: ‘/proc/1790/task/1875/ns’: Permission denied
find: ‘/proc/1790/task/1876/fd’: Permission denied
find: ‘/proc/1790/task/1876/fdinfo’: Permission denied
find: ‘/proc/1790/task/1876/ns’: Permission denied
find: ‘/proc/1790/task/1877/fd’: Permission denied
find: ‘/proc/1790/task/1877/fdinfo’: Permission denied
find: ‘/proc/1790/task/1877/ns’: Permission denied
find: ‘/proc/1790/task/1878/fd’: Permission denied
find: ‘/proc/1790/task/1878/fdinfo’: Permission denied
find: ‘/proc/1790/task/1878/ns’: Permission denied
find: ‘/proc/1790/task/1879/fd’: Permission denied
find: ‘/proc/1790/task/1879/fdinfo’: Permission denied
find: ‘/proc/1790/task/1879/ns’: Permission denied
find: ‘/proc/1790/task/1880/fd’: Permission denied
find: ‘/proc/1790/task/1880/fdinfo’: Permission denied
find: ‘/proc/1790/task/1880/ns’: Permission denied
find: ‘/proc/1790/task/1881/fd’: Permission denied
find: ‘/proc/1790/task/1881/fdinfo’: Permission denied
find: ‘/proc/1790/task/1881/ns’: Permission denied
find: ‘/proc/1790/task/1882/fd’: Permission denied
find: ‘/proc/1790/task/1882/fdinfo’: Permission denied
find: ‘/proc/1790/task/1882/ns’: Permission denied
find: ‘/proc/1790/task/1883/fd’: Permission denied
find: ‘/proc/1790/task/1883/fdinfo’: Permission denied
find: ‘/proc/1790/task/1883/ns’: Permission denied
find: ‘/proc/1790/task/1884/fd’: Permission denied
find: ‘/proc/1790/task/1884/fdinfo’: Permission denied
find: ‘/proc/1790/task/1884/ns’: Permission denied
find: ‘/proc/1790/task/1885/fd’: Permission denied
find: ‘/proc/1790/task/1885/fdinfo’: Permission denied
find: ‘/proc/1790/task/1885/ns’: Permission denied
find: ‘/proc/1790/task/1886/fd’: Permission denied
find: ‘/proc/1790/task/1886/fdinfo’: Permission denied
find: ‘/proc/1790/task/1886/ns’: Permission denied
find: ‘/proc/1790/task/1897/fd’: Permission denied
find: ‘/proc/1790/task/1897/fdinfo’: Permission denied
find: ‘/proc/1790/task/1897/ns’: Permission denied
find: ‘/proc/1790/task/1899/fd’: Permission denied
find: ‘/proc/1790/task/1899/fdinfo’: Permission denied
find: ‘/proc/1790/task/1899/ns’: Permission denied
find: ‘/proc/1790/fd’: Permission denied
find: ‘/proc/1790/fdinfo’: Permission denied
find: ‘/proc/1790/ns’: Permission denied
find: ‘/proc/1902/task/1902/fd’: Permission denied
find: ‘/proc/1902/task/1902/fdinfo’: Permission denied
find: ‘/proc/1902/task/1902/ns’: Permission denied
find: ‘/proc/1902/task/1936/fd’: Permission denied
find: ‘/proc/1902/task/1936/fdinfo’: Permission denied
find: ‘/proc/1902/task/1936/ns’: Permission denied
find: ‘/proc/1902/task/1937/fd’: Permission denied
find: ‘/proc/1902/task/1937/fdinfo’: Permission denied
find: ‘/proc/1902/task/1937/ns’: Permission denied
find: ‘/proc/1902/task/1938/fd’: Permission denied
find: ‘/proc/1902/task/1938/fdinfo’: Permission denied
find: ‘/proc/1902/task/1938/ns’: Permission denied
find: ‘/proc/1902/fd’: Permission denied
find: ‘/proc/1902/fdinfo’: Permission denied
find: ‘/proc/1902/ns’: Permission denied
find: ‘/proc/1934/task/1934/fd’: Permission denied
find: ‘/proc/1934/task/1934/fdinfo’: Permission denied
find: ‘/proc/1934/task/1934/ns’: Permission denied
find: ‘/proc/1934/fd’: Permission denied
find: ‘/proc/1934/fdinfo’: Permission denied
find: ‘/proc/1934/ns’: Permission denied
find: ‘/proc/1939/task/1939/fd’: Permission denied
find: ‘/proc/1939/task/1939/fdinfo’: Permission denied
find: ‘/proc/1939/task/1939/ns’: Permission denied
find: ‘/proc/1939/fd’: Permission denied
find: ‘/proc/1939/fdinfo’: Permission denied
find: ‘/proc/1939/ns’: Permission denied
find: ‘/proc/1940/task/1940/fd’: Permission denied
find: ‘/proc/1940/task/1940/fdinfo’: Permission denied
find: ‘/proc/1940/task/1940/ns’: Permission denied
find: ‘/proc/1940/task/1943/fd’: Permission denied
find: ‘/proc/1940/task/1943/fdinfo’: Permission denied
find: ‘/proc/1940/task/1943/ns’: Permission denied
find: ‘/proc/1940/task/1944/fd’: Permission denied
find: ‘/proc/1940/task/1944/fdinfo’: Permission denied
find: ‘/proc/1940/task/1944/ns’: Permission denied
find: ‘/proc/1940/task/1945/fd’: Permission denied
find: ‘/proc/1940/task/1945/fdinfo’: Permission denied
find: ‘/proc/1940/task/1945/ns’: Permission denied
find: ‘/proc/1940/fd’: Permission denied
find: ‘/proc/1940/fdinfo’: Permission denied
find: ‘/proc/1940/ns’: Permission denied
find: ‘/proc/1988/task/1988/fd’: Permission denied
find: ‘/proc/1988/task/1988/fdinfo’: Permission denied
find: ‘/proc/1988/task/1988/ns’: Permission denied
find: ‘/proc/1988/task/1989/fd’: Permission denied
find: ‘/proc/1988/task/1989/fdinfo’: Permission denied
find: ‘/proc/1988/task/1989/ns’: Permission denied
find: ‘/proc/1988/task/1990/fd’: Permission denied
find: ‘/proc/1988/task/1990/fdinfo’: Permission denied
find: ‘/proc/1988/task/1990/ns’: Permission denied
find: ‘/proc/1988/fd’: Permission denied
find: ‘/proc/1988/fdinfo’: Permission denied
find: ‘/proc/1988/ns’: Permission denied
find: ‘/proc/2300/task/2300/fd’: Permission denied
find: ‘/proc/2300/task/2300/fdinfo’: Permission denied
find: ‘/proc/2300/task/2300/ns’: Permission denied
find: ‘/proc/2300/task/2301/fd’: Permission denied
find: ‘/proc/2300/task/2301/fdinfo’: Permission denied
find: ‘/proc/2300/task/2301/ns’: Permission denied
find: ‘/proc/2300/task/2302/fd’: Permission denied
find: ‘/proc/2300/task/2302/fdinfo’: Permission denied
find: ‘/proc/2300/task/2302/ns’: Permission denied
find: ‘/proc/2300/fd’: Permission denied
find: ‘/proc/2300/fdinfo’: Permission denied
find: ‘/proc/2300/ns’: Permission denied
find: ‘/proc/2323/task/2323/fd’: Permission denied
find: ‘/proc/2323/task/2323/fdinfo’: Permission denied
find: ‘/proc/2323/task/2323/ns’: Permission denied
find: ‘/proc/2323/task/2324/fd’: Permission denied
find: ‘/proc/2323/task/2324/fdinfo’: Permission denied
find: ‘/proc/2323/task/2324/ns’: Permission denied
find: ‘/proc/2323/fd’: Permission denied
find: ‘/proc/2323/fdinfo’: Permission denied
find: ‘/proc/2323/ns’: Permission denied
find: ‘/proc/2366/task/2366/fd’: Permission denied
find: ‘/proc/2366/task/2366/fdinfo’: Permission denied
find: ‘/proc/2366/task/2366/ns’: Permission denied
find: ‘/proc/2366/task/2368/fd’: Permission denied
find: ‘/proc/2366/task/2368/fdinfo’: Permission denied
find: ‘/proc/2366/task/2368/ns’: Permission denied
find: ‘/proc/2366/task/2439/fd’: Permission denied
find: ‘/proc/2366/task/2439/fdinfo’: Permission denied
find: ‘/proc/2366/task/2439/ns’: Permission denied
find: ‘/proc/2366/task/2440/fd’: Permission denied
find: ‘/proc/2366/task/2440/fdinfo’: Permission denied
find: ‘/proc/2366/task/2440/ns’: Permission denied
find: ‘/proc/2366/task/2441/fd’: Permission denied
find: ‘/proc/2366/task/2441/fdinfo’: Permission denied
find: ‘/proc/2366/task/2441/ns’: Permission denied
find: ‘/proc/2366/task/3054/fd’: Permission denied
find: ‘/proc/2366/task/3054/fdinfo’: Permission denied
find: ‘/proc/2366/task/3054/ns’: Permission denied
find: ‘/proc/2366/fd’: Permission denied
find: ‘/proc/2366/fdinfo’: Permission denied
find: ‘/proc/2366/ns’: Permission denied
find: ‘/proc/2417/task/2417/fd’: Permission denied
find: ‘/proc/2417/task/2417/fdinfo’: Permission denied
find: ‘/proc/2417/task/2417/ns’: Permission denied
find: ‘/proc/2417/fd’: Permission denied
find: ‘/proc/2417/fdinfo’: Permission denied
find: ‘/proc/2417/ns’: Permission denied
find: ‘/proc/2644/task/2644/fd’: Permission denied
find: ‘/proc/2644/task/2644/fdinfo’: Permission denied
find: ‘/proc/2644/task/2644/ns’: Permission denied
find: ‘/proc/2644/task/2646/fd’: Permission denied
find: ‘/proc/2644/task/2646/fdinfo’: Permission denied
find: ‘/proc/2644/task/2646/ns’: Permission denied
find: ‘/proc/2644/task/2860/fd’: Permission denied
find: ‘/proc/2644/task/2860/fdinfo’: Permission denied
find: ‘/proc/2644/task/2860/ns’: Permission denied
find: ‘/proc/2644/fd’: Permission denied
find: ‘/proc/2644/fdinfo’: Permission denied
find: ‘/proc/2644/ns’: Permission denied
find: ‘/proc/2645/task/2645/fd’: Permission denied
find: ‘/proc/2645/task/2645/fdinfo’: Permission denied
find: ‘/proc/2645/task/2645/ns’: Permission denied
find: ‘/proc/2645/fd’: Permission denied
find: ‘/proc/2645/fdinfo’: Permission denied
find: ‘/proc/2645/ns’: Permission denied
find: ‘/proc/3703/task/3703/fd’: Permission denied
find: ‘/proc/3703/task/3703/fdinfo’: Permission denied
find: ‘/proc/3703/task/3703/ns’: Permission denied
find: ‘/proc/3703/fd’: Permission denied
find: ‘/proc/3703/fdinfo’: Permission denied
find: ‘/proc/3703/ns’: Permission denied
find: ‘/proc/4975/task/4975/fd’: Permission denied
find: ‘/proc/4975/task/4975/fdinfo’: Permission denied
find: ‘/proc/4975/task/4975/ns’: Permission denied
find: ‘/proc/4975/fd’: Permission denied
find: ‘/proc/4975/fdinfo’: Permission denied
find: ‘/proc/4975/ns’: Permission denied
find: ‘/proc/4999/task/4999/fd’: Permission denied
find: ‘/proc/4999/task/4999/fdinfo’: Permission denied
find: ‘/proc/4999/task/4999/ns’: Permission denied
find: ‘/proc/4999/fd’: Permission denied
find: ‘/proc/4999/fdinfo’: Permission denied
find: ‘/proc/4999/ns’: Permission denied
find: ‘/proc/7011/task/7011/fd’: Permission denied
find: ‘/proc/7011/task/7011/fdinfo’: Permission denied
find: ‘/proc/7011/task/7011/ns’: Permission denied
find: ‘/proc/7011/fd’: Permission denied
find: ‘/proc/7011/fdinfo’: Permission denied
find: ‘/proc/7011/ns’: Permission denied
find: ‘/proc/7016/task/7016/fd’: Permission denied
find: ‘/proc/7016/task/7016/fdinfo’: Permission denied
find: ‘/proc/7016/task/7016/ns’: Permission denied
find: ‘/proc/7016/fd’: Permission denied
find: ‘/proc/7016/fdinfo’: Permission denied
find: ‘/proc/7016/ns’: Permission denied
find: ‘/proc/7017/task/7017/fd’: Permission denied
find: ‘/proc/7017/task/7017/fdinfo’: Permission denied
find: ‘/proc/7017/task/7017/ns’: Permission denied
find: ‘/proc/7017/fd’: Permission denied
find: ‘/proc/7017/fdinfo’: Permission denied
find: ‘/proc/7017/ns’: Permission denied
find: ‘/proc/7018/task/7018/fd’: Permission denied
find: ‘/proc/7018/task/7018/fdinfo’: Permission denied
find: ‘/proc/7018/task/7018/ns’: Permission denied
find: ‘/proc/7018/fd’: Permission denied
find: ‘/proc/7018/fdinfo’: Permission denied
find: ‘/proc/7018/ns’: Permission denied
find: ‘/proc/7019/task/7019/fd’: Permission denied
find: ‘/proc/7019/task/7019/fdinfo’: Permission denied
find: ‘/proc/7019/task/7019/ns’: Permission denied
find: ‘/proc/7019/fd’: Permission denied
find: ‘/proc/7019/fdinfo’: Permission denied
find: ‘/proc/7019/ns’: Permission denied
find: ‘/proc/7020/task/7020/fd’: Permission denied
find: ‘/proc/7020/task/7020/fdinfo’: Permission denied
find: ‘/proc/7020/task/7020/ns’: Permission denied
find: ‘/proc/7020/fd’: Permission denied
find: ‘/proc/7020/fdinfo’: Permission denied
find: ‘/proc/7020/ns’: Permission denied
find: ‘/proc/7035/task/7035/fd’: Permission denied
find: ‘/proc/7035/task/7035/fdinfo’: Permission denied
find: ‘/proc/7035/task/7035/ns’: Permission denied
find: ‘/proc/7035/fd’: Permission denied
find: ‘/proc/7035/fdinfo’: Permission denied
find: ‘/proc/7035/ns’: Permission denied
find: ‘/proc/7091/task/7091/fd’: Permission denied
find: ‘/proc/7091/task/7091/fdinfo’: Permission denied
find: ‘/proc/7091/task/7091/ns’: Permission denied
find: ‘/proc/7091/fd’: Permission denied
find: ‘/proc/7091/fdinfo’: Permission denied
find: ‘/proc/7091/ns’: Permission denied
find: ‘/proc/10567/task/10567/fd’: Permission denied
find: ‘/proc/10567/task/10567/fdinfo’: Permission denied
find: ‘/proc/10567/task/10567/ns’: Permission denied
find: ‘/proc/10567/fd’: Permission denied
find: ‘/proc/10567/fdinfo’: Permission denied
find: ‘/proc/10567/ns’: Permission denied
find: ‘/proc/10589/task/10589/fd’: Permission denied
find: ‘/proc/10589/task/10589/fdinfo’: Permission denied
find: ‘/proc/10589/task/10589/ns’: Permission denied
find: ‘/proc/10589/fd’: Permission denied
find: ‘/proc/10589/fdinfo’: Permission denied
find: ‘/proc/10589/ns’: Permission denied
find: ‘/proc/20514/task/20514/fd’: Permission denied
find: ‘/proc/20514/task/20514/fdinfo’: Permission denied
find: ‘/proc/20514/task/20514/ns’: Permission denied
find: ‘/proc/20514/fd’: Permission denied
find: ‘/proc/20514/fdinfo’: Permission denied
find: ‘/proc/20514/ns’: Permission denied
find: ‘/proc/29236/task/29236/fd’: Permission denied
find: ‘/proc/29236/task/29236/fdinfo’: Permission denied
find: ‘/proc/29236/task/29236/ns’: Permission denied
find: ‘/proc/29236/fd’: Permission denied
find: ‘/proc/29236/fdinfo’: Permission denied
find: ‘/proc/29236/ns’: Permission denied
find: ‘/proc/29265/task/29265/fd’: Permission denied
find: ‘/proc/29265/task/29265/fdinfo’: Permission denied
find: ‘/proc/29265/task/29265/ns’: Permission denied
find: ‘/proc/29265/fd’: Permission denied
find: ‘/proc/29265/fdinfo’: Permission denied
find: ‘/proc/29265/ns’: Permission denied
find: ‘/proc/29369/task/29369/fd’: Permission denied
find: ‘/proc/29369/task/29369/fdinfo’: Permission denied
find: ‘/proc/29369/task/29369/ns’: Permission denied
find: ‘/proc/29369/fd’: Permission denied
find: ‘/proc/29369/fdinfo’: Permission denied
find: ‘/proc/29369/ns’: Permission denied
find: ‘/proc/29675/task/29675/fd’: Permission denied
find: ‘/proc/29675/task/29675/fdinfo’: Permission denied
find: ‘/proc/29675/task/29675/ns’: Permission denied
find: ‘/proc/29675/fd’: Permission denied
find: ‘/proc/29675/fdinfo’: Permission denied
find: ‘/proc/29675/ns’: Permission denied
find: ‘/proc/29787/task/29787/fd’: Permission denied
find: ‘/proc/29787/task/29787/fdinfo’: Permission denied
find: ‘/proc/29787/task/29787/ns’: Permission denied
find: ‘/proc/29787/fd’: Permission denied
find: ‘/proc/29787/fdinfo’: Permission denied
find: ‘/proc/29787/ns’: Permission denied
find: ‘/proc/30047/task/30047/fd’: Permission denied
find: ‘/proc/30047/task/30047/fdinfo’: Permission denied
find: ‘/proc/30047/task/30047/ns’: Permission denied
find: ‘/proc/30047/fd’: Permission denied
find: ‘/proc/30047/fdinfo’: Permission denied
find: ‘/proc/30047/ns’: Permission denied
find: ‘/proc/30062/task/30062/fd’: Permission denied
find: ‘/proc/30062/task/30062/fdinfo’: Permission denied
find: ‘/proc/30062/task/30062/ns’: Permission denied
find: ‘/proc/30062/fd’: Permission denied
find: ‘/proc/30062/fdinfo’: Permission denied
find: ‘/proc/30062/ns’: Permission denied
find: ‘/home/server/.config/nautilus-actions’: Permission denied
/home/server/.vnc/passwd
find: ‘/home/benlavery/.ssh’: Permission denied
find: ‘/home/benlavery/.cache’: Permission denied

```

Many thanks for your help so far,

Ben

---

### Post by deathadder on 2012-06-19
I can't see the passwd command in there anywhere which is strange, can you check the status of the passwd package with:
```
dpkg-query -s passwd
```

---

### Post by idoitprone on 2012-06-19
> **forquare said:**
> Many thanks for your reply, deathadder.

My $PATH is as follows:
```
$ echo $PATH
/home/server/perl5/perlbrew/bin:/home/server/perl5/perlbrew/perls/perl-5.15.9/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```Also to note:
```
$ /usr/bin/passwd
-bash: /usr/bin/passwd: No such file or directory
```

note taken
but

did you realize that passwd should be located at

/bin

you should be able to run it

```
/bin/passwd
```
i still wondering why u cant run /bin commands

---

### Post by hwttdz on 2012-06-19
Can you do "find / -iname 'passwd' 2>/dev/null" (just removes any error output to make things a little more legible).  

And I'd do "sudo apt-get install --reinstall passwd".

@idoitprone, passwd is in /usr/bin on my system as well.

---

### Post by forquare on 2012-06-19
passwd package status:
```
$ dpkg-query -s passwd
Package: passwd
Status: install ok installed
Multi-Arch: foreign
Priority: required
Section: admin
Installed-Size: 2000
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: shadow
Version: 1:4.1.4.2+svn3283-3ubuntu5
Replaces: manpages-tr (<< 1.0.5), manpages-zh (<< 1.5.1-1)
Depends: libc6 (>= 2.15), libpam0g (>= 0.99.7.1), libselinux1 (>= 1.32), libpam-modules, debianutils (>= 2.15.2)
Conffiles:
 /etc/default/useradd cc9f9a7713ab62a32cd38363d958f396
 /etc/cron.daily/passwd db990990933b6f56322725223f13c2bc
 /etc/pam.d/passwd eaf2ad85b5ccd06cceb19a3e75f40c63
 /etc/pam.d/chfn 4d466e00a348ba426130664d795e8afa
 /etc/pam.d/chsh a6e9b589e90009334ffd030d819290a6
 /etc/pam.d/chpasswd 9900720564cb4ee98b7da29e2d183cb2
 /etc/pam.d/newusers 1454e29bfa9f2a10836563e76936cea5
Description: change and administer password and group data
 This package includes passwd, chsh, chfn, and many other programs to
 maintain password and group data.
 .
 Shadow passwords are supported.  See /usr/share/doc/passwd/README.Debian
Homepage: http://pkg-shadow.alioth.debian.org/
Original-Maintainer: Shadow package maintainers <pkg-shadow-devel@lists.alioth.debian.org>

```

A quick look in /bin:
```
$ /bin/passwd
-bash: /bin/passwd: No such file or directory
```

I can run /bin commands:
```
$ /bin/bzip2
bzip2: I won't write compressed data to a terminal.
bzip2: For help, type: `bzip2 --help'.
```

Finding passwd, no errors:
```
$ find / -iname 'passwd' 2>/dev/null
/usr/share/lintian/overrides/passwd
/usr/share/doc/passwd
/etc/passwd
/etc/pam.d/passwd
/etc/cron.daily/passwd
/home/server/.vnc/passwd
```

Trying to reinstall passwd:
```
$ sudo apt-get install --reinstall passwd
[sudo] password for server: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 935 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu/ precise/main passwd i386 1:4.1.4.2+svn3283-3ubuntu5 [935 kB]
Fetched 935 kB in 2s (415 kB/s) 
(Reading database ... 254758 files and directories currently installed.)
Preparing to replace passwd 1:4.1.4.2+svn3283-3ubuntu5 (using .../passwd_1%3a4.1.4.2+svn3283-3ubuntu5_i386.deb) ...
Unpacking replacement passwd ...
Processing triggers for man-db ...
Setting up passwd (1:4.1.4.2+svn3283-3ubuntu5) ...
$
$
$ passwd
Changing password for server.
(current) UNIX password: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
```

It works :D  Thank you so much!

---

### Post by drmrgd on 2012-06-19
Wow!  That's totally bizarre.  Glad to see that a simple re-install works.  I hope that also fixes 'shutdown' and 'reboot' for you.

---

