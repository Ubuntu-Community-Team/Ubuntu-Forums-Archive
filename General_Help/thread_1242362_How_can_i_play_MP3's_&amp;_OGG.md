---
title: "How can i play MP3's &amp; OGG"
date: 2009-08-17
forum: General Help
---

### Post by sububtu on 2009-08-17
hi ,,,
how can i play MP3's& OGGvorbis Files,, i had downloaded some instllation packages frm ubuntu archive.. but i got some security warnings,, but allows installation, is there any alternate and easiest way for installation..?:guitar:

---

### Post by mthalis on 2009-08-17
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by jambel on 2009-08-17
you can also try [vlc]("http://www.videolan.org/")

---

### Post by abhilashm86 on 2009-08-17
> **sububtu said:**
> hi ,,,
how can i play MP3's& OGGvorbis Files,, i had downloaded some instllation packages frm ubuntu archive.. but i got some security warnings,, but allows installation, is there any alternate and easiest way for installation..?:guitar:

what type of security warnings you got?? always while installing or performing important tasks, linux wants to be as a root,
you have a lot of media players totem, vlc, banshee, mplayer............

---

### Post by sububtu on 2009-08-17
Error message is** "Install unauthentacated Software?" **i just ignored it and continued...
i think i had done a wrong installation... i had downloaded the entire files frm the archive regardless of the architechture, mine is i386 based system, now im tried to install VLC player, the file i used to install is - *wxvlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3_all.deb*Am i correct? it also require some other files and alutomatically connects to the repository 
 
what i need is the simple and easiest way to play MP3 & OGG files...

---

### Post by credobyte on 2009-08-17
From Ubuntu repositories:
```
sudo apt-get install ubuntu-restricted-extras

```

From [Mediabuntu]("https://help.ubuntu.com/community/Medibuntu") repositories:
```
sudo apt-get install w32codecs non-free-codecs
```

---

### Post by sububtu on 2009-08-17
giong through the VLC link i saw these links...



