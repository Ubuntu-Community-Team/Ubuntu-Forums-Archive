---
title: "Flash wont install"
date: 2009-07-25
forum: General Help
---

### Post by eandrade on 2009-07-25
i am having the most difficult time installing flash. i have tryied installing the tar ball, official site's deb, the non free and open source flash and none of them work. when i go to a flash site im asked to install flash.


OS : Ubuntu 8.04

---

### Post by mikewhatever on 2009-07-25
To help troubleshoot, can you post the output of the following commands from Terminal:

dpkg -s gnash
dpkg -s swfdec-gnome
uname -m

---

### Post by eandrade on 2009-07-25
Package: gnash
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 1000
Maintainer: Alexander Sack <asac@ubuntu.com>
Architecture: i386
Version: 0.8.2-0ubuntu3
Depends: gnash-common (= 0.8.2-0ubuntu3), libc6 (>= 2.7-1), libgcc1 (>= 1:4.1.1-21), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.12.0), libstdc++6 (>= 4.2.1-4), libx11-6, libxext6
Description: free SWF movie player
 Gnash is a free Flash movie player, which works either standalone, or as
 plugin for Firefox/Mozilla or Konqueror. Currently it is in a alpha state.
 The plugins are under heavy development at this time.
 .
 Gnash supports the majority of Flash opcodes up to SWF version 7, and
 a wide sampling of ActionScript classes for SWF version 8.5. All the
 core ones are implemented, and many of the newer ones work, but may be
 missing some of their methods.
 .
 Included in the Gnash is an XML based messaging system, as specified in
 the Flash specification. This lets a flash movie communicate over a TCP/IP
 socket, and parse the incoming XML message. This lets a movie be a remote
 control for other devices or applications.
 .
 This package includes the standalone GTK+-based OpenGL player.
 .
 Homepage: [http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)
Original-Maintainer: Miriam Ruiz <little_miry@yahoo.es>


Package: swfdec-gnome
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 676
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 2.22.2-1
Depends: gconf2, libatk1.0-0 (>= 1.20.0), libc6 (>= 2.2), libcairo2 (>= 1.6.0), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.12.0), liboil0.3, libpango1.0-0 (>= 1.20.1), libswfdec-0.6-90
Description: Tools to play SWF files (Macromedia Flash) on GNOME
 This package contains programs to integrate Flash functionality into the
 GNOME desktop. It's main application is swfdec-player, a stand-alone viewer
 for Flash files. It also contains swfdec-thumbnailer, a program that
 provides screenshots for files to display in the Nautilus file manager.
Original-Maintainer: Santiago Garcia Mantinan <manty@debian.org>


i686

---

### Post by mikewhatever on 2009-07-25
You have both gnash and swfdec installed, and have been trying to install adobe flash, the third plugin. That's too much.

Close the web browser and run the following commands:

sudo apt-get purge gnash swfdec-gnome
sudo apt-get autoremove
sudo apt-get install flashplugin-nonfree

---

### Post by eandrade on 2009-07-25
i followed the steps 

