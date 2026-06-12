---
title: "Can not start GUI, AIGLX error r600_dri.so failed"
date: 2010-01-11
forum: General Help
---

### Post by kingnh on 2010-01-11
I have had Ubuntu running fine for about a month and then all of a sudden I can not boot to the GUI. I get dumped to a login prompt. I have tried booting an older kernel and same problem. I go into recovery mode with networking and when I manually enter "startx" I get:
 
AIGLX error: dlopen of /usr/lib/dri/r600_dri.so failed (no such file or directory)
 
Which is correct, that file does not exist.
 
I have tried:
dpkg-reconfigure xserver-xorg
 
It does nothing, just returns with no output.
 
graphics card: Mobility Radeon HD 4500 series, this is on an HP Pavillion laptop.
 
I even tried to purge and reinstall the ubuntu-dekstop package to no avail.
 
This happened all of a sudden last time I booted I was in the graphical desktop just fine. Boot up now and SOL.
 
 
Was running Gnome desktop. 
 
Tried /etc/init.d gdm restart, it complained and said to try "service gdm restart" which I did and I get this: "restart: Unknown instance"
 
So I try "service gdm start" and it says running, process 1744
 
running "gdm" now gets: "symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime
 
apt-get update: works
 
apt-get upgrade I get errors:
gconftool-2: symbol lookup error: gconftool-2: undefined symbol: g_option_context_set_translation_domain --- followed by more errors and eventually "dpkg returned an error code (1)"
 
 
Searched google and these forums and can not find anything that works.
 
Help appreciated -- all use to work fine, now it does not. It is possible the last tiem I was in the UI I ran a SW update for everything. 
 
-Kevin

---

### Post by kingnh on 2010-01-11
Been searching online and trying many things and anything I try to do to with apt-get yields this error, ""symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime".   
 
And it seems many people get this, but nobody ever has any fixes other than a complete wipe and re-install of Ubuntu.  I have already done this once when I tried to update my video driver.  Is there no other way?   
 
Is there a way to see a list of recently updated packages and "undo" them?
 
Last time I had the GUI running I was installing many packages to install an open source XMPP server which required quite a bit of development packages installed including QT and others.  Is it possible one of these blew away some libraries that Gnome desktop needs?  If  I could simply back out all those things I installed would the system restore to a previously working state?

---

### Post by kingnh on 2010-01-11
Well scratch that, found out how to get list of recently installed packages but apt-get is completely broken.  Anything I try with it I get "undefined symbol: g_option_context_set_translation_domain"

---

### Post by kingnh on 2010-01-11
OK, solved it and thought I would post what worked for me.  
 
It seems as if I had updated the version of gLib to 2.0 and that was interferring with a ton of things.    So I moved the glib libraries that were installed in \usr\local\lib to a random temp directory and all was well.  As described here:
[http://sites.google.com/site/asidoothings/ubuntu-stalling-on-boot-no-login-screen](http://sites.google.com/site/asidoothings/ubuntu-stalling-on-boot-no-login-screen)
 
 
But then I still had the problems described here, and the solution suggested here worked.
[http://ubuntuforums.org/showthread.php?t=1026086](http://ubuntuforums.org/showthread.php?t=1026086)
 
Am back up and running.
 
Of course, hopefully I don't really need glib 2.0 for anything -- seems as if you cant run it with latest Ubuntu.

---

