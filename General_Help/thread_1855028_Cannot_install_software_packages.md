---
title: "Cannot install software packages"
date: 2011-10-05
forum: General Help
---

### Post by anotherstiffler on 2011-10-05
Hello,

Getting a pretty annoying set of errors that I believe are all related.

1. When I use the terminal with sudo apt-get upgrade, I get this error at the end
[HTML]debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up libssl1.0.0 (1.0.0e-2ubuntu4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing libssl1.0.0 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libssl1.0.0:i386 (1.0.0e-2ubuntu4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing libssl1.0.0:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up lightdm (1.0.1-0ubuntu3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing lightdm (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openssl:
 openssl depends on libssl1.0.0 (>= 1.0.0); however:
  Package libssl1.0.0 is not configured yet.
dpkg: error processing openssl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libssl1.0.0
 libssl1.0.0:i386
 lightdm
 man-db
 openssl
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/HTML]

2. When I try to use Ubuntu Software Manager to install a program, I get this error (if it doesn't automatically just crash to begin with):

[HTML]installArchives() failed: debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up libssl1.0.0 (1.0.0e-2ubuntu4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing libssl1.0.0 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 libssl1.0.0
Setting up libssl1.0.0 (1.0.0e-2ubuntu4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing libssl1.0.0 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libssl1.0.0:i386 (1.0.0e-2ubuntu4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing libssl1.0.0:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openssl:
 openssl depends on libssl1.0.0 (>= 1.0.0); however:
  Package libssl1.0.0 is not configured yet.
dpkg: error processing openssl (--configure):
 dependency problems - leaving unconfigured
Setting up lightdm (1.0.1-0ubuntu3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing lightdm (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 libssl1.0.0
[/HTML]

3. When I try to install using Synaptic Package Manager I get this error:
[HTML]debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up libssl1.0.0 (1.0.0e-2ubuntu4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing libssl1.0.0 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libssl1.0.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libssl1.0.0 (1.0.0e-2ubuntu4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing libssl1.0.0 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libssl1.0.0:i386 (1.0.0e-2ubuntu4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing libssl1.0.0:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openssl:
 openssl depends on libssl1.0.0 (>= 1.0.0); however:
  Package libssl1.0.0 is not configured yet.
dpkg: error processing openssl (--configure):
 dependency problems - leaving unconfigured
Setting up lightdm (1.0.1-0ubuntu3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing lightdm (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 libssl1.0.0
 libssl1.0.0:i386
 man-db
 openssl
 lightdm
[/HTML]

Any ideas on what I should do? Didn't want to mess with those packages since they seem important to the OS.

---

### Post by Bucky Ball on 2011-10-05
Have you got Synaptic Package Manager open at the same time?

'sudo apt-get update' should be run before the 'sudo apt-get upgrade' command. ;)

ps: I have asked mods to move this thread as the Community Cafe forum is not intended for problem solving but light-hearted banter ...

---

### Post by philinux on 2011-10-05
Moved to General Help.

---

### Post by anotherstiffler on 2011-10-05
> **Bucky Ball said:**
> Have you got Synaptic Package Manager open at the same time?

'sudo apt-get update' should be run before the 'sudo apt-get upgrade' command. ;)

Of course not! Well, admittedly I did once, but I learned my lesson quickly. Heh.

And I did run the update before upgrade multiple times, but I'll go ahead and try a few more times. :P

---

### Post by anotherstiffler on 2011-10-05
> **philinux said:**
> Moved to General Help.

My apologies. I had multiple tabs open and thought I was publishing this in the right spot. Thanks for moving this around.

---

### Post by philinux on 2011-10-05
> **anotherstiffler said:**
> My apologies. I had multiple tabs open and thought I was publishing this in the right spot. Thanks for moving this around.

No worries. 

Just to make sure I'd reboot and then try update and upgrade.
Post back if you got same errors.

---

### Post by anotherstiffler on 2011-10-05
Alright. Rebooted and launched the terminal with "sudo apt-get update". Received an error within a few seconds:

"Sorry, the package "flashplugin-install 10.3.183.10ubuntu5" failed to install or upgrade."

Followed by, "System program problem detected."

And then, "Sorry, the package "ttf-mscorefonts-installer 3.3ubuntu4" failed to install or upgrade."

And finally, "Sorry, Update Manager closed unexpectedly."

The apt-get update finished in the terminal, I hit "report problem" on those error windows, and continued with apt-get upgrade, which seemed to work fine. Closed the terminal to install Audacity via Ubuntu Software, which worked fine. Successfully uninstalled and reinstalled Synapse via Synaptic Package Manager as well.

All seems fine now, except for those errors at the start. Any ideas on what those could be from?

---

### Post by philinux on 2011-10-05
> **anotherstiffler said:**
> Alright. Rebooted and launched the terminal with "sudo apt-get update". Received an error within a few seconds:

"Sorry, the package "flashplugin-install 10.3.183.10ubuntu5" failed to install or upgrade."

Followed by, "System program problem detected."

And then, "Sorry, the package "ttf-mscorefonts-installer 3.3ubuntu4" failed to install or upgrade."

And finally, "Sorry, Update Manager closed unexpectedly."

The apt-get update finished in the terminal, I hit "report problem" on those error windows, and continued with apt-get upgrade, which seemed to work fine. Closed the terminal to install Audacity via Ubuntu Software, which worked fine. Successfully uninstalled and reinstalled Synapse via Synaptic Package Manager as well.

All seems fine now, except for those errors at the start. Any ideas on what those could be from?

Make sure all synaptic update manager are closed. Open a terminal and report back exactly what it says.

```
sudo dpkg --configure -a
```

Use copy and paste to get that into the terminal.

---

### Post by anotherstiffler on 2011-10-05
Got back nothing at all.

---

### Post by philinux on 2011-10-05
> **anotherstiffler said:**
> Got back nothing at all.

Well that's a good sign.

How about.

sudo apt-get install -f

---

### Post by anotherstiffler on 2011-10-05
Here's what I get in return.

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libatk1.0-0:i386 libcogl5 libswscale0 gnome-js-common gir1.2-gstreamer-0.10
  libxcomposite1:i386 libavutil50 nspluginwrapper gir1.2-upowerglib-1.0
  libseed0 gir1.2-telepathyglib-0.12 gir1.2-json-1.0 libnspr4-0d:i386
  libcairo2:i386 libindicator3-3 libmozjs185-1.0 mutter-common
  gir1.2-polkit-1.0 xulrunner-2.0-mozjs libavcodec52 libdatrie1:i386
  libmutter0 gir1.2-telepathylogger-0.2 libgdk-pixbuf2.0-0:i386
  libpanel-applet-4-0 libpixman-1-0:i386 libclutter-1.0-common
  libxinerama1:i386 gjs nspluginviewer:i386 libxft2:i386 libdbusmenu-gtk3-3
  libclutter-1.0-0 libthai0:i386 libpostproc51 libavformat52 libjasper1:i386
  gir1.2-mutter-3.0 libpango1.0-0:i386 libxcb-render0:i386 libxcursor1:i386
  libxcb-shm0:i386 libcogl-common gir1.2-panelapplet-4.0 mysql-common
  libxrandr2:i386 libnss3-1d:i386 libgjs0c libgtk2.0-0:i386 gir1.2-cogl-1.0
  gir1.2-clutter-1.0 libllvm2.9:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


---

### Post by gordintoronto on 2011-10-05
What version of Ubuntu? It sounds like you have Update Manager running when you try to run other programs which conflict.

---

### Post by philinux on 2011-10-06
> **anotherstiffler said:**
> Here's what I get in return.

That looks absolutely fine.

Just run.

```
sudo apt-get autoremove
```

Look here for info on the above command and more:-
```
man apt-get
```

After that just run the normal update manager and see what it says. Should be fine.

---

### Post by anotherstiffler on 2011-10-07
> **philinux said:**
> That looks absolutely fine.

Just run.

```
sudo apt-get autoremove
```

Look here for info on the above command and more:-
```
man apt-get
```

After that just run the normal update manager and see what it says. Should be fine.

Seems to me that everything is working. Thanks for all of the help!

Now I just need to figure out how to get Minecraft running. :P

---

### Post by Bucky Ball on 2011-10-07
Nice work all! Please mark as 'Solved' from 'Thread Tools' to help others. ;)

---

### Post by anotherstiffler on 2011-10-08
> **Bucky Ball said:**
> Nice work all! Please mark as 'Solved' from 'Thread Tools' to help others. ;)

Done! Thanks for all of the help, guys. If any of you have any thought on how to fix my video driver problem now, I would love to see what those are. :)

[http://ubuntuforums.org/showthread.php?t=1856691](http://ubuntuforums.org/showthread.php?t=1856691)

---

