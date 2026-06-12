---
title: "ZSNES will not uninstall"
date: 2009-10-30
forum: General Help
---

### Post by Jor_727 on 2009-10-30
I've been searching around everywhere, and I cannot find a solution for this.  Hopefully somebody can help me.

```

jord@Lolcano:~$ sudo apt-get remove zsnes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libevolution5.0-cil gcj-4.3-base libpopt-dev libavutil-unstripped-49
  libportaudio0 libgcj9-0 libgcj-bc libxcb-keysyms0 libgda3-common libdiscid0
  ttf-kannada-fonts toolame libjaxp1.3-java-gcj python-numeric libass1
  libqscintilla2-3 libcsound64-5.1 libamrnb3 libdvbpsi4 gcj-4.4-jre-lib
  libggi-target-x libgcj10 wwwconfig-common libx264-65 libtorrent-rasterbar2
  libamrwb3 gcj-4.4-base libggi2 libgcj-common libgii1 ttf-telugu-fonts
  python-pyopenssl libjs-mochikit libgcj9-jar libao2 libffado0
  libgii1-target-x imagemagick-doc libkadm55 transmission-daemon libgda3-bin
  ttf-oriya-fonts libqtscriptbindings1 libgda3-3 javascript-common bsd-mailx
  libgmyth0 mailx python-xlib ladcca2 ttf-bengali-fonts
  nvidia-180-kernel-source python-storm qt4-qtconfig libmusicbrainz3-6
  nvidia-180-libvdpau
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  zsnes
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 4,166kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing zsnes (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 zsnes
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


And I even tried this:

```

jord@Lolcano:~$ sudo aptitude purge zsnes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  bsd-mailx{u} gcj-4.3-base{u} gcj-4.4-base{u} gcj-4.4-jre-lib{u} 
  imagemagick-doc{u} javascript-common{u} ladcca2{u} libamrnb3{u} 
  libamrwb3{u} libao2{u} libass1{u} libavutil-unstripped-49{u} 
  libcsound64-5.1{u} libdiscid0{u} libdvbpsi4{u} libevolution5.0-cil{u} 
  libffado0{u} libgcj-bc{u} libgcj-common{u} libgcj10{u} libgcj9-0{u} 
  libgcj9-jar{u} libgda3-3{u} libgda3-bin{u} libgda3-common{u} 
  libggi-target-x{u} libggi2{u} libgii1{u} libgii1-target-x{u} libgmyth0{u} 
  libjaxp1.3-java-gcj{u} libjs-mochikit{u} libkadm55{u} 
  libmusicbrainz3-6{u} libpopt-dev{u} libportaudio0{u} libqscintilla2-3{u} 
  libqtscriptbindings1{u} libtorrent-rasterbar2{u} libx264-65{u} 
  libxcb-keysyms0{u} mailx{u} nvidia-180-kernel-source{u} 
  nvidia-180-libvdpau{u} python-numeric{u} python-pyopenssl{u} 
  python-storm{u} python-xlib{u} qt4-qtconfig{u} toolame{u} 
  transmission-daemon{u} ttf-bengali-fonts{u} ttf-kannada-fonts{u} 
  ttf-oriya-fonts{u} ttf-telugu-fonts{u} wwwconfig-common{u} zsnes{ap} 
