---
title: "How to delete folders from Places side bar in  File Browser"
date: 2009-11-06
forum: General Help
---

### Post by edmonds on 2009-11-06
I have a NAS server with a files folder and a Music folder.
When i upgraded to koala at first these folders could not be seen but i was able to get to it through the network link in  the side bar in  File Browser.

The problem is that now my fstab seems to working  again  and the Music and Files Folders are there and mounted, but there are now 2 more folders, another Music and Files folder, unmounted.

The fstab file only mention one of each. 

When i right click on  the folders in places in  File Browser the remove option is faded out.

How do i delete them?

i just opened nautilus in  sudo: gksu nautilus in  the hope that that i would then see these extra folders but be able to right click remove. But the folders are not there.

what am i doing  wrong?

thanks
tom

---

### Post by clauber on 2009-11-06
Please, post us the results of this command on that folder: ls -la. I'd like to see what it appears.

---

### Post by edmonds on 2009-11-06
hi clauber
thanks for responding  so fast.
do you  mean the media folder?

:/media$ ls -la
total 28
drwxr-xr-x  7 root root 4096 2009-11-06 06:56 .
drwxr-xr-x 23 root root 4096 2009-11-02 14:14 ..
lrwxrwxrwx  1 root root    6 2008-09-17 14:37 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-09-17 14:37 cdrom0
drwxrwxrwx  6 root root 4096 2008-09-08 14:18 Files
lrwxrwxrwx  1 root root    7 2008-09-17 14:37 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2008-09-17 14:37 floppy0
-rw-r--r--  1 root root    0 2009-11-06 06:56 .hal-mtab
drwxr-xr-x  2 root root 4096 2009-02-23 11:11 Lappy
drwxrwxrwx 62 root root 4096 2009-08-30 12:21 Music


which looks right??
tom

---

### Post by edmonds on 2009-11-09
any ideas anyone?

---

### Post by dave_t_uk on 2009-11-18
Yep, I'm facing exactly the same problem too.

I tinkered around with mapping some network and local drives, and eventually got them to work.  Two local drives are mapped to /media/c and /media/d, and these work fine.  They are now automounted in my /etc/fstab.

HOWEVER, in the tinkering, I gained two new entries in my 'places' list which shows on the left side of every nautilus window, and also in the 'Places' menu on the taskbar.  I now have 'c' and 'd' in this menu, when I click either of them, I get a message box pop up saying:

```
Unable to mount c
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged
```

I don't know what FUSE means.  Anyway, my drives are working fine and are already mapped.  I just want rid of these shortcuts that don't work.  

As an asside, a new Ubuntu user is likely to be pretty scared off by this message.  I'd confidently guess that someone who was used to windows would not understand the terms mount, NTFS, block, FUSE, volume, NTFS-3G, setuid, or root, making this message quite terrifying.

Here's the relevant info from my system:
```

dave@black:~$ ls -la /media
total 36
drwxr-xr-x  7 root root   4096 2009-11-18 20:58 .
drwxr-xr-x 20 root root   4096 2009-10-30 09:54 ..
drwxrwxrwx  1 root root  16384 2009-11-18 19:49 c
lrwxrwxrwx  1 root root      6 2009-04-28 19:31 cdrom -> cdrom0
drwxr-xr-x  2 root root   4096 2009-04-28 19:31 cdrom0
drwxrwxrwx  1 root root   8192 2009-11-15 21:53 d
-rw-r--r--  1 root root      0 2009-11-18 20:58 .hal-mtab
drwxr-xr-x  1 dave users     0 2000-01-08 12:33 myshare
drwxr-xr-x  1 dave users     0 2000-01-03 23:26 openshare
dave@black:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=5c2b66c9-5454-493b-9f33-85f745eb792e /               ext4    relatime,errors=remount-ro 0       1
/dev/sda7       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# lines added by DT 2009-10-31:
UUID=0468E11368E103F0 /media/c ntfs-3g defaults,user,locale=en_GB.utf8 0 0
UUID=39C980456ACE87F0 /media/d ntfs-3g defaults,user,locale=en_GB.utf8 0 0
//192.168.2.107/openshare /media/openshare cifs username=,password=,uid=1000,gid=100 0 0 
//192.168.2.107/myshare /media/myshare cifs username=admin,password=xxxxxx,uid=1000,gid=100 0 0 
dave@black:~$ cat .gtk-bookmarks 
file:///home/dave/Documents
file:///home/dave/Music
file:///home/dave/Pictures
file:///home/dave/Videos
dave@black:~$ 

```

---

### Post by dcstar on 2009-11-19
> **edmonds said:**
> 
.........
i just opened nautilus in  sudo: gksu nautilus in  the hope that that i would then see these extra folders but be able to right click remove. But the folders are not there.


```
gksudo "dbus-launch nautilus --no-desktop --browser %U"
```

---

### Post by edmonds on 2009-11-19
hi
tried that. got this:
Initializing nautilus-gdu extension
Initializing nautilus-image-converter extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Shutting down nautilus-image-converter extension
Shutting down nautilus-gdu extension

(nautilus:2786): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
tom@elvis3:~$ gksudo "dbus-launch nautilus --no-desktop --browser %U"^C

a file browser window appeared but i coudn't right click remove either of the folders

---

### Post by nicknefarious on 2009-11-26
I also have both of these problems - firstly the extra (duplicate) folders, or in my case, partitions in the places menu after having troubles mounting some of the partitions. Any luck trying to remove them? Anybody have any solutions?

Also have the problem when trying to run nautilus in root mode from terminal. Exactly the same error.

Nick

---

### Post by edmonds on 2009-11-26
hi nick
no, they are still there. 
no idea what to do.
tom

---

### Post by nicknefarious on 2009-11-26
In actual fact this is the complete error message I get when trying to launch nautilus in root mode....

** (nautilus:2660): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2660): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2660): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:2660): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time
Shutting down nautilus-gdu extension

---

### Post by eltopo1 on 2010-05-06
I'm having the same problem, anyone got an idea? The partitions from this one drive still show up in the places list, even though they're successfully mounted just above. I don't have the option to unmount them anywhere, and when I click on them it says

```
mount: /dev/sdb2 already mounted or /media/MOVIEZ busy
mount: according to mtab, /dev/sdb2 is already mounted on /media/MOVIEZ
```

It's not a critical fault but it is annoying...

---

### Post by edmonds on 2010-05-06
it went away when i upgraded. 
sorry

tom

---

