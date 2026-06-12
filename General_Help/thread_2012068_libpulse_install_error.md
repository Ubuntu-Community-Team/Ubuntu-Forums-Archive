---
title: "libpulse install error"
date: 2012-06-28
forum: General Help
---

### Post by crotty on 2012-06-28
Hi,

I have an error when I try to fix my current 12.04 LTS installation. It involved libpulse, but I can't seem to figure out what to do here.

```
root@chopper:~# uname -a
Linux chopper 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
root@chopper:~# cat /etc/motd
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-24-generic x86_64)
```

```

root@chopper:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libpulse0
The following packages will be upgraded:
  libpulse0
1 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.
11 not fully installed or removed.
Need to get 0 B/289 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: error processing libpulse0 (--configure):
 libpulse0:amd64 1:1.1-0ubuntu15 cannot be configured because libpulse0:i386 is in a different version (1:1.1-0ubuntu15.1)
dpkg: error processing libpulse0:i386 (--configure):
 libpulse0:i386 1:1.1-0ubuntu15.1 cannot be configured because libpulse0:amd64 is in a different version (1:1.1-0ubuntu15)
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libpulse-mainloop-glib0:
 libpulse-mainloop-glib0 depends on libpulse0 (>= 1:1.1-0ubuntu15.1); however:
  Version of libpulse0 on system is 1:1.1-0ubuntu15.
dpkg: error processing libpulse-mainloop-glib0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpulse-mainloop-glib0:i386:
 libpulse-mainloop-glib0:i386 depends on libpulse0 (>= 1:1.1-0ubuntu15.1); however:
  Package libpulse0:i386 is not configured yet.
dpkg: error processing libpulse-mainloop-glib0:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpulsedsp:
 libpulsedsp depends on libpulse0 (>= 1:1.1-0ubuntu15.1); however:
No apport report written because MaxReports is reached already
                                                                Version of libpulse0 on system is 1:1.1-0ubuntu15.
dpkg: error processing libpulsedsp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpulsedsp:i386:
 libpulsedsp:i386 depends on libpulse0 (>= 1:1.1-0ubuntu15.1); however:
No apport report written because MaxReports is reached already
                                                                Package libpulse0:i386 is not configured yet.
dpkg: error processing libpulsedsp:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio-utils:
 pulseaudio-utils depends on libpulse0 (>= 1:1.1-0ubuntu15.1); however:
  Version of libpulse0 on system is 1:1.1-0ubuntu15.
 pulseaudio-utils depends on libpulsedsp; however:
  Package libpulsedsp is not configured yet.
dpkg: error processing pulseaudio-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pulseaudio:
 pulseaudio depends on libpulse0 (>= 1:1.1-0ubuntu15.1); however:
  Version of libpulse0 on system is 1:1.1-0ubuntu15.
 pulseaudio depends on pulseaudio-utils; however:
  Package pulseaudio-utils is not configured yet.
dpkg: error processing pulseaudio (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pulseaudio-esound-compat:
 pulseaudio-esound-compat depends on libpulse0 (>= 1:1.1-0ubuntu15.1); however:
  Version of libpulse0 on system is 1:1.1-0ubuntu15.
 pulseaudio-esound-compat depends on pulseaudio; however:
  Package pulseaudio is not configured yet.
dpkg: error processing pulseaudio-esound-compat (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pulseaudio-module-x11:
 pulseaudio-module-x11 depends on libpulse0 (>= 1:1.1-0ubuntu15.1); however:
  Version of libpulse0 on system is 1:1.1-0ubuntu15.
 pulseaudio-module-x11 depends on pulseaudio; however:
  Package pulseaudio is not configured yet.
 pulseaudio-module-x11 depends on pulseaudio-utils; however:
  Package pulseaudio-utils is not configured yet.
dpkg: error processing pulseaudio-module-x11 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pulseaudio-module-bluetooth:
 pulseaudio-module-bluetooth depends on libpulse0 (>= 1:1.1-0ubuntu15.1); however:
  Version of libpulse0 on system is 1:1.1-0ubuntu15.
 pulseaudio-module-bluetooth depends on pulseaudio; however:
  Package pulseaudio is not configured yet.
dpkg: error processing pulseaudio-module-bluetooth (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libpulse0
 libpulse0:i386
 libpulse-mainloop-glib0
 libpulse-mainloop-glib0:i386
 libpulsedsp
 libpulsedsp:i386
 pulseaudio-utils
 pulseaudio
 pulseaudio-esound-compat
 pulseaudio-module-x11
 pulseaudio-module-bluetooth
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Removing libpulse0 (apt-get remove libpulse0) has a ton of unmet, seemingly serious dependencies, so I'm kind of at a loss. I've done an update (100 times, hoping for a magic fix...), but to no avail. 

Any help would be greatly appreciated.

Thanks!

---

### Post by jmfal on 2012-06-28
Welcome to Ubuntu

Try  restarting and get to the grub screen>>> select dpkg  fix broken packages>>follow the prompts and manually enter command if asked.
When you get back to the menu >>resume normal boot and follow prompts.

---

### Post by jmfal on 2012-06-28
Sorry left something out

after you get to grub screen select the recovery kernal then dpkg

---

### Post by crotty on 2012-07-02
Hi jmfal,

thanks very much for your answer, I didn't know about that option before this. It did actually install all of the things that the libpulse error was blocking (new kernel, etc), but did not resolve the libpulse error itself. I still have the same issue...any further ideas?

Thanks again!

---

### Post by jmfal on 2012-07-02
Try this

```
      sudo apt-get install --fix-missing 
