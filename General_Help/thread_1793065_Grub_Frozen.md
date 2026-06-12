---
title: "Grub Frozen"
date: 2011-06-28
forum: General Help
---

### Post by Mr. Beekeeper on 2011-06-28
I deleted my Windows partition to go completely Linux, and now GRUB is frozen.  It loads up the selection screen and there's no way to select or do anything; its frozen.  Any suggestions?  Thanks in advance.
Grub 2 v1.99.

---

### Post by oldfred on 2011-06-29
I do not know why deleting windows would change anything in grub?

Post this from liveCD:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Mr. Beekeeper on 2011-06-29
Wow, this is a facepalm moment.  I have an older computer with the PS/2 connector for my keyboard.  My mouse is USB.  I had the keyboard plugged into the mouse PS/2 slot on the computer.   I must have accidentally done it while rearranging my room.  The odd thing is that the keyboard worked ok after the OS loaded up, but not before.  This became apparent when I couldn't get into the BIOS.  GRUB just seemed "stuck" because it was waiting for my input.  I feel so intelligent right now.... 

:lolflag:

---

### Post by oldfred on 2011-06-29
Whatever it takes to make it work. 

I thought it was great when they color coded the ps/2 cnnectors, but then I connected them so rarely I forget which is which.

There have been issues with BIOS settings to turn USB keyboard & mouse on and connecting to USB ports. Windows & Ubuntu would work as they seemed to ignore BIOS but grub did not as it used BIOS.

---

