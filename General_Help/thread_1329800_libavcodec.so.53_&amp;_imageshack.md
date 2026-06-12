---
title: "libavcodec.so.53 &amp; imageshack"
date: 2009-11-17
forum: General Help
---

### Post by joey-elijah on 2009-11-17
I've installed the official ImageShack uploader in Karmic but i hit the same brick wall as i did in Jaunty: 

joey@joey-ubuntu:~$ imageshack-uploader 
imageshack-uploader: error while loading shared libraries: libavcodec.so.52: cannot open shared object file: No such file or directory

Any one got any clues on how to resolve this?

---

### Post by zedstrange on 2010-01-01
No clue but i would like to know the answer too
am using Karmic 64bit

---

### Post by Excedio on 2010-01-05
Also having this problem. Any solution yet? Also going to contact [s]Imagesgack[/s] [[COLOR=#444444]CodeMinders[/COLOR]]("http://codeminders.com/") about this, they are the developers of the software.

---

### Post by Excedio on 2010-01-05
Ok...I emailed the programers for the software and with this:
 
> 
[FONT=Calibri][SIZE=3]Hey There[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I recently made the switch from Photobucket to Imageshack &#8211; I found out that Photobucket will no longer be supporting Linux so I dropped them. Then I saw that Imageshack had a bulk uploader (developed by you all of course :-)), and that it was available for Linux&#8230;natively&#8230;AWESOME! I downloaded the DEB file and installed it, however, when I clicked on the program in Applications > Internet > Imageshack Uploader it did not do anything. I then ran it in the terminal and got this:[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]excedio@excedio-desktop:~$ imageshack-uploader[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]imageshack-uploader: error while loading shared libraries: libavcodec.so.52: cannot open shared object file: No such file or directory[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]excedio@excedio-desktop:~$[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I am currently using Ubuntu 9.10 64bit. Please help, I really want to support your software.[/SIZE][/FONT]

 
and here is the reply I got:
 
> 
[FONT=Calibri][SIZE=3]Excedio,[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]There is some problem with Ubuntu 9.10. We are looking into it. [/SIZE][SIZE=3]Also you probably aware that uploader is open source. So, if somebody is willing to [/SIZE][/FONT][FONT=Calibri][SIZE=3]take a look at the problem and send us patches it would help.[/SIZE][/FONT]
 
[FONT=Calibri][[SIZE=3]http://code.google.com/p/imageshack-uploader/[/SIZE]]("http://code.google.com/p/imageshack-uploader/")[/FONT]
 
[FONT=Calibri][SIZE=3]We do not have Ubuntu 9.10 handy, so we will need to install it first to test and debug and [/SIZE][/FONT][FONT=Calibri][SIZE=3]that might take few days.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Sincerely,[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Vadim Zaliva,[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]President, Tristero Consulting[/SIZE][/FONT]
 

 
Since I am far from being a programer, maybe someone else in the forum can help out. Also, I am posting this same information in this ([http://ubuntuforums.org/showthread.php?p=8614588#post8614588](http://ubuntuforums.org/showthread.php?p=8614588#post8614588)) thread. It's related to the same thing.

---

### Post by Excedio on 2010-01-05
See here:
 
[http://code.google.com/p/imageshack-uploader/issues/detail?id=181](http://code.google.com/p/imageshack-uploader/issues/detail?id=181)

---

### Post by A2K on 2010-01-05
Hello. I am developer working on this project.
Ubuntu Karmic Koala has libavcodec.so.52 (see [here](http://packages.ubuntu.com/search?keywords=libavcodec&searchon=names&suite=karmic&section=all)) in repos and there is dependency for it in imageshack-uploader package.
I have tried installing ubuntu today, updating it and installing imageshack-uploader package. It works without any problems.

Are you using some extra repositories with newer version of ffmpeg/libavcodec?

I have two solutions for you.

You can try downgrade to distro's ffmpeg/libavcodec version:
1) Locate that extra repository with newer libavcodec version
2) Remove it from repository list
3) Run sudo aptitude update
4) Remove package ffmpeg with it's dependencies
5) Removed cached deb file from /var/cache/apt/archives
6) Install ffmpeg package again

**OR**

you can try to create symlink, but i'm not if it will work for you:
1) Check libavcodec version you have:
$ ls /usr/lib/libavcodec.so.*
/usr/lib/libavcodec.so.52  /usr/lib/libavcodec.so.52.20.0
on my system it is **52.20.0**
note: /usr/lib/libavcodec.so.52 (you may have 53 or some other version) here is symlink to /usr/lib/libavcodec.so.52.20.0 (you may have 53.x.y).
2) Create symlink:
$ sudo ln -s /usr/lib/libavcodec.so.*52.20.0* /usr/lib/libavcodec.so.52
**Important**: change 52.20.0 to your libavcodec version from step 1.

Good luck.

---

### Post by Excedio on 2010-01-05
> **A2K said:**
> you can try to create symlink, but i'm not if it will work for you:
1) Check libavcodec version you have:
$ ls /usr/lib/libavcodec.so.*
/usr/lib/libavcodec.so.52  /usr/lib/libavcodec.so.52.20.0
on my system it is **52.20.0**
note: /usr/lib/libavcodec.so.52 (you may have 53 or some other version) here is symlink to /usr/lib/libavcodec.so.52.20.0 (you may have 53.x.y).
2) Create symlink:
$ sudo ln -s /usr/lib/libavcodec.so.*52.20.0* /usr/lib/libavcodec.so.52
**Important**: change 52.20.0 to your libavcodec version from step 1.

