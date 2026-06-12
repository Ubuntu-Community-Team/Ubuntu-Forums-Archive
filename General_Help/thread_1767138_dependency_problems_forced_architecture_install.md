---
title: "dependency problems forced architecture install"
date: 2011-05-25
forum: General Help
---

### Post by watgrad on 2011-05-25
Hello,
I'm trying to install a 32bit app in 64bit ubuntu 11.04

I get errors indicating dependency problems - I've checked and all the dependencies are met in synaptic.
Any ideas how to resolve this?

Here is the output I get when I try to install:

sudo dpkg -i --force-architecture *.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 191532 files and directories currently installed.)
Preparing to replace kobo-desktop:i386 1.8-1 (using kobo-desktop.deb) ...
Unpacking replacement kobo-desktop:i386 ...
dpkg: dependency problems prevent configuration of kobo-desktop:i386:
 kobo-desktop:i386 depends on libusb-0.1-4.
 kobo-desktop:i386 depends on libpng3.
 kobo-desktop:i386 depends on libpng12-0.
 kobo-desktop:i386 depends on libjpeg62.
 kobo-desktop:i386 depends on libxml2.
dpkg: error processing kobo-desktop:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_CA.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 kobo-desktop:i386

---

### Post by matt_symes on 2011-05-25
Hi

Have you installed the 32 bit libraries ?

```
sudo apt-get install ia32-libs
```

Kind regards

---

### Post by watgrad on 2011-05-25
Hi - thanks for the suggestion.
Yes they are already installed...

---

### Post by oldos2er on 2011-05-25
Have you installed these: 

kobo-desktop:i386 depends on libusb-0.1-4.
 kobo-desktop:i386 depends on libpng3.
 kobo-desktop:i386 depends on libpng12-0.
 kobo-desktop:i386 depends on libjpeg62.
 kobo-desktop:i386 depends on libxml2.

---

### Post by watgrad on 2011-05-25
Hi - yes I checked on synaptic and these were already installed.  I reinstalled them and then tried to reinstall my application - but still get the same error message....

---

### Post by linuxinstalledfromhdd on 2011-05-25
Have you tried to install this one?

[http://dl.dropbox.com/u/2183775/kobo-desktop.deb](http://dl.dropbox.com/u/2183775/kobo-desktop.deb)

---

### Post by oldos2er on 2011-05-25
You may need to get the 32-bit versions of those libraries and install them to /lib32 or /usr/lib32. I'd ask the developer first though.

---

### Post by watgrad on 2011-05-25
> **linuxinstalledfromhdd said:**
> Have you tried to install this one?

[http://dl.dropbox.com/u/2183775/kobo-desktop.deb](http://dl.dropbox.com/u/2183775/kobo-desktop.deb)

Hi - thanks for the suggestion - it has the same problem.

---

### Post by Velvet_Man on 2011-09-08
I was having the same problem trying to install the kobo desktop deb file in 64-bit Ubuntu 11.04. After some searching around on Google, I figured out how to get it up and running. Here's what I had to do.

1. Make sure ia32libs is installed
> sudo apt-get install ia32-libs

2. Install all of the dependencies (I think this turn out to be unnecessary, but just in case...)
> sudo apt-get install libusb-0.1-4
sudo apt-get install libpng3
sudo apt-get install libpng12-0
sudo apt-get install libjpeg62
sudo apt-get install libxml2

3. Install all of the dependencies from step 2 in 32-bit. To do this, I installed a program called getlibs that will install 32-bit libraries in a 64-bit system.You can find out more about getlibs here [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)  or here   [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/)

4. Use getlibs to install 32-bit libraries
> getlibs -p libusb-0.1-4
getlibs -p libpng3
getlibs -p libpng12-0
getlibs -p libjpeg62
getlibs -p libxml2

5. This still didn't work for me. After some more searching, I found out Kobo Desktop is also depend on libzip1. So...
> getlibs -p libzip1

6. Install the deb file with dpkg
> sudo dpkg -i --force-architecture kobo-desktop.deb


After that, I just hit Super, typed kobo-desktop, hit Enter (thanks to Unity) and it launched right away. It works perfectly.

---

### Post by Graipher on 2011-11-28
I know this post is now 2 month old, but I'm not able to install this same package under 11.10:

This still did'nt work for me. Somehow he still says he's missing all of the dependencies:

dpkg -i --force-architecture kobo-desktop.deb 
(Lese Datenbank ... 368185 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Ersetzen von kobo-desktop:i386 2.1.3-1 (durch kobo-desktop.deb) ...
Ersatz für kobo-desktop:i386 wird entpackt ...
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von kobo-desktop:i386:
 kobo-desktop:i386 hängt ab von libusb-0.1-4.
 kobo-desktop:i386 hängt ab von libpng3.
 kobo-desktop:i386 hängt ab von libxml2.
 kobo-desktop:i386 hängt ab von libzip1.
dpkg: Fehler beim Bearbeiten von kobo-desktop:i386 (--install):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
Trigger für desktop-file-utils werden verarbeitet ...
Trigger für gnome-menus werden verarbeitet ...
Trigger für bamfdaemon werden verarbeitet ...
Rebuilding /usr/share/applications/bamf.index...
Fehler traten auf beim Bearbeiten von:
 kobo-desktop:i386

Sorry for the german errorlog, but all it says is just the same as in the first post, only it did'nt issue the warning
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)

I followed the steps of Velvet_man precisely.

I tried to check in /lib32 if they were actually there, and only the png12 ones are there. 
However, apparently getlibs install them to /usr/lib32, which is where I found all the installed libs
And it seems as if dpkg does'nt find these libs (observe that libpng12 is not declared as a missing dependency and libpng12 is the only one  present in /lib32)

I also tried copying the missing libs from /usr/lib32 to /lib32, but still get the same error.

---

### Post by PapymousotEng on 2013-03-23
Hello, I have one problem to download "getlibs-all" 
I have the message 404 no found thus impossible to download it.
What must I do ?? I can resolve my problem without getlibs-all because I work with Ubuntu 12.04.1 64 bites?
Please I'm absolutely need it

Sorry for my english (I'm French)

---

### Post by sandyd on 2013-03-23
**Necromancing - Thread Closed**

Please do not post in threads more than one year old as many things change between Ubuntu Releases

Thanks!

---

