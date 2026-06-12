---
title: "Gnome Icons look like they are in front of a black square"
date: 2009-11-28
forum: General Help
---

### Post by Weepleman on 2009-11-28
I have Ubuntu 9.10 with gnome and an intel 945GM graphic card.  All of a sudden for no reason that I can find all of the icons I have and pretty much anything else that I can clicklooks like it is in front of a black square.  It is pretty anoying for normal things because they look worse as well, but it is pretty bad for thing like battery and volume control because they do not work right.  Is there anything I can do about this here is a screen shot:

[IMG]http://justincrg.webs.com/Pictures/Screenshot.png[/IMG]

---

### Post by raktarok on 2009-11-28
Does this happen with other iconsets too? you could try removing the icon theme and again reinstalling it, but I don't know if this will help...

---

### Post by jamesisin on 2009-11-28
You can try different icon sets by navigating to System --> Preferences --> Appearance then selecting the Theme tab and clicking the Customize button.  When the Customize Theme dialog appears, click on the Icons tab.

It looks like this is effecting your icons in the top panel as well?

Also, please use thumbnails in your posts (rather than the full images).

---

### Post by Weepleman on 2009-11-28
The same thing happens in all themes and yes, it does happen in the top bar thing, and sorry about the full size picture, I don't know how to post a thumbnail

---

### Post by jamesisin on 2009-11-28
The easiest way to do it in terms of entering code is to create a smaller version of the image and store it with the image:

```
<a href="http://PATH/TO/YOUR/IMAGE.PNG">
<img src="http://PATH/TO/YOUR/IMAGE_thumbnail.PNG">
</a>
```

You can code it to create the thumbnail on the fly in the browser, but the code isn't as easy.

Or you could just post smaller images when details are less important (Gimp has a great crop tool).

Are you using Compiz?  You may try switching back to MetaCity to see if that alters matters.

I take it this isn't causing any problems, per se; it's merely an appearance issue?

---

### Post by jamesisin on 2009-11-28
Don't mean to harp on the image issue, but I figured out a better solution for you.  (I don't often post images.)

In the composition window there is a paperclip icon for attaching files.  If you attach an image using that method, the site creates a thumbnail server-side.  Check this out:

[http://ubuntuforums.org/showthread.php?t=1339308](http://ubuntuforums.org/showthread.php?t=1339308)

---

### Post by Weepleman on 2009-11-28
For most things it is just an apperaence issue, but for something like the volume control it completly removes any usefulness of it

---

### Post by raktarok on 2009-11-28
Check and see if this occurs when logged in as another user. If it does not, then we can at least know that its a configuration problem, and we could try deleting some files in the home folder.

---

### Post by Weepleman on 2009-11-28
It still happens in another user

---

### Post by jamesisin on 2009-11-28
So, what happens when you click on the volume icon?

---

### Post by Weepleman on 2009-11-28
It still shows the volume adjust, but I cannot just look at it and see the volume level

---

### Post by jamesisin on 2009-11-28
I found this, but I don't think it's your issue:

[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/237562](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/237562)

What about the icons in a folder (using icon view)--are those also effected?

---

### Post by Weepleman on 2009-11-28
Yes, those are affected too

---

### Post by JCollierDavis on 2009-11-28
I have the same problem in UNR.  It started after Thursday's (26 NOV) update.  I didn't catch which packages were updated, but as soon as the reboot finished all the icons, even the ones in the system tray look terrible.

The bootsplash looks terrible too.  The animation has disappeared and replaced with a white bar.

---

### Post by raktarok on 2009-11-28
You can take a look at what packages were updated by doing this:
```
sudo gedit /var/log/apt/term.log
```
Scoll down to the end, and try to see what packages were updated. Look if there were any relevant packages. 
Other than that, I can't offer any suggestions. I really don't know what is causing the problem. Maybe you can try installing an alternate file manager(eg thunar) and see if that helps...

---

### Post by Weepleman on 2009-12-01
Three Cheers for the new update, Yeah!  That completely fix my problem :) sorry if anyone else's did not get fixed, but updating my computer last night worked for me!

---

### Post by jamesisin on 2009-12-01
Well, there you have it.  You may want to mark your thread as solved.  Not clear what the protocol is for 'fixed by update'.

---