Thank you for replying in the forum, it's very much appreciated.

Unfortunately, this did not work for me. I still get the same error. I'm going to give the first option a try.

---

### Post by LightningCrash on 2010-01-14
I am having this issue on Kubuntu 9.10 x86_64

I straced imageshack's uploader and it's looking for the 32-bit libavcodec library
snippet:
open("/lib32/libavcodec.so.52", O_RDONLY) = -1 ENOENT (No such file or directory)                   

`ldd /usr/bin/imageshack-uploader` says it's also missing other items:
        libavcodec.so.52 => not found
        libavformat.so.52 => not found
        libswscale.so.0 => not found
        libavutil.so.49 => not found

I used `getlibs /usr/bin/imageshack-uploader` to grab them and everything worked fine.
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by Excedio on 2010-01-14
Fail.. :-(

```
excedio@excedio-desktop:~$ getlibs /usr/bin/imageshack-uploader
libavcodec.so.52: libavcodec-extra-52
libavformat.so.52: libavformat-extra-52
libswscale.so.0: libswscale-extra-0
libavutil.so.49: libavutil-extra-49
The following i386 packages will be installed:
libavcodec-extra-52
libavformat-extra-52
libavutil-extra-49
libswscale-extra-0
Continue [Y/n]? y
Downloading ...
Failed to download file http://mirrors.kernel.org/ubuntu/pool/non-free/f/ffmpeg-extra/libavcodec-extra-52_0.5+svn20090706-2ubuntu3+medibuntu1_i386.deb
The mirrors do not have the requested file or there is no internet connection
Failed to download file http://mirrors.kernel.org/ubuntu/pool/non-free/f/ffmpeg-extra/libavformat-extra-52_0.5+svn20090706-2ubuntu3+medibuntu1_i386.deb
The mirrors do not have the requested file or there is no internet connection
Failed to download file http://mirrors.kernel.org/ubuntu/pool/non-free/f/ffmpeg-extra/libavutil-extra-49_0.5+svn20090706-2ubuntu3+medibuntu1_i386.deb
The mirrors do not have the requested file or there is no internet connection
Failed to download file http://mirrors.kernel.org/ubuntu/pool/non-free/f/ffmpeg-extra/libswscale-extra-0_0.5+svn20090706-2ubuntu3+medibuntu1_i386.deb
The mirrors do not have the requested file or there is no internet connection
No packages to install
excedio@excedio-desktop:~$
```

---

### Post by Excedio on 2010-01-14
So I found libavcodec-extra-52_0.5+svn20090706-2ubuntu3+medibuntu1_i386.deb

I force installed it and my computer went nuts telling me that I had broken packages. So I had to force re-install the 64bit version.

Long story short here.. It seems that the Imageshack-uploader needs to be 64bit as well.

---

### Post by LightningCrash on 2010-01-15
I always use Argonne's mirrors (mirror.anl.gov), that may be why getlibs worked fine on mine.

---

### Post by Excedio on 2010-01-16
> **LightningCrash said:**
> I always use Argonne's mirrors (mirror.anl.gov), that may be why getlibs worked fine on mine.

Tried the mirror that you suggested and the same thing happened :-|

---

### Post by LightningCrash on 2010-01-17
> **Excedio said:**
> Tried the mirror that you suggested and the same thing happened :-|

Are you running i386 or AMD64?

I just tried it on my 9.10 i386 laptop and it only griped about ffmpeg. I installed ffmpeg and it opened just fine.

---

### Post by zillacles on 2010-01-18
Using getlibs solved it for me on 64bit Karmic. Thanks!

---

### Post by Excedio on 2010-01-18
> **LightningCrash said:**
> Are you running i386 or AMD64?
 
I just tried it on my 9.10 i386 laptop and it only griped about ffmpeg. I installed ffmpeg and it opened just fine.
 
64bit Karmic. I don't understand why I would not be to use
```
 
getlibs /usr/bin/imageshack-uploader

```
but other's can. Doesn't make sense to me.

---

### Post by illbashu on 2010-01-22
> **zillacles said:**
> Using getlibs solved it for me on 64bit Karmic. Thanks!

How? I have Ubuntu 9.10 64bit and I keep getting the shitty "The mirrors do not have the requested file or there is no internet connection" prob. What mirror are you using and how do I change mine?

---

### Post by illbashu on 2010-01-22
I built it from the source and it's working fine.

Instructions. 
[http://code.google.com/p/imageshack-uploader/wiki/BuildInstructions](http://code.google.com/p/imageshack-uploader/wiki/BuildInstructions)

Source.
[http://code.google.com/p/imageshack-uploader/source/checkout](http://code.google.com/p/imageshack-uploader/source/checkout)

You'll need a Dev key which you can request here.
[http://reg.imageshack.us/content.php?page=email&q=marketing&sub=XML%20API%20Request](http://reg.imageshack.us/content.php?page=email&q=marketing&sub=XML%20API%20Request)

---

### Post by Excedio on 2010-01-22
I'm not very good at compiling from source, would you mind providing a step-by-step?

---

### Post by illbashu on 2010-01-22
make a folder and cd into it.

```
sudo apt-get install mercurial
```

```
hg clone https://imageshack-uploader.googlecode.com/hg/ imageshack-uploader

```

cd into the folder that is downloaded.

Getting the dependencies.
```
sudo aptitude install libqt4-gui libqt4-core libqt4-xml qt4-dev-tools
```

Request a key from link above.
```
IMAGESHACK_DEVELOPER_KEY="YOURdeveloperKEY" qmake

```

```
sudo make install 
```

---

### Post by Excedio on 2010-01-22
> **illbashu said:**
> make a folder and cd into it.
 
```
sudo apt-get install mercurial
```
 
```
hg clone https://imageshack-uploader.googlecode.com/hg/ imageshack-uploader

```
 
cd into the folder that is downloaded.
 
Getting the dependencies.
```
sudo aptitude install libqt4-gui libqt4-core libqt4-xml qt4-dev-tools
```
 
Request a key from link above.
```
IMAGESHACK_DEVELOPER_KEY="YOURdeveloperKEY" qmake

```
 
```
sudo make install 
```
 
Thanks, I'll try this at home tonight. :-)

---

### Post by illbashu on 2010-01-22
1 more thing, make sure you have ffmpeg installed.

---

### Post by Excedio on 2010-02-12
Now I'm getting this..

```

excedio@excedio-desktop:~/imageshack-uploader$ IMAGESHACK_DEVELOPER_KEY="redacted" qmake
Package libavcodec was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavcodec.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavcodec' found
Package libavformat was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavformat.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavformat' found
Package libswscale was not found in the pkg-config search path.
Perhaps you should add the directory containing `libswscale.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libswscale' found
Package libavutil was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavutil.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavutil' found
Project ERROR: Could not find ffmpeg libraries
excedio@excedio-desktop:~/imageshack-uploader$

```

---

### Post by illbashu on 2010-02-12
> **Excedio said:**
> Now I'm getting this..

```

excedio@excedio-desktop:~/imageshack-uploader$ IMAGESHACK_DEVELOPER_KEY="key" qmake
Package libavcodec was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavcodec.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavcodec' found
Package libavformat was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavformat.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavformat' found
Package libswscale was not found in the pkg-config search path.
Perhaps you should add the directory containing `libswscale.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libswscale' found
Package libavutil was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavutil.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavutil' found
Project ERROR: Could not find ffmpeg libraries
excedio@excedio-desktop:~/imageshack-uploader$

```

1) Remove the Devs key, that is suppose to be private. 

2 ```
sudo aptitude install libavcodec-dev libavformat-dev libswscale-dev libavutil-dev
```

That should fix that error.

---

### Post by philpem on 2010-02-19
> **Excedio said:**
> 
```
Failed to download file http://mirrors.kernel.org/ubuntu/pool/non-free/f/ffmpeg-extra/libavcodec-extra-52_0.5+svn20090706-2ubuntu3+medibuntu1_i386.deb
The mirrors do not have the requested file or there is no internet connection
```

There's a bug in Getlibs. On line 413, it checks to see if a mirror has been specified on the command line. If not, it uses the kernel.org mirror as a fallback. Problem is, it checks the wrong variable... it checks the state of $mirror, not $mirror2...

So edit /usr/bin/getlibs in (say) gedit, zip to line 413 and change this:
```
if [ -z $mirror ]; then
```
to this:
```
if [ -z $mirror2 ]; then
```

This should make getlibs work OK. Also check that you've got the Medibuntu repository in your apt/sources.list. I seem to have Medibuntu packages on my system but Medibuntu isn't on my sources list (?!) -- this might be down to having upgraded from 9.04.


EDIT1: The Medibuntu sources are in /etc/apt/sources.list.d, which Getlibs ignores. Working on a patch to fix this now... For now, applying the above patch and using the command "sudo getlibs -m [http://packages.medibuntu.org/](http://packages.medibuntu.org/) /usr/bin/imageshack-uploader" should work.


EDIT2: Fixed the other bug. Line 382, change this:
```
                if [ -f "/etc/apt/sources.list" ]; then
                    linkmirror=`grep -o -m 1 "$linkmirror[^ ]*" /etc/apt/sources.list`
                elif [ -f "/etc/apt/sources.lst" ]; then
                    linkmirror=`grep -o -m 1 "$linkmirror[^ ]*" /etc/apt/sources.lst`
                else
```
to this:
```
                if [ -f "/etc/apt/sources.list" ]; then
                    linkmirror=`grep -h -o -m 1 "$linkmirror[^ ]*" /etc/apt/sources.list /etc/apt/sources.list.d/*.list`
                elif [ -f "/etc/apt/sources.lst" ]; then
                    linkmirror=`grep -h -o -m 1 "$linkmirror[^ ]*" /etc/apt/sources.lst /etc/apt/sources.list.d/*.list`
                else
```

You will also need to apply the patch in "EDIT1".

Then run these commands to install the required libraries:
```
sudo getlibs /usr/bin/imageshack-uploader
sudo getlibs -p libamrnb3
sudo getlibs -p libamrwb3
```

You should now be able to run the ImageShack Uploader.

---

### Post by Excedio on 2010-02-19
> **philpem said:**
> There's a bug in Getlibs. On line 413, it checks to see if a mirror has been specified on the command line. If not, it uses the kernel.org mirror as a fallback. Problem is, it checks the wrong variable... it checks the state of $mirror, not $mirror2...
 
So edit /usr/bin/getlibs in (say) gedit, zip to line 413 and change this:
```
if [ -z $mirror ]; then
```
to this:
```
if [ -z $mirror2 ]; then
```
 
This should make getlibs work OK. Also check that you've got the Medibuntu repository in your apt/sources.list. I seem to have Medibuntu packages on my system but Medibuntu isn't on my sources list (?!) -- this might be down to having upgraded from 9.04.
 
 
EDIT1: The Medibuntu sources are in /etc/apt/sources.list.d, which Getlibs ignores. Working on a patch to fix this now... For now, applying the above patch and using the command "sudo getlibs -m [http://packages.medibuntu.org/](http://packages.medibuntu.org/) /usr/bin/imageshack-uploader" should work.
 
 
EDIT2: Fixed the other bug. Line 382, change this:
```
                if [ -f "/etc/apt/sources.list" ]; then
                    linkmirror=`grep -o -m 1 "$linkmirror[^ ]*" /etc/apt/sources.list`
                elif [ -f "/etc/apt/sources.lst" ]; then
                    linkmirror=`grep -o -m 1 "$linkmirror[^ ]*" /etc/apt/sources.lst`
                else
```
to this:
```
                if [ -f "/etc/apt/sources.list" ]; then
                    linkmirror=`grep -h -o -m 1 "$linkmirror[^ ]*" /etc/apt/sources.list /etc/apt/sources.list.d/*.list`
                elif [ -f "/etc/apt/sources.lst" ]; then
                    linkmirror=`grep -h -o -m 1 "$linkmirror[^ ]*" /etc/apt/sources.lst /etc/apt/sources.list.d/*.list`
                else
```
 
You will also need to apply the patch in "EDIT1".
 
Then run these commands to install the required libraries:
```
sudo getlibs /usr/bin/imageshack-uploader
sudo getlibs -p libamrnb3
sudo getlibs -p libamrwb3
```
 
You should now be able to run the ImageShack Uploader.
 
 
YOU ROCK! IT WORKS!!! :-D
 
Thanks so much man! :-D

---

### Post by illbashu on 2010-02-19
> **Excedio said:**
> Now I'm getting this..

```

excedio@excedio-desktop:~/imageshack-uploader$ IMAGESHACK_DEVELOPER_KEY="redacted" qmake
Package libavcodec was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavcodec.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavcodec' found
Package libavformat was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavformat.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavformat' found
Package libswscale was not found in the pkg-config search path.
Perhaps you should add the directory containing `libswscale.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libswscale' found
Package libavutil was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavutil.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavutil' found
Project ERROR: Could not find ffmpeg libraries
excedio@excedio-desktop:~/imageshack-uploader$

```

Did you get it working?

Edit: I guess you did seeing above post.

---

### Post by abdusamed on 2010-08-31
What does Image Shack Uploader has to do with SMPlayers other files installs? I like fixed my mplayer 2 days ago after a month of it not working. The last thing and the thing which I don't want to is to mess it up again with exactly same file missing.

From what I can see, both have close enough the same error. Something got to do with libav..52

---

### Post by abdusamed on 2010-09-02
> **philpem said:**
> There's a bug in Getlibs. On line 413, it checks to see if a mirror has been specified on the command line. If not, it uses the kernel.org mirror as a fallback. Problem is, it checks the wrong variable... it checks the state of $mirror, not $mirror2...

So edit /usr/bin/getlibs in (say) gedit, zip to line 413 and change this:
```
if [ -z $mirror ]; then
```to this:
```
if [ -z $mirror2 ]; then
```This should make getlibs work OK. Also check that you've got the Medibuntu repository in your apt/sources.list. I seem to have Medibuntu packages on my system but Medibuntu isn't on my sources list (?!) -- this might be down to having upgraded from 9.04.


EDIT1: The Medibuntu sources are in /etc/apt/sources.list.d, which Getlibs ignores. Working on a patch to fix this now... For now, applying the above patch and using the command "sudo getlibs -m [http://packages.medibuntu.org/](http://packages.medibuntu.org/) /usr/bin/imageshack-uploader" should work.


EDIT2: Fixed the other bug. Line 382, change this:
```
                if [ -f "/etc/apt/sources.list" ]; then
                    linkmirror=`grep -o -m 1 "$linkmirror[^ ]*" /etc/apt/sources.list`
                elif [ -f "/etc/apt/sources.lst" ]; then
                    linkmirror=`grep -o -m 1 "$linkmirror[^ ]*" /etc/apt/sources.lst`
                else
```to this:
```
                if [ -f "/etc/apt/sources.list" ]; then
                    linkmirror=`grep -h -o -m 1 "$linkmirror[^ ]*" /etc/apt/sources.list /etc/apt/sources.list.d/*.list`
                elif [ -f "/etc/apt/sources.lst" ]; then
                    linkmirror=`grep -h -o -m 1 "$linkmirror[^ ]*" /etc/apt/sources.lst /etc/apt/sources.list.d/*.list`
                else
```You will also need to apply the patch in "EDIT1".

Then run these commands to install the required libraries:
```
sudo getlibs /usr/bin/imageshack-uploader
sudo getlibs -p libamrnb3
sudo getlibs -p libamrwb3
```You should now be able to run the ImageShack Uploader.

getlibs -- DNE! [does not exists]

now what?

---

### Post by orengolan on 2010-10-10
similar error appear on ubuntu 10.10:
```
error while loading shared libraries: libavutil.so.49: cannot open shared object file: No such file or directory 
```

any clues?

---

### Post by mc4man on 2010-10-10
> any clues?
Well maverick uses libavutil50
I guess you could try 3 things.

Wait for the uploader to update to the 0.6 ffmpeg

Install the uploader available in maverick repos

grab just the the [lucid libavutil49]("http://packages.ubuntu.com/lucid/libavutil49") and install, may work out, may not
(You can install it without issue - nothing in mav. should be using it

edit

As it happens my maverick was lucid upgraded in May and libavutil49 is still installed (screen

The current imageshack-uploader from the site loads up fine ( though I'd probably be inclined to use the maverick build instead - both 2.2, the site one is slightly newer

---

### Post by orengolan on 2010-10-11
installed libavutil49 and it's working.

Thanks!

---

### Post by tareq.mhd on 2010-10-16
I am facing this problem.
```
tareq@tareq-laptop:~/Desktop/imageshack-uploader$ sudo make install
Makefile:328: warning: overriding commands for target `clean'
Makefile:302: warning: ignoring old commands for target `clean'
lrelease translations/ar_IQ.ts translations/bg_BG.ts translations/cz_CZ.ts translations/de_DE.ts translations/el_GR.ts translations/en_US.ts translations/es_ES.ts translations/fi_FI.ts translations/fr_FR.ts translations/hu_HU.ts translations/it_IT.ts translations/ka_GE.ts translations/kr_KR.ts translations/lt_LT.ts translations/lv_LV.ts translations/nb_NO.ts translations/nl_NL.ts translations/pl_PL.ts translations/pt_BR.ts translations/ro_RO.ts translations/ru_RU.ts translations/sk_SK.ts translations/sv_SE.ts translations/th_TH.ts translations/tr_TR.ts translations/zh_CN.ts
Updating 'translations/ar_IQ.qm'...
    Generated 167 translation(s) (165 finished and 2 unfinished)

    Ignored 13 untranslated source text(s)
Updating 'translations/bg_BG.qm'...
    Generated 180 translation(s) (178 finished and 2 unfinished)
Updating 'translations/cz_CZ.qm'...
    Generated 180 translation(s) (20 finished and 160 unfinished)
Updating 'translations/de_DE.qm'...
    Generated 180 translation(s) (180 finished and 0 unfinished)
Updating 'translations/el_GR.qm'...
    Generated 165 translation(s) (163 finished and 2 unfinished)

    Ignored 15 untranslated source text(s)
Updating 'translations/en_US.qm'...
    Generated 180 translation(s) (180 finished and 0 unfinished)
Updating 'translations/es_ES.qm'...
    Generated 169 translation(s) (169 finished and 0 unfinished)
Updating 'translations/fi_FI.qm'...
    Generated 180 translation(s) (180 finished and 0 unfinished)
Updating 'translations/fr_FR.qm'...
    Generated 164 translation(s) (163 finished and 1 unfinished)

    Ignored 16 untranslated source text(s)
Updating 'translations/hu_HU.qm'...
    Generated 180 translation(s) (180 finished and 0 unfinished)
Updating 'translations/it_IT.qm'...
    Generated 167 translation(s) (166 finished and 1 unfinished)

    Ignored 13 untranslated source text(s)
Updating 'translations/ka_GE.qm'...
    Generated 180 translation(s) (180 finished and 0 unfinished)
Updating 'translations/kr_KR.qm'...
    Generated 180 translation(s) (13 finished and 167 unfinished)
Updating 'translations/lt_LT.qm'...
    Generated 182 translation(s) (182 finished and 0 unfinished)
Updating 'translations/lv_LV.qm'...
    Generated 167 translation(s) (166 finished and 1 unfinished)

    Ignored 13 untranslated source text(s)
Updating 'translations/nb_NO.qm'...
    Generated 180 translation(s) (180 finished and 0 unfinished)
Updating 'translations/nl_NL.qm'...
    Generated 165 translation(s) (163 finished and 2 unfinished)

    Ignored 15 untranslated source text(s)
Updating 'translations/pl_PL.qm'...
    Generated 167 translation(s) (166 finished and 1 unfinished)

    Ignored 13 untranslated source text(s)
Updating 'translations/pt_BR.qm'...
    Generated 165 translation(s) (163 finished and 2 unfinished)

    Ignored 15 untranslated source text(s)
Updating 'translations/ro_RO.qm'...
    Generated 180 translation(s) (14 finished and 166 unfinished)
Updating 'translations/ru_RU.qm'...
    Generated 180 translation(s) (180 finished and 0 unfinished)
Updating 'translations/sk_SK.qm'...
    Generated 180 translation(s) (180 finished and 0 unfinished)
Updating 'translations/sv_SE.qm'...
    Generated 180 translation(s) (180 finished and 0 unfinished)
Updating 'translations/th_TH.qm'...
    Generated 169 translation(s) (169 finished and 0 unfinished)
Updating 'translations/tr_TR.qm'...
    Generated 167 translation(s) (166 finished and 1 unfinished)

    Ignored 13 untranslated source text(s)
Updating 'translations/zh_CN.qm'...
    Generated 180 translation(s) (180 finished and 0 unfinished)
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DUNIX_TRANSLATIONS_DIR=\"/usr/share/imageshack-uploader/translations\" -DVERSION=\"2.3.0\" -DDEVELOPER_KEY=\"369BDIRW3fcf19e1586ae237d0c99856e3293fbf\" -DQT_NO_DEBUG -DQT_XML_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtXml -I/usr/include/qt4 -Iqtsingleapplication -Iqtsingleapplication -I. -I. -o qtsingleapplication.o qtsingleapplication/qtsingleapplication.cpp
make: g++: Command not found
make: *** [qtsingleapplication.o] Error 127
tareq@tareq-laptop:~/Desktop/imageshack-uploader$ sudo getlibs /usr/bin/imageshack-uploader
sudo: getlibs: command not found
```

---

### Post by tareq.mhd on 2010-10-16
still no reply !

---

### Post by dpwilson on 2010-11-25
> **mc4man said:**
> 

grab just the the [lucid libavutil49]("http://packages.ubuntu.com/lucid/libavutil49") and install, may work out, may not
(You can install it without issue - nothing in mav. should be using it



Worked for me on 10.10   :D

---

### Post by dancordi on 2010-12-08
I fixed installing libavutil49 for lucid downloaded here:
[http://packages.ubuntu.com/lucid/i386/libavutil49/download](http://packages.ubuntu.com/lucid/i386/libavutil49/download)

---

### Post by ron999 on 2011-07-07
Hi

I'm trying to compile imageshack-uploader using illbashu's commands from post #19.

```
sudo apt-get install mercurial
hg clone https://imageshack-uploader.googlecode.com/hg/ imageshack-uploader
cd imageshack-uploader
sudo aptitude install libqt4-gui libqt4-core libqt4-xml qt4-dev-tools
IMAGESHACK_DEVELOPER_KEY="xxxxxxxxxxxxxxxx" qmake
sudo make install
```


But there are error messages.:confused:


Is it because my FFmpeg is a new one from git?
And is there a solution?
> [SIZE="1"]
ron@ubuntu:~$ ffmpeg
ffmpeg version N-31267-g4e59c8e, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jul  6 2011 20:16:25 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab --disable-encoder=vorbis --enable-libvo-amrwbenc --enable-libvo-aacenc
  libavutil    51. 11. 0 / 51. 11. 0
  libavcodec   53.  7. 0 / 53.  7. 0
  libavformat  53.  5. 0 / 53.  5. 0
  libavdevice  53.  2. 0 / 53.  2. 0
  libavfilter   2. 24. 3 /  2. 24. 3
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0[/SIZE]

Error messages attached below...


[COLOR="Red"]EDIT[/COLOR]

I'ts fixed now.
I compiled and installed **FFmpeg-0.7.1**.

Then as suggested by illbashu:-
```
sudo aptitude install libavcodec-dev libavformat-dev libswscale-dev libavutil-dev
```

Then imageshack-uploader compiled and installed OK using the instructions.

Aftewards I re-installed my FFmpeg-git.

---

