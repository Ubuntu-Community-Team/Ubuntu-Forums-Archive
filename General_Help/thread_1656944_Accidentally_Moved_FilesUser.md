---
title: "Accidentally Moved Files/User"
date: 2010-12-31
forum: General Help
---

### Post by robbrownu on 2010-12-31
I was having problems logging in this morning, and I think I made things worse!
 
Initially, I was trying to get around a Nautilus log in error.  I followed some of the suggestions in the following chain of posts here. Using this, I was able to log in, but I entered what seems to be a perfectly clean version of Ubuntu...with no access to my files.

[[COLOR=#444444]http://art.ubuntuforums.org/showthre...1553056&page=3[/COLOR]]("http://art.ubuntuforums.org/showthread.php?t=1553056&page=3")

Now, I can't seem to find any of my original files.  Some of the commands I entered in the terminal included:

sudo chown -R Robert:Robert /home/Robert

AND 

sudo nano /etc/gdm/custom.conf
 
I'm afraid that I may have deleted the files, or have moved them to another user or someplace on the drive I can't see.  Anyone have any ideas?
 
I'm a bit of a noob, as evidenced by the fact that I messed this up.  Any advice is welcome.
 
Thanks.
Rob

---

### Post by Idefix82 on 2011-01-01
The chown command probably shoudn't have any such disastrous consequences. The second command opens a configuration file for editing, so the question is how you edited it.

Let's assume that you had some files directly in the folder /home/Robert/Documents. Then what is the output of
```
sudo ls -lha /home/Robert/Documents
```?
In any case, the output from
```
sudo ls -la /home/Robert
```
might also be useful.

If you remember reasonably exactly the file name of a file that used to be there, e.g. myVeryPersonalFile.txt, then you can try
```
locate myVeryPersonalFile.txt
```
and post the output here.

---

### Post by robbrownu on 2011-01-01
Here's the outputs:

robert@robert-OptiPlex-GX260:~$ ls /home
robert

robert@robert-OptiPlex-GX260:~$ ls -la /home
total 16
drwxr-xr-x  4 root   root   4096 2010-11-22 15:58 .
drwxr-xr-x 22 root   root   4096 2010-12-26 09:07 ..
drwxr-xr-x  3 root   root   4096 2010-11-22 15:58 .ecryptfs
drwxr-xr-x 28 robert robert 4096 2011-01-01 08:57 robert
robert@robert-OptiPlex-GX260:~$ tail -5 /etc/password
tail: cannot open `/etc/password' for reading: No such file or directory
robert@robert-OptiPlex-GX260:~$ sudo ls -lha /home/robert/documents
[sudo] password for robert: 
ls: cannot access /home/robert/documents: No such file or directory
robert@robert-OptiPlex-GX260:~$ sudo ls -la /home/robert
ls: cannot access /home/robert/.gvfs: Permission denied
total 164
drwxr-xr-x 28 robert robert  4096 2011-01-01 09:21 .
drwxr-xr-x  4 root   root    4096 2010-11-22 15:58 ..
lrwxrwxrwx  1 robert robert    56 2010-11-22 15:58 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
drwx------  3 robert robert  4096 2010-12-31 10:58 .adobe
-rw-------  1 robert robert    50 2010-12-31 16:58 .bash_history
drwx------  8 robert robert  4096 2011-01-01 08:57 .cache
drwxr-xr-x  8 robert robert  4096 2010-12-31 13:16 .config
drwx------  3 robert robert  4096 2010-12-31 10:55 .dbus
drwxr-xr-x  2 robert robert  4096 2010-12-31 10:55 Desktop
-rw-r--r--  1 robert robert    41 2011-01-01 08:57 .dmrc
drwxr-xr-x  2 robert robert  4096 2010-12-31 10:55 Documents
drwxr-xr-x  2 robert robert  4096 2010-12-31 10:55 Downloads
lrwxrwxrwx  1 robert robert    32 2010-11-22 15:58 .ecryptfs -> /home/.ecryptfs/robert/.ecryptfs
-rw-------  1 robert robert    16 2010-12-31 10:55 .esd_auth
drwx------  3 robert robert  4096 2010-12-31 13:19 .evolution
drwx------  4 robert robert  4096 2011-01-01 08:57 .gconf
drwx------  2 robert robert  4096 2011-01-01 09:21 .gconfd
drwx------  7 robert robert  4096 2010-12-31 13:31 .gnome2
drwx------  2 robert robert  4096 2010-12-31 10:57 .gnome2_private
drwx------  2 robert robert  4096 2010-12-31 13:47 .gnupg
-rw-r--r--  1 robert robert   142 2011-01-01 08:57 .gtk-bookmarks
d?????????  ? ?      ?          ?                ? .gvfs
-rw-------  1 robert robert  1134 2011-01-01 08:57 .ICEauthority
drwxr-xr-x  3 robert robert  4096 2010-12-31 10:55 .local
drwx------  3 robert robert  4096 2010-12-31 10:58 .macromedia
drwx------  4 robert robert  4096 2010-12-31 10:57 .mozilla
drwxr-xr-x  2 robert robert  4096 2010-12-31 10:55 Music
drwxr-xr-x  2 robert robert  4096 2010-12-31 10:55 .nautilus
drwxr-xr-x  2 robert robert  4096 2010-12-31 10:55 Pictures
lrwxrwxrwx  1 robert robert    31 2010-11-22 15:58 .Private -> /home/.ecryptfs/robert/.Private
drwxr-xr-x  2 robert robert  4096 2010-12-31 10:55 Public
drwx------  2 robert robert  4096 2011-01-01 08:57 .pulse
-rw-------  1 robert robert   256 2010-12-31 10:55 .pulse-cookie
lrwxrwxrwx  1 robert robert    52 2010-11-22 15:58 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt
-rw-------  1 robert robert   218 2010-12-31 13:31 .recently-used.xbel
drwx------  2 robert robert  4096 2010-12-31 13:47 .ssh
-rw-r--r--  1 robert robert     0 2011-01-01 09:21 .sudo_as_admin_successful
drwxr-xr-x  2 robert robert  4096 2010-12-31 10:55 Templates
drwxrwxr-x  2 robert robert  4096 2010-12-31 13:16 Ubuntu One
drwxr-xr-x  2 robert robert  4096 2010-12-31 10:55 Videos
-rw-------  1 robert robert  1090 2011-01-01 08:58 .xsession-errors
-rw-------  1 robert robert 19925 2010-12-31 16:58 .xsession-errors.old

The locate function doesn't turn up any of the files that I know were on the machine.

---

### Post by Idefix82 on 2011-01-01
The locate command not returning anything is bad news. However, note that Linux distinguishes between small and capital letters. I.e. in the above example, the command
```
locate myverypersonalfile.txt
```
would not return anything, since the file name is different from myVeryPersonalFile.txt. In particular, you mistyped the /Documents in
```
sudo ls -lha /home/robert/documents
```
which is why it said that there is no such directory. So you might want to try that again.

---

### Post by robbrownu on 2011-01-01
Ok...tried it again, here's what I got:

robert@robert-OptiPlex-GX260:~$ sudo ls -lha /home/robert/Documents
total 8.0K
drwxr-xr-x  2 robert robert 4.0K 2010-12-31 10:55 .
drwxr-xr-x 28 robert robert 4.0K 2011-01-01 17:33 ..

This seems promising because it was around 10:55 when I started putting in the commands.  The negative side is that "4.0K" is much smaller than the stuff I'd loaded on the machine (loaded with pictures and MS Office files).

Any thoughts?

---

### Post by AlphaLexman on 2011-01-01
What directories are encrypted, ?
[LIST]
[*]/home/Robert/Private
[*]/home/Robert
[*]/home
[/LIST] 

Take a look at:
```
cat /usr/share/ecryptfs-utils/ecryptfs-record-passphrase
```

---

### Post by robbrownu on 2011-01-01
here's what i got:

robert@robert-OptiPlex-GX260:~$ cat /usr/share/ecryptfs-utils/ecryptfs-record-passphrase
Name: Record your encryption passphrase
Priority: High
OnlyAdminUsers: False
DisplayIf: test -e $HOME/.ecryptfs/wrapped-passphrase -a ! -e $HOME/.ecryptfs/.wrapped-passphrase.recorded
Terminal: True
GettextDomain: ecryptfs-utils
Command: "sh -c 'ecryptfs-unwrap-passphrase $HOME/.ecryptfs/wrapped-passphrase 2>/dev/null && echo [Enter] && head -n1 && touch $HOME/.ecryptfs/.wrapped-passphrase.recorded '"
Description: To encrypt your home directory or "Private" folder, a strong
 passphrase has been automatically generated. Usually your directory is unlocked
 with your user password, but if you ever need to manually recover this
 directory, you will need this passphrase. Please print or write it down and
 store it in a safe location.
 .
 If you click "Run this action now", enter your login password at the
 "Passphrase" prompt and you can display your randomly generated passphrase.
 .
 Otherwise, you will need to run "ecryptfs-unwrap-passphrase" from the command
 line to retrieve and record your generated passphrase.

---

