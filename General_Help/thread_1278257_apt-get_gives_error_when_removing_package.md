---
title: "apt-get gives error when removing package"
date: 2009-09-29
forum: General Help
---

### Post by glubbdrubb on 2009-09-29
I have been havin some issues with gnome-do lately. It simply won't run.

So I try to uninstall it and it give me the following error after pressing 'y':

```
Do you want to continue [Y/n]? y
(Reading database ... 194236 files and directories currently installed.)
Removing gnome-do ...
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: error processing gnome-do (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 gnome-do
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


I have rebooted and tried again a few times with out success.

Edit: I now can't get apt-get to update the sources list and add/remove programmes says:

```
This is a major failure of your software management system. 
Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' 
and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```

---

### Post by philinux on 2009-09-29
Your bottom bit of code, the system is telling you what to do.

sudo apt-get install -f

---

### Post by glubbdrubb on 2009-09-29
I did that and it tried to uninstall gnome-do again with the same result.

---

### Post by philinux on 2009-09-29
Have a look in synaptic for custom filters>broken packages.

Maybe use synaptic to reinstall gnome-do.

---

### Post by glubbdrubb on 2009-09-29
Reinstallation is not given as an option. It would need to be uninstalled before it could be reinstalled anyway, and that is the problem. I can't uninstall it.

---

### Post by glubbdrubb on 2009-10-01
bump

---

### Post by arrange on 2009-10-01
Could you post the output of```
ls -l /var/lib/gconf/debian.defaults/%gconf-tree.xml
ls -al /usr/share/gconf/defaults
sudo update-gconf-defaults
```

---

### Post by glubbdrubb on 2009-10-01
Here you go:

```
victor@victor-desktop:~$ ls -l /var/lib/gconf/debian.defaults/%gconf-tree.xml
-rw-r--r-- 1 root root 40277 2009-06-26 17:19 /var/lib/gconf/debian.defaults/%gconf-tree.xml

victor@victor-desktop:~$ ls -al /usr/share/gconf/defaults
total 124
drwxr-xr-x 2 root root  4096 2009-09-29 15:49 .
drwxr-xr-x 4 root root  4096 2009-04-20 16:01 ..
-rw-r--r-- 1 root root 41833 2009-04-17 07:34 05_panel-default-setup.entries
-rw-r--r-- 1 root root   253 2009-05-01 21:29 10_compiz-gnome
-rw-r--r-- 1 root root    47 2009-05-15 16:46 10_evolution
-rw-r--r-- 1 root root    53 2009-04-14 13:44 10_fast-user-switch-applet
-rw-r--r-- 1 root root   103 2009-04-23 13:54 10_gnome-applets
-rw-r--r-- 1 root root   390 2009-04-08 17:34 10_gnome-power-manager
-rw-r--r-- 1 root root    92 2009-04-12 01:48 10_gnome-screensaver
-rw-r--r-- 1 root root    68 2009-04-08 23:41 10_gnome-session
-rw-r--r-- 1 root root    93 2009-05-08 19:41 10_gnome-settings-daemon
lrwxrwxrwx 1 root root    40 2009-05-23 10:16 10_libgksu -> /etc/alternatives/libgksu-gconf-defaults
-rw-r--r-- 1 root root   553 2009-03-23 14:00 10_libgnome2-common
-rw-r--r-- 1 root root   164 2009-03-17 17:29 10_libgnomevfs2-common
-rw-r--r-- 1 root root    40 2009-05-14 11:41 10_metacity-common
-rw-r--r-- 1 root root   277 2009-04-23 13:24 10_nautilus-data
-rw-r--r-- 1 root root   102 2009-04-08 01:43 10_rhythmbox
-rw-r--r-- 1 root root    76 2009-04-14 12:46 10_totem-common
-rw-r--r-- 1 root root    92 2009-04-12 01:48 15_gnome-screensaver
-rw-r--r-- 1 root root    39 2009-04-03 00:03 16_gnome-session-canberra
-rw-r--r-- 1 root root   303 2008-10-24 16:24 16_ubuntu-artwork
-rw-r--r-- 1 root root   295 2009-04-17 18:07 16_ubuntu-wallpapers

victor@victor-desktop:~$ sudo update-gconf-defaults
[sudo] password for victor: 
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'


```

I added the lines between the "print-outs"

---

### Post by arrange on 2009-10-01
Hmmm... I can't see if the link is broken... Could you give me some more output :)?```
ls -l /etc/alternatives/libgksu-gconf-defaults /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo
```

---

### Post by glubbdrubb on 2009-10-01
```
victor@victor-desktop:~$ ls -l /etc/alternatives/libgksu-gconf-defaults /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo
ls: cannot access /etc/alternatives/libgksu-gconf-defaults: No such file or directory
-rw-r--r-- 1 root root 26 2009-04-08 16:25 /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo
victor@victor-desktop:~$ ls -l /etc/alternatives/libgksu-gconf-defaults /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo

