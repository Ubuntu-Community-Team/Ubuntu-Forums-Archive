---
title: "gmail as mounted hardrive"
date: 2006-03-19
forum: General Help
---

### Post by souteneur3190 on 2006-03-19
is there a program to mount you the space in your google account as a hardrive?

---

### Post by ewtesterman@cox.net on 2006-03-19
If you use fire fox you can use the gspace extension. I use it all of the time.

---

### Post by souteneur3190 on 2006-03-19
wut version of firefox do you have?

---

### Post by stabface on 2006-03-19
there is one for windows called gdrive, not sure of linux. I used it and it is pretty cool

---

### Post by tuxcantfly on 2006-03-19
[http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html)

is the url for the fuse-based driver

---

### Post by tuxcantfly on 2006-03-19
sudo apt-get install gmailfs

installs the package

---

### Post by souteneur3190 on 2006-03-19
ok, how do i access it, gmailfs, that is

---

### Post by tuxcantfly on 2006-03-19
sudo modprobe fuse

(you may get an error message, if you do, install a new kernel from dapper or build the fuse module using module-assistant)

sudo mkdir /media/gmail

sudo mount -t gmailfs /media/gmail -o username=gmailuser, password=gmailpass, fsname=zOlRRa

the rest of the documentation is at
[http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-using.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-using.html)

---

### Post by LordMelkor on 2006-03-19
I got this error...
i used the command:

mount -t gmailfs /usr/share/gmailfs/gmailfs.py /path/of/mount/point -o username=gmailuser, password=gmailpass, fsname=zOlRRa 

with password fsname etc filled in. I had to include this:

/usr/share/gmailfs/gmailfs.py 

because otherwise it said that i wasnt using the mount command correctly.

krishanu@ubuntu:~$ gmailfs.py:Gmailfs:mountpoint: '/media/gmail'
gmailfs.py:Gmailfs:unnamed mount options: ['rw']
gmailfs.py:Gmailfs:named mount options: {'username': '****', 'password': '****', 'fsname': '****'}
Traceback (most recent call last):
  File "/usr/share/gmailfs/gmailfs.py", line 1117, in ?
    server = Gmailfs()
  File "/usr/share/gmailfs/gmailfs.py", line 603, in __init__
    self.ga.login()
  File "/usr/lib/python2.4/site-packages/libgmail/__init__.py", line 281, in login
    raise GmailLoginFailure
libgmail.GmailLoginFailure

I starred out my pass, etc... how do I fix this? :confused:

---

### Post by tuxcantfly on 2006-03-20
there's a howto at [http://ubuntuforums.org/showthread.php?t=139872](http://ubuntuforums.org/showthread.php?t=139872)

---

