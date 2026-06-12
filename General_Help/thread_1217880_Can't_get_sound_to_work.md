---
title: "Can't get sound to work"
date: 2009-07-20
forum: General Help
---

### Post by gmsbeak22 on 2009-07-20
[SIZE=3]I have been playing with Ubuntu 9.04[/SIZE][-o<[SIZE=3] for a few days now and can hear all the sounds on  the sound wav. files.  But I cannot hear sound on Websites.  I have tried all forums suggestions but no help.  Can't get it to work.  The settings in preferences are HDA INTEL ALC888 Analog.  My PC is a Compaq Presario Intel Celeron D processor 360,  Intel graphics media accelerator 950.  Please someone help,  I am really impresses with Ubuntu.  [/SIZE]:confused::confused::confused:

---

### Post by cooper77z on 2009-07-20
Hey, I messed up my sound too on a previous install because I was manipulating the options and the drivers. I finally just did a reinstall because I couldn't find the system change that I made.

---

### Post by prshah on 2009-07-20
> **gmsbeak22 said:**
> [SIZE=3]and can hear all the sounds on  the sound wav. files.  But I cannot hear sound on Websites.

Do you have the pulse daemon running? Check by: Open a terminal (Applications-Accessories-Terminal) and give the command```
ps -e | grep pulse
```

---

### Post by Quarkrad on 2009-07-20
Try this - it worked for me.  Open terminal and type:

alsamixer


a window will pop showing the volume level of several elements.  Use the up/down, left/right arrows to move left to right and adjust the levels.

---

### Post by gmsbeak22 on 2009-07-21
3234 ?        00:00:00 pulseaudio  is what i get when i do that.

---

### Post by prshah on 2009-07-21
> **gmsbeak22 said:**
> 3234 ?        00:00:00 pulseaudio  is what i get when i do that.

So pulse is running. Have you installed restricted-extras? That is required to play most audio and video codecs. If you are using ubuntu, give the below command in a terminal```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by gmsbeak22 on 2009-07-21
It did a bunch of downloading but the sound still doesn't work?  I can hear sounds in the sound menu, but i just won't play on videos and websites?

---

### Post by gmsbeak22 on 2009-08-30
Okay, here is the update on the sound delema.  The last image cd i burned of 9.04 have been unsuccessful in making the sound work for Ubuntu.  I recently read an article that said, if you use Microsoft Internet explorer to download a image file that it will have errors (figures.)  So I downloaded a fresh version of Ubuntu 9.04 with Firefox and it works perfect, no sound issues at all.  the only problem I ma having now is with wine.  I cannot load Office 07.  it always says there is an error.  However, I was able to load office 03, but I am a Student at DeVry University and I need Office 07 to write my papers.  I am getting the hint of Linux and hope to completly do away with windows.  can someone help.  Also i cant get itunes to work either it will frezze.

---

