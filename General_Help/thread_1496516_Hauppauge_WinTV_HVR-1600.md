---
title: "Hauppauge WinTV HVR-1600"
date: 2010-05-29
forum: General Help
---

### Post by accguy9009 on 2010-05-29
I am running 10.04. I would like to know if this OS can be used 
to watch tv using my Hauppauge WinTV HVR-1600 NTSC/ATSC/QAM Combo. Where I want to use this I have standard cable service from TW (not digital cable). I also would like to get an HDTV antenna to see some over the air HDTV. I see that Kaffeine appears to be designed to work with tv tuners but mine doesn't appear to be recognized by this OS. I have, of course, heard of Mythbuntu.

Is Mythbuntu the same OS as 10.04 with just a media center included? Like going from XP to MCE or Windows 7 starter to Home Premium? I see by poking around on google that my card has been known to have driver issues on Linux. I assume it is due to the chip-set my card uses. I would also be interested to know if this card can be supported under Linux without me having to jump through all kinds of hoops as I am a Linux newbie.

Thanks in advance

---

### Post by muaythaimaster74 on 2010-05-29
Check out tv-viewer... it's an easy way to get started without doing a full blown mythtv setup...  I use it with my pvr-150 and it works great.  Your hvr-1600 is supported as well..

[http://tv-viewer.sourceforge.net/mediawiki/index.php/Main_Page](http://tv-viewer.sourceforge.net/mediawiki/index.php/Main_Page)

---

### Post by accguy9009 on 2010-05-29
Thanks I will check it out

---

### Post by accguy9009 on 2010-05-30
Ok, I followed the link above and downloaded a "tar"(whatever this is).

The read me file contains the following instruction,

Installation
------------
Installing TV-Viewer is done by the following 2 commands:

$ ./configure.tcl

% ./install.tcl (You may need root privileges)


For more configuration details run 
$ ./configure.tcl --help

I typed this command into the terminal  ./configure.tcl
I received this error message- configure.tcl: No such file or directory

I have no idea what to do next or what I did wrong.Any help would be welcomed. Thanks in advance

---

### Post by muaythaimaster74 on 2010-05-31
You're probably missing a few steps.. I'll outline how I installed it.

1.  Open a terminal.  (in the accessories portion of your menu.. ie.Applications-> accessories-> terminal).
2.  Change to the directory you downloaded tv-viewer to.  cd ~/Downloads
3.  untar the files.  tar zxvf tv-viewer-0.8.1.1.tar.gz
4.  Change to the newly formed directory.  cd tv-viewer-0.8.1.1
5.  Satisfy dependencies.  sudo apt-get install tcl8.5 tk8.5 ivtv-utils libgtk-img xdg-utils
6.  start the configure program.  ./configure.tcl
7.  install the program.  sudo ./install.tcl
8.  test the program.  tv-viewer

The rest is pretty straightforward with gui's and such...

good luck!

---

### Post by accguy9009 on 2010-06-01
I appreciate your help on this I really do. I do have a few questions about your walk thru on how to install tv viewer.

1. Open a terminal. (in the accessories portion of your menu.. ie.Applications-> accessories-> terminal).
2. Change to the directory you downloaded tv-viewer to. cd ~/Downloads
3. untar the files. tar zxvf tv-viewer-0.8.1.1.tar.gz
4. Change to the newly formed directory. cd tv-viewer-0.8.1.1
5. Satisfy dependencies. sudo apt-get install tcl8.5 tk8.5 ivtv-utils libgtk-img xdg-utils
6. start the configure program. ./configure.tcl
7. install the program. sudo ./install.tcl
8. test the program. tv-viewer

1. Ok, I already know how to do this
2. The folder containing tv-viewer is in my home directory
when you say change to directory... do you mean I should enter this command into the terminal  cd ~/Downloads   ? I should have the tar file in the downloads folder in my home directory right?
3.By untar the files do you mean enter this command into the terminal
tar zxvf tv-viewer-0.8.1.1.tar.gz   ? Is that what you mean?
4.Enter this into the terminal, cd tv-viewer-0.8.1.1.   ?
5.Enter this into the terminal, sudo apt-get install tcl8.5 tk8.5 ivtv-utils libgtk-img xdg-utils   ? 
6. Enter this into the terminal, ./configure.tcl   ?
7. Enter this into the terminal, sudo ./install.tcl  ?
8. Open the program from the application menu?

Thanks for the help. The vocabulary is new to me. I feel like Tom cruise talking to robert duvall in Days of thunder cause I am an idiot, I don't have the vocabulary, lol

---

### Post by inameiname on 2010-06-01
Personally, I use TVTime for TW analog cable, and SMPlayer for digital broadcast. It wasn't that hard to get set up and works just fine for me.

This is how I got tvtime to work for mine. Just check these two links  out:


[http://ubuntuforums.org/showthread.php?t=1477837](http://ubuntuforums.org/showthread.php?t=1477837)

[http://ubuntuforums.org/showthread.php?t=1472297](http://ubuntuforums.org/showthread.php?t=1472297)

---

### Post by accguy9009 on 2010-06-01
Thanks, I want to use tv-viewer for analog cable from tw as well.

---

### Post by muaythaimaster74 on 2010-06-03
accguy9009... you're catching on fine.  all commands are entered into the terminal without quotes of course.

1.  no further explanation needed.
2.  the command "cd ~/Downloads" is entered in the terminal and will take you to the Downloads folder in your home directory.
3.  the command "tar zxvf tv-viewer-0.8.1.1.tar.gz" will untar or "unzip" the file... kind of like extracting or using winzip in windows.
4.  the command "cd tv-viewer-0.8.1.1" will "change directory" to the new directory you untarred.
5.  the command "sudo apt-get install tcl8.5 tk8.5 ivtv-utils libgtk-img xdg-utils" will download and install the dependencies (what is needed by ubuntu to operate tv-viewer).
6.  the command "./configure.tcl" will start the configure program which will setup the tv-viewer program for your specific hardware.
7.  the command "sudo ./install.tcl" will install the program for global usage.
8.  the command "tv-viewer" will then start the tv-viewer program.  If you're using gnome, you can log out and back in and tv-viewer will be in the Applications-> Multimedia directory I believe... though it may be in one of the other directories... I'm using openbox right now so I don't know for sure.  you can always start the program from the terminal by typing tv-viewer if need be.

Good luck!

---

### Post by drewsus on 2010-11-20
> **inameiname said:**
> Personally, I use TVTime for TW analog cable, and SMPlayer for digital broadcast. It wasn't that hard to get set up and works just fine for me.

This is how I got tvtime to work for mine. Just check these two links  out:


[http://ubuntuforums.org/showthread.php?t=1477837](http://ubuntuforums.org/showthread.php?t=1477837)

[http://ubuntuforums.org/showthread.php?t=1472297](http://ubuntuforums.org/showthread.php?t=1472297)

I have the wintv-hvr-1600
I have tried mythtv, tvtime, vlc and tv-viewer with no success. 

The only thing that did anything was 
```
cat /dev/video0 > ~/test.mpg
```
It created an expanding file that I could open with mplayer that had audio and garbled video. 
Every just says "tv-viewer/tvtime/etc worked great for me!"
But I can only assume that they didn't work right out of the box for everyone. There must have been some kind of configuration, but no one seems to really share it. Do you or anyone else have any tips/walkthroughs?

---

