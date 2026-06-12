---
title: "scanimage/sane permissions"
date: 2010-01-24
forum: General Help
---

### Post by themagicmanfromtrent on 2010-01-24
I'm having a problem with the permissions on my scanner, I can't seem to get any non-root user to scan.

sudo scanimage works every time, but how can I modify the permissions so anyone can scan images?

scanimage as a non-root user gives the following error:

```
abukalam-server@abukalam-server:/var/www$ scanimage
scanimage: open of device brother2:bus6;dev1 failed: Error during device I/O
```

---

### Post by sisco311 on 2010-01-25
Add your user to the scanner group:
```
sudo gpasswd -a username scanner
```

EDIT:
In order the changes take effect, you have to log out and log back in.

---

### Post by themagicmanfromtrent on 2010-01-25
I'm already a member of scanner. I don't think that group owns the printer, how can I chown the printer?

Here's the list of groups and users:

```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:abukalam-server
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:abukalam-server
fax:x:21:
voice:x:22:
cdrom:x:24:abukalam-server
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:abukalam-server
plugdev:x:46:abukalam-server
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
klog:x:103:
fuse:x:104:
ssl-cert:x:105:
lpadmin:x:106:abukalam-server
crontab:x:107:
mlocate:x:108:
ssh:x:109:
sambashare:x:110:abukalam-server
saned:x:111:abukalam-server
winbindd_priv:x:112:
netdev:x:113:
messagebus:x:114:
avahi:x:115:
polkituser:x:116:
haldaemon:x:117:
abukalam-server:x:1000:
admin:x:118:abukalam-server
openldap:x:120:
saneusers:x:1001:abukalam-server,www-data,nobody,root,daemon,bin,sys,sync,games,man,lp,news,mail,uucp,proxy,backup,syslog,klog,hplip,sshd,landscape,libuuid,messagebus,saned,irc,gnats,polkituser,haldaemon,openldap,mysql,mt-daapd,list,ava$
mysql:x:121:
bind:x:122:
postfix:x:123:
postdrop:x:124:
dhcpd:x:125:
scanner:x:1002:abukalam-server,www-data
landscape:x:126:
debian-transmission:x:119:

```

---

### Post by kwstas on 2010-03-06
hi,

i have the same problem with my xerox phaser 3100MFP.
i still haven't found any solution to this but just for now i made a link of "xsane" on my desktop which i run as admin(with right click).

if anyone solves it pls post.

---

### Post by sisco311 on 2010-03-06
Do you know the device name of the scanner?

What's the output of:
```
ls -al /dev/usb*
```?

---

### Post by kwstas on 2010-03-08
hi,
 > ls -al /dev/usb*

gives me this:

> lrwxrwxrwx 1 root root      7 2010-03-08 16:07 /dev/usblp0 -> usb/lp0
crw-rw---- 1 root root 253, 0 2010-03-08 18:07 /dev/usbmon0
crw-rw---- 1 root root 253, 1 2010-03-08 18:07 /dev/usbmon1
crw-rw---- 1 root root 253, 2 2010-03-08 18:07 /dev/usbmon2
crw-rw---- 1 root root 253, 3 2010-03-08 18:07 /dev/usbmon3
crw-rw---- 1 root root 253, 4 2010-03-08 18:07 /dev/usbmon4
crw-rw---- 1 root root 253, 5 2010-03-08 18:07 /dev/usbmon5

/dev/usb:
total 0
drwxr-xr-x  2 root root     60 2010-03-08 16:07 .
drwxr-xr-x 16 root root   4200 2010-03-08 16:07 ..
crw-rw----  1 root lp   180, 0 2010-03-08 16:07 lp0


---

### Post by sisco311 on 2010-03-08
Add your user to the lp (lowercase L) group:
```
sudo gpasswd -a **username** lp
```
log out & log back in.

---

### Post by kwstas on 2010-03-09
> Add your user to the lp (lowercase L) group:
     Code:
     sudo gpasswd -a **username** lp 
log out & log back in.     it worked! i can now run "xsane" as user but when i try to save the image i get error "failed to create file: permission denied" and it doesn't save it.

---

### Post by sisco311 on 2010-03-09
Make sure that the ~/.sane directory is owned by your user:
```
sudo chown -R $USER: ~/.sane
```

Did you run *sudo xsane*?
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by DawieS on 2010-03-09
I have found that XSane requires the destination folder, where images will be saved, to be private (not readable by others). Click on the stiffy icon (left of the filename) and choose 'Create Folder' on the next screen. You may name it 'scan', or whatever, and the permissions will be correctly set upon creation.

Alternatively you may use a file browser to create and set the permissions of the destination folder.

---

### Post by kwstas on 2010-03-09
:popcorn:

great news!

in addition of sisco311's instructions i found and did these too:

[http://jamesmcdonald.id.au/gnu-linux/xsane-failed-to-create-file-permission-denied-error](http://jamesmcdonald.id.au/gnu-linux/xsane-failed-to-create-file-permission-denied-error)

and everything works fine!

---

### Post by tuxrouge on 2010-05-05
My problem is not exactly the same

```
$ sudo sane\-find\-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x0924 [XEROX], product=0x3cee [ Phaser 3100MFP]) at libusb:007:002
```
```
$ scanimage -L
device `XeroxPhaser3100:usb:007:002' is a XEROX 3100MFP Feeder/Flatbed Scanner
```

but xsane, in root mode find nothing (in user mode too)

any idea ?

---

### Post by DawieS on 2010-05-05
> **tuxrouge said:**
> but xsane, in root mode find nothing (in user mode too)

any idea ?
You probably also have a driver problem like I had. Please see [_**this**_]("http://ubuntuforums.org/showthread.php?t=1394193&highlight=scanner") thread. Although you have a different scanner, the same procedure will probably work using the Windows driver.

---

### Post by dumpster25 on 2011-07-30
This is Natty 11.04 related 
I had a similar problem where I was trying to use the scan with the command scanimage.

One user, USER1 was able to scan from the terminal with scanimage and other users were not able to.

I checked to see if it was related to group affiliation. I had another user, USER2 that belonged to the same groups as USER1 who was able to scan. But USER2 couldn't scan

The issue was that as soon I logged into the Window Environment/Desktop of USER2 as USER2 I suddenly had access to the scanner.

So in my case it is dependent on which user's is logged on to the system through it's Desktop Environment at the time.

I haven't looked into it further, but I hope this info sames some time and headaches to others :)

---

