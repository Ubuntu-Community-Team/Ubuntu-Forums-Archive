---
title: "tovid"
date: 2006-02-14
forum: General Help
---

### Post by neoroses on 2006-02-14
hiya this is pretty urgent - i am trying to install tovid but it wont work i get this:
sam@tuxbox:~$ tar xvfz /home/sam/tovid-0.25.tar.gz
tovid-0.25/
tovid-0.25/src/
tovid-0.25/src/makevcd.sh
tovid-0.25/src/makexml.sh
tovid-0.25/src/pymakexml.py
tovid-0.25/src/tovid-init.sh
tovid-0.25/src/previd.sh
tovid-0.25/src/Makefile.am
tovid-0.25/src/Makefile.in
tovid-0.25/src/idvid.sh
tovid-0.25/src/tovid-interactive.sh
tovid-0.25/src/dvrequant.sh
tovid-0.25/src/tovid-init.sh.in
tovid-0.25/src/postproc.sh
tovid-0.25/src/pytovid.py
tovid-0.25/src/makeslides.sh
tovid-0.25/src/tovidgui.py
tovid-0.25/src/tovid-batch.sh
tovid-0.25/src/makemenu.sh
tovid-0.25/src/pymakemenu.py
tovid-0.25/src/tovid.sh
tovid-0.25/src/tovid-test.sh
tovid-0.25/src/makedvd.sh
tovid-0.25/NEWS
tovid-0.25/docs/
tovid-0.25/docs/man/
tovid-0.25/docs/man/makemenu.1
tovid-0.25/docs/man/makedvd.1
tovid-0.25/docs/man/makexml.1
tovid-0.25/docs/man/makeslides.1
tovid-0.25/docs/man/tovid.1
tovid-0.25/docs/man/idvid.1
tovid-0.25/docs/man/postproc.1
tovid-0.25/aclocal.m4
tovid-0.25/icons/
tovid-0.25/icons/tovid_icon_32.png
tovid-0.25/icons/tovid_icon_48.png
tovid-0.25/icons/tovid_icon_64.png
tovid-0.25/icons/tovid_icon_128.png
tovid-0.25/README
tovid-0.25/configure
tovid-0.25/configure.ac
tovid-0.25/install-sh
tovid-0.25/missing
tovid-0.25/Makefile.am
tovid-0.25/Makefile.in
tovid-0.25/setuplib.py.in
tovid-0.25/AUTHORS
tovid-0.25/setup.sh
tovid-0.25/INSTALL
tovid-0.25/libtovid/
tovid-0.25/libtovid/TDL.py
tovid-0.25/libtovid/Option.py
tovid-0.25/libtovid/Disc.py
tovid-0.25/libtovid/Globals.py
tovid-0.25/libtovid/Project.py
tovid-0.25/libtovid/Video.py
tovid-0.25/libtovid/Menu.py
tovid-0.25/libtovid/__init__.py
tovid-0.25/libtovid/VideoPlugins.py
tovid-0.25/libtovid/Standards.py
tovid-0.25/ChangeLog
tovid-0.25/COPYING
tovid-0.25/bootstrap
sam@tuxbox:~$ cd /home/sam/tovid-0.25
sam@tuxbox:~/tovid-0.25$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
configure: Checking for required core dependencies...
checking for grep... ok
checking for sed... ok
checking for md5sum... ok
checking for mplayer... ok
checking for mencoder... MISSING
checking for mplex... ok
checking for mpeg2enc... ok
checking for yuvfps... ok
checking for yuvdenoise... ok
checking for ppmtoy4m... ok
checking for mp2enc... ok
checking for ffmpeg... ok
checking for sox... ok
./configure: line 2194: gawk: command not found
./configure: line 2195: gawk: command not found
./configure: line 2194: gawk: command not found
./configure: line 2195: gawk: command not found
./configure: line 2194: gawk: command not found
./configure: line 2195: gawk: command not found
./configure: line 2194: gawk: command not found
./configure: line 2195: gawk: command not found
./configure: line 2194: gawk: command not found
./configure: line 2195: gawk: command not found
./configure: line 2194: gawk: command not found
./configure: line 2195: gawk: command not found
./configure: line 2194: gawk: command not found
./configure: line 2195: gawk: command not found
./configure: line 2194: gawk: command not found
./configure: line 2195: gawk: command not found
./configure: line 2194: gawk: command not found
./configure: line 2195: gawk: command not found
./configure: line 2194: gawk: command not found
./configure: line 2195: gawk: command not found
./configure: line 2194: gawk: command not found
./configure: line 2195: gawk: command not found
./configure: line 2194: gawk: command not found
./configure: line 2195: gawk: command not found
./configure: line 2194: gawk: command not found
./configure: line 2195: gawk: command not found
configure: Checking for optional dependencies...
configure: Checking for ImageMagick...
checking for composite... ok
checking for convert... ok
configure: Checking for dvd tools...
checking for spumux... ok
checking for dvdauthor... ok
checking for growisofs... ok
checking for mkisofs... ok
configure: Checking for vcd tools...
checking for vcdxbuild... MISSING
checking for cdrdao... ok
configure: WARNING: Cannot find vcdimager! You cannot burn (S)VCDs.
configure: Checking for transcode...
checking for tcprobe... MISSING
checking for tcrequant... MISSING
configure: WARNING: Cannot find transcode! You cannot use postproc.
./configure: line 2690: gawk: command not found
./configure: line 2691: gawk: command not found
./configure: line 2690: gawk: command not found
./configure: line 2691: gawk: command not found
./configure: line 2690: gawk: command not found
./configure: line 2691: gawk: command not found
./configure: line 2690: gawk: command not found
./configure: line 2691: gawk: command not found
./configure: line 2690: gawk: command not found
./configure: line 2691: gawk: command not found
./configure: line 2690: gawk: command not found
./configure: line 2691: gawk: command not found
./configure: line 2690: gawk: command not found
./configure: line 2691: gawk: command not found
./configure: line 2690: gawk: command not found
./configure: line 2691: gawk: command not found
./configure: line 2690: gawk: command not found
./configure: line 2691: gawk: command not found
./configure: line 2690: gawk: command not found
./configure: line 2691: gawk: command not found
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/tovid-init.sh
config.status: creating setuplib.py
configure:

