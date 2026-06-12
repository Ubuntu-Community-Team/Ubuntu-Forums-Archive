---
title: "Can't mount harddrive"
date: 2010-02-15
forum: General Help
---

### Post by Noadi on 2010-02-15
Okay so here's the problem: I just bought a new laptop with Windows 7 on it. My eventual plan is to dual boot it with Ubuntu but that's not my problem. I knew my old laptop was nearing it's end and I had recently backed up my files onto an external HD. All but a handful of files I've created since my last backup. To save time I tried just accessing my old laptop via the network and transferring those few files. 

Well something messed up and the old laptop crashed and now Ubuntu won't load at all. When I boot it using an old 7.04 live cd (handy and didn't want to burn a new one) I get this error when trying to access the harddrive: 
> Unable to mount the volume. 
mount: wrong fs type, bad option, bad superblock on /dev/ 
sda1, missing codepage or other error in some cases useful info is found in syslog -try dmesg|tail or soI'm not good with the technical stuff so I have no idea what that means. All I want is to retrieve some photos, couple text documents, and a couple videos I shot for my business. Any way to do this I would appreciate.

---

### Post by darolu on 2010-02-15
Boot from the LiveCD; open a terminal and enter this command:
```
sudo fdisk -l
```
Please post what you got from it.

---

### Post by Noadi on 2010-02-15
Here's what I got (found thumb drive with Karmic so using that):
> fdisk: invalid option -- '1'
Usage: fdisk [-b SSZ] [-u] DISK   Change Partition Table
           fdisk -l [-b SSZ] [-u] DISK List partition table(s)


and some more stuff but I'm thinking the invalid option is the most important part right?

---

