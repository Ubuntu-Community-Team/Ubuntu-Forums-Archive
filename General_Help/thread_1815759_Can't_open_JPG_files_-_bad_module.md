---
title: "Can't open JPG files - bad module?"
date: 2011-07-31
forum: General Help
---

### Post by MDguy on 2011-07-31
While trying to install Cinelerra on Ubuntu 10.10, I copied/moved around some of the .so modules located under /usr/lib.  Now I find that I cannot open JPG images - Image Viewer will give me the following error (see screenshot):
```
Unable to load image-loading module:/usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-jpeg.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-jpeg.so: undefined symbol: jpeg_resync_to_restart
```Attempting to open the image with GIMP will give me (see screenshot 2):
```

GIMP Message
Plug-in crashed: "file-jpeg"
(/usr/lib/gimp/2.0/plug-ins/file-jpeg)

The dying plug-in may have messed up GIMP's internal state.
You may want to save your images and restart GIMP to be on the safe side.

GIMP message

Opening '/usr/share/backgrounds/Crocosmia_by_sirpecangum.jpg' failed:
Procedure 'file-jpeg-load' received no return 
values.

```PNG files will open fine.

Any assistance would be appreciated!

---

### Post by thefasterblueone on 2011-07-31
Try searching for the module and put it back in /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/


```
sudo find / -name libpixbufloader-jpeg.so
```

---

### Post by MDguy on 2011-07-31
> **thefasterblueone said:**
> Try searching for the module and put it back in /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/


```
sudo find / -name libpixbufloader-jpeg.so
```

Thanks for the reply, but when I looked I saw that the module is actually still there - perhaps it's corrupted?

EDIT: I obtained a copy of libpixbufloader-jpeg.so from the LiveCD and replaced the current module with new one, but I'm still getting the same error message.

---

### Post by thefasterblueone on 2011-07-31
How about reinstalling Gimp?

---

### Post by MDguy on 2011-08-01
> **thefasterblueone said:**
> How about reinstalling Gimp?
I'm fairly sure it's not a GIMP problem, since the images won't open with **ANY** image viewer/editor that I've tried.

---

### Post by MDguy on 2011-08-03
I am also finding that certain programs such as Filezilla and  Ubuntu Software Center will not open because of this problem.  If I type "filezilla" into the terminal, I get:
```
filezilla: symbol lookup error: /usr/lib/libtiff.so.4: undefined symbol: jpeg_resync_to_restart
```

---

### Post by MDguy on 2011-08-06
bump

---

### Post by MDguy on 2011-08-09
bump

---

### Post by ofnuts on 2011-08-09
> **MDguy said:**
> Thanks for the reply, but when I looked I saw that the module is actually still there - perhaps it's corrupted?

EDIT: I obtained a copy of libpixbufloader-jpeg.so from the LiveCD and replaced the current module with new one, but I'm still getting the same error message.
I'm not convinced your problem is with  libpixbufloader-jpeg.so. I'm not an expert in this, but the origina messagel is ambiguous, it may be telling you that  libpixbufloader-jpeg.so can't be loaded because it references a "jpeg_resync_to_restart" symbol than can't be found. 

You may be missing something a bit further downstream, such as libjpeg.so. If this is the case, you can also try to deinstall/resinstall it.

---

### Post by MDguy on 2011-08-09
> **ofnuts said:**
> I'm not convinced your problem is with  libpixbufloader-jpeg.so. I'm not an expert in this, but the origina messagel is ambiguous, it may be telling you that  libpixbufloader-jpeg.so can't be loaded because it references a "jpeg_resync_to_restart" symbol than can't be found. 

You may be missing something a bit further downstream, such as libjpeg.so. If this is the case, you can also try to deinstall/resinstall it.
Okay, I downloaded libjpeg-8b from [this]("http://www.linuxfromscratch.org/blfs/view/svn/general/libjpeg.html") site, and after installing it, I am getting this error:
[ATTACH]199689[/ATTACH]
It seems to have done something related to the problem, but still didn't repair it completely.

---

### Post by ofnuts on 2011-08-10
> **MDguy said:**
> Okay, I downloaded libjpeg-8b from [this]("http://www.linuxfromscratch.org/blfs/view/svn/general/libjpeg.html") site, and after installing it, I am getting this error:
[ATTACH]199689[/ATTACH]
It seems to have done something related to the problem, but still didn't repair it completely.Don't know why you download it from there.. this is part of your standard repository (package libjpeg62 on my 10.04). 

