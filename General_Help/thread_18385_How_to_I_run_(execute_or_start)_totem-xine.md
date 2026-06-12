---
title: "How to I run (execute or start) totem-xine"
date: 2005-03-06
forum: General Help
---

### Post by trinity on 2005-03-06
Hi Guys,

I installed *totem-xine* two days ago, but how do I start it.  For e.g., to run MPlayer we type [FONT=Courier New]gmplayer[/FONT] in the Terminal, likewise what command should I use to run *totem-xine*.  I tried [FONT=Courier New]totem-xine[/FONT] it wouldn't work.  :| 

Thanks for all help.

---

### Post by darrenadams on 2005-03-06
You just need to type totem from a terminal. The -xine or -gstreamer part just refers to the backend that the totem package has been compiled with

---

### Post by bored2k on 2005-03-06
[QUOTE=darrenadams]You just need to type totem from a terminal. The -xine or -gstreamer part just refers to the backend that the totem package has been compiled with[/QUOTE]
 He's saying it wont open on totem-xine wich is really weird.

To install totem-xine, usually u have to remove totem-gstreamer [default], so if u open the totem on the panel, wich one opens? [may i suggest xine-ui or vlc]

---

### Post by poofyhairguy on 2005-03-06
[QUOTE=bored2k] [may i suggest xine-ui or vlc][/QUOTE]

Or Gxine. I don't know why Totem is even installed in ubuntu. In its default "OSS pure" configuration,  its near worthless.

---

### Post by trinity on 2005-03-08
[QUOTE=darrenadams]You just need to type totem from a terminal. The -xine or -gstreamer part just refers to the backend that the totem package has been compiled with[/QUOTE]hmm ... that explain things.  Now it plays mp3 files, but no VCDs.  When I open the *.DAT from the VCD, it pops up a message "pluggins not found for this type".  I have w32codecs installed already.  Do I need more such codecs or plugins ..?

[QUOTE=bored2k][may i suggest xine-ui or vlc][/QUOTE][QUOTE=poofyhairguy]Or Gxine. ..[/QUOTE]I don't have a NET connection at home.  Once I download all the required packages I will try this one as well and will let you know. :)

---

### Post by bored2k on 2005-03-08
[QUOTE=trinity]hmm ... that explain things.  Now it plays mp3 files, but no VCDs.  When I open the *.DAT from the VCD, it pops up a message "pluggins not found for this type".  I have w32codecs installed already.  Do I need more such codecs or plugins ..?

I don't have a NET connection at home.  Once I download all the required packages I will try this one as well and will let you know. :)[/QUOTE]
 VCD's ?

Open wxvlc [comes with vlc]

Open disc > Disc type > VCD

---

### Post by trinity on 2005-03-10
vlc is too cool ..!  Installed xine-ui, but for some reason my system hangs shortly after launching the app.  I had to hard reset everytime.  Also tried the MPlayer from Hoary (in Warty) it's also looking cool, but I guess I will go with vlc for now.  Got to try GXine yet.  

I wonder why in the world totem is shipped by default, which is of no use at all in it's original form.  I think I will do some research on this totem thingy to get it working .. :)

My box has two CD drives in it.  The master drive is is a DVD/CD-RW/CD-R combo drive and the slave is a plain CD-ROM.  I would like to use the CD-ROM for watching VCDs.  When I tried changing the drive to /media/cdrom1 or /dev/cdrom1, the light goes on in the CD-ROM drive and nothing happens after that.  Neither vlc nor gmplayer works with the 2nd drive.  Any ideas ..?  

Also opening the *.DAT file directly from the VCDs works on Windows Version of vlc, but it wouldn't work in Linux version though.  :(

Thanks for all the help.

---

