---
title: "I can't install Webcamstudio in 11.04"
date: 2011-04-29
forum: General Help
---

### Post by oopsie on 2011-04-29
I downloaded the 0.56 deb file from the webcamstudio site, The first problem was that double clicking it appeared to do nothing. But I did some searching and found how to install using gdebi.

But if I look at the terminal part of gdebi it says this
```

install: cannot stat `webcamstudio.ko': No such file or directory
make: *** [install] Error 1

 * Modprobe webcamstudio failed. Please use 'dmesg' to find out why.

```


Does anybody know what's going on and how to fix it?

---

### Post by huangweiqiu on 2011-04-29
Make sure you follow the official tutorial step by step

[http://www.ws4gl.org/download/installing-on-ubuntu](http://www.ws4gl.org/download/installing-on-ubuntu)

---

### Post by oopsie on 2011-04-29
I'm not doing anything different than when I used webcamstudio in 10.10 or 10.04

But okay, lets follow your advice and follow the official tutorial.
```
Locate the Webcamstudio.deb package, double click it and follow the prompts for an installation.
```
Double clicking it does nothing. I have to use gdebi or the command line to install it.

During installation I get the error I posted about earlier.

So there you are. Step 1, and no success.

---

### Post by es@urito on 2011-05-02
Same problem here. Any ideas?

---

### Post by wh1zz0 on 2011-07-16
> **es@urito said:**
> Same problem here. Any ideas?

Just cd to the directory where you downloaded your webcamstudio .deb package (webcamstudio_0.56_all.deb) and run the following command.

```
sudo dpkg -i webcamstudio_0.56_all.deb

```

Worked for me.

---

### Post by radiobuzzer on 2011-09-04
I also have the same problem. I get the same error, even if trying with dpkg from commandline. There problem is somewhere else

---

### Post by arkmundi on 2011-09-29
Ditto with the problem install.  FYI, the deb wanted to open with Ubuntu Software Center, so OK to that, took some time trying to install, then I get an icon in my applications list, but no application behind it!  Will try & try again, gotta be a way!

---

### Post by arkmundi on 2011-09-29
Here's the install listing:
(Reading database ... 168913 files and directories currently installed.)
Preparing to replace webcamstudio 0.56 (using webcamstudio_0.56_all.deb) ...
Unpacking replacement webcamstudio ...
Setting up webcamstudio (0.56) ...
Removing the webcamstudio module from memory
ERROR: Module webcamstudio does not exist in /proc/modules
Removing webcamstudio.ko from the modules
rm: cannot remove `/lib/modules/2.6.38-11-generic/kernel/drivers/misc/webcamstudio.ko': No such file or directory
Restating the webcamstudio service to update the module
 * Stopping WebcamStudio kernel module webcamstudio                      [ OK ] 
 * Starting WebcamStudio kernel module webcamstudio                             make -C /lib/modules/2.6.38-11-generic/build SUBDIRS=/tmp/webcamstudio-src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  CC [M]  /tmp/webcamstudio-src/webcamstudio.o
/tmp/webcamstudio-src/webcamstudio.c:191:2: error: #error "need CONFIG_VIDEO_V4L1_COMPAT"
/tmp/webcamstudio-src/webcamstudio.c:215:28: fatal error: linux/videodev.h: No such file or directory
compilation terminated.
make[2]: *** [/tmp/webcamstudio-src/webcamstudio.o] Error 1
make[1]: *** [_module_/tmp/webcamstudio-src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make: *** [all] Error 2
install -d /lib/modules/2.6.38-11-generic/kernel/drivers/misc
install -m 644 -c webcamstudio.ko /lib/modules/2.6.38-11-generic/kernel/drivers/misc
install: cannot stat `webcamstudio.ko': No such file or directory
make: *** [install] Error 1

 * Modprobe webcamstudio failed. Please use 'dmesg' to find out why.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for ureadahead ...
Processing triggers for python-support ...

---

### Post by arkmundi on 2011-09-29
From:
[http://ubuntuforums.org/showthread.php?t=1752243](http://ubuntuforums.org/showthread.php?t=1752243)
Config_video_v4l1_compat
we see that:  
"I've realized that my kernel 2.6.38-9-generic-pae is compiled without CONFIG_VIDEO_V4L1_COMPAT."
I've got 2.6.38-11-generic from fresh,clean install of natty, so ... that appears to be the problem.

---