### Post by darolu on 2010-02-15
It is a lowercase "L" not number "one" :P try copy and paste if you like:
```
sudo fdisk -l
```
It will print a table with your hard drives and their device nomenclature, find your hard drive on the list (you can tell by the size (MB) of it) and check if it is /dev/sda1 or /dev/sdb2 etc.
Ultimately what I want you to do is determine what file system your hard drive has, and then change your fstab file accordingly (tell the system what file system your hard drive has, right now is confused and can't determine it).
Well if you do find /dev/sda1 (you may find your hard drive has different letter assigned) then you do:
```
sudo parted /dev/sda1
```
You will now find a screen that looks like this:
```
GNU Parted 1.8.8.1.159-1e0e
Usando /dev/sda1
¡Bienvenido a GNU Parted! Teclee «help» para ver la lista de comandos.
(parted)
```
Yours will be in English (or w/e language you use) of course, after the (parted) part you will need to type "p" and hit enter, after this it will print something like:
```
GNU Parted 1.8.8.1.159-1e0e
Usando /dev/sda1
¡Bienvenido a GNU Parted! Teclee «help» para ver la lista de comandos.
(parted) p                                                                
Modelo: Desconocida (unknown)
Disco /dev/sda1: 52.4GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. loop

Numero  Inicio  Fin     Tamaño  Sistema de ficheros  Banderas
 1      0.00B   52.4GB  52.4GB  ntfs

(parted)
```
In my case, it is a **ntfs** file system (is my windows partition), in your case should be different, probably ext3 or xfs; with that info we can edit your fstab file, we'll wait for your reply to tell you how to do this.

---

### Post by Noadi on 2010-02-15
Okay maybe I'm an idiot, tried ```
sudo fdisk -l
``` and got a result. It's long
> Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads. 63 sectors/track, 4864 cylinders
Units= cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008ddcb
Device Boot      Start         End      Blocks   Id  System
/dev/sda1    *           1        4659    37423386   83  Linux
/dev/sda2             4660        4864     1646662+   5  Extended
/dev/sda5             4660        4864     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 2011 MB, 2011168768 bytes
62 heads, 62  sectors/track, 1021 cylinders
Units = cylinders of 3844 * 512 =  1968128 bytes
Disk identifier: 0x000e1579

   Device Boot       Start         End      Blocks   Id  System
/dev/sdb1   *           1        1021     1962331    6  FAT16




---

### Post by Noadi on 2010-02-15
Okay you replied while I was copying that.

---

### Post by darolu on 2010-02-15
Don't worry about it, it happens a lot (confusing "L" with "one"), more than you would imagine.
I edited my last post with more info/instructions, post what parted gave you please.
Edit: I just read your post, it is /dev/sda1.

---

### Post by Noadi on 2010-02-15
I got:
> Model: Unknown (unknown)
Disk /dev/sda1: 38.3GB
Sector size  (logical/physical): 512B/512B
Partition Table: loop

Number   Start  End     Size    File system  Flags
 1      0.00B  38.3GB  38.3GB  ext3

---

### Post by darolu on 2010-02-15
Good, we are almost done; what happens is, you are using 7.04 LiveCD, that system identifies any ID=83 (in your fdisk info) as Ext2, but in reality it is Ext3, this is what causes the error, don't worry your info should be safe.
To fix this, type this in your command line:
```
sudo mkdir /media/mydrive
```
This will create a directory in /media that will be used as mount point for your hard drive.
Then do this:
```
gksu gedit /etc/fstab
```
You'll see a file that looks like:
```
# <file system>	<mount point>	<type>	<options>	<dump>	<pass>
proc	/proc	proc	defaults	0	0
# / was on /dev/sda5 during installation
UUID=7bf127fb-aa85-4bb1-bb38-c32bef9be900	/	ext4	errors=remount-ro	0	1
# /home was on /dev/sda6 during installation
UUID=cf396376-a6f1-456d-bd37-17dd36922f25	/home	ext4	defaults	0	2
# swap was on /dev/sda2 during installation
UUID=75670437-949c-48ee-97e8-641633ece53a	none	swap	sw	0	0
# cdrom/dvdrom
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0
```
At the end of the document type this line, save the file and close gedit (you can copy & pase):
```
/dev/sda1 /media/mydrive ext3 defaults,user,exec,rw 0 0
```
Afther that, back in your command line type:
```
sudo mount /dev/sda1
```
This should mount your hard drive, located at */media/mydrive* to access it with Nautilus and start backing your files up type this:
```
gksu nautilus /media/mydrive
```
A nautilus window should pop up and you will be able to copy your files with it (files should be under /home/youruser).

---

### Post by Noadi on 2010-02-15
Didn't work, getting: 
ubuntu@ubuntu:~$ sudo mount /dev/sda1
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

There wasn't much in the file that ```
gksu gedit /etc/fstab
``` brought up just:> aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

tried putting 
```
/dev/sda1 /media/mydrive ext3 defaults,user,exec,rw 0 0
```
at the end and replacing "/dev/sda5 swap swap defaults 0 0" with it and neither worked

---

### Post by darolu on 2010-02-15
No, don't replace the last line; it is normal your fstab file was that empty as it is a LiveCD one.

Your /etc/fstab file should look like:
```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

/dev/sda1 /media/mydrive ext3 defaults,**errors=remount-ro** 0 0
```
Notice how I replaced the options to include errors=remount-ro; save your file and try "sudo mount /dev/sda1" again.
Make sure the "/media/mydrive" directory does exist:
```
ls /media
```

---

### Post by Noadi on 2010-02-15
media/mydrive exists but still getting the same error even with the change you just made.

Thanks for being so patient with me.

---

### Post by darolu on 2010-02-15
Try forcing it with:
```
sudo mount -a -fv /dev/sda1
```

---

### Post by Noadi on 2010-02-15
This is what I'm getting now 
> ubuntu@ubuntu:~$ sudo mount -a -fv /dev/sda1
/dev/sda1 on /media/mydrive type ext3 (rw,errors=remount-ro)
ubuntu@ubuntu:~$ gksu nautilus /media/mydrive
(nautilus:4444): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:4444): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:4444): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:4444): WARNING **: No marshaller for signature of signal 'ShareCreateError'

(nautilus:4444): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time

---

### Post by darolu on 2010-02-15
Lets try a simpler approach, reboot with your LiveCD in to generate a fresh mtab; jump directly to edit your fstab file (gksu gedit /etc/fstab), use the first options I gave you. Make sure to create the directory again first (with sudo mkdir /media/mydirectory).
```
/dev/sda1 /media/mydirectory ext3 defaults,users,exec,rw 0 0
```
Then click on Places and your hard drive, lets see if it mounts that way.
If it doesn't work, it may be because you're using 7.04, I don't remember if 7.04 has support for ext3 file system; if it fails again, please type this in your command line (I don't remember what kernel 7.04 uses) and post what it gives you:
```
uname -srvo
```

---

### Post by Noadi on 2010-02-15
Thanks. I'm going to try that in the morning and let you know how it turns out. I have learned my lesson, back up, back up, back up. Especially important things like your business logo svg file.

---

### Post by Noadi on 2010-02-15
Making a brand new fresh bootable usb drive with latest version to see if that helps when I try again in the morning,

---

### Post by Noadi on 2010-02-16
Okay gave it one more try before bed using the last idea and no luck.
I got this error again:
> Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
uname -srvo
``` returned: Linux 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 GNU/Linux

Hopefully with sleep I'll be a little less frustrated, I'm about ready to scream and that would be bad at 2:15am.

---

### Post by ironclaw on 2010-02-16
It looks like a corrupted ext3 or ext4 file system. Try to fix that by booting up on a live CD, then run
```
sudo e2fsck -p /dev/sda1
```

This will call e2fsck to automatically repair the file system.

---

### Post by Noadi on 2010-02-16
Oh boy, I think I might be getting on over my head. Here's what I got:
> ubuntu@ubuntu:~$ sudo e2fsck -p /dev/sda1
Error reading block 4620802 (Attempt to read block from filesystem resulted in short read).  

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
Please tell me that isn't as scary as it sounds?

---

### Post by ironclaw on 2010-02-16
That doesn't sound too good. The safest thing to do now before attempting any more recovery is to image the partition to a backup file, so that if this partition is messed up later on, you will always have an original backup. To do that, you'll need to attach another hard drive (external will work) with at least 39 GB of free space. Mount the backup partition with at least 39 GB free, then
```
sudo dd bs=1M if=/dev/sda1 of=<path to backup partition>/sda1.img
```where <path to backup partition> will probably be a directory in /media/ if it is automounted. The command will write a file called sda1.img into the root directory of the backup partition, and will take 1-2 hours.

After that, unmount and disconnect the backup drive. Now you can do anything to /dev/sda1 - try running e2fsck in interactive mode:
```
sudo e2fsck /dev/sda1
```e2fsck will prompt you during the recovery process. You can probably answer 'yes' to all of the prompts, since you have a backup. Hopefully the file system will be repaired and the backup turns out to be redundant...

The backup part is of course up to you - if the data is important, image the partition before running e2fsck. If you can live without the data, you can skip the backup and hope for the best with e2fsck.

---

### Post by Noadi on 2010-02-16
Okay. Only slightly scary. Thankfully while the files are pretty important they aren't needed immediately, I can take my time to get this right. I'll make the backup image tonight and try e2fsck tomorrow.

---

