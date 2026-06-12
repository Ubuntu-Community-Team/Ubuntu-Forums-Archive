---
title: "Looking for info/tutorial about external media"
date: 2006-04-17
forum: General Help
---

### Post by dglp on 2006-04-17
I am haphazardly finding my way through Kubuntu and Linux at the same time. There are some very basic things that I haven't developed a clear idea about. One of those things has to do with the ways linux sees external devices, such as my external hard drives (via the USB port), my camera (also via USB), but that they aren't consistently accessible as drives/folders. I need to figure out a few things.

I see that every time I attach something to the USB port, it shows up as /media/sba1. I gather that I can assign different  paths/names for distinct devices, but I don't understand the terminology of what to write, where to write it, and some of the concepts around that process. 

So I'm looking for a combination of a tutorial for new users, and specifically for information about how various bits of hardware get recognised. 

Any recommendations?

---

### Post by aysiu on 2006-04-17
This tutorial is written specifically for Windows partitions, but the same logic applies to most external media, too: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by dglp on 2006-04-18
Thanks Aysiu, that's helped me through part of the process.

I'm still unclear about various things. For example, I don't understand part of a string: where the psychocats tutorial says
>  This is what it might look like before we change it: 
...
**/dev/hda1       /media/hda1        ntfs    defaults        0       0** and
>  This is what it should look like after we change it: 
...
**/dev/hda1       /windows        ntfs    nls=utf8,umask=0222        0       0** It's pretty clear that if I do something other than hda1, the part that says **nls=utf8,umask=0222 **will need to say something else. What is that part of the string doing? 

On a related point, let's say that I'm going to create a new mount point for external devices. Would I then do these same steps, starting by creating a directory? Let's call this directory /ext. Is that an OK name? I would be writing this ```
sudo mkdir /ext
``` and then editing fstab in some fashion to associate an external device with that directory. 

Yes? Partly? No?

---

### Post by aysiu on 2006-04-18
[QUOTE=dglp]
It's pretty clear that if I do something other than hda1, the part that says **nls=utf8,umask=0222 **will need to say something else. What is that part of the string doing?[/quote] Actually, this part has to do with the permissions with which the partition or drive is mounted.

It will not change based on the /dev location, but it will change based on the filesystem. For example, NTFS will be ```
ntfs nls=utf8,umask=0222 0 0
``` and FAT32 or FAT16 will be ```
vfat iocharset=utf8,umask=000 0 0
```

This is independent of the /dev location and mount point.

So you could very well have a line that reads: ```
/dev/sda1 /external vfat iocharset=utf8,umask=000 0 0
```

> 
On a related point, let's say that I'm going to create a new mount point for external devices. Would I then do these same steps, starting by creating a directory? Let's call this directory /ext. Is that an OK name? I would be writing this ```
sudo mkdir /ext
``` and then editing fstab in some fashion to associate an external device with that directory.  Every partition and drive needs a unique mount point. So, yes, if you create a directory called /ext for /dev/sda1, you would need to create another directory /ext_second for /dev/sdb1.

Now, generally, with external media, Ubuntu will just create temporary directories in /media for you, but it sounds as if you want to define your own static mount point for you device.

---

### Post by dglp on 2006-04-18
[quote=aysiu]Actually, this part has to do with the permissions with which the partition or drive is mounted.[/quote] Aha! Permissions! I was struggling with that earlier. When I hooked up the external hard drive and then tried to drop a file into it, I got this message.

[IMG]http://nunovo.zoto.com/img/45/96d734336e4e09a7a133ab308cd74263-.jpg[/IMG]
 and this
[IMG]http://nunovo.zoto.com/img/45/8b7c9e217589e8593e4752e849384be8-.jpg[/IMG]

[IMG]http://nunovo.zoto.com/img/45/df0dc9810895b9b34a177aaa9bd7ddb0-.jpg[/IMG]

I poked around looking for something that would allow me to change permissions. I'm used to looking in a Windows environment, so I was not making a lot of progress....

but eventually, by picking my GID and UID as owners, I was able to do this:[IMG]http://nunovo.zoto.com/img/640x480x1/479de9443bc8d366d76af15d23a8708c-.jpg[/IMG]

I have no idea whether I could have picked a 'better' owner - I only tried the IUD and GID as options. So your comments below about how permissions change depending on filesystem are quite relevant! Is there a list somewhere that will help me identify what permissions go with what devices/systems? For example,  my camera, or a parallel port ZIP drive, an Archos (mp3) Jukebox, or other devices? 
[quote=aysiu]It will not change based on the /dev location, but it will change based on the filesystem. For example, NTFS will be ```
ntfs nls=utf8,umask=0222 0 0
``` and FAT32 or FAT16 will be ```
vfat iocharset=utf8,umask=000 0 0
``` This is independent of the /dev location and mount point. So you could very well have a line that reads: ```
/dev/sda1 /external vfat iocharset=utf8,umask=000 0 0
``` Every partition and drive needs a unique mount point. So, yes, if you create a directory called /ext for /dev/sda1, you would need to create another directory /ext_second for /dev/sdb1.[/quote] sdA1, sdA2, sdB1? What are the naming conventions? Can I continue to add mount points under /media/sda# and devices under /dev/sda#? Do I need to make distinctions between serial, parallel, USB, et cetera? [quote=aysiu] Now, generally, with external media, Ubuntu will just create temporary directories in /media for you, but it sounds as if you want to define your own static mount point for you device.[/quote] Well, this was the confusing thing after my initial success. The first imte I hooked up my Camera, it showed up as sda1, and I moved some screenshots off the laptop and into the camera memory, then took the camera to a networked machgine and offloaded the images. When I went back to the laptop, sda1 failed to show any of the folders or images. I then tried hooking up the external HDD, with the same result. It came up as sda1, but showed no contents. I have eventually figured it out, and having a static mount point means I know where to look for the contents, and can put a shortcut on the taskbar.

Overall, I've made progress, but a lot of it is by lucky guesses! Not because I actually know what needs doing...;)

---

### Post by aysiu on 2006-04-18
[QUOTE=dglp]
I have no idea whether I could have picked a 'better' owner - I only tried the IUD and GID as options. So your comments below about how permissions change depending on filesystem are quite relevant![/quote] Well, the problem with FAT32 and NTFS is that these don't support Linux permissions (FAT32 doesn't support permissions at all), so you mount them using a *umask*, which I don't fully understand, but I think has something to do with the permissions for when files are created. The owner of FAT32 and NTFS partitions will always be *root*, as far as I know. The parameters outlined here

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

allow people other than the owner to read/write (FAT32) or read (NTFS) the Windows drive.

Ext3 is the opposite: it can be mounted with permissions, but it doesn't use *umask*. > Is there a list somewhere that will help me identify what permissions go with what devices/systems? For example,  my camera, or a parallel port ZIP drive, an Archos (mp3) Jukebox, or other devices? I don't know, but this may help:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
> sdA1, sdA2, sdB1? What are the naming conventions? I don't know, but I know that my hard drives show up as /dev/hda1, /dev/hda2, and if I have a second hard drive, it shows up as /dev/hdb1, /dev/hdb2. All my external devices show up as /dev/sda1, /dev/sdb1, etc. > Can I continue to add mount points under /media/sda# and devices under /dev/sda#? I actually advise that if you do mount points in /etc/fstab that you not use /media or /mnt as the folder of the mount point or the parent folder of the mount point. Sometimes that messes up the permissions, particularly for FAT32. > Do I need to make distinctions between serial, parallel, USB, et cetera? I don't know.

I've answered as best I know.

---