FINAL SUMMARY

Required dependencies   ALL FOUND

Other dependencies      SOME MISSING

  magick (needed to make menus and slideshows)
    composite:    ok part of ImageMagick ([www.imagemagick.org](www.imagemagick.org))
    convert:      ok part of ImageMagick ([www.imagemagick.org](www.imagemagick.org))

  dvd (needed to make DVD menus and burn DVDs)
    spumux:       ok part of dvdauthor (dvdauthor.sf.net)
    dvdauthor:    ok part of dvdauthor (dvdauthor.sf.net)
    growisofs:    ok part of dvd+rw-tools: (fy.chalmers.se/~appro/linux/DVD+RW)
    mkisofs:      ok part of cdrecord (cdrecord.berlios.de)

  vcd (needed to burn (S)VCDs)
    vcdxbuild:    MISSING part of vcdimager ([www.vcdimager.org](www.vcdimager.org))
    cdrdao:       ok part of cdrecord (cdrecord.berlios.de)

  transcode (needed to compress encode videos)
    tcprobe:      MISSING part of transcode ([www.transcoding.org](www.transcoding.org))
    tcrequant:    MISSING part of transcode ([www.transcoding.org](www.transcoding.org))

 You may now type './setup.sh' to compile and install tovid.

sam@tuxbox:~/tovid-0.25$ ./setup.sh
Please enter the root password to install tovid system-wide
Password:
Making and installing the executables...
Making install in src
make[1]: Entering directory `/home/sam/tovid-0.25/src'
rm -f "dvrequant"
echo "#! `command -v sh`"  > dvrequant
cat ./dvrequant.sh >> dvrequant
chmod ugo+x dvrequant
rm -f "idvid"
echo "#! `command -v sh`"  > idvid
cat ./idvid.sh >> idvid
chmod ugo+x idvid
rm -f "makedvd"
echo "#! `command -v sh`"  > makedvd
cat ./makedvd.sh >> makedvd
chmod ugo+x makedvd
rm -f "makemenu"
echo "#! `command -v sh`"  > makemenu
cat ./makemenu.sh >> makemenu
chmod ugo+x makemenu
rm -f "makeslides"
echo "#! `command -v sh`"  > makeslides
cat ./makeslides.sh >> makeslides
chmod ugo+x makeslides
rm -f "makevcd"
echo "#! `command -v sh`"  > makevcd
cat ./makevcd.sh >> makevcd
chmod ugo+x makevcd
rm -f "makexml"
echo "#! `command -v sh`"  > makexml
cat ./makexml.sh >> makexml
chmod ugo+x makexml
rm -f "postproc"
echo "#! `command -v sh`"  > postproc
cat ./postproc.sh >> postproc
chmod ugo+x postproc
rm -f "previd"
echo "#! `command -v sh`"  > previd
cat ./previd.sh >> previd
chmod ugo+x previd
rm -f "tovid"
echo "#! `command -v sh`"  > tovid
cat ./tovid.sh >> tovid
chmod ugo+x tovid
rm -f "tovid-batch"
echo "#! `command -v sh`"  > tovid-batch
cat ./tovid-batch.sh >> tovid-batch
chmod ugo+x tovid-batch
rm -f "tovid-init"
echo "#! `command -v sh`"  > tovid-init
cat ./tovid-init.sh >> tovid-init
chmod ugo+x tovid-init
rm -f "tovid-interactive"
echo "#! `command -v sh`"  > tovid-interactive
cat ./tovid-interactive.sh >> tovid-interactive
chmod ugo+x tovid-interactive
rm -f "tovid-test"
echo "#! `command -v sh`"  > tovid-test
cat ./tovid-test.sh >> tovid-test
chmod ugo+x tovid-test
rm -f "pytovid"
echo "#! `command -v python`"  > pytovid
cat ./pytovid.py >> pytovid
chmod ugo+x pytovid
rm -f "pymakemenu"
echo "#! `command -v python`"  > pymakemenu
cat ./pymakemenu.py >> pymakemenu
chmod ugo+x pymakemenu
rm -f "pymakexml"
echo "#! `command -v python`"  > pymakexml
cat ./pymakexml.py >> pymakexml
chmod ugo+x pymakexml
rm -f "tovidgui"
echo "#! `command -v python`"  > tovidgui
cat ./tovidgui.py >> tovidgui
chmod ugo+x tovidgui
make[2]: Entering directory `/home/sam/tovid-0.25/src'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
 /usr/bin/install -c 'dvrequant' '/usr/local/bin/dvrequant'
 /usr/bin/install -c 'idvid' '/usr/local/bin/idvid'
 /usr/bin/install -c 'makedvd' '/usr/local/bin/makedvd'
 /usr/bin/install -c 'makemenu' '/usr/local/bin/makemenu'
 /usr/bin/install -c 'makeslides' '/usr/local/bin/makeslides'
 /usr/bin/install -c 'makevcd' '/usr/local/bin/makevcd'
 /usr/bin/install -c 'makexml' '/usr/local/bin/makexml'
 /usr/bin/install -c 'postproc' '/usr/local/bin/postproc'
 /usr/bin/install -c 'previd' '/usr/local/bin/previd'
 /usr/bin/install -c 'tovid' '/usr/local/bin/tovid'
 /usr/bin/install -c 'tovid-batch' '/usr/local/bin/tovid-batch'
 /usr/bin/install -c 'tovid-init' '/usr/local/bin/tovid-init'
 /usr/bin/install -c 'tovid-interactive' '/usr/local/bin/tovid-interactive'
 /usr/bin/install -c 'tovid-test' '/usr/local/bin/tovid-test'
 /usr/bin/install -c 'pytovid' '/usr/local/bin/pytovid'
 /usr/bin/install -c 'pymakemenu' '/usr/local/bin/pymakemenu'
 /usr/bin/install -c 'pymakexml' '/usr/local/bin/pymakexml'
 /usr/bin/install -c 'tovidgui' '/usr/local/bin/tovidgui'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/sam/tovid-0.25/src'
