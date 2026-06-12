---
title: "Ubuntu bootup hangs"
date: 2010-05-13
forum: General Help
---

### Post by Siberian Tiger on 2010-05-13
If I did not post this at the correct place, can the moderators please submit this topic to the right location and let me know where the topic was moved too, please!

When Ubuntu boots up (sometimes before or during the splash screen) intermittently, the OS will hang during boot up.  This occurs on both Ubuntu 9.10, aswell as the current major release Ubuntu 10.04.

My hardware specs are:
Motherboard: ASUS P7P55-m (MicroATX)
CPU: Intel Core i5 750
VGA: MSI R5770-PMD1G (HD5770 Radeon ATI) <FGLRX Drivers are installed, and enabled>
I doubt I will need to go further than this.

Any help that will help resolve this matter, will be greatly appropriated.
I' am trying really hard, to use Ubuntu; but having to press the 'Reset Switch' nearly ten times just to get Ubuntu to boot up, is really not healthy, especially with the hardware itself.

---

### Post by joebu23 on 2010-05-13
Well, the first step towards figuring it out would be to get it to boot.  After you get it to boot, go to /var/log/syslog and open it with your preferred text editor and go to the end to see if there are any clues in it.

My guess is that it is hardware related.  Have you installed any new hardware lately?  (Although it sounds like you haven't)

Also, you might want to try to go into /etc/X11/xorg.conf and edit the driver used for your video card to vesa just to rule out the driver as the cause.  You might also want to try pulling the video card out altogether if possible and see if it boots that way.

---

### Post by mike555 on 2010-05-13
I don't know if this is it, but do you have any cards in the cardreader ? my laptop was slow to start when I had my camera memory stick in the slot ......

---

### Post by Mad dog on 2010-05-13
I have the same issue. I press ctrl+alt+del and it reboots and always works.

---

### Post by Siberian Tiger on 2010-05-14
[QUOTE="joebu23"]Well, the first step towards figuring it out would be to get it to boot.   After you get it to boot, go to /var/log/syslog and open it with your  preferred text editor and go to the end to see if there are any clues in  it.[/QUOTE]

I will keep my eye on the system log, however I can't seem to find the cause so far...

[QUOTE="joebu23"]My guess is that it is hardware related.  Have you installed any new  hardware lately?  (Although it sounds like you haven't)[/QUOTE]

No.

[QUOTE="joebu23"]Also, you might want to try to go into /etc/X11/xorg.conf and edit the  driver used for your video card to vesa just to rule out the driver as  the cause.     [/QUOTE]
No change, or worse.

  [QUOTE="joebu23"]You might also want to try pulling the video card out altogether if  possible and see if it boots that way.[/QUOTE]
Unfortunately, I don't have another VGA device, so I can not perform this task.

[QUOTE="mike555"]I don't know if this is it, but do you have any cards in the cardreader ?  my laptop was slow to start when I had my camera memory stick in the  slot ......     [/QUOTE]
No.  No cardreader is installed.

[QUOTE="Mad dog"]I have the same issue. I press ctrl+alt+del and it reboots and always  works.[/QUOTE]
I have tried those keys many times, and they do nothing for me.  The only way to reset or reload back to CMOS, is by using the 'Reset Switch'.

---

