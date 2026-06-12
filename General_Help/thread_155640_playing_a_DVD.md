---
title: "playing a DVD?"
date: 2006-04-05
forum: General Help
---

### Post by syxbit on 2006-04-05
i tried searching, so please don't flame me, (i'm also new)
how can i play a DVD
i've used VLC on windows, and thought it had an mpeg2 decoder on it.
i don't see any options for vlc in the package manager thing.
i went to the vlc homepage, and there's no ubuntu download
do i get the debian download?

on another note,
i used to have a creative soundblaster Audigy, and ubuntu wouldn't recognise it.
i recently bought a creative X-fi.
ubuntu still doesn't.
i don't care that much (it's just a bit of a pain)
i have onboard nforce 2 soundcard, which might work.
any ideas?
also, is there some guide to getting mp3's to work.
i'd love to learn how to use linux (i know almost nothing) and would like to learn a little on the terminal, but everywhere i go, it seems there's a very steep learning curve.
is there some beginners guide to do your basic stuff like dvd/mp3 stuff.

on another note, i tried to install Opera web browser (i know, firefox is probably better, but it would be good practice to try to install something)
i downloaded the ubuntu version, 
it's a package in TAR.GZ
what do i do with this, i tried unzipping, but couldn't get too far.](*,) 
help would be appreciated 
:-D

---

### Post by the_tiger on 2006-04-05
If you are new to Ubuntu I cannot recommended the Official Wiki enough [http://wiki.ubuntu.com/](http://wiki.ubuntu.com/) . Within the Restricted Formats section ([https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)) of this wiki is an easy to follow section on DVD describing installation of the required librarys, decryption codecs and how to enable DMA so that playback will not stutter. I hope this helps.

Totem is a good program for watching DVDs. It has menu naviagtion and will allow for ac3 passthrough.

Update: This wiki will also have information on playing mp3s.

---

### Post by syxbit on 2006-04-05
so, all i do for mp3 playback is enable Adding Repositories, and then in the terminal type
sudo apt-get install  gstreamer0.8-mad

sounds easy enough!!, so this will make mp3's play inside Rhythmbox and Totem!

then for dvd playback, and other formats (that wiki doesn't say what, just that this will make "other" non-free formats work i type

sudo apt-get install  gstreamer0.8-plugins  gstreamer0.8-plugins-multiverse  gstreamer0.8-ffmpeg

but what does this do? is this also needed?
wget -c [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)
  sudo dpkg -i w32codecs_20050412-0.0_i386.deb

also, it says to type th is
sudo apt-get install libdvdread3
  sudo /usr/share/doc/libdvdread3/examples/install-css.sh

as you can see, i'm a little confused.
and this will all change with ubuntu 6.06 :(

is this right?
thanks, as i don't have ubuntu installed right now, and wouldn't do it again unless i can have these things work
thanks for the input guys!

---

### Post by n_hendrick on 2006-04-05
a note on your creative soundblaster audigy or xi-fi. You may need to enable the tone mixer setting in the "alsamixer" program. If that doesn't work try enabling the digital analog setting. I had a similar problem with ubuntu not recognizing my  creative soundcard. I had to unmute the tone setting in alsamixer. Previously in hoary I had to unmute the digital analog setting in alsamixer. I have a audigy.

---

### Post by the_tiger on 2006-04-06
wget -c [ftp://ftp.nerim.net/debian-marillat/...2-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/...2-0.0_i386.deb)

This command will get the w32 codec package from the internet. It is a .deb file which is a Debian software package file. Debian is the flavour of linux upon which  Ubuntu is based.

sudo dpkg -i w32codecs_20050412-0.0_i386.deb

This is the command to install the package. sudo is the super user command which makes sure only those with permission may install the file 

The w32 codecs as it says in the wiki are required for Windows codecs (Windows Media 9, RealMedia) - this support has been bundled into the w32codecs package. Basically because they are commercial license codecs they cannot be bundled with Ubuntu.

In order to read most commercial DVDs it is necessary to unscramble them. As it says in the wiki:

Most commercial DVDs are encrypted with CSS (the Content Scrambling System). The movie players provided in Ubuntu are capable of reading DVDs that are not encrypted. If it is legal for you to circumvent CSS, then you can enable reading encrypted DVDs in vlc, mplayer, xine and totem-xine by installing libdvdcss2.

This command:

sudo apt-get install libdvdread3

will get the libdvdread3 file from the ubuntu repositories. This a range of approved software for the Ubuntu release you are using.

The next command:

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

runs a script, equivalent of a batch file if you are used to windows. It will correctly setup the library for css decryption.

I hope this helps.

I am sure it will be possible to achieve within Ubuntu all that you specified that you wished to. The installation is quite small and dual booting is now so much easier I would throughly recommend installing and having a play.

---

### Post by damu on 2006-04-06
To install VLC, just go to the main menu of Ubuntu : applications/add applications

You will find VLC for gnome in the section "Sound&Video" , "more programs".

Now to sort out, mulitmedia codecs, DVD issues and so on, I would really suggest you to install and use [Automatix]("http://ubuntuforums.org/showthread.php?t=138405"), or EasyUbuntu

I you want to install Automatix, in a termainal window, type :
> wget [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)

and, once it is downloaded, to install it type

> sudo dpkg -i automatix_5.7-3_i386.deb

Once the installation is done, just go to applications/System tools/Automatix

In Automatix, just tick any of the softwares, functionnalities that you need, and click OK ...net Automatix do the job for u...that's it, u should be sorted!

---

### Post by quincyjones on 2006-04-21
Hi, I'm new to Ubuntu and Linux.
When I try to install "VLC for gnome", it says its been discontinued and that I should install "WXVLC", which I can't find. Can I install "VLC for gtk+", what is "gtk+"?:rolleyes:

---

### Post by Zorro on 2006-04-21
What repositories are you using? apt-cache search vlc show up anything?

Just *apt-get install vlc* should do the trick.. (it did in my case) :/

---

