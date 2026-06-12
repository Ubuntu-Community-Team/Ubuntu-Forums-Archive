---
title: "Installing with --force-* using dpkg gets reverted by apt-get in 11.10"
date: 2011-10-16
forum: General Help
---

### Post by DoktorSeven on 2011-10-16
I have a 32-bit package I install using **dpkg --force-architecture --force-depends package_i386.deb**.  Yes, the use of "force" isn't really recommended, but in this case, the 32-bit ia32-libs provide most and I provide the rest. 

This worked perfectly in 11.04 and still works just fine in 11.10 -- the program runs flawlessly.  Until I try to install or update using apt-get or any package management program, which removes the package (it doesn't say why, but I assume for dependency problems), even though I have told it to **force** the dependencies/architecture.  This didn't happen in 11.04 and using --force-* with dpkg was enough to tell apt-get to leave my package alone.

From what I understand, using --force-* to prevent apt-get from removing the package for dependency issues is the correct behavior.  If something has changed, than what would be the correct way to force the installation of a different architecture with provided 32-bit libs?

---

### Post by philinux on 2011-10-16
Multiarch is the change.

 [http://www.ubuntugeek.com/new-features-in-ubuntu-11-10-oneiric.html](http://www.ubuntugeek.com/new-features-in-ubuntu-11-10-oneiric.html)

---

### Post by DoktorSeven on 2011-10-16
Interesting.

Multiarch seems to be very broken if the intent is to allow you to install 32-bit libs as you would others: for example, trying to install 32-bit libsdl with apt-get wants to remove all *64-bit* SDL packages as well as anything that depends on them.

```
sudo apt-get install libsdl1.2debian:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  anagramarama-data libcaca-dev dvgrab python-pyaudio libslang2-dev libaudiofile-dev fb-music-high libgsasl7
  libfluidsynth1 zaz-data libquicktime2 libasound2-dev libtinyxml2.6.2 libftgl2 libxdg-basedir1 libvorbis-dev
  libncurses5-dev libavahi-client-dev libogg-dev libboost-iostreams1.46.1 chromium-bsu-data libalut0 python-ogg
  kdenlive-data recordmydesktop libtinfo-dev ttf-uralic scummvm-data libxt-dev libglc0 libesd0-dev libntlm0
  frozen-bubble-data python-pyvorbis libaudio-dev pokerth-data libmikmod2-dev armagetronad-common doom-wad-shareware
  libpulse-dev libircclient1 frogatto-data libmlt-data libavahi-common-dev libboost-regex1.46.1 libaa1-dev python-opengl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsdl1.2debian-alsa:i386
The following packages will be REMOVED:
  anagramarama armagetronad beneath-a-steel-sky chocolate-doom chromium-bsu crack-attack dosbox e-uae ffmpeg
  flight-of-the-amazon-queen fofix frogatto frozen-bubble kdenlive libmlt++3 libmlt4 libsdl-gfx1.2-4 libsdl-image1.2
  libsdl-mixer1.2 libsdl-mixer1.2-dev libsdl-net1.2 libsdl-net1.2-dev libsdl-pango1 libsdl-perl libsdl-sound1.2
  libsdl-ttf2.0-0 libsdl-ttf2.0-dev libsdl1.2-dev libsdl1.2debian libsdl1.2debian-alsa libsmpeg-dev libsmpeg0 mame
  mednafen melt mplayer mupen64plus pokerth prboom python-pygame scummvm smplayer smplayer-themes smplayer-translations
  snes9x-gtk stella zaz
The following NEW packages will be installed:
  libsdl1.2debian:i386 libsdl1.2debian-alsa:i386
0 upgraded, 2 newly installed, 47 to remove and 0 not upgraded.
Need to get 202 kB of archives.
After this operation, 319 MB disk space will be freed.

```

---

### Post by DoktorSeven on 2011-10-18
Bumping this for possibly some insight.  Basically the problem persists -- installing 32-bit packages on 64 bit Ubuntu is no longer possible, because --force-* no longer works (it gets immediately reverted or behaves the same as trying to use multiarch) and when trying to use the new multiarch, it attempts to *replace* the 64-bit library dependencies with 32-bit ones.

Here's an example, if you want one: Gens/GS ([http://segaretro.org/Gens/GS](http://segaretro.org/Gens/GS)).  This is the case with any 32-bit package, so it's not restricted to gaming so I don't feel this belongs in Gaming forum.  (It does the same thing whether or not the --force-* flags are used.)

```

$ sudo dpkg --force-architecture --force-depends -i Gens_2.16.7_i386.deb
Selecting previously deselected package gens:i386.
(Reading database ... 301655 files and directories currently installed.)
Unpacking gens:i386 (from Gens_2.16.7_i386.deb) ...
dpkg: gens:i386: dependency problems, but configuring anyway as you requested:
 gens:i386 depends on libsdl1.2debian (>= 1.1.3).
 gens:i386 depends on xdg-utils.
Setting up gens:i386 (2.16.7) ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...

$ sudo apt-get install [anything here]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gens:i386 : Depends: libsdl1.2debian:i386 (>= 1.1.3) but it is not going to be installed
             Depends: xdg-utils:i386 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  anagramarama-data libcaca-dev dvgrab python-pyaudio libslang2-dev libaudiofile-dev fb-music-high libgsasl7 libfluidsynth1
  zaz-data libasound2-dev libtinyxml2.6.2 libftgl2 libxdg-basedir1 libvorbis-dev libncurses5-dev libavahi-client-dev
  libogg-dev libboost-iostreams1.46.1 chromium-bsu-data libalut0 python-ogg kdenlive-data recordmydesktop libtinfo-dev
  ttf-uralic scummvm-data libxt-dev libglc0 libesd0-dev libntlm0 frozen-bubble-data python-pyvorbis libaudio-dev
  pokerth-data libmikmod2-dev armagetronad-common doom-wad-shareware libpulse-dev libircclient1 frogatto-data libmlt-data
  libavahi-common-dev libboost-regex1.46.1 libaa1-dev python-opengl libsdl1.2debian:i386 libsdl1.2debian-alsa:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsdl1.2debian:i386 libsdl1.2debian-alsa:i386
The following packages will be REMOVED:
  anagramarama armagetronad beneath-a-steel-sky chocolate-doom chromium-bsu crack-attack dosbox e-uae ffmpeg
  flight-of-the-amazon-queen fofix frogatto frozen-bubble gens:i386 gstreamer0.10-plugins-bad-multiverse kdenlive
  libmjpegtools-1.9 libmlt++3 libmlt4 libsdl-gfx1.2-4 libsdl-image1.2 libsdl-mixer1.2 libsdl-mixer1.2-dev libsdl-net1.2
  libsdl-net1.2-dev libsdl-pango1 libsdl-perl libsdl-sound1.2 libsdl-ttf2.0-0 libsdl-ttf2.0-dev libsdl1.2-dev
  libsdl1.2debian libsdl1.2debian-alsa libsmpeg-dev libsmpeg0 mame mednafen melt mplayer mupen64plus pokerth python-pygame
  scummvm smplayer smplayer-themes smplayer-translations snes9x-gtk stella zaz
The following NEW packages will be installed:
  libsdl1.2debian:i386 libsdl1.2debian-alsa:i386
0 upgraded, 2 newly installed, 49 to remove and 0 not upgraded.
Need to get 202 kB of archives.
After this operation, 324 MB disk space will be freed.
Do you want to continue [Y/n]? 

```

Either there is something seriously wrong with multilib or I am not quite understanding how this is supposed to be done.  Disabling multiarch (removing /etc/dpkg/dpkg.cfg.d/multiarch then sudo apt-get update / upgrade) removes Flash plugin and creates a dependency problem with qdbus:

```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  qdbus
The following NEW packages will be installed:
  qdbus
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/27.8 kB of archives.
After this operation, 213 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: error processing /var/cache/apt/archives/qdbus_4%3a4.7.4-0ubuntu8_amd64.deb (--unpack):
 qdbus: 4:4.7.4-0ubuntu8 (Multi-Arch: foreign) is not co-installable with qdbus:i386 4:4.7.4-0ubuntu8 (Multi-Arch: foreign) which is currently installed
Errors were encountered while processing:
 /var/cache/apt/archives/qdbus_4%3a4.7.4-0ubuntu8_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Even re-enabling multiarch creates a dependency resolution issue that ultimately comes back to it wanting to remove the 64-bit libsdl again.  

Anyone know any way out of this?  I hope there's just something simple I am overlooking that makes multiarch work like I think it should -- installing 32-bit and 64-bit libraries side by side.

---

### Post by daniel_m on 2011-11-19
I had this same problem and tinkered a lot with my system before it seemed to be fixed. This is what I believe did it.

Some context (previous actions):
- disable multiarch (which was what supposedly caused the problem)
- play with aptitude uninstalling and reinstalling packages, uninstalled qdbus and could not install it again
```
root@mercurio:/var/cache/apt/archives# apt-get -f install qdbus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  qdbus
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.8 kB of archives.
After this operation, 213 kB of additional disk space will be used.
Get:1 [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric/main qdbus amd64 4:4.7.4-0ubuntu8 [27.8 kB]
Fetched 27.8 kB in 0s (78.7 kB/s)
dpkg: error processing /var/cache/apt/archives/qdbus_4%3a4.7.4-0ubuntu8_amd64.deb (--unpack):
 qdbus: 4:4.7.4-0ubuntu8 (Multi-Arch: foreign) is not co-installable with qdbus:i386 4:4.7.4-0ubuntu8 (Multi-Arch: foreign) which is currently installed
Errors were encountered while processing:
 /var/cache/apt/archives/qdbus_4%3a4.7.4-0ubuntu8_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@mercurio:/var/cache/apt/archives# apt-cache policy qdbus
qdbus:
  Installed: (none)
  Candidate: 4:4.7.4-0ubuntu8
  Version table:
     4:4.7.4-0ubuntu8 0
        500 [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric/main amd64 Packages

```FIX:
1. apt-get clean / aptitude clean / whatever clears your package manager cache
2. reenable multiarch
3. apt-get update
4. apt-get install qdbus
```

root@mercurio:/etc/dpkg/dpkg.cfg.d# apt-get install qdbus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  qdbus:i386
The following NEW packages will be installed:
  qdbus
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0 B/27.8 kB of archives.
After this operation, 4,096 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: qdbus:i386: dependency problems, but removing anyway as you requested:
 libqt4-dbus:i386 depends on qdbus.
 libqt4-dbus depends on qdbus; however:
  Package qdbus is not installed.
  Package qdbus:i386 is to be removed.
(Reading database ... 166432 files and directories currently installed.)
Removing qdbus:i386 ...
Processing triggers for man-db ...
(Reading database ... 166427 files and directories currently installed.)
Unpacking qdbus (from .../qdbus_4%3a4.7.4-0ubuntu8_amd64.deb) ...
Processing triggers for man-db ...
Setting up qdbus (4:4.7.4-0ubuntu8) ..

```5. disable multiarch again. All is well, hopefully.

I cannot explain what happened, but that seemed to do the trick. It managed to "remove" the package that was not really installed.

---

### Post by oldos2er on 2011-11-20
> **DoktorSeven said:**
> Interesting.

Multiarch seems to be very broken 

It is for me too. See [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101?comments=all](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101?comments=all)

---

