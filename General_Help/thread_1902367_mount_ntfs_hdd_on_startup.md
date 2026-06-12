---
title: "mount ntfs hdd on startup"
date: 2011-12-30
forum: General Help
---

### Post by MaxPayneFH on 2011-12-30
Is there a way to make Ubuntu automatically load ntfs hard drives and partitions automatically on startup :confused:

This would be really helpful for me since all my music is in a separate hard drive from the OS.

---

### Post by gsgleason on 2011-12-30
Of course.

Add an entry to your /etc/fstab or via autofs.

---

### Post by Derek Karpinski on 2011-12-30
[LIST=1]
[*]In Terminal (Ctrl-Alt-T), ```
sudo cp /etc/fstab /etc/fstab~bak
```
[*]In nautilus (the file manager) browse to your ntfs hdd and double click on it. This is just to make sure it's mounted.
[*]From terminal (Ctrl-Alt-T), make a folder to mount your hdd to: ```
sudo mkdir /mnt/music
``` replace 'music' with whatever you want. (I suggest no spaces in the name)
[*]Again, still in Terminal, type:```
sudo blkid
```
[*]Find your ntfs hdd in the list, and copy the UUID (long string of nonsensical characters)
[*]Again, in your still open Terminal, type:```
gksudo gedit /etc/fstab
```
[*]Enter your password when prompted.
[*]All the way at the end of the file enter: ```
# Mount ntfs drive to /mnt/music
 
UUID="THE UUID FROM ABOVE" /mnt/music ntfs defaults,umask=000 0 0
```
[*]Reboot.........
[/LIST][https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) for an explaination of the syntax of the fstab file..................or if you want to do all this with a GUI, install 'pysdm'

---

### Post by MaxPayneFH on 2011-12-30
> **Derek Karpinski said:**
> 
[LIST=1]
[*]In Terminal (Ctrl-Alt-T), ```
sudo cp /etc/fstab /etc/fstab~bak
```
[*]In nautilus (the file manager) browse to your ntfs hdd and double click on it. This is just to make sure it's mounted.
[*]From terminal (Ctrl-Alt-T), make a folder to mount your hdd to: ```
sudo mkdir /mnt/music
``` replace 'music' with whatever you want. (I suggest no spaces in the name)
[*]Again, still in Terminal, type:```
sudo blkid
```
[*]Find your ntfs hdd in the list, and copy the UUID (long string of nonsensical characters)
[*]Again, in your still open Terminal, type:```
gksudo gedit /etc/fstab
```
[*]Enter your password when prompted.
[*]All the way at the end of the file enter: ```
# Mount ntfs drive to /mnt/music
 
UUID="THE UUID FROM ABOVE" /mnt/music ntfs defaults,umask=000 0 0
```
[*]Reboot.........
[/LIST]
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) for an explaination of the syntax of the fstab file..................or if you want to do all this with a GUI, install 'pysdm'

