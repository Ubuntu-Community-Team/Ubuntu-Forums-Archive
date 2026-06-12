---
title: "Video name ends with .mp4.dap How to retain the format ?"
date: 2011-06-03
forum: General Help
---

### Post by astrobob.tk on 2011-06-03
Hello,

I have a couple of videos that end with the extension: .mp4.dap

the videos, apparently, were .mp4 but instead are not .mp4.dap where .dap are DarkAdapted Presets File. DarkAdapted is a software which applies a red or green filter to the screen to help your eyes get dark adapted.

Anyways, i tried removing .dap but the videos can't play. Could you please help ?

One more related question is: I thought that Linux in general & Ubuntu in particular allows changing the video format by simply changing the extension name, but this doesn't seem to work now; i recall it once worked sometime ago. Am I mistaken or what ?

thanks

---

### Post by flipper T on 2011-06-03
changing the extension of any file does nothing to change the file itself in ubuntu

---

### Post by linuxinstalledfromhdd on 2011-06-03
When I am working with video files like that I use HandBrake, it is an open-source program designed to convert MPEG video  (including DVD-Video) into an MPEG-4 video file in MPEG-4 Part 14 (.mp4)  or Matroska (.mkv) containers.

 The program is used to convert DVDs into other forms so they can be  viewed on iPods, iPhones and with the Apple QuickTime Player and most  media players.
 Originally developed for BeOS, HandBrake is now available for Linux, Microsoft Windows and Mac OS X.
 
```
sudo add-apt-repository ppa:stebbins/handbrake-releases 
sudo apt-get update 
sudo apt-get install handbrake-gtk
```And the one I probably use the most specifically for post conversion is WinFF

```
sudo apt-get install winff
```And you can't just rename a video file in Ubuntu and have it automatically convert to a different format. :)

---

### Post by astrobob.tk on 2011-06-03
thanks for the reply guys, but still you didn't mention the .dap thing :S

---

### Post by linuxinstalledfromhdd on 2011-06-03
What program was used to create a file with that kind of extension?

---

### Post by astrobob.tk on 2011-06-04
> **linuxinstalledfromhdd said:**
> What program was used to create a file with that kind of extension?

Well the vids (which are opencourseware) were copied from a friend; i assume that they were downloaded with flashgot. The thing is that just 4/35 vids end with .dap & they do not run under totem. The others, which do not end with .dap, do work normally.

I believe this happened on my system b/c I have the "DarkAdapted" software & if i recall correctly (long before copying the vids) I tried DarkAdapted under wine.

---

### Post by jamesisin on 2011-06-04
Maybe those weren't finished downloading?

[http://filext.com/file-extension/DAP](http://filext.com/file-extension/DAP)

---

### Post by astrobob.tk on 2011-06-04
> **jamesisin said:**
> Maybe those weren't finished downloading?

[http://filext.com/file-extension/DAP](http://filext.com/file-extension/DAP)


That is very likely. I will take this as the answer. Maybe I will recheck if those files work with the guy I got them from.

Am gona mark the thread as solved for now.

Thank you all.

---

