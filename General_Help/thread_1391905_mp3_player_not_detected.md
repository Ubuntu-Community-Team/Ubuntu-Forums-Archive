---
title: "mp3 player not detected"
date: 2010-01-27
forum: General Help
---

### Post by hairchin on 2010-01-27
I have used other mp3s with no problem being detected. They always popped up on the desktop after i plugged them into the usb. This time I have a Coby MP815 player and nothing happens when i plug it into usb. Is this a microsoft proprietary issue associated with this specific product? Can I get around this problem? What do I need to do? Please be very simplistic with your response as I am learning and fairly new to this.

I do not have the manual for the Coby MP3 that is why I ask

---

### Post by hwttdz on 2010-01-27
To make it pop up when you plug it in I think you might need a .is_audio_player file in the / of the mp3 player filesystem. See here [http://live.gnome.org/Rhythmbox/FAQ](http://live.gnome.org/Rhythmbox/FAQ)

Also if you browse to "/media" in nautilus what do you see.  Or you could post the output of "ls /media/".

---

### Post by hairchin on 2010-01-27
what is nautilus how do i access it?

---

### Post by Megafag on 2010-01-27
> **hairchin said:**
> what is nautilus how do i access it?

Nautilus is the file manager. just open a "window" and find /media. should be above your home directory.

---

### Post by hwttdz on 2010-01-27
Nautilus is the file manager, you can either run "nautilus" from a terminal or open anything in your "places" menu. /media is under the root file tree (hence the leading slash).  ~/media would mean the media directory in your home folder.

---

### Post by hairchin on 2010-01-29
how do i run nautilus from terminal what command is needed?

---

### Post by hwttdz on 2010-01-29
To run nautilus from the terminal type "nautilus" (no quotes, it was quoted above to show it was a command) and press enter.  You can even get fancy and open nautilus in your /media directory with "nautilus /media".  In general to run any program from the terminal just type the name of the program.  This becomes a huge timesaver in that it prevents you from having to navigate menus.  

You successfully opened it using the places menu?

---

### Post by JackRock on 2010-02-04
I'm having the same problem with a Coby MP705-2G.  My "ls media" output is as follows:

```
cdrom   floppy   sdb1  usb0  usb2  usb4  usb6
cdrom0  floppy0  usb   usb1  usb3  usb5  usb7
```

I cannot access through any of the usb folders here.

---