0 packages upgraded, 0 newly installed, 57 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 175MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing zsnes (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 zsnes
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```

---

### Post by pixelp on 2009-10-30
```
Package is in a very bad inconsistent state - you should reinstall it before attempting a removal.
```
As the output said: Try to reinstall it before removing it.

---

### Post by Jor_727 on 2009-10-30
Didn't work.

```

jord@Lolcano:~$ sudo apt-get install zsnes
[sudo] password for jord: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libevolution5.0-cil gcj-4.3-base libpopt-dev libavutil-unstripped-49
  libportaudio0 libgcj9-0 libgcj-bc libxcb-keysyms0 libgda3-common libdiscid0
  ttf-kannada-fonts toolame libjaxp1.3-java-gcj python-numeric libass1
  libqscintilla2-3 libcsound64-5.1 libamrnb3 libdvbpsi4 gcj-4.4-jre-lib
  libggi-target-x libgcj10 wwwconfig-common libx264-65 libtorrent-rasterbar2
  libamrwb3 gcj-4.4-base libggi2 libgcj-common libgii1 ttf-telugu-fonts
  python-pyopenssl libjs-mochikit libgcj9-jar libffado0 libgii1-target-x
  imagemagick-doc libkadm55 transmission-daemon libgda3-bin ttf-oriya-fonts
  libqtscriptbindings1 libgda3-3 javascript-common bsd-mailx libgmyth0 mailx
  python-xlib ladcca2 ttf-bengali-fonts nvidia-180-kernel-source python-storm
  qt4-qtconfig libmusicbrainz3-6 nvidia-180-libvdpau
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  zsnes
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/934kB of archives.
After this operation, 94.2kB of additional disk space will be used.
(Reading database ... 282011 files and directories currently installed.)
Preparing to replace zsnes 1.510-2.2ubuntu2 (using .../zsnes_1.510-2.2ubuntu3_i386.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Exec format error
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/zsnes_1.510-2.2ubuntu3_i386.deb (--unpack):
 there is no script in the new version of the package - giving up
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/zsnes_1.510-2.2ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Jor_727 on 2009-10-31
Bump!

---

### Post by Jor_727 on 2009-11-01
Bump... Again...

---

### Post by ikacer on 2009-11-01
you should try reinstalling it. In synaptic you can click the checkbox and choose "reinstall". With apt-get there is a "--reinstall" option you can give which I think does the same thing, though I've never used it.

---

### Post by Jor_727 on 2009-11-01
Hooray!  Finally fixed it.  This is how:


I first located all the relevant ZSNES files.

```

jord@Lolcano:~$ locate zsnes
/home/jord/.zsnes
/home/jord/.icons/hydroxygen/128x128/apps/zsnes.png
/home/jord/.icons/hydroxygen/16x16/apps/zsnes.png
/home/jord/.icons/hydroxygen/22x22/apps/zsnes.png
/home/jord/.icons/hydroxygen/24x24/apps/zsnes.png
/home/jord/.icons/hydroxygen/32x32/apps/zsnes.png
/home/jord/.icons/hydroxygen/48x48/apps/zsnes.png
/home/jord/.icons/hydroxygen/72x72/apps/zsnes.png
/home/jord/.local/share/Trash/info/zsnes151src.tar.bz2.trashinfo
/home/jord/.local/share/Trash/info/zsnes_1_51.trashinfo
/home/jord/.local/share/applications/userapp-zsnes-5YXK2U.desktop
/home/jord/.zsnes/zfont.txt
/home/jord/.zsnes/zinput.cfg
/home/jord/.zsnes/zmovie.cfg
/home/jord/.zsnes/zsnesl.cfg
/home/jord/Desktop/EXTERNAL/My Documents/SNES Emulator/zsnesw.cfg
/home/jord/Desktop/EXTERNAL/My Documents/SNES Emulator/Games/Edited Super Metroid/zsnesw.cfg
/home/jord/Desktop/EXTERNAL/My Documents/SNES Emulator/Games/Legend of Zelda - A Link to the Past/zsnesw.cfg
/home/jord/Desktop/EXTERNAL/My Documents/SNES Emulator/Games/Super Metroid/zsnesw.cfg
/home/jord/Emulator Games/SNES/Edited Super Metroid/zsnesw.cfg
/home/jord/Emulator Games/SNES/Legend of Zelda - A Link to the Past/zsnesw.cfg
/home/jord/Emulator Games/SNES/Super Metroid/zsnesw.cfg
[B]/usr/bin/zsnes
/usr/share/app-install/desktop/zsnes.desktop
/usr/share/app-install/icons/zsnes.xpm
/usr/share/applications/zsnes.desktop
/usr/share/doc/zsnes
/usr/share/doc/zsnes/README.Debian
/usr/share/doc/zsnes/about.txt.gz
/usr/share/doc/zsnes/advanced.txt.gz
/usr/share/doc/zsnes/authors.txt
/usr/share/doc/zsnes/changelog.Debian.gz
/usr/share/doc/zsnes/copyright
/usr/share/doc/zsnes/examples
/usr/share/doc/zsnes/faq.txt.gz
/usr/share/doc/zsnes/games.txt.gz
/usr/share/doc/zsnes/gui.txt.gz
/usr/share/doc/zsnes/history.txt.gz
/usr/share/doc/zsnes/html
/usr/share/doc/zsnes/index.txt
/usr/share/doc/zsnes/install.txt.gz
/usr/share/doc/zsnes/license.txt.gz
/usr/share/doc/zsnes/netplay.txt.gz
/usr/share/doc/zsnes/opengl.txt
/usr/share/doc/zsnes/readme.txt.gz
/usr/share/doc/zsnes/srcinfo.txt.gz
/usr/share/doc/zsnes/stdards.txt
/usr/share/doc/zsnes/support.txt.gz
/usr/share/doc/zsnes/thanks.txt
/usr/share/doc/zsnes/todo.txt
/usr/share/doc/zsnes/examples/README
/usr/share/doc/zsnes/examples/debian.smc.gz
/usr/share/doc/zsnes/examples/source
/usr/share/doc/zsnes/examples/source/col.map
/usr/share/doc/zsnes/examples/source/deb.map
/usr/share/doc/zsnes/examples/source/deb.set
/usr/share/doc/zsnes/examples/source/debian.asm
/usr/share/doc/zsnes/html/about.htm
/usr/share/doc/zsnes/html/advanced.htm
/usr/share/doc/zsnes/html/faq.htm
/usr/share/doc/zsnes/html/games.htm
/usr/share/doc/zsnes/html/gui.htm
/usr/share/doc/zsnes/html/history.htm
/usr/share/doc/zsnes/html/images
/usr/share/doc/zsnes/html/index.htm
/usr/share/doc/zsnes/html/license.htm
/usr/share/doc/zsnes/html/netplay.htm
/usr/share/doc/zsnes/html/readme.htm
/usr/share/doc/zsnes/html/styles
/usr/share/doc/zsnes/html/support.htm
/usr/share/doc/zsnes/html/images/cheat.png
/usr/share/doc/zsnes/html/images/config.png
/usr/share/doc/zsnes/html/images/f1_menu.png
/usr/share/doc/zsnes/html/images/game.png
/usr/share/doc/zsnes/html/images/gui.png
/usr/share/doc/zsnes/html/images/misc.png
/usr/share/doc/zsnes/html/images/netplay.png
/usr/share/doc/zsnes/html/images/quick.png
/usr/share/doc/zsnes/html/images/saveslot.png
/usr/share/doc/zsnes/html/images/zsneslogo.png
/usr/share/doc/zsnes/html/styles/corner.png
/usr/share/doc/zsnes/html/styles/jipcy.css
/usr/share/doc/zsnes/html/styles/plaintxt.css
/usr/share/doc/zsnes/html/styles/print.css
/usr/share/doc/zsnes/html/styles/radio.css
/usr/share/doc/zsnes/html/styles/release.css
/usr/share/doc/zsnes/html/styles/shared.css
/usr/share/doc-base/zsnes
/usr/share/man/man1/zsnes.1.gz
/usr/share/menu/zsnes
/usr/share/pixmaps/zsnes.xpm
/var/cache/apt/archives/zsnes_1.510-2.2ubuntu3_i386.deb
/var/crash/zsnes.0.crash
/var/lib/doc-base/documents/zsnes
/var/lib/doc-base/omf/zsnes
/var/lib/doc-base/omf/zsnes/zsnes-C.omf
/var/lib/dpkg/info/zsnes.list
/var/lib/dpkg/info/zsnes.md5sums
/var/lib/dpkg/info/zsnes.postinst
/var/lib/dpkg/info/zsnes.postrm
/var/lib/dpkg/info/zsnes.prerm[/B]

```


I then deleted the bold directories/files with the command

```

sudo rm -rf <directory/file>

```

Then all I had to do was put

```

sudo apt-get install zsnes

```

and it worked!

---

