---
title: "problem installing packages &amp; software through synaptic &amp; software center"
date: 2010-09-30
forum: General Help
---

### Post by chinmay3 on 2010-09-30
I don't know what gone wrong but nowdays whenever I try to install new software or packages from software center or through synaptic package manager every time I get some random error messages. I checked threads for similar problems but can't find any useful solution.
I am attaching some screenshots to help , if anyone can help me.
any type of help will be appreciated.
thank you in advance

---

### Post by andrewthomas on 2010-09-30
Try 

```
sudo dpkg --configure -a
```

---

### Post by sikander3786 on 2010-09-30
Also try

```

sudo apt-get install -f

```

from a terminal if the above one doesn't fix it.

---

### Post by chinmay3 on 2010-10-01
I tried above command but problem is as it is. I got following error messages.

---

### Post by sikander3786 on 2010-10-01
What about sudo apt-get install -f ?

Instead of posting thumbnails, just copy paste the output from the terminal.

---

### Post by chinmay3 on 2010-10-01
> **sikander3786 said:**
> What about sudo apt-get install -f ?

Instead of posting thumbnails, just copy paste the output from the terminal.
when I did as you suggested I got following output in terminal.........

chinmay@chinmay-desktop:~$ sudo apt-get install -f
[sudo] password for chinmay: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 liblash2 libbinio1ldbl libdiscid0 vcdimager libaudclient2
  libsvga1 libresid-builder0c2a libsox-fmt-ao libopenjpeg2 transcode-doc
  dvdauthor libcue1 blt python-tk libgnomecanvasmm-2.6-1c2a libsox-fmt-pulse
  libaudid3tag2 ffmpeg liblzo2-2 libavfilter0 libsox-fmt-mp3 libmowgli1
  libsox-fmt-base libfluidsynth1 sox libsox-fmt-oss libaudcore1 libsidplay2
  libsox-fmt-alsa libgnomemm-2.6-1c2 apport-hooks-medibuntu libgconfmm-2.6-1c2
  libmcs1 libgnome-vfsmm-2.6-1c2a libgnomeuimm-2.6-1c2a libsox1a
  libglademm-2.4-1c2a libmusicbrainz3-6 libavdevice52
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 133 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up automake (1:1.11.1-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing automake (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gnome-common:
 gnome-common depends on automake (>= 1:1.9); however:
  Package automake is not configured yet.
dpkg: error processing gnome-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 automake
 gnome-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sikander3786 on 2010-10-01
Try

```

sudo apt-get install --reinstall gnome-common automake

```

If that doesn't help either, as a last resort you can see post # 5 in the following thread.

[http://ubuntuforums.org/showthread.php?p=9880309](http://ubuntuforums.org/showthread.php?p=9880309)

Before that, you should wait for some other useful replies from mates. Might be some one figures a better way out.

---

### Post by chinmay3 on 2010-10-01
> **sikander3786 said:**
> Try

```

sudo apt-get install --reinstall gnome-common automake

```

If that doesn't help either, as a last resort you can see post # 5 in the following thread.

[http://ubuntuforums.org/showthread.php?p=9880309](http://ubuntuforums.org/showthread.php?p=9880309)

Before that, you should wait for some other useful replies from mates. Might be some one figures a better way out.
No luck. Problem persisting .
output of above command is .....
chinmay@chinmay-desktop:~$ sudo apt-get install --reinstall gnome-common automake
[sudo] password for chinmay: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 liblash2 libbinio1ldbl libdiscid0 vcdimager libaudclient2
  libsvga1 libresid-builder0c2a libsox-fmt-ao libopenjpeg2 transcode-doc
  dvdauthor libcue1 blt python-tk libgnomecanvasmm-2.6-1c2a libsox-fmt-pulse
  libaudid3tag2 ffmpeg liblzo2-2 libavfilter0 libsox-fmt-mp3 libmowgli1
  libsox-fmt-base libfluidsynth1 sox libsox-fmt-oss libaudcore1 libsidplay2
  libsox-fmt-alsa libgnomemm-2.6-1c2 apport-hooks-medibuntu libgconfmm-2.6-1c2
  libmcs1 libgnome-vfsmm-2.6-1c2a libgnomeuimm-2.6-1c2a libsox1a
  libglademm-2.4-1c2a libmusicbrainz3-6 libavdevice52
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 133 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up automake (1:1.11.1-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing automake (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gnome-common:
 gnome-common depends on automake (>= 1:1.9); however:
  Package automake is not configured yet.
dpkg: error processing gnome-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 automake
 gnome-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

ok thanks. I will wait & watch if anybody else has solution.

---

### Post by plucky on 2010-10-01
> Setting up automake (1:1.11.1-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing automake (--configure):
subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gnome-common:
gnome-common depends on automake (>= 1:1.9); however:
Package automake is not configured yet.
dpkg: error processing gnome-common (--configure):
dependency problems - leaving unconfigured

You probably need to get the system to download the automake.deb file again.

Try from a terminal ```
sudo apt-get clean
sudo apt-get install --reinstall gnome-common automake
```

The first command will delete all the files that were previously downloaded and stored in /var/cache/apt/archives,so if you want to save them,do so before you run the "clean" command.

Good luck

---

### Post by chinmay3 on 2010-10-01
> **plucky said:**
> You probably need to get the system to download the automake.deb file again.

Try from a terminal ```
sudo apt-get clean
sudo apt-get install --reinstall gnome-common automake
```

The first command will delete all the files that were previously downloaded and stored in /var/cache/apt/archives,so if you want to save them,do so before you run the "clean" command.

Good luck
This one also useless. After putting these commands I got same error messages again.
& even though when I tried to install one package I got following error message.........

installArchives() failed: perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Selecting previously deselected package xbmc-dbg. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 228550 files and directories currently installed.) 
Unpacking xbmc-dbg (from .../xbmc-dbg_1%3a9.11-lucid3_i386.deb) ... 
Setting up automake (1:1.11.1-1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing automake (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of gnome-common: 
 gnome-common depends on automake (>= 1:1.9); however: 
  Package automake is not configured yet. 
dpkg: error processing gnome-common (--configure): 
 dependency problems - leaving unconfigured 
Setting up xbmc-dbg (1:9.11-lucid3) ... 
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing: 
 automake 
 gnome-common 
dpkg: dependency problems prevent configuration of gnome-common: 
 gnome-common depends on automake (>= 1:1.9); however: 
  Package automake is not configured yet. 
dpkg: error processing gnome-common (--configure): 
 dependency problems - leaving unconfigured
Thanks.

---

### Post by sikander3786 on 2010-10-01
Manually clean up your apt-get cache as described in the link in my above post. I doubt if there is any other solution left for this.

---

### Post by chinmay3 on 2010-10-02
:guitar: Finally it get solved. I manually cleaned packages ( gnome-common & automake ) & thereafter it seems like everything is going fine. 

Thanks all for such a great support.

---