```

---

### Post by arrange on 2009-10-01
Try restoring the broken link```
sudo ln -s /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo /etc/alternatives/libgksu-gconf-defaults
```then run ```
sudo update-gconf-defaults
```If you don't see any error messages, you're probably done.

---

### Post by glubbdrubb on 2009-10-01
No such luck:

```
victor@victor-desktop:~$ sudo ln -s /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo /etc/alternatives/libgksu-gconf-defaults
[sudo] password for victor: 
ln: creating symbolic link `/etc/alternatives/libgksu-gconf-defaults': No such file or directory

victor@victor-desktop:~$ sudo update-gconf-defaults
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
```

---

### Post by karlmp on 2009-10-01
use aptitude

type "sudo aptitude" and press enter

---

### Post by glubbdrubb on 2009-10-01
Aptitude is just another way of running the same operation - uninstalling gnome-do. This is the part that does not work.

---

### Post by arrange on 2009-10-01
You don't have */etc/alternatives*?! Could you check that?```
stat /etc/alternatives
```

---

### Post by glubbdrubb on 2009-10-01
It seems I do not.

No such file or directory

---

### Post by arrange on 2009-10-01
Hmmm... Then you will have to rebuild your */etc/alternatives* directory (BTW: any idea how you may have lost it?). Try```
sudo mkdir /etc/alternatives
sudo update-alternatives --all
```When being prompt and unsure what to do, just press Enter. (This procedure presupposes that your */var/lib/dpkg/alternatives* directory is intact :))

---

### Post by glubbdrubb on 2009-10-02
Those commands ran successfully but when trying to remove gnome-do I got the same error.

As for it going missing, it have something to do with all the system crashes I have had lately or this: [http://ubuntuforums.org/showthread.php?p=8025301]("http://ubuntuforums.org/showthread.php?p=8025301")

---

### Post by arrange on 2009-10-02
Now run ```
sudo ln -s /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo /etc/alternatives/libgksu-gconf-defaults
sudo update-gconf-defaults
```again. Do you still see the same errors? If so, post the output of *ls -al /etc/alternatives*.

---

### Post by glubbdrubb on 2009-10-02
I will run it when I get home. Expect a late reply. Around 4 PM GMT

---

### Post by glubbdrubb on 2009-10-02
Well, it did not give any errors and gnome0do uninstalled successfully.

But now it seems I can't update my software sources file. I tried using the gui but it does not save my settings and can't remember where the actual text file is.

So now I can't install anything or update anything.

So far, so good. (that is my way of saying thanks)

Edit: I just realised that some of my comments could be taken as sarcastic. They are not. They are completely sincere.

---

### Post by arrange on 2009-10-02
You seem to have a lot of strange problems... :)

OK, the *sources.list* file is at */etc/apt/sources.list*. If you want to find out why it's not working, post here the output of```
sudo stat /etc/apt/sources.list
gksu software-properties-gtk
```(the second command will launch the gui, so try to do some adjustments and save them)

---

### Post by glubbdrubb on 2009-10-02
```
victor@victor-desktop:~$ sudo stat /etc/apt/sources.list
[sudo] password for victor: 
stat: cannot stat `/etc/apt/sources.list': No such file or directory
victor@victor-desktop:~$ gksu software-properties-gtk
could not open file '/etc/apt/sources.list'
could not open file '/etc/apt/sources.list'
gpg: keyblock resource `/etc/apt/trusted.gpg': file open error
gpg: fatal: /etc/apt: directory does not exist!
secmem usage: 0/0 bytes in 0/0 blocks of pool 0/32768

```

Wow, I had no idea this was actually possible. I thought only root could delete this file.

---

### Post by arrange on 2009-10-02
First try reinstalling *apt*```
sudo apt-get --reinstall install apt
```

---

### Post by glubbdrubb on 2009-10-02
Almost the definition of Catch 22

```
victor@victor-desktop:~$ sudo apt-get --reinstall install apt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of apt is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Perhaps I could just copy your or any  generic sources.list file?

---

### Post by arrange on 2009-10-02
This could be just a server being down... The problem is you don't have the whole */etc/apt* directory... And reinstallation could restore it.

Try reinstalling via *Synaptic*.

---

### Post by glubbdrubb on 2009-10-02
I can only remove it in synaptic. And I have no experience when it comes to compiling source code. With out apt, how would I re-install apt? With Yum?

---

### Post by glubbdrubb on 2009-10-02
I know how it happened. I was practicing using the terminal.

So I copied the etc directory into another folder. I was practicing removing folders and files that start with the letter a. I must have made a mistake and deleted the contents of the original etc folder instead of my practice folder.

This also explains why Firefox says I don't have Adobe flash installed anymore.

The easiest thing to do is a reinstall. But since the Karmic Beta is out I may as well start with that.

---

### Post by arrange on 2009-10-02
I guess so. But yet - you can learn (or damage) a lot by trying to repair things :)

Reinstalling *apt* should be possible```
arrange@jj:~$ sudo apt-get --reinstall install apt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 30 not upgraded.
Need to get 0B/1659kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 139680 files and directories currently installed.)
Preparing to replace apt 0.7.20.2ubuntu6 (using .../apt_0.7.20.2ubuntu6_i386.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
Setting up apt (0.7.20.2ubuntu6) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
arrange@jj:~$
```

But if your */etc* is almost empty, you'll be better off reinstalling anyway...

---