make[1]: Leaving directory `/home/sam/tovid-0.25/src'
make[1]: Entering directory `/home/sam/tovid-0.25'
make[2]: Entering directory `/home/sam/tovid-0.25'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/man/man1" || mkdir -p -- "/usr/local/man/man1"
 /usr/bin/install -c -m 644 './docs/man/idvid.1' '/usr/local/man/man1/idvid.1'
 /usr/bin/install -c -m 644 './docs/man/makedvd.1' '/usr/local/man/man1/makedvd.1'
 /usr/bin/install -c -m 644 './docs/man/makemenu.1' '/usr/local/man/man1/makemenu.1'
 /usr/bin/install -c -m 644 './docs/man/makeslides.1' '/usr/local/man/man1/makeslides.1'
 /usr/bin/install -c -m 644 './docs/man/makexml.1' '/usr/local/man/man1/makexml.1'
 /usr/bin/install -c -m 644 './docs/man/postproc.1' '/usr/local/man/man1/postproc.1'
 /usr/bin/install -c -m 644 './docs/man/tovid.1' '/usr/local/man/man1/tovid.1'
make[2]: Leaving directory `/home/sam/tovid-0.25'
make[1]: Leaving directory `/home/sam/tovid-0.25'
Installing the python libararies...
running install
error: invalid Python installation: unable to open /usr/lib/python2.4/config/Makefile (No such file or directory)
Could not install the python libraries!
Try "su -c './setup'"
sam@tuxbox:~/tovid-0.25$


i have tryed su -c ./setup and this dont wrk..help would me appreciated :D thank you

---

### Post by taurus on 2006-02-14
You need to install a GCC compiler and all the necessary libraries before you can build a program from source,

sudo apt-get install build-essential

However, you can install tovid with apt-get or synaptic!!!  Just add the following two lines to the end of your /etc/apt/sources.list and run

> 
deb [http://packages.kirya.net](http://packages.kirya.net) unstable main contrib non-free
deb-src [http://packages.kirya.net](http://packages.kirya.net) unstable main contrib non-free


sudo apt-get update
sudo apt-get install tovid

---

### Post by neoroses on 2006-02-14
thank you very much - will this program then appear under sound and video? if not how do i run it? thanks

---

### Post by neoroses on 2006-02-14
ok its installed how do i open it for use now?:S sorry for my n00bness

---

### Post by taurus on 2006-02-14
I am still at work and not in front of my computer (Ubuntu) right now but just look through all the options in the menu then.  Otherwise, type this at the prompt,

sudo tovidgui.py

---

### Post by RikoW on 2006-02-15
[QUOTE=taurus]
sudo tovidgui.py[/QUOTE]

You should not need to run it via sudo!
tovid/tovidgui.py runs just fine under a regular user

Cheers,

             Riko

---

### Post by taurus on 2006-02-15
[QUOTE=RikoW]You should not need to run it via sudo!
tovid/tovidgui.py runs just fine under a regular user

Cheers,

             Riko[/QUOTE]
Yes, you can run tovidgui.py as a regular user BUT assuming you can write to a DVD!!!

---

### Post by RikoW on 2006-02-15
[QUOTE=taurus]Yes, you can run tovidgui.py as a regular user BUT assuming you can write to a DVD!!![/QUOTE]

True! Just add the user to the group "cdrom", which is allowed to write to the drives in a "normal" Ubuntu installation. Certainly safer than running an application unnecessarily with root priviliges. ;) 

If you are the default user, you should be a member of that group already. To find out, type:

```
id *username*
```

If not, you can use the Users and Groups dialog in the System -> Administration menu.

Cheers,
               Riko

---

### Post by neoroses on 2006-02-15
rite ok i finaly got it to encode my video to pal dvd however before the burnstage it came up with a error message,,,,so now i have the mpeg...anway i kan now put this onto a dvd? thanks

---

### Post by taurus on 2006-02-15
What was the error message?  Now, you can just use k3b to burn it to your DVD then...

---

### Post by neoroses on 2006-02-15
i can use k3b to burn the mpeg to dvd????

here isthe tovid log 

The following commands will be run:
=========================================
makemenu -pal -dvd -align left -textcolor "rgb(255,255,255)" -highlightcolor "rgb(255,255,0)" -selectcolor "rgb(255,0,0)" -font "Default" "pdy-aeontcxvid.avi.tovid encoded.mpg" "/tmp/Untitled_menu_1"
------------------------
tovid -overwrite -pal -dvd -full  -in "/home/sam/Desktop/pdy-aeontcxvid.avi.tovid_encoded.mpg" -out "/tmp/pdy-aeontcxvid.avi.tovid encoded.mpg.tovid_encoded" 
------------------------
makexml -dvd -overwrite -menu "/tmp/Untitled_menu_1.mpg" "/tmp/pdy-aeontcxvid.avi.tovid encoded.mpg.tovid_encoded.mpg" "/tmp/Untitled_disc"
------------------------
Running command: makemenu -pal -dvd -align left -textcolor "rgb(255,255,255)" -highlightcolor "rgb(255,255,0)" -selectcolor "rgb(255,0,0)" -font "Default" "pdy-aeontcxvid.avi.tovid encoded.mpg" "/tmp/Untitled_menu_1"
--------------------------------
makemenu
A script to generate DVD/(S)VCD menus
Part of the tovid suite, version 0.25
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
Adding title pdy-aeontcxvid.avi.tovid encoded.mpg
Adding title /tmp/Untitled_menu_1
Usage: makemenu [OPTIONS] "Title1" "Title2" ... -out {output prefix}

Common options:

    -pal | -ntsc | -ntscfilm            Set TV standard
    -dvd | -vcd | -svcd                 Encode to standard format
    -background IMAGE                   ex: -background star_field.png
    -audio AUDIOFILE                    ex: -audio foo_fighters.mp3
    -font "FONTNAME"                    ex: -font Courier

Example: 

    makemenu -background ocean.jpg "First" "Second" "Third" -out mymenu
        Create 'mymenu.mpg' with three titles and a custom background image.

See the makemenu manual page ('man makemenu') for additional documentation.
=========================================================
*** Please provide an output prefix with the -out option.
Running command: tovid -overwrite -pal -dvd -full  -in "/home/sam/Desktop/pdy-aeontcxvid.avi.tovid_encoded.mpg" -out "/tmp/pdy-aeontcxvid.avi.tovid encoded.mpg.tovid_encoded" 
Using config file /home/sam/.tovid/tovid.config, containing the following options:
(none)
Changing to working directory: /home/sam
--------------------------------
tovid 
DVD and (S)VCD video conversion script
Version 0.25
[http://www.tovid.org](http://www.tovid.org)
--------------------------------

=========================================================

Converting /home/sam/Desktop/pdy-aeontcxvid.avi.tovid_encoded.mpg to compliant PAL DVD format
Storing log and temporary files in /home/sam/tovid-temp.gcmP4D

=========================================================

Probing video for information. This may take several minutes...
The encoding process is estimated to require 3730 MB of disk space.
You currently have 21743 MB available in this directory.
Analysis of file /home/sam/Desktop/pdy-aeontcxvid.avi.tovid_encoded.mpg:
  720 x 576 pixels, 25.000 fps
  Duration (best guess): 01:28:49 (HH:MM:SS)
  MPEG2 video with ac3 audio

=========================================================

Audio and video streams appear to already be compliant with the
selected output format. If you want to force encoding (for instance,
to change the bitrate or take advantage of denoising), run tovid
again with the '-force' option. A symbolic link has been created
in place of the output file:
    /tmp/pdy-aeontcxvid.avi.tovid encoded.mpg.tovid_encoded.mpg --> /home/sam/Desktop/pdy-aeontcxvid.avi.tovid_encoded.mpg

=========================================================

Done!
Cleaning up...
Removing temporary files...
removed `/home/sam/tovid-temp.gcmP4D/tovid.log'
removed `/home/sam/tovid-temp.gcmP4D/tovid.scratch'
removed directory: `/home/sam/tovid-temp.gcmP4D'
Running command: makexml -dvd -overwrite -menu "/tmp/Untitled_menu_1.mpg" "/tmp/pdy-aeontcxvid.avi.tovid encoded.mpg.tovid_encoded.mpg" "/tmp/Untitled_disc"
--------------------------------
makexml
A script to generate XML for authoring a VCD, SVCD, or DVD.
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
The file /tmp/Untitled_menu_1.mpg was not found.
Adding a titleset-level menu using file: /tmp/Untitled_menu_1.mpg
Adding title: /tmp/pdy-aeontcxvid.avi.tovid encoded.mpg.tovid_encoded.mpg as title number 1 of titleset 1
Calculating the duration of the video using the following command:
idvid -terse "/tmp/pdy-aeontcxvid.avi.tovid encoded.mpg.tovid_encoded.mpg"
This may take a few minutes, so please be patient...
The duration of the video is 01:28:49
Closing titleset 1 with 1 title(s).
==========================================
Some of the video files you specified were not found.
The XML file was written anyway, but you might want to
double-check to make sure you didn't make a typing mistake.
==========================================
Done. The resulting XML was written to /tmp/Untitled_disc.xml.
You can now author, image and/or burn the disc by running:
    makedvd /tmp/Untitled_disc.xml
