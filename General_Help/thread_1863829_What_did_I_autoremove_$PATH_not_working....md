---
title: "What did I autoremove? $PATH not working..."
date: 2011-10-18
forum: General Help
---

### Post by J V on 2011-10-18
[SOLVED] Autoremove removed wine dependencies (I had not installed the wine package itsself)

I write scripts to use different wineprefixes and wineversions for gaming, this one worked fine yesterday, so the only possible change is that I did an "apt-get upgrade" and "apt-get autoremove"

Last time I checked $PATH was a pretty important thing so why isn't it working now?

Can anyone tell me how to find a list of autoremoved packages? They don't show up in history.
```
j@jonux:~$ ./GW
./GW: line 6: /media/Data/Wine/WineVersions/1.3.24/bin/wine: No such file or directory
j@jonux:~$ ls -l /media/Data/Wine/WineVersions/1.3.24/bin/
total 1328
-rwxr-xr-x 1 j j   8187 2011-08-11 17:18 function_grep.pl
-rwxr-xr-x 1 j j   1576 2011-08-11 17:18 msiexec
-rwxr-xr-x 1 j j   1576 2011-08-11 17:18 notepad
-rwxr-xr-x 1 j j   1576 2011-08-11 17:18 regedit
-rwxr-xr-x 1 j j   1576 2011-08-11 17:18 regsvr32
-rwxr-xr-x 1 j j 347244 2011-08-11 17:18 widl
-rwxr-xr-x 1 j j   7244 2011-08-11 17:18 wine
-rwxr-xr-x 1 j j   1576 2011-08-11 17:18 wineboot
-rwxr-xr-x 1 j j 100272 2011-08-11 17:18 winebuild
-rwxr-xr-x 1 j j   1576 2011-08-11 17:18 winecfg
-rwxr-xr-x 1 j j   1576 2011-08-11 17:18 wineconsole
lrwxrwxrwx 1 j j      7 2011-09-28 22:40 winecpp -> winegcc
-rwxr-xr-x 1 j j   1576 2011-08-11 17:18 winedbg
-rwxr-xr-x 1 j j 137044 2011-08-11 17:18 winedump
-rwxr-xr-x 1 j j   1576 2011-08-11 17:18 winefile
lrwxrwxrwx 1 j j      7 2011-09-28 22:40 wineg++ -> winegcc
-rwxr-xr-x 1 j j  28740 2011-08-11 17:18 winegcc
-rwxr-xr-x 1 j j  91261 2011-08-11 17:18 winemaker
-rwxr-xr-x 1 j j   1576 2011-08-11 17:18 winemine
-rwxr-xr-x 1 j j   1576 2011-08-11 17:18 winepath
-rwxr-xr-x 1 j j  11532 2011-08-11 17:18 wine-preloader
-rwxr-xr-x 1 j j 338396 2011-08-11 17:18 wineserver
-rwxr-xr-x 1 j j  39784 2011-08-11 17:18 wmc
-rwxr-xr-x 1 j j 188396 2011-08-11 17:18 wrc
j@jonux:~$ cat GW
#!/bin/bash
PATH="/media/Data/Wine/WineVersions/1.3.24/bin:$PATH"
export WINEPREFIX="/media/Data/Wine/WinePrefixes/GW"
export WINEDEBUG="-all"
cd "/media/Data/Wine/WinePrefixes/GW/drive_c/Program Files/Guild Wars"
wine Gw.exe
#winecfg
#wineserver -k
```

---

### Post by mikejonesey on 2011-10-18
path option is not exported so does not become an environment variable (may be required, rather than a local var...)

(in your code above anyways...)

---

### Post by J V on 2011-10-18
It worked without exporting for literally years, and exporting doesn't make any difference, same error.

Although since it does know that the file is there I can only assume that the problem is with something else. It knows where the file should be but doesn't correctly open it.

---

### Post by mikejonesey on 2011-10-18
not sure as a test do;

env | grep PATH=/

and paste that path+your wine bin path, see if that makes a diff, maybee it's wine that it's not finding the path of... maybee ur script is running as sh instead of bash or summin...

---

### Post by ubu_dynamite on 2011-10-18
Is wine executable?

---

