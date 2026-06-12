---
title: "How do I set up a unique icon for each USB drive AND have their window pop open?"
date: 2010-11-22
forum: General Help
---

### Post by Mike_tn on 2010-11-22
I have a pencil case I carry with a USB hub and 9 USB sticks in it. I like their unique icons and their root windows to pop up upon insertion.

If this is answered elsewhere, please direct me. I looked several times in several ways on google and these forums.

I tried this:
The autorun.inf file on the USB root written this way:

[Autorun]
Action=Start Blue512MB
Icon=BlueFlashIcon\BlueFlashIcon.ico
Label=Blue512MB

Then put the BlueFlashIcon.ico icon image in a folder titled BlueFlashIcon

In Ubuntu (Mav) I get the new personal icon image for that USB stick appearing on the desktop but the USB root window won't pop open automatically when the stick is inserted. I have to dig to the desktop, find it and click it or go into Places on the menu.

OR

If when I put nothing special on the flash, no autorun.inf, no icon image, then the window for the USB pops open upon insertion, which I like, but only get the generic icon that looks the same as all 9 external drives. The labels are unique but icons offer faster recognition over reading labels, when they are needed, much nicer to use~

Ideas?
Do I have to use .svg icons or another kind of text file? 
How do I set up a unique icon for each USB drive AND have the window pop up upon insertion?
Help please!

---

### Post by mrnelson1986 on 2010-11-22
Sounds to me like you just need to figure out the command to add to the autostart file that opens up a window in nautilus.  I'm not sure of the command, but you are along the right track since you already figured out how to assign the icon, name, etc.

---

### Post by Mike_tn on 2010-11-23
Hi mrnelson,

Thanks for the encouragement, I might have quit trying otherwise!

I played with my autorun file but also found some other posts with info.

***
_An Aside:_
 Funny you get better hits from forum search queries if you pick an appropriate forum first. 
If you search all forums the results are incredibly thin, bordering on useless.
I got more than better results by searching icon questions in the Desktop Environments forum category.
***

Only need on the autorun.inf file is a reference to where the icon is:

[B][Autorun]
Icon=BlueFlashIcon\BlueFlashIcon.ico[/B]


And if you want the label a certain way in Windows you can add "Label=name":

[B][Autorun]
Icon=BlueFlashIcon\BlueFlashIcon.ico
Label=Blue512MB[/B]

But Linux won't pick up on the Label command. Not really needed though.

This gives the icon you want, appears the same in both Operating Systems
In Windows you also get an Autoplay pop up dialogue box
In Linux, just the icon, no pop up.
Works on both USB devices and hard disk partitions in both OS.
Need to use ".ico" type Icon file for it to work in both systems.
GIMP will convert any Icon to .ico


I also found this in Desktop Environments category but don't have my Linux box here to test it:

[B]"Right-click on the icon you want to change and choose properties. 
The dialog that appears will have a representative icon, 
left-click on the icon and navigate your way to the icon you want.
Usually icon themes are located in /usr/share/icons."  [/B]

I'll check it out. It it's really slick I'll mark this thread solved tomorrow.

---

### Post by Mike_tn on 2010-11-24
I decided this was best for my needs>

A text file with the name AND extension changed to autorun.inf put on the root of any partition or mass storage device (USB) with this text saved to it:

[B][Autorun]
Icon=yourFolderName\yourIconName.ico[/B]

Then create a folder named properly, corosponding to what you typed in the autorun.inf, and put your icon choice in that.

That way your icons for every device external to your Linux OS, which might be read by other systems, will have the same icon. Plus in Linux the icon appears not only on the desktop but also in the main menu's Places dropdown, and in every folder window on the left side if you have the places option picked for view. 

It won't give you an auto popup folder upon insertion with this method but that seems less of a loss. To compensate I found you can create a launcher up top in the panel with the command "nautilus /media" and if you don't change the default icon of the custom launcher it will make a fat pad in the panel that's easy to click even if you get sleepy. It will open your media folder, showing its icons. If media items, partitions & mass storage, are mounted they will have your icons you set up with the autorun.inf, overlaid on each of the folders representing your partitions and devices.

---

### Post by Paddy Landau on 2010-11-25
I believe that Linux does not run "Action" for security reasons.

However, you may find "UseAutoPlay=1" works. Try it and let us know.

Wikipedia gives useful information on [autorun.inf]("http://en.wikipedia.org/wiki/Autorun.inf#.5Bautorun.5D").

---

### Post by Mike_tn on 2010-11-25
> **Paddy Landau said:**
> I believe that Linux does not run "Action" for security reasons.
However, you may find "UseAutoPlay=1" works.
Adding a UseAutoPlay=1 entry has no noticable effect for me.

Wikipedia has a lot of good info on autorun.inf, Applys to Windows, I can read it for that if needed.

thanks for feedback

---

