---
title: "evince issues after upgrade to 9.10 karmic koala"
date: 2009-11-02
forum: General Help
---

### Post by sharky6000 on 2009-11-02
Hello, 

evince is acting strange after the upgrade to 9.10 Karmic Koala. 

It seems like it's not saving its state properly; it doesn't save the zoom level from the last time it was opened, but more importantly: it doesn't save any icons onto the tool bar. The result is that every time it opens PDFs, it does so at a very low zoom level and with an empty toolbar. 

The output indicates permission issues, but everything seems to look fine (see below). I use Xfce, but the problem occurs in Gnome as well (same error output). My first suspicion was that my drive was 100% full, but that's not the problem either. 

Anybody run into this and know of a fix?

```

evince

(evince:5691): EggSMClient-WARNING **: Failed to connect to the session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed


** (evince:5691): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name

(evince:5691): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/lanctot/.recently-used.xbel', but the parser failed: Failed to open file '/home/lanctot/.recently-used.xbel': Permission denied.

** (evince:5691): WARNING **: Failed to create file '/home/lanctot/.gnome2/evince/evince-crashed.W1TI2U': Permission denied
I/O error : Permission denied
I/O error : Permission denied

** (evince:5691): WARNING **: Failed to write XML data to /home/lanctot/.gnome2/evince/evince_toolbar.xml.tmp

(evince:5691): Gtk-WARNING **: Attempting to store changes into `/home/lanctot/.recently-used.xbel', but failed: Failed to create file '/home/lanctot/.recently-used.xbel.YDKS2U': Permission denied

lanctot@host:lanctot% ls -lh /home/lanctot/.recently-used.xbel
-rw------- 1 lanctot lanctot 218 2009-11-02 20:36 /home/lanctot/.recently-used.xbel
lanctot@host:lanctot% ls -la | grep gnome2
drwx------    7 lanctot lanctot      4096 2009-11-02 20:36 .gnome2
drwx------    2 lanctot lanctot      4096 2009-06-23 13:31 .gnome2_private
-rw-r--r--    1 lanctot lanctot        89 2006-12-30 13:29 .gtkrc-1.2-gnome2
drwx------   13 lanctot lanctot      4096 2009-11-02 20:25 .old-gnome2
lanctot@host:lanctot% ls -lh /home/lanctot/.gnome2/evince/
total 0
lanctot@host:lanctot% ls -lh /home/lanctot/.gnome2
total 24K
drwx------ 2 lanctot lanctot 4.0K 2009-11-02 20:34 accels
drwxr-xr-x 2 lanctot lanctot 4.0K 2009-11-02 20:33 evince
drwx------ 2 lanctot lanctot 4.0K 2009-11-02 20:30 keyrings
drwxr-xr-x 2 lanctot lanctot 4.0K 2009-11-02 20:34 nautilus-scripts
drwx------ 3 lanctot lanctot 4.0K 2009-11-02 20:34 panel2.d
-rw-r--r-- 1 lanctot lanctot   53 2009-11-02 20:31 Vim

lanctot@host:lanctot% df -h ~
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5             105G   56G   44G  57% /data
lanctot@host:lanctot% dpkg --list | grep evince
ii  evince                                         2.28.1-0ubuntu1                            Document (postscript, pdf) viewer
ii  python-evince                                  2.28.0-0ubuntu1                            Python module for evince

```

---

### Post by zoro98020 on 2009-11-27
I had the same problem - inexplicable access denied permission problems. I strace'd it and sure enough the system calls are failing

open("/home/zoro/.ICEauthority", O_RDONLY) = -1 EACCES (Permission denied)
This happens with MANY relevant files. So after fiddling around a bit:

su
cd /usr/bin
mv evince evince.bin
ln -s evince.bin evince

And vaola! it just works.

Undu the above and its busted again.
cp evince.bin evince doesn't work
ln evince.bin  evince doesn't work

WTF?

---

### Post by zoro98020 on 2009-11-27
OK, seems to be something to do with AppArmor.

In /etc/apparmor.d I have among other things:
disable/
-rw-r--r-- 1 root root 2052 2009-11-11 01:03 usr.bin.evince
-rw-r--r-- 1 root root 4866 2009-10-28 08:50 usr.bin.firefox-3.5

In dir disable I find:
lrwxrwxrwx 1 root root 35 2009-10-31 10:36 usr.bin.firefox-3.5 -> /etc/apparmor.d/usr.bin.firefox-3.5

I added evince to disable
lrwxrwxrwx 1 root root 30 2009-11-27 09:37 usr.bin.evince -> /etc/apparmor.d/usr.bin.evince

Undo my symlink hack from previous post and restart AppArmor:
/etc/init.d/apparmor restart

And bingo! It works

---

### Post by sharky6000 on 2009-12-22
Excellent, that second fix worked for me (didn't try the first one). 

And, it seems like someone has logged a bug:

[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg352949.html]("http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg352949.html")

Thanks!

---

### Post by omer.qadir on 2010-04-21
Thanks. Works for me too.

---

### Post by iridgedati on 2010-05-28
> **zoro98020 said:**
> I had the same problem - inexplicable access denied permission problems. I strace'd it and sure enough the system calls are failing

open("/home/zoro/.ICEauthority", O_RDONLY) = -1 EACCES (Permission denied)
This happens with MANY relevant files. So after fiddling around a bit:

su
cd /usr/bin
mv evince evince.bin
ln -s evince.bin evince

And vaola! it just works.

Undu the above and its busted again.
cp evince.bin evince doesn't work
ln evince.bin  evince doesn't work

WTF?
This worked for me! Thanks for posting it!

---

### Post by satnelav on 2010-05-31
The second solution worked for me on Lucid Lynx when evince had broken on the most recent update (31 May 2010). Thanks.

---