Thanks for using makexml!

---

### Post by TomAnthony on 2006-02-16
I'm getting this error when trying to run the Tovid GUI:

Traceback (most recent call last):
  File "/usr/local/bin/tovidgui", line 33, in ?
    from libtovid import TDL, Parser, Project
ImportError: cannot import name Parser

Any ideas whats wrong here?

---

### Post by mgsfan on 2006-02-18
I am getting the same error as you

---

### Post by TomAnthony on 2006-02-20
I got this answer from the Tovid forum, and it works for me:

Posted: Mon Feb 20, 2006 5:42 am  by Mac North

Remove "Parser" from line 33 in /usr/local/bin/tovidgui (or wherever you installed it) and things should be ok. wapcaplet would know more about why Parser isn't needed. I think because Save/Load project funtionality is still under development?

---

### Post by mgsfan on 2006-02-20
erm..how would I go about that...lol

---

### Post by jtpratt on 2006-03-16
depending on which version of Tovid you installed......

for 0.22 in repository run this command in terminal:
tovid-gui

for 0.25 latest version installed from source:
tovidgui

there is no need for the .py extension - you don't need it to run the program.

I have tovid and other video conversion info on my Ubuntu 5.10 guide page:
[http://smorgasbord.net/convert_video_linux]("http://smorgasbord.net/convert_video_linux")

---

