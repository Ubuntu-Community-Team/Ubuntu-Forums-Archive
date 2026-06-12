---
title: "Bootloader, Screenrotation, HDMI Problems;HP tm2"
date: 2011-01-08
forum: General Help
---

### Post by Faoesch on 2011-01-08
Hello Everybody :),
I have several Problems with my laptop:

1. I can't seem to get rid of my bootloader, I read in several forums that I have to put in the command "sudo nano -w /boot/grub/menu.lst" and change the default status to 0.
2. Because I have a tablet pc I can rotate my screen. What I want now is, that my laptop, when I rotate my screen (like a book), that the screen rotates. I found a blog of Fred he's explaining how to rotate the screen. [http://linuxquirks.blogspot.com/2010/11/automatic-screen-rotation-on-hp.html](http://linuxquirks.blogspot.com/2010/11/automatic-screen-rotation-on-hp.html) ; Now my problem is, that I don't have any clue how to bind the Programm to the key. On Fred's Blog he says how to do it with Ubuntu but I can't find out how it works with Kubuntu.
3. For my last problem the HDMI doesn't work. Or at least I don't know how to connect the laptop to the tv. When I'm on the channel and press fn + f4, well... nothing happens.

So I'm thankful for any kind of help. :)

---

### Post by Favux on 2011-01-08
Hi Faoesch,

The python script he's badmouthing is Magick Rotation:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

The loads of CPU overhead he's talking about was 2 to maybe 3%.  However the new version 1.2 has eliminated that and you won't see Magick in Top now except when you rotate.  Plus it does other stuff aside from automatic rotation without the need of using a button.  For example toggle your multi-touch on and off.

If you want to stick to his script the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") shows a more detailed version of Gnome key binding using Compiz settings.  That may give you more ideas on how to do it in KDE.

HDMI may not work with the ATI card disabled it looks like.  See;
[http://ubuntuforums.org/showthread.php?t=1410752](http://ubuntuforums.org/showthread.php?t=1410752)
[http://ubuntuforums.org/showthread.php?t=1616327](http://ubuntuforums.org/showthread.php?t=1616327)

What release of Ubuntu are you using?  I don't think that command will work for Grub2.

---

### Post by Faoesch on 2011-01-09
Well I'm using Kubuntu 10.10. I had problems with my ATI that's why I disabled it ([http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1525654](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1525654)).

Thanks for the link for the screenrotation. I'll have a look at it when I have a bit more time.

---

