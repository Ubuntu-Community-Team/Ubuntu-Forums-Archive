---
title: "OpenTTD tar.bz souce code install help needed please!"
date: 2012-02-06
forum: General Help
---

### Post by scratman on 2012-02-06
Hi guys, I play OpenTTD, and a new version has just been released on the website [http://www.openttd.org/](http://www.openttd.org/)

I would like to play this version, but I don't know how to install it from source code. OpenTTD do provide .deb packages to install, but no longer for Ubuntu 10.10, the version I use.

I have tried to install from source, ([http://binaries.openttd.org/releases/1.1.5/openttd-1.1.5-linux-generic-i686.tar.gz](http://binaries.openttd.org/releases/1.1.5/openttd-1.1.5-linux-generic-i686.tar.gz)) but I'm not too sure what I'm doing. Would anybody be able to provide me with instructions for installing OpenTTD from source? The source and packages can be found at [http://www.openttd.org/en/download-stable](http://www.openttd.org/en/download-stable)

Thanks in advance.

Note, here's what I've tried so far....

Downloaded to my home/Downloads folder with browser, then in Terminal....

```

user@Pc:~$ cd Downloads
user@Pc:~/Downloads$ tar -zxvf openttd-1.1.5-linux-generic-i686.tar.gz
openttd-1.1.5-linux-generic-i686/
openttd-1.1.5-linux-generic-i686/gm/
openttd-1.1.5-linux-generic-i686/gm/orig_win.obm
openttd-1.1.5-linux-generic-i686/gm/no_music.obm
openttd-1.1.5-linux-generic-i686/data/
openttd-1.1.5-linux-generic-i686/data/no_sound.obs
openttd-1.1.5-linux-generic-i686/data/orig_win.obg
openttd-1.1.5-linux-generic-i686/data/opntitle.dat
openttd-1.1.5-linux-generic-i686/data/orig_dos_de.obg
openttd-1.1.5-linux-generic-i686/data/openttd.grf
openttd-1.1.5-linux-generic-i686/data/openttd.32.bmp
openttd-1.1.5-linux-generic-i686/data/orig_win.obs
openttd-1.1.5-linux-generic-i686/data/orig_dos.obs
openttd-1.1.5-linux-generic-i686/data/orig_dos.obg
openttd-1.1.5-linux-generic-i686/scripts/
openttd-1.1.5-linux-generic-i686/scripts/on_server.scr.example
openttd-1.1.5-linux-generic-i686/scripts/on_client.scr.example
openttd-1.1.5-linux-generic-i686/scripts/autoexec.scr.example
openttd-1.1.5-linux-generic-i686/scripts/pre_dedicated.scr.example
openttd-1.1.5-linux-generic-i686/scripts/on_dedicated.scr.example
openttd-1.1.5-linux-generic-i686/scripts/game_start.scr.example
openttd-1.1.5-linux-generic-i686/scripts/on_server_connect.scr.example
openttd-1.1.5-linux-generic-i686/scripts/readme.txt
openttd-1.1.5-linux-generic-i686/scripts/pre_server.scr.example
openttd-1.1.5-linux-generic-i686/openttd
openttd-1.1.5-linux-generic-i686/man/
openttd-1.1.5-linux-generic-i686/man/openttd.6.gz
openttd-1.1.5-linux-generic-i686/COPYING
openttd-1.1.5-linux-generic-i686/docs/
openttd-1.1.5-linux-generic-i686/docs/32bpp.txt
openttd-1.1.5-linux-generic-i686/docs/multiplayer.txt
openttd-1.1.5-linux-generic-i686/lang/
openttd-1.1.5-linux-generic-i686/lang/turkish.lng
openttd-1.1.5-linux-generic-i686/lang/hebrew.lng
openttd-1.1.5-linux-generic-i686/lang/norwegian_nynorsk.lng
openttd-1.1.5-linux-generic-i686/lang/vietnamese.lng
openttd-1.1.5-linux-generic-i686/lang/slovak.lng
openttd-1.1.5-linux-generic-i686/lang/luxembourgish.lng
openttd-1.1.5-linux-generic-i686/lang/hungarian.lng
openttd-1.1.5-linux-generic-i686/lang/welsh.lng
openttd-1.1.5-linux-generic-i686/lang/japanese.lng
openttd-1.1.5-linux-generic-i686/lang/czech.lng
openttd-1.1.5-linux-generic-i686/lang/esperanto.lng
openttd-1.1.5-linux-generic-i686/lang/catalan.lng
openttd-1.1.5-linux-generic-i686/lang/galician.lng
openttd-1.1.5-linux-generic-i686/lang/icelandic.lng
openttd-1.1.5-linux-generic-i686/lang/indonesian.lng
openttd-1.1.5-linux-generic-i686/lang/estonian.lng
openttd-1.1.5-linux-generic-i686/lang/simplified_chinese.lng
openttd-1.1.5-linux-generic-i686/lang/romanian.lng
openttd-1.1.5-linux-generic-i686/lang/traditional_chinese.lng
openttd-1.1.5-linux-generic-i686/lang/latvian.lng
openttd-1.1.5-linux-generic-i686/lang/polish.lng
openttd-1.1.5-linux-generic-i686/lang/danish.lng
openttd-1.1.5-linux-generic-i686/lang/malay.lng
openttd-1.1.5-linux-generic-i686/lang/slovenian.lng
openttd-1.1.5-linux-generic-i686/lang/swedish.lng
openttd-1.1.5-linux-generic-i686/lang/afrikaans.lng
openttd-1.1.5-linux-generic-i686/lang/arabic_egypt.lng
openttd-1.1.5-linux-generic-i686/lang/finnish.lng
openttd-1.1.5-linux-generic-i686/lang/english.lng
openttd-1.1.5-linux-generic-i686/lang/ukrainian.lng
openttd-1.1.5-linux-generic-i686/lang/english_US.lng
openttd-1.1.5-linux-generic-i686/lang/portuguese.lng
openttd-1.1.5-linux-generic-i686/lang/croatian.lng
openttd-1.1.5-linux-generic-i686/lang/russian.lng
openttd-1.1.5-linux-generic-i686/lang/belarusian.lng
openttd-1.1.5-linux-generic-i686/lang/greek.lng
openttd-1.1.5-linux-generic-i686/lang/serbian.lng
openttd-1.1.5-linux-generic-i686/lang/korean.lng
openttd-1.1.5-linux-generic-i686/lang/dutch.lng
openttd-1.1.5-linux-generic-i686/lang/norwegian_bokmal.lng
openttd-1.1.5-linux-generic-i686/lang/german.lng
openttd-1.1.5-linux-generic-i686/lang/french.lng
openttd-1.1.5-linux-generic-i686/lang/irish.lng
openttd-1.1.5-linux-generic-i686/lang/brazilian_portuguese.lng
openttd-1.1.5-linux-generic-i686/lang/lithuanian.lng
openttd-1.1.5-linux-generic-i686/lang/spanish.lng
openttd-1.1.5-linux-generic-i686/lang/italian.lng
openttd-1.1.5-linux-generic-i686/lang/bulgarian.lng
openttd-1.1.5-linux-generic-i686/changelog.txt
openttd-1.1.5-linux-generic-i686/known-bugs.txt
openttd-1.1.5-linux-generic-i686/media/
openttd-1.1.5-linux-generic-i686/media/openttd.desktop
openttd-1.1.5-linux-generic-i686/media/openttd.128.png
openttd-1.1.5-linux-generic-i686/media/openttd.48.png
openttd-1.1.5-linux-generic-i686/media/openttd.32.png
openttd-1.1.5-linux-generic-i686/media/openttd.32.xpm
openttd-1.1.5-linux-generic-i686/media/openttd.16.png
openttd-1.1.5-linux-generic-i686/media/openttd.64.png
openttd-1.1.5-linux-generic-i686/media/openttd.256.png
openttd-1.1.5-linux-generic-i686/ai/
openttd-1.1.5-linux-generic-i686/ai/compat_0.7.nut
openttd-1.1.5-linux-generic-i686/ai/compat_1.1.nut
openttd-1.1.5-linux-generic-i686/ai/compat_1.0.nut
openttd-1.1.5-linux-generic-i686/readme.txt
user@Pc:~/Downloads$ cd openttd-1.1.5-linux-generic-i686
user@Pc:~/Downloads/openttd-1.1.5-linux-generic-i686$ ./configure
bash: ./configure: No such file or directory
user@Pc:~/Downloads/openttd-1.1.5-linux-generic-i686$ 

```


What am I doing that's so wrong here guys?  Any suggestions?

---

### Post by oldos2er on 2012-02-06
What does readme.txt say?

---

### Post by scratman on 2012-02-07
Hi guys, thanks for the assistance.

As far as compiling goes, the relevant part of the readme simply states :-

> Linux/Unix:
  OpenTTD can be built with GNU "make". On non-GNU systems it's called "gmake".
  However, for the first build one has to do a "./configure" first.

The whole readme can be found here [http://svn.openttd.org/trunk/readme.txt]("http://svn.openttd.org/trunk/readme.txt")

As for Private Messages, Sharpietool61, I'm not sure why I can't receive them, or even how to check whether they're disabled on my account!

---

### Post by Toz on 2012-02-07
The file you downloaded is a pre-compiled binary. You don't need to make or build it. To run it, simply:
```

cd openttd-1.1.5-linux-generic-i686
./openttd

```
...however, make sure you have also installed the graphics, music & sound files as per section 4.1 of the readme file. You will need to download those files and uncompress them to the data directory.

You might also want to copy over any saved data files.

---

### Post by scratman on 2012-02-07
Thank you so much!!!  It's working fine now!  What was I doing wrong?

---

### Post by Toz on 2012-02-07
> **scratman said:**
> Thank you so much!!!  It's working fine now!  What was I doing wrong?
You were trying to compile it as if it were source code, but it's already compiled. You just needed to execute the pre-compiled file (plus add in the extra data files).

---

