---
title: "Screen Resolution"
date: 2005-02-24
forum: General Help
---

### Post by Rhizome21 on 2005-02-24
I think my resolution is a bit big. I had Ubuntu, and with the help of a friend we got to get the screen resolution fixed through some text editor.

Now I re-installed Ubuntu and I would like to fix the screen resolution not available in the screen resolution menu.

right now im running at  1400 X 1050, at 60 Hz

and I know it can run at 1600 x 1200, at 75 Hz. I have the 1600 x 1200, but at 60 Hz, and  it doesn't take the whole screen up of my monitor.

Can anyone show me how to fix this?

I'm using a Geforce 4 ti4600

---

### Post by Leif on 2005-02-24
If the display doesn't fit the monitor, this is something you need to fix from the monitor panel itself. Some have a nifty auto/set kind of button which will do it for you, but otherwise you need to set height/width manually.

---

### Post by hashimoto on 2005-02-24
You can set all the needed screen settings by opening a terminal and typing "sudo dpkg-reconfigure xserver-xfree86" (provided that you are running Warty). That takes you to a text based setup for keyboard, mouse and display. If everything else is OK, you probably only need to select the additional resolutions and correct the horizontal and vertical refresh rates. Have your display manual at hand.

---

### Post by Rhizome21 on 2005-02-25
ok this comes up when i open that command..

                                                                           &#9474;
 &#9474; Rather than communicating directly with the video hardware, the X server  &#9474;
 &#9474; may be configured to perform some operations, such as video mode          &#9474;
 &#9474; switching, via the kernel's framebuffer driver.                           &#9474;
 &#9474;                                                                           &#9474;
 &#9474; In theory, either approach should work, but in practice, sometimes one    &#9474;
 &#9474; does and the other does not.  Enabling this option is the safe bet, but   &#9474;
 &#9474; feel free to turn it off if it appears to cause problems.                 &#9474;
 &#9474;                                                                           &#9474;
 &#9474; Use kernel framebuffer device interface?
YES or NO?

what do i do?

---

### Post by TravisNewman on 2005-02-25
[QUOTE=Rhizome21]ok this comes up when i open that command..

                                                                           &#9474;
 &#9474; Rather than communicating directly with the video hardware, the X server  &#9474;
 &#9474; may be configured to perform some operations, such as video mode          &#9474;
 &#9474; switching, via the kernel's framebuffer driver.                           &#9474;
 &#9474;                                                                           &#9474;
 &#9474; In theory, either approach should work, but in practice, sometimes one    &#9474;
 &#9474; does and the other does not.  Enabling this option is the safe bet, but   &#9474;
 &#9474; feel free to turn it off if it appears to cause problems.                 &#9474;
 &#9474;                                                                           &#9474;
 &#9474; Use kernel framebuffer device interface?
YES or NO?

what do i do?[/QUOTE]
 just say yes to that and if it doesn't work or causes problems, go back in and say no.

*also moved this topic to the appropriate location

---

### Post by Rhizome21 on 2005-02-26
cool i got the screen resolution fixed!  :D

---

### Post by shandabrown on 2005-11-17
HI!
I have a dell computer that broke and they brought me a new system under my warranty but when I went to try to fix the screen resolution it's not working.  Well of course I call dell, and they tell me it's probably a software problem or maybe a drive that wasn't fully activated when I got the new system.  So i say tell me what to do.  They say they would love to but that isn't covered under my warranty but they can help me for the low price of a 100.  Dell is a rip off.  Can anyone help me?

---

