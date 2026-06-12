---
title: "System Crashing On Navigating Into Folder With Video Files"
date: 2011-04-02
forum: General Help
---

### Post by krenic on 2011-04-02
Whenever I navigate into a folder containing video files, my entire system freezes/crashes. The keyboard, video, and the entire system become entirely unresponsive.

I can recreate the problem every single time by simply opening a nautilus window, then going into a directory containing 1 or more video files (avi, mkv, mp4, etc.). It doesn't seem to matter whether I stay in the folder, or quickly navigate away either. Seconds later, the system freezes entirely, to the point where my capslock key does not even toggle the capslock indicator.

I first noticed the problem when I installed 10.10 months ago on my Acer AspireOne D250. I had recently upgraded to ubuntu natty beta hoping the problem might have been fixed.

Has anyone experienced a similar problem? I have been unable to find a similar bug report, and I thought I would ask here before I file a bugreport.

Any input/suggestion would be greatly appreciated.

---

### Post by Krytarik on 2011-04-02
Although my system doesn't freeze, I disable thumbnailing for videos, because it doesn't have a real benefit, and it causes a heavy system load, at least if no thumbnail has already been created and it still exists.

To fine-tune thumbnailing for specific  files, you can use gconf-editor.
- press Alt+F2
- enter:
```
gconf-editor
```- browse to "/desktop/gnome/thumbnailers"
- untick the key "enable" in the respective mimetype folders

AVI    = "video@x-msvideo"
MPEG    = "video@mpeg"
FLV    = "video@x-flv"

To get the mimetype for a particular file, right-click at it and choose "Properties".

Greetings.

---

