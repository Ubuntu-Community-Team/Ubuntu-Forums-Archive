---
title: "Patch my kernel?"
date: 2012-03-31
forum: General Help
---

### Post by eakergd on 2012-03-31
I deleted this post off the laptops forum, because it is a question that belongs in the general help forum, and is not specific to laptops. So please don't lock this thread.

Help, please. I have a Sony Vaio F-series -- a lot of little  stuff like the Sony keys, brightness, and the backlit keyboard are not  working. I found a patch file, but I don't know how to apply it. Is it a patch for the kernel or the sony-laptop module?  -- How do you tell?   Anyway, if someone could help I would be most appreciative. The patch  can be found here: [http://code.google.com/p/vaio-f11-li...3-2.6.39.patch]("http://code.google.com/p/vaio-f11-linux/downloads/detail?name=vaio-test13-2.6.39.patch")


Thanks,

Gary

---

### Post by HiImTye on 2012-03-31
from that page, if you go to 'project home' then you can see full instructions on how to use it

---

### Post by eakergd on 2012-03-31
Yes, that instruction file says to go to /usr/src/linux, but that directory doesn't exist on my system. I have /usr/src/linux-headers-3.0.0.12, and /usr/src/linux-headers-3.0.0.12-generic. Not sure which one has the kernel I need to patch.

I tried applying the patch in both of those directories, and all I got was a bunch of errors.

---

### Post by Thewhistlingwind on 2012-03-31
Open a terminal window:

Change directories to the one that your source files are in:

```
cd /path/to/your/directory
```For example, for Music it would be:

```
cd /home/myusername/Music
```OR

```
~/Music
```The ~ expands to your home directory.

To apply the patch:

```
man patch
```Will tell you more about the patch utility. 

You'll have to go over the kernel sources with it. (You can download them from [http://www.kernel.org/](http://www.kernel.org/))

I'm pretty sure a copy of the Ubuntu version of the Linux kernel is in /usr/src/ and you can patch that version and compile it. (I only link kernel.org in case you want to go the whole mile and compile a whole new kernel. You probably just want the Ubuntu Linux kernel source.)

Theres Internet tutorials elsewhere on compiling your patched kernel.

---

### Post by electrojustin on 2012-03-31
Have you installed linux-source? If thats the case I believe it puts the source in a compressed file in /usr/src (maybe called linux-source-<your version number here>.tar.bz2?). It looks like the tutorial just sorta assumes you uncompress the source into /usr/src/linux.

---

### Post by electrojustin on 2012-03-31
Oh and a word of advice as far as kernel recompiling goes: you may want to use xconfig instead of menuconfig-I find it just overall easier to use.

---

### Post by eakergd on 2012-04-01
OK, thanks for the help so far. I downloaded the source files, so now I have linux-source-3.0. Now when I switch to that directory and attempt to patch, I am still getting errors. It says it cannot find the file to patch.

Here is the output of the patch program:

dad@dad-laptop:/usr/src/linux-source-3.0.0$ sudo patch -p1 < /home/dad/Desktop/vaio-test13-2.6.39.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Signed-off-by: Marco Chiappero <marco@absence.it>
|--- a/include/linux/sonypi.h    2011-04-19 06:26:00.000000000 +0200
|+++ b/include/linux/sonypi.h    2011-04-22 17:15:33.832788228 +0200
--------------------------
File to patch: linux-source-3.0.0.tar.bz2
patching file linux-source-3.0.0.tar.bz2
Hunk #1 FAILED at 114.
1 out of 1 hunk FAILED -- saving rejects to file linux-source-3.0.0.tar.bz2.rej
can't find file to patch at input line 14
Perhaps you used the wrong -p or --strip option?


It keeps giving me the same error for each hunk. 

Any ideas what I should try next?

Thanks,

---

### Post by eakergd on 2012-04-01
bump

---

### Post by pbrane on 2012-04-01
> **eakergd said:**
> OK, thanks for the help so far. I downloaded the source files, so now I have linux-source-3.0. Now when I switch to that directory and attempt to patch, I am still getting errors. It says it cannot find the file to patch.