[LIST]
[*]       [libvlc-dev_1.0.1-1~ppa4_amd64.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/libvlc-dev_1.0.1-1%7Eppa4_amd64.deb")          (74.6 KiB)
[*]       [libvlc-dev_1.0.1-1~ppa4_i386.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/libvlc-dev_1.0.1-1%7Eppa4_i386.deb")          (67.6 KiB)
[*]       [libvlc-dev_1.0.1-1~ppa4_lpia.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/libvlc-dev_1.0.1-1%7Eppa4_lpia.deb")          (67.6 KiB)
[*]       [libvlc2_1.0.1-1~ppa4_amd64.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/libvlc2_1.0.1-1%7Eppa4_amd64.deb")          (51.3 KiB)
[*]       [libvlc2_1.0.1-1~ppa4_i386.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/libvlc2_1.0.1-1%7Eppa4_i386.deb")          (49.7 KiB)
[*]       [libvlc2_1.0.1-1~ppa4_lpia.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/libvlc2_1.0.1-1%7Eppa4_lpia.deb")          (49.7 KiB)
[*]       [libvlccore-dev_1.0.1-1~ppa4_amd64.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/libvlccore-dev_1.0.1-1%7Eppa4_amd64.deb")          (563.1 KiB)
[*]       [libvlccore-dev_1.0.1-1~ppa4_i386.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/libvlccore-dev_1.0.1-1%7Eppa4_i386.deb")          (537.3 KiB)
[*]       [libvlccore-dev_1.0.1-1~ppa4_lpia.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/libvlccore-dev_1.0.1-1%7Eppa4_lpia.deb")          (537.6 KiB)
[*]       [libvlccore2_1.0.1-1~ppa4_amd64.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/libvlccore2_1.0.1-1%7Eppa4_amd64.deb")          (388.2 KiB)
[*]       [libvlccore2_1.0.1-1~ppa4_i386.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/libvlccore2_1.0.1-1%7Eppa4_i386.deb")          (399.7 KiB)
[*]       [libvlccore2_1.0.1-1~ppa4_lpia.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/libvlccore2_1.0.1-1%7Eppa4_lpia.deb")          (399.3 KiB)
[*]       [mozilla-plugin-vlc_1.0.1-1~ppa4_amd64.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/mozilla-plugin-vlc_1.0.1-1%7Eppa4_amd64.deb")          (33.8 KiB)
[*]       [mozilla-plugin-vlc_1.0.1-1~ppa4_i386.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/mozilla-plugin-vlc_1.0.1-1%7Eppa4_i386.deb")          (33.6 KiB)
[*]       [mozilla-plugin-vlc_1.0.1-1~ppa4_lpia.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/mozilla-plugin-vlc_1.0.1-1%7Eppa4_lpia.deb")          (33.7 KiB)
[*]       [vlc-data_1.0.1-1~ppa4_all.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-data_1.0.1-1%7Eppa4_all.deb")          (5.8 MiB)
[*]       [vlc-dbg_1.0.1-1~ppa4_amd64.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-dbg_1.0.1-1%7Eppa4_amd64.deb")          (12.3 MiB)
[*]       [vlc-dbg_1.0.1-1~ppa4_i386.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-dbg_1.0.1-1%7Eppa4_i386.deb")          (11.8 MiB)
[*]       [vlc-dbg_1.0.1-1~ppa4_lpia.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-dbg_1.0.1-1%7Eppa4_lpia.deb")          (11.8 MiB)
[*]       [vlc-nox_1.0.1-1~ppa4_amd64.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-nox_1.0.1-1%7Eppa4_amd64.deb")          (2.6 MiB)
[*]       [vlc-nox_1.0.1-1~ppa4_i386.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-nox_1.0.1-1%7Eppa4_i386.deb")          (2.6 MiB)
[*]       [vlc-nox_1.0.1-1~ppa4_lpia.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-nox_1.0.1-1%7Eppa4_lpia.deb")          (2.6 MiB)
[*]       [vlc-plugin-ggi_1.0.1-1~ppa4_amd64.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-plugin-ggi_1.0.1-1%7Eppa4_amd64.deb")          (6.3 KiB)
[*]       [vlc-plugin-ggi_1.0.1-1~ppa4_i386.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-plugin-ggi_1.0.1-1%7Eppa4_i386.deb")          (6.1 KiB)
[*]       [vlc-plugin-ggi_1.0.1-1~ppa4_lpia.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-plugin-ggi_1.0.1-1%7Eppa4_lpia.deb")          (6.0 KiB)
[*]       [vlc-plugin-jack_1.0.1-1~ppa4_amd64.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-plugin-jack_1.0.1-1%7Eppa4_amd64.deb")          (11.1 KiB)
[*]       [vlc-plugin-jack_1.0.1-1~ppa4_i386.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-plugin-jack_1.0.1-1%7Eppa4_i386.deb")          (10.7 KiB)
[*]       [vlc-plugin-jack_1.0.1-1~ppa4_lpia.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-plugin-jack_1.0.1-1%7Eppa4_lpia.deb")          (10.7 KiB)
[*]       [vlc-plugin-pulse_1.0.1-1~ppa4_amd64.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-plugin-pulse_1.0.1-1%7Eppa4_amd64.deb")          (7.0 KiB)
[*]       [vlc-plugin-pulse_1.0.1-1~ppa4_i386.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-plugin-pulse_1.0.1-1%7Eppa4_i386.deb")          (6.9 KiB)
[*]       [vlc-plugin-pulse_1.0.1-1~ppa4_lpia.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-plugin-pulse_1.0.1-1%7Eppa4_lpia.deb")          (6.9 KiB)
[*]       [vlc-plugin-sdl_1.0.1-1~ppa4_amd64.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-plugin-sdl_1.0.1-1%7Eppa4_amd64.deb")          (12.1 KiB)
[*]       [vlc-plugin-sdl_1.0.1-1~ppa4_i386.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-plugin-sdl_1.0.1-1%7Eppa4_i386.deb")          (11.5 KiB)
[*]       [vlc-plugin-sdl_1.0.1-1~ppa4_lpia.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-plugin-sdl_1.0.1-1%7Eppa4_lpia.deb")          (11.5 KiB)
[*]       [vlc-plugin-svgalib_1.0.1-1~ppa4_amd64.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-plugin-svgalib_1.0.1-1%7Eppa4_amd64.deb")          (4.9 KiB)
[*]       [vlc-plugin-svgalib_1.0.1-1~ppa4_i386.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc-plugin-svgalib_1.0.1-1%7Eppa4_i386.deb")          (4.6 KiB)
[*]       [vlc_1.0.1-1~ppa4.diff.gz]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc_1.0.1-1%7Eppa4.diff.gz")          (51.3 KiB)
[*]       [vlc_1.0.1-1~ppa4.dsc]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc_1.0.1-1%7Eppa4.dsc")          (3.1 KiB)
[*]       [vlc_1.0.1-1~ppa4_amd64.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc_1.0.1-1%7Eppa4_amd64.deb")          (1.5 MiB)
[*]       [vlc_1.0.1-1~ppa4_i386.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc_1.0.1-1%7Eppa4_i386.deb")          (1.5 MiB)
[*]       [vlc_1.0.1-1~ppa4_lpia.deb]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc_1.0.1-1%7Eppa4_lpia.deb")          (1.5 MiB)
[*]       [vlc_1.0.1.orig.tar.gz]("https://launchpad.net/%7Ec-korn/+archive/vlc/+files/vlc_1.0.1.orig.tar.gz")
[/LIST]

Do i need to install all these depending on the Architecture ??

---

### Post by slakkie on 2009-08-17
mplayer ftw!!

```

Playing /path/to/Opgezwolle/Eigen_wereld/20.De_Jug.ogg.
Playing /path/to/Harrie_Jekkers/harrie Jekkers - Oliebol van Krentenkoe/17 Quuc le Cocq de Haan.mp3.

```

---

### Post by t0p on 2009-08-17
OP, are you running ubuntu?  If so, you have 2 apps that can play music: rhythmbox and totem (movie player).  They should play ogg files fine.

If you want to play mp3s, you need the correct codec.  To get a wide variety of proprietary codecs including mp3,  open terminal (Applications > Accessories > Terminal) and type in 

```
sudo apt-get install ubuntu-restricted-extras
```
er
You'll be prompted for your password.  When you type it in, you won't see the letters or asterisks - but type it in anyway.  A bunch of files will download.  When installation finishes, you'll be able to play mp3s, plus lots of other formats for sound, video etc.

---

### Post by 3rdalbum on 2009-08-17
Go into System > Administration > Software Sources and make sure that the first four checkboxes are ticked. Click Close. If asked to reload the package list, click "Reload".

Now play an MP3 using Totem Movie Player. Ubuntu will ask you if you want to download MP3 codecs. The rest is simple.

Ogg Vorbis and Ogg Theora support is available out-of-the-box. Note that Ogg is a container format, not a codec, so if your file won't play then you need to find out what codec is used within the Ogg file and install it.

---

### Post by andrew.46 on 2009-08-17
Hi sububtu,

I note your profile says that you are using Gutsy Gibbon, is this the case? I only ask as of course April 18th, 2009 was the 'End of Life' for Gutsy and I am not sure what state the repositories are in.

All the best,

Andrew

---

### Post by slakkie on 2009-08-17
EOL repo's can be found at:

old-releases.ubuntu.com, so you can still maintain it and upgrade to a newer version.

---

### Post by sububtu on 2009-08-26
Currently im using Ubuntu 9.04,
evrything fine , except the Mp3, im a beginner,i dont hav a highspeed inet connection, so what i had done was ,, dwnloaded lots of packages and installed,("exactly i dnt know what i had done"),but the aim was to play MP3 files,im downloaded ".deb" packages frm the buntu archive (i had tried the files with names mp3:)), nothing happend,some installation gives an error msg - some what like "dependency not satisfied "now hardly, i installed **gmusic browser**, i think it can play mp3 files, but under settings -> audio tab, i cant see any devices, the "gstreamer item is grayed" , what i need is the codec / a player to play mp3ssss:confused:

---

### Post by jocko on 2009-08-26
> **sububtu said:**
> Currently im using Ubuntu 9.04,
evrything fine , except the Mp3, im a beginner,i dont hav a highspeed inet connection, so what i had done was ,, dwnloaded lots of packages and installed,("exactly i dnt know what i had done"),but the aim was to play MP3 files,im downloaded ".deb" packages frm the buntu archive (i had tried the files with names mp3:)), nothing happend,some installation gives an error msg - some what like "dependency not satisfied "now hardly, i installed **gmusic browser**, i think it can play mp3 files, but under settings -> audio tab, i cant see any devices, the "gstreamer item is grayed" , what i need is the codec / a player to play mp3ssss:confused:
Are you saying that you have manually downloaded random packages and installed them manually? That's the windows way and not how to do things in ubuntu.
Just open up synaptic (System-->Administration-->Synaptic package manager) and use the search function to find packages and mark them for installation (right-click). Hit apply and let synaptic download and install the packages.
Install the package **ubuntu-restricted-extras**, that will give you the codecs you need for most media file formats, plus a few more things that you probably want.
If you want a simple music player, install **audacious**.
For a multi-purpose audio and video player, install **vlc** or **mplayer**, or just use the already installed player totem (program-->audio & video-->movie player).
Again: **don't download the .deb files from a web browser**. Let the package manager do it for you. Much easier and less risc of breaking your applications that way.

---

### Post by 3rdalbum on 2009-08-26
> **sububtu said:**
> Currently im using Ubuntu 9.04,
evrything fine , except the Mp3, im a beginner,i dont hav a highspeed inet connection, so what i had done was ,, dwnloaded lots of packages and installed,("exactly i dnt know what i had done"),but the aim was to play MP3 files,im downloaded ".deb" packages frm the buntu archive (i had tried the files with names mp3:)), nothing happend,some installation gives an error msg - some what like "dependency not satisfied "now hardly, i installed **gmusic browser**, i think it can play mp3 files, but under settings -> audio tab, i cant see any devices, the "gstreamer item is grayed" , what i need is the codec / a player to play mp3ssss:confused:

"gstreamer0.10-fluendo-mp3". Install it in Synaptic if you have an internet connection available to you. If not, download it manually from the site you've been getting packages from.

The reason why you're getting "dependency not satisfied" errors is because packages depend on other packages - for instance, a desktop publishing program might depend on a font rendering library. The library is not included in the package, because lots of other programs make use of the library and it's inefficient to have twenty copies of the same library. So you need to install the dependencies as well, if your system complains.

Better yet, get a reasonable internet connection at home and the package manager will resolve dependencies for you.

---

### Post by sububtu on 2009-08-26
[SIZE=4][B]BINGO!!!
[/B][SIZE=2]I got it, Now it works... 
:guitar::guitar::guitar::guitar:i dont hav a high speed  internet for dwnloading via package manager , ,,[/SIZE][/SIZE]

---