> eric@eric-desktop:~$ sudo apt-get purge gnash swfdec-gnome
[sudo] password for eric: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-thread1.34.1 libboost-date-time1.34.1 gnash-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gnash* mozilla-plugin-gnash* swfdec-gnome*
0 upgraded, 0 newly installed, 3 to remove and 270 not upgraded.
After this operation, 2032kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 108571 files and directories currently installed.)
Removing mozilla-plugin-gnash ...
Removing gnash ...
Removing swfdec-gnome ...
Purging configuration files for swfdec-gnome ...
eric@eric-desktop:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
eric@eric-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-thread1.34.1 libboost-date-time1.34.1 gnash-common
Use 'apt-get autoremove' to remove them.
Suggested packages:
  konqueror-nsplugins libflashsupport msttcorefonts ttf-xfree86-nonfree
  x-ttcidfont-conf xfs
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 0 newly installed, 0 to remove and 269 not upgraded.
Need to get 0B/18.9kB of archives.
After this operation, 8192B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 108502 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.115.0ubuntu0.7.10 (using .../flashplugin-nonfree_9.0.159.0ubuntu1~hardy1_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (9.0.159.0ubuntu1~hardy1) ...
Downloading...
--14:57:18--  [http://download.macromedia.com/pub/flashplayer/installers/current/9/install_flash_player_9.tar.gz](http://download.macromedia.com/pub/flashplayer/installers/current/9/install_flash_player_9.tar.gz)
           => `./install_flash_player_9.tar.gz'
Resolving download.macromedia.com... 72.246.87.191
Connecting to download.macromedia.com|72.246.87.191|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,057,882 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%   14.16 KB/s
   50K .......... .......... .......... .......... ..........  3%   26.23 KB/s
  100K .......... .......... .......... .......... ..........  5%   22.79 KB/s
  150K .......... .......... .......... .......... ..........  6%   61.74 KB/s
  200K .......... .......... .......... .......... ..........  8%   26.12 KB/s
  250K .......... .......... .......... .......... .......... 10%   66.79 KB/s
  300K .......... .......... .......... .......... .......... 11%   54.96 KB/s
  350K .......... .......... .......... .......... .......... 13%   24.13 KB/s
  400K .......... .......... .......... .......... .......... 15%   68.14 KB/s
  450K .......... .......... .......... .......... .......... 16%   71.41 KB/s
  500K .......... .......... .......... .......... .......... 18%   70.42 KB/s
  550K .......... .......... .......... .......... .......... 20%   25.95 KB/s
  600K .......... .......... .......... .......... .......... 21%   10.74 KB/s
  650K .......... .......... .......... .......... .......... 23%  194.76 KB/s
  700K .......... .......... .......... .......... .......... 25%  190.30 KB/s
  750K .......... .......... .......... .......... .......... 26%  105.35 MB/s
  800K .......... .......... .......... .......... .......... 28%  127.38 MB/s
  850K .......... .......... .......... .......... .......... 30%   33.07 KB/s
  900K .......... .......... .......... .......... .......... 31%   25.06 KB/s
  950K .......... .......... .......... .......... .......... 33%   62.56 KB/s
 1000K .......... .......... .......... .......... .......... 35%   28.81 KB/s
 1050K .......... .......... .......... .......... .......... 36%   74.30 KB/s
 1100K .......... .......... .......... .......... .......... 38%   56.56 KB/s
 1150K .......... .......... .......... .......... .......... 40%   28.27 KB/s
 1200K .......... .......... .......... .......... .......... 41%   74.23 KB/s
 1250K .......... .......... .......... .......... .......... 43%   34.37 KB/s
 1300K .......... .......... .......... .......... .......... 45%   53.45 KB/s
 1350K .......... .......... .......... .......... .......... 46%   56.73 KB/s
 1400K .......... .......... .......... .......... .......... 48%   32.86 KB/s
 1450K .......... .......... .......... .......... .......... 50%   56.23 KB/s
 1500K .......... .......... .......... .......... .......... 51%   57.96 KB/s
 1550K .......... .......... .......... .......... .......... 53%   35.43 KB/s
 1600K .......... .......... .......... .......... .......... 55%   56.59 KB/s
 1650K .......... .......... .......... .......... .......... 56%   46.20 KB/s
 1700K .......... .......... .......... .......... .......... 58%   48.33 KB/s
 1750K .......... .......... .......... .......... .......... 60%   44.20 KB/s
 1800K .......... .......... .......... .......... .......... 61%   37.17 KB/s
 1850K .......... .......... .......... .......... .......... 63%   62.98 KB/s
 1900K .......... .......... .......... .......... .......... 65%   45.60 KB/s
 1950K .......... .......... .......... .......... .......... 66%   36.92 KB/s
 2000K .......... .......... .......... .......... .......... 68%   56.99 KB/s
 2050K .......... .......... .......... .......... .......... 70%   38.70 KB/s
 2100K .......... .......... .......... .......... .......... 71%   44.67 KB/s
 2150K .......... .......... .......... .......... .......... 73%   38.82 KB/s
 2200K .......... .......... .......... .......... .......... 75%   62.42 KB/s
 2250K .......... .......... .......... .......... .......... 77%   41.44 KB/s
 2300K .......... .......... .......... .......... .......... 78%   48.74 KB/s
 2350K .......... .......... .......... .......... .......... 80%   42.72 KB/s
 2400K .......... .......... .......... .......... .......... 82%   42.45 KB/s
 2450K .......... .......... .......... .......... .......... 83%   44.89 KB/s
 2500K .......... .......... .......... .......... .......... 85%   66.14 KB/s
 2550K .......... .......... .......... .......... .......... 87%   39.82 KB/s
 2600K .......... .......... .......... .......... .......... 88%   44.85 KB/s
 2650K .......... .......... .......... .......... .......... 90%   44.68 KB/s
 2700K .......... .......... .......... .......... .......... 92%   43.40 KB/s
 2750K .......... .......... .......... .......... .......... 93%   47.90 KB/s
 2800K .......... .......... .......... .......... .......... 95%   50.23 KB/s
 2850K .......... .......... .......... .......... .......... 97%   46.51 KB/s
 2900K .......... .......... .......... .......... .......... 98%   42.89 KB/s
 2950K .......... .......... .......... ......               100%   39.97 KB/s

14:58:33 (41.64 KB/s) - `./install_flash_player_9.tar.gz' saved [3057882/3057882]

Download done.
Flash Plugin installed.

eric@eric-desktop:~$ 
but
youtube gives me "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. [Get the latest Flash player]("http://www.adobe.com/go/getflashplayer/")." and miniclip also asks me to install flash

---

### Post by mikewhatever on 2009-07-25
Well, but does it work? Hardy Heron's repositories have an older version of flash, 9.0.159 to be precise. You can try and install the newest version from adobe's deb file, but remove the one from the repositories first with the following command:

sudo apt-get purge flashplugin-nonfree

Edit: I got the second command wrong in the previous post. It should have been autoremove and not autoclean. Now fixed, try running it again.

---

### Post by lovinglinux on 2009-07-25
Don't forget to restart the browser after installing/removing flash plugins.

---

### Post by eandrade on 2009-07-26
it still does not work a all

---

### Post by bcschmerker on 2009-07-26
> **mikewhatever said:**
> Well, but does it work? Hardy Heron's repositories have an older version of flash, 9.0.159 to be precise. You can try and install the newest version from adobe's deb file, but remove the one from the repositories first with the following command:

sudo apt-get purge flashplugin-nonfree

Edit: I got the second command wrong in the previous post. It should have been autoremove and not autoclean. Now fixed, try running it again.Correction:  The Hardy repository should have _flashplugin-nonfree-10.0.1.218+10.0.0.515ubuntu1+really9.0.124.0ubuntu2_ as the latest version; its size as of 26 July 2009 is 168 kB.  Hope this helps with the Flash install.

---

### Post by HappyFeet on 2009-07-26
Go [here]("http://get.adobe.com/flashplayer/") and download the tar.gz flash file. Right click it and select "exract here". Open the extracted folder and copy the **libflashplayer.so** file. Then go to your home folder and do ctrl-H to show hidden directories. Go to the .mozilla folder and open it. Create a new folder inside of .mozilla called **plugins**. Open the plugins folder and right click-paste (the libflashplayer.so file)
Restart firefox if open.

---

