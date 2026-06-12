---
title: "strange problem"
date: 2011-10-24
forum: General Help
---

### Post by Elshentenawy on 2011-10-24
firefox stopped working suddenly I cannt open it any way it doesn't respond any way when I use the terminal to open it it says 
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox
when I type sudo apt-get install firefox 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 190 not upgraded.

---

### Post by papibe on 2011-10-24
Could you post the results of these commands?
```
apt-cache policy firefox

ps aux | grep firefox

```
Please paste your results using the # tag (available when replying).
Regards.

---

### Post by Elshentenawy on 2011-10-24
apt-cache policy firefox

firefox:
  Installed: 7.0.1+build1+nobinonly-0ubuntu2
  Candidate: 7.0.1+build1+nobinonly-0ubuntu2
  Version table:
 *** 7.0.1+build1+nobinonly-0ubuntu2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main i386 Packages
        100 /var/lib/dpkg/status

 ps aux | grep firefox

ubuntu    7873  0.0  0.0   4448   808 pts/0    S+   20:44   0:00 grep --color=auto firefox

---

### Post by papibe on 2011-10-24
It seems to be installed. Try this:
```
/usr/bin/firefox
```
Regards.

---

### Post by Elshentenawy on 2011-10-24
bash: /usr/bin/firefox: No such file or directory

---

### Post by papibe on 2011-10-24
Something definitively went wrong. I would reinstall firefox:
```
sudo apt-get update
sudo apt-get --reinstall install firefox
```
Tell us how it goes,
Regards.

---

### Post by Elshentenawy on 2011-10-24
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release: The following signatures were invalid: NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release: The following signatures were invalid: NODATA 2

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

and 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 190 not upgraded.
Need to get 16.8 MB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main firefox i386 7.0.1+build1+nobinonly-0ubuntu2 [16.8 MB]
Fetched 16.8 MB in 5min 10s (54.0 kB/s)                                                                                          
dpkg: warning: 'find' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by mikejonesey on 2011-10-24
system>admin>software sources...

update software sources and try again...

---

### Post by Elshentenawy on 2011-10-24
bash: admin: Permission denied

---

### Post by mikejonesey on 2011-10-24
su-to-root -X -c /usr/bin/software-properties-gtk

or

gksu /usr/bin/software-properties-gtk

---

### Post by Elshentenawy on 2011-10-24
ubuntu@ubuntu:~$ su-to-root -X -c /usr/bin/software-properties-gtk
The program 'su-to-root' is currently not installed.  You can install it by typing:
sudo apt-get install menu
ubuntu@ubuntu:~$ sudo apt-get install menu
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  menu-l10n
The following NEW packages will be installed:
  menu
0 upgraded, 1 newly installed, 0 to remove and 190 not upgraded.
Need to get 453 kB of archives.
After this operation, 2,150 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/universe menu i386 2.1.45ubuntu1 [453 kB]
Fetched 453 kB in 7s (57.7 kB/s)                                               
dpkg: warning: 'find' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)





ubuntu@ubuntu:~$ gksu /usr/bin/software-properties-gtk

(gksu:11069): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:11069): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:11069): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:11069): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
ubuntu@ubuntu:~$ gksu /usr/bin/software-properties-gtk

(gksu:11087): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:11087): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:11087): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:11087): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


and it opens software sources 
with revert and close option I don't know what to do ?

---

### Post by mikejonesey on 2011-10-25
dpkg: warning: 'find' not found in PATH or not executable.

lol u've messed up ur path env var, alot of people seem to be doing this...

temp fix it using standard dirs;

```
export PATH=/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin:/usr/local/sbin
```

you can add this to your bashrc or profile to autorun...

```
echo "export PATH=/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin:/usr/local/sbin" >> ~/.bashrc
```

anyways... you say gksu /usr/bin/software-properties-gtk works... on the drop down list select other, in the new popup there should be a button... "select best server", try that...

---

### Post by mikejonesey on 2011-10-25
if your reinstall still fails, try to purge and install

apt-get purge "pack name here"
apt-get install "pack name here"

:)

---