I must have done one of these steps wrong because when I booted I got a message saying one of the drives failed to mount.
Anyway I removed the lines I added and searched for pysdm on ubunto software center and a program called "storage device manager" showed up; after messing with the program for a while I found a check saying "file system is mounted at boot time" so I managed to make ubunto mount my ntfs drive on startup.:P
However  it mounted the drive in read only mode :( and when I uncheck the option to mount it in read only mode, push ok and apply, when I open the assistant windows again the option to mount the drive in read only mode is checked again :X

---

### Post by Rodney9 on 2011-12-30
sudo apt-get install ntfs-3g

NTFS-3G uses FUSE (Filesystem in Userspace) to provide support for the NTFS
filesystem used by Microsoft Windows. It can:

 * create, remove, rename, or move files, directories, hard links, and streams;
 * read and write files, including streams, sparse files, and transparently
   compressed files;
 * handle special files like symbolic links, devices, and FIFOs;
 * provide standard management of file ownership and permissions, including
   POSIX ACLs.

This package also contains the tools previously available in the ntfsprogs
package.



For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Derek Karpinski on 2011-12-31
ntfs-3g should be installed by default. If not, in Terminal enter:
```
sudo apt-get update

sudo apt-get install ntfs-3g
```

please paste the output of ```
sudo blkid
```My instructions may have been misinterpreted.

```
UUID="THE UUID FROM ABOVE" /mnt/music ntfs defaults,umask=000 0 0
```"THE UUID FROM ABOVE" does NOT include the quotes. Only the characters. Sorry.

---

### Post by MaxPayneFH on 2012-01-06
Sorry for not saying anything but I've been somewhat busy and didn't have much time.

I got things to work n my desktop via GUI, I found out what I needed to do was click the button that said defaults and the disk was no longer mounted in read only mode.

Since I might as well leave whats working untouched I tried mounting an ntfs partition on a laptop via terminal and I got the following message when I try to edit fstab:

```

(gksudo:2196): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:2196): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:2196): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:2196): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

```But this laptop has many other problems running ubunto, probably because it has an uncommon chipset.

Although it shows this error message fstab is editable but it ust have screwed up something again because the drive failed to mount on startup, so eventually I resorted to pysdm once more and the ntfs partition on the laptop is mounting on startup. 

Anyway thanks or your help guys and really grateful for your support.

---

### Post by Saubazi on 2012-01-06
I think you need to specify ntfs-3g in the /etc/fstab 
AND I think that mounting windows partitions in the boot is
broken at the moment - at least it was.

---

### Post by Derek Karpinski on 2012-01-06
> **MaxPayneFH said:**
> Sorry for not saying anything but I've been somewhat busy and didn't have much time.
 
I got things to work n my desktop via GUI, I found out what I needed to do was click the button that said defaults and the disk was no longer mounted in read only mode.
 
Since I might as well leave whats working untouched I tried mounting an ntfs partition on a laptop via terminal and I got the following message when I try to edit fstab:
 
```

(gksudo:2196): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
 
(gksudo:2196): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
 
(gksudo:2196): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
 
(gksudo:2196): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

```But this laptop has many other problems running ubunto, probably because it has an uncommon chipset.
 
Although it shows this error message fstab is editable but it ust have screwed up something again because the drive failed to mount on startup, so eventually I resorted to pysdm once more and the ntfs partition on the laptop is mounting on startup. 
 
Anyway thanks or your help guys and really grateful for your support.
 
```
[FONT=Courier New]sudo apt-get install gtk2-engines-pixbuf[/FONT]
```
 
Will fix this.
 
Post the output of 'sudo blkid', and post the output of your fstab.
 
> **Saubazi said:**
> I think you need to specify ntfs-3g in the /etc/fstab 
AND I think that mounting windows partitions in the boot is
broken at the moment - at least it was.
 
ntfs or ntfs-3g.......didn't matter on my box. I was able to mount the Windows partition at boot using the above method.

---

### Post by MaxPayneFH on 2012-01-06
>  	Code:
 	[FONT=Courier New]sudo apt-get install gtk2-engines-pixbuf[/FONT] 

This seems to have fixed the error I had while opening fstab.

Here the output of sudo blkid:

```
/dev/sda1: LABEL="Sistema" UUID="422CB7C92CB7B5EF" TYPE="ntfs" 
/dev/sda5: UUID="1faa0037-2eb4-425c-96be-5beef10c56a9" TYPE="ext4" 
/dev/sda6: UUID="06efff09-955a-4ceb-9647-c48a702a8a5d" TYPE="swap"
```

And the output of my fstab, but its already after pysdm added a couple of lnes at the end:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid      0  0  
# / was on /dev/sda5 during installation
UUID=1faa0037-2eb4-425c-96be-5beef10c56a9  /            ext4  errors=remount-ro        0  1  
# swap was on /dev/sda6 during installation
UUID=06efff09-955a-4ceb-9647-c48a702a8a5d  none         swap  sw                       0  0  


/dev/sda1                                  /media/sda1  ntfs  nls=iso8859-1,umask=000  0  0  
```

---

### Post by Saubazi on 2012-01-07
> **Derek Karpinski said:**
> 
 
ntfs or ntfs-3g.......didn't matter on my box. I was able to mount the Windows partition at boot using the above method.

For reading yes, but if my memory serves me correctly having filesystem as ntfs does not support writing...I donot know if it has changed ever since...

---