### Post by J V on 2011-10-18
```
env | grep path gives:

PATH=/media/Data/Wine/WineVersions/1.3.24/bin:/home/j/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```wine is executable, and no it's not a symlink.

It even has the same md5sum as a fresh download so it's not corrupted.

This is almost certainly a problem with bash. If I could see a list of packages it autoremoved that would help but I don't know how (Synaptic only shows specific removal/installation not automatics)

---

### Post by smurphy_it on 2011-10-18
Did you look at the log file ?

```
sudo cat /var/log/apt/history.log
```

---

### Post by J V on 2011-10-18
Awesome! The entries in question are:

```
Start-Date: 2011-10-18  00:03:31
Remove: kubuntu-debug-installer (10.04ubuntu4), libdbusmenu-qt2 (0.3.2-0ubuntu1), lib32bz2-1.0 (1.0.5-4ubuntu0.1), python-packagekit (0.5.7-0ubuntu2.2), melt (0.5.4-1), libpackagekit-qt-12 (0.5.7-0ubuntu2.2), libical0 (0.44-3), libqca2 (2.0.2-1ubuntu2), dvgrab (3.5-1), libavutil50 (0.6.2-1ubuntu1~ppa1~lucid1), libpth20 (2.0.7-14), libqt4-qt3support (4.6.2-0ubuntu5.3), libpolkit-qt-1-0 (0.95.1-1fakesync1), libsensors4 (3.1.2-2), swh-plugins (0.4.15+1-4), lib32ncurses5 (5.7+20090803-2ubuntu3), nspluginwrapper (1.2.2-0ubuntu6.10.04.1), libxine1-x (1.1.17-1ubuntu3), genisoimage (1.1.10-1ubuntu1), kpackagekit (0.5.4-0ubuntu4.3), librdf0 (1.0.10-1ubuntu1), libmlt++3 (0.5.4-1), libcvaux4 (2.0.0-3ubuntu2), libsox-fmt-base (14.3.0-1.1build1), ia32-libs (2.7ubuntu26.1), libqt4-test (4.6.2-0ubuntu5.3), libqt4-script (4.6.2-0ubuntu5.3), libqt4-designer (4.6.2-0ubuntu5.3), libboost-program-options1.40.0 (1.40.0-4ubuntu4), kdelibs5 (4.4.5-0ubuntu1.1), libxcb-xv0 (1.5-2), libsox-fmt-alsa (14.3.0-1.1build1), phonon (4.6.2-0ubuntu5.3), libapm1 (3.2.2-14), oxygen-icon-theme (4.4.5-0ubuntu1), plasma-scriptengine-javascript (4.4.5-0ubuntu1), gdebi-core (0.6.0ubuntu2), libexiv2-6 (0.19-1), librasqal2 (0.9.17-1), libmagickcore2-extra (6.5.7.8-1ubuntu1.1), dvdauthor (0.6.14-3ubuntu4), libc6-i386 (2.11.1-0ubuntu7.8), kdesudo (3.4.2.3-0ubuntu1.1), libxosd2 (2.2.14-1.7), lib32gcc1 (4.4.3-4ubuntu5), libqt4-xmlpatterns (4.6.2-0ubuntu5.3), libakonadiprivate1 (1.3.1-0ubuntu3), libx264-98 (0.98.1653+git88b90d9-3ubuntu2~ppa1~lucid1), libsoprano4 (2.4.2+dfsg.1-0ubuntu1.1), kdenlive-data (0.7.7.1-0ubuntu1), lib32asound2 (1.0.22-0ubuntu7), recordmydesktop (0.3.8.1+svn602-1ubuntu1), libqt4-help (4.6.2-0ubuntu5.3), python-qt4 (4.7.2-0ubuntu1), libclucene0ldbl (0.9.21b-2), shared-desktop-ontologies (0.3-1), python-sip (4.10.1-0ubuntu1), linux-headers-2.6.32-33 (2.6.32-33.72), libgraphviz4 (2.20.2-8ubuntu3), virtuoso-nepomuk (6.1.0-0ubuntu3), phonon-backend-xine (4.4.0-0ubuntu2), libvpx0 (0.9.6-1~ppa1~lucid1), libgavl1 (1.1.1-3), kdepimlibs-data (4.4.5-0ubuntu1.1), icoutils (0.29.1-0ubuntu1~lucid), software-properties-kde (0.75.10.1), frei0r-plugins (1.1.22git20090409+repack-0ubuntu3), libdjvulibre21 (3.5.22-1ubuntu4.1), libxine1-console (1.1.17-1ubuntu3), soprano-daemon (2.4.2+dfsg.1-0ubuntu1.1), libcv4 (2.0.0-3ubuntu2), fancontrol (3.1.2-2), libphonon4 (4.6.2-0ubuntu5.3), polkit-kde-1 (0.95.1-2ubuntu1), install-package (0.5.2), packagekit (0.5.7-0ubuntu2.2), libxss1 (1.2.0-2), tcl8.4 (8.4.19-4), libqt4-assistant (4.6.2-0ubuntu5.3), gdebi-kde (0.6.0ubuntu2), libplasma3 (4.4.5-0ubuntu1.1), libxine1-misc-plugins (1.1.17-1ubuntu3), kdepimlibs5 (4.4.5-0ubuntu1.1), libhighgui4 (2.0.0-3ubuntu2), update-manager-kde (0.134.11), kdelibs-bin (4.4.5-0ubuntu1.1), libpackagekit-glib2-12 (0.5.7-0ubuntu2.2), libattica0 (0.1.3-0ubuntu1), tk8.4 (8.4.19-4), app-install-data (0.10.04.7), libgpgme11 (1.2.0-1.2ubuntu1), libstreams0 (0.7.2-0ubuntu1), libqt4-webkit (4.6.2-0ubuntu5.3), libraptor1 (1.4.21-1ubuntu1), lib32z1 (1.2.3.3.dfsg-15ubuntu1), linux-headers-2.6.32-33-generic (2.6.32-33.72), exiv2 (0.19-1), libva1 (1.0.1-3~ppa1~lucid2), kdelibs5-data (4.4.5-0ubuntu1.1), kdebase-runtime (4.4.5-0ubuntu1), lib32stdc++6 (4.4.3-4ubuntu5), libqt4-scripttools (4.6.2-0ubuntu5.3), lib32v4l-0 (0.6.4-1ubuntu1), libdjvulibre-text (3.5.22-1ubuntu4.1), libsox1a (14.3.0-1.1build1), libmlt-data (0.5.4-1), libxcb-shape0 (1.5-2), libssh-4 (0.4.2-1ubuntu1), libxcb-shm0 (1.5-2), kdebase-runtime-data (4.4.5-0ubuntu1), libiodbc2 (3.52.6-4), libxine1-bin (1.1.17-1ubuntu3), libmlt2 (0.5.4-1), python-kde4 (4.4.5-0ubuntu1), libstreamanalyzer0 (0.7.2-0ubuntu1), packagekit-backend-apt (0.5.7-0ubuntu2.2), libxine1 (1.1.17-1ubuntu3)
End-Date: 2011-10-18  00:04:30

Start-Date: 2011-10-18  00:05:03
Upgrade: apt-transport-https (0.7.25.3ubuntu9.7, 0.7.25.3ubuntu9.8), apt-utils (0.7.25.3ubuntu9.7, 0.7.25.3ubuntu9.8), apt (0.7.25.3ubuntu9.7, 0.7.25.3ubuntu9.8), tzdata-java (2011j-0ubuntu0.10.04, 2011k-0ubuntu0.10.04), tzdata (2011j-0ubuntu0.10.04, 2011k-0ubuntu0.10.04)
End-Date: 2011-10-18  00:05:15

```Now at this point I'm clueless... I don't know which of these packages has to do with execution of binaries and bash, or perhaps it's an xfce-terminal issue, either way I don't know what I'm looking for.

Edit: It's definitely the autoremove, installing ia32-libs got it to the point where it was now complaining about opengl so I will crosscheck the wine dependencies with this list and see what I need, or just install wine and let it do it, thanks!

---

### Post by decoherence on 2011-10-18
Can you confirm that /media/Data/Wine/WineVersions/1.3.24/bin still exists? Try running wine by typing that full path.

Standard procedure when your shell script doesn't do what you want is to run the shell in debug mode using the -x flag.

You can either do this by running

```
bash -x GW
```

or by adding -x to your #!/bin/bash line

Hopefully this will give you a clue as to why it's crapping out.

---