Installed files look like this (again, on my 10.04, if you have a  different distro version you may have a different libjpeg version).

```
ll /usr/lib/libjpeg.*
-rw-r--r-- 1 root root 165904 2010-03-12 15:22 /usr/lib/libjpeg.a
-rw-r--r-- 1 root root    941 2010-03-12 15:22 /usr/lib/libjpeg.la
lrwxrwxrwx 1 root root     17 2010-11-07 17:47 /usr/lib/libjpeg.so -> libjpeg.so.62.0.0
lrwxrwxrwx 1 root root     17 2010-10-01 00:40 /usr/lib/libjpeg.so.62 -> libjpeg.so.62.0.0
-rw-r--r-- 1 root root 128616 2010-03-12 15:22 /usr/lib/libjpeg.so.62.0.0

```

So look for the files, and check if your links are still OK (in a Unix install, the *.so are usually links to specific versions (*.so.nn.nn.nn)

---

### Post by MDguy on 2011-08-10
My output looks fairly similar:
```
ll /usr/lib/libjpeg.*
-rw-r--r-- 1 root root 1298934 2011-08-09 19:37 /usr/lib/libjpeg.a
-rwxr-xr-x 1 root root     914 2011-08-09 19:37 /usr/lib/libjpeg.la*
lrwxrwxrwx 1 root root      13 2011-08-09 19:37 /usr/lib/libjpeg.so -> libjpeg.so.62
-rw-r--r-- 1 root root   38212 2011-07-27 17:36 /usr/lib/libjpeg.so.62
lrwxrwxrwx 1 root root      16 2011-08-09 19:37 /usr/lib/libjpeg.so.8 -> libjpeg.so.8.0.2*
-rwxr-xr-x 1 root root  797643 2011-08-09 19:37 /usr/lib/libjpeg.so.8.0.2*
```

I tried reinstalling libjpeg62 using the command "sudo apt-get install --reinstall libjpeg62", but it gave me this error:
```
sudo apt-get install --reinstall libjpeg62
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of libjpeg62 is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

---

### Post by ofnuts on 2011-08-10
> **MDguy said:**
> My output looks fairly similar:
```
ll /usr/lib/libjpeg.*
-rw-r--r-- 1 root root 1298934 2011-08-09 19:37 /usr/lib/libjpeg.a
-rwxr-xr-x 1 root root     914 2011-08-09 19:37 /usr/lib/libjpeg.la*
lrwxrwxrwx 1 root root      13 2011-08-09 19:37 /usr/lib/libjpeg.so -> libjpeg.so.62
-rw-r--r-- 1 root root   38212 2011-07-27 17:36 /usr/lib/libjpeg.so.62
lrwxrwxrwx 1 root root      16 2011-08-09 19:37 /usr/lib/libjpeg.so.8 -> libjpeg.so.8.0.2*
-rwxr-xr-x 1 root root  797643 2011-08-09 19:37 /usr/lib/libjpeg.so.8.0.2*
```I tried reinstalling libjpeg62 using the command "sudo apt-get install --reinstall libjpeg62", but it gave me this error:
```
sudo apt-get install --reinstall libjpeg62
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of libjpeg62 is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

Similar but still quite different.
- Your libjpeg.a is much bigger 
- Your libjpeg.so.62 is much smaller than mine
- You obviously have two versions (v8 is from 10.10 it seems).

Since you are on 10.10 your repository may have a more recent version of libjpeg than 6.2 (8?)

---

### Post by MDguy on 2011-08-12
> **ofnuts said:**
> Similar but still quite different.
- Your libjpeg.a is much bigger 
- Your libjpeg.so.62 is much smaller than mine
- You obviously have two versions (v8 is from 10.10 it seems).

Since you are on 10.10 your repository may have a more recent version of libjpeg than 6.2 (8?)
So how should I go about fixing this?  From the output Filezilla gives, it seems like libjpeg may not be the only problem.

---

### Post by ofnuts on 2011-08-13
> **MDguy said:**
> So how should I go about fixing this?  From the output Filezilla gives, it seems like libjpeg may not be the only problem.
Backup your /home and reinstall?

---

