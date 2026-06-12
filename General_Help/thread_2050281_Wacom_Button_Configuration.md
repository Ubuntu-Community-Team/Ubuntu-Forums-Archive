---
title: "Wacom Button Configuration"
date: 2012-08-30
forum: General Help
---

### Post by zorbama on 2012-08-30
Hello.

I have purchased a Wacom Intuos5 Touch, and received it today. Surprisingly, it worked out of the box, no special steps necessary.

However, I am having small problems with configuring the buttons on the side. It seems that some of the buttons do certain functions, i.e. left-click, right-click and middle-click, but the rest don't do anything. This doesn't change when I use the GUI for Wacom Tablets configuration.
It's most obvious with the touch-ring and the button in its middle: the GUI says that the button is configured to change modes of the ring, but in reality it's used as left-click. The ring doesn't do anything no matter what I configure it to do.

How can I change this behavior? Also, is there an option to toggle the touch-sensitivity? I searched the internet and most things I found are either old or very confusing.

Thanks in advance!

-Amir

---

### Post by Favux on 2012-08-30
Hi Amir,

I'm guessing Ubuntu Precise 12.04 with Unity.  Is that right?

Still early days with the Gnome Wacom tablet gui.  There is a problem with non-sequential buttons.  But there are some patches being worked on and reviewed to deal with that pending.

Center button is Button 1, or at least it is on the Intuos4.  Then from top down is Button 2,3,8,9 and 10,11,12,13.  The skip is because X reserves buttons 4 through 7 for scrolling.  That's also fixed in the patch set.

How to use xsetwacom to configure the Buttons/ExpressKeys is described here:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)

I don't know if the driver supports the central button toggling through selections or not.  If you detect different button presses in xev, or even the same button press code, I'd think you could bind it to a script anyway.  In windows it may just be the button is stepping through a script's selections.  You could ask on the linuxwacom-discuss mailing list.  Several of the developers have Intuos5's.

For touch sensitivity you might want to look at some xinput parameters along with the Wacom ones (man wacom and man xsetwacom entered in a terminal).  See part VI. here:  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562) or here:  [http://forums.linuxmint.com/viewtopic.php?f=42&t=110408](http://forums.linuxmint.com/viewtopic.php?f=42&t=110408)

---

### Post by zorbama on 2013-03-03
Favux,
I believe I forgot to properly thank you for the information. It was of great help. I'm now able to configure my tablet (almost) completely to my heart's content.
Thank you, and aplogies. :)

---

