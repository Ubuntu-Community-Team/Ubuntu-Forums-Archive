---
title: "Weird keyboard layout"
date: 2011-06-06
forum: General Help
---

### Post by olilo on 2011-06-06
I installed Ubuntu 11.04. 

I wonder how to set the keyboard layout.

I keep using the rescue cd because whenever I choose a keyboard layout the system does not seem to keep it like that.

After rebooting it loads another layout and I can't find which keys to type in that unknown layout. So for the moment, my password is 'tt' because I know it will work in both layout.

I have a belgium azerty keyboard. For the moment the upper option in the keyboard layout screen is USA and the lower option is Belgium. Which is weird since I thought that the upper option was of higher priority. But at least it works like that. At least until I reboot I think :(

PS: the rescue cd has also a keyboard layout problem. I chose belgium and I end up with a usa layout.

Can someone help me ?

Thanks.

---

### Post by hwttdz on 2011-06-06
If you mean this layout: [http://wiki.laptop.org/go/Keyboard_layouts#French_AZERTY_fr_FR](http://wiki.laptop.org/go/Keyboard_layouts#French_AZERTY_fr_FR)

Then one option would be to put something in your rc.local to run

setxkbmap fr

Another is to edit your xorg.conf to change the default setup:
[http://ubuntuforums.org/showthread.php?t=544984](http://ubuntuforums.org/showthread.php?t=544984)

Current ubuntu versions create an xorg.conf on the fly, "sudo Xorg -configure" will get you one.

---

### Post by olilo on 2011-06-07
```
setxkbmap -layout be
``` works in a terminal. I've set it in rc.local but after reboot the system added a new entry *USA* in the keyboard layout screen and the layout was the american one.

---

### Post by olilo on 2011-06-13
I followed the tips from that page:
  [http://blog.al4.co.nz/2011/06/keyboard-layout-switching-to-usa-in-ubuntu-11-04/](http://blog.al4.co.nz/2011/06/keyboard-layout-switching-to-usa-in-ubuntu-11-04/)

And now that issue is solved :)

---