```

And post any errors

---

### Post by crotty on 2012-07-02
```
root@chopper:~# apt-get install --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libpulse-mainloop-glib0 : Depends: libpulse0 (>= 1:1.1-0ubuntu15.1) but 1:1.1-0ubuntu15 is installed
 libpulse0 : Breaks: libpulse0:i386 (!= 1:1.1-0ubuntu15) but 1:1.1-0ubuntu15.1 is installed
 libpulse0:i386 : Breaks: libpulse0 (!= 1:1.1-0ubuntu15.1) but 1:1.1-0ubuntu15 is installed
 libpulsedsp : Depends: libpulse0 (>= 1:1.1-0ubuntu15.1) but 1:1.1-0ubuntu15 is installed
 pulseaudio : Depends: libpulse0 (>= 1:1.1-0ubuntu15.1) but 1:1.1-0ubuntu15 is installed
 pulseaudio-esound-compat : Depends: libpulse0 (>= 1:1.1-0ubuntu15.1) but 1:1.1-0ubuntu15 is installed
 pulseaudio-module-bluetooth : Depends: libpulse0 (>= 1:1.1-0ubuntu15.1) but 1:1.1-0ubuntu15 is installed
 pulseaudio-module-x11 : Depends: libpulse0 (>= 1:1.1-0ubuntu15.1) but 1:1.1-0ubuntu15 is installed
 pulseaudio-utils : Depends: libpulse0 (>= 1:1.1-0ubuntu15.1) but 1:1.1-0ubuntu15 is installed
E: Unmet dependencies. Try using -f.
```

Then when I do the -f install, I get the error I posted in the original message.

---

### Post by jmfal on 2012-07-02
You have to use sudo in the commmand

```
  sudo apt-get install  -f      
```

Enter your pass word at the prompt(it will be hidden)  press enter

---

### Post by crotty on 2012-07-02
Ya, I was already root. I just keep a root terminal around when I'm sitting at my desk.

---

### Post by jmfal on 2012-07-02
DON'T DO THAT ITS TOO EASY TO BREAK SOMETHING!!

Please log out of root ,, save it for real problems.

Do you have a problem with sound??

Or are you trying to install one of the music players?

---

### Post by crotty on 2012-07-02
Right now I don't have any problems with sound. Amarok/pandora/etc play fine, and audio alerts play. All I'm trying to do is apt-get upgrade, and getting blocked by some weird libpulse dependency error. 

Is there a more detailed log file somewhere that I'm missing that might shed more light on the situation?

---

### Post by jmfal on 2012-07-02
The errors from trying to update are good enough.

You can try to completely remove and reistall > libpulse <  in synaptic then run your updates/upgrades.

Or you can remove libpulse then update/upgrade and go and re-install libpulse.
Either way you need to close synaptic before you run the terminal.

---

### Post by crotty on 2012-07-02
Surgery appears to have fixed it:

```
sudo dpkg --force-depends -r libpulse0
apt-get -f install
```

After forcing that guy out of there, everything appears to be back to normal.

Thanks very much for your time and help, jmfal!

---

### Post by jmfal on 2012-07-02
Your Welcome, 

If tis thread is solved please mark it [SOLVED] using the forum tools.

---