Here is the output of the patch program:

dad@dad-laptop:/usr/src/linux-source-3.0.0$ sudo patch -p1 < /home/dad/Desktop/vaio-test13-**2.6.39**.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Signed-off-by: Marco Chiappero <marco@absence.it>
|--- a/include/linux/sonypi.h    2011-04-19 06:26:00.000000000 +0200
|+++ b/include/linux/sonypi.h    2011-04-22 17:15:33.832788228 +0200
--------------------------
File to patch: linux-source-3.0.0.tar.bz2
patching file linux-source-3.0.0.tar.bz2
Hunk #1 FAILED at 114.
1 out of 1 hunk FAILED -- saving rejects to file linux-source-3.0.0.tar.bz2.rej
can't find file to patch at input line 14
Perhaps you used the wrong -p or --strip option?


It keeps giving me the same error for each hunk. 

Any ideas what I should try next?

Thanks,

This looks like a patch for the 2.6.39 kernel, it obviously isn't working for your 3.0.0 kernel. You need to find a patch for your specific kernel or see if the latest kernel has what you need. You may be able to look at the patch in a text editor and apply the code fix manually to the kernel source. You *really* need to know what you are doing though.

You can review this to see how to build a new kernel on ubuntu.
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")

---

### Post by matt_symes on 2012-04-01
Hi

From the terminal, type

```
pwd
```

and 

```
ls
```

Post back results here.

Kind regards

---

### Post by eakergd on 2012-04-04
OK, after a little investigation, I determined that the sony_laptop module is included in my kernel, but the defaults are set wrong - lsmod shows that the module is loaded.

I found this post on an arch-linux forum: 

 						There is a solution with the unpatched standard-kernel:
Seems  as if with the last kernel-update the default-option of the backlight  is set to non-active. To enable the keyboard backlight  `/sys/devices/platform/sony-laptop/kbd_backlight` has to be set to "1".  Also there is /sys/devices/platform/sony-laptop/kbd_backlight_timeout`,  where you may set: 0(default)=10secs, 1=30secs, 2=60secs and  3=unlimited.


When I go to the /sys/devices/platform/sony-laptop directory, there is indeed a file called kbd_backlight that has only the number "0" in it. There is also a file called kbd_backlight_timeout with the same entry. So when I attempt to edit these files with "sudo gedit" I get the following error: "Could not create a backup file while saving /sys/devices/platform/sony-laptop/kbd_backlight" with a button that says "save anyway" but nothing happens when I try to save anyway.


So I got the bright idea to boot from a live disk, but when I mount the hard drive and navigate to the sys folder, it is empty, so I am assuming that this folder is populated by the kernel when I boot up.


So what is populating this folder, and how do I change the settings that are found in it?


Thanks, again.


BTW, I studied a little about modifying the kernel, and I am really not interested in learning to program. I just want this freakin' thing to work. I haven't been this frustrated with linux since I started using it over 2 years ago.

---

### Post by eakergd on 2012-04-04
bump

---

### Post by brainwash on 2012-04-04
You should edit the files with *gksu gedit* instead of plain sudo, because gedit is a graphical application.

The changes have to be reapplied on every boot, so you might just add following lines to the startup script */etc/rc.local* (before exit 0):
```
echo 1 > /sys/devices/platform/sony-laptop/kbd_backlight
echo 0 > /sys/devices/platform/sony-laptop/kbd_backlight_timeout
```

---

### Post by eakergd on 2012-04-04
> **brainwash said:**
> You should edit the files with *gksu gedit* instead of plain sudo, because gedit is a graphical application.

The changes have to be reapplied on every boot, so you might just add following lines to the startup script */etc/rc.local* (before exit 0):
```
echo 1 > /sys/devices/platform/sony-laptop/kbd_backlight
echo 0 > /sys/devices/platform/sony-laptop/kbd_backlight_timeout
```


YOU ROCK, brainwash!! Thank you! Only change I made was I sent a "echo 10" instead of "echo 0" to the second line. 

Four days to figure this out ... Thanks a bundle!

---

