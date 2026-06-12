---
title: "Some Serious Wine help"
date: 2006-05-24
forum: General Help
---

### Post by tamarku on 2006-05-24
OK, I have gone 100% Linux, Ubuntu on my desktop and Simply Mepis on my laptop.  BUT I have to deal with Windows XP for work.  I would really like to see if I could get my works VPN software working on wine but I can't even get Internet Explorer to work .  I have tried thread after thread after thread and nothing.  I've used Synaptic, I done the terminal apt-get thing.  I've gone through winecfg and winetools to no avail.  Anyone who could get me going it would be greatly appreciated.  Wipe my machine clean of WINE, get it re-installed, and get programs to actually run on it would be wonderful.  If I could just get the simplest thing to run I will try to get everything else going myself.  

Thanks in advance to anyone who is willing to walk a nOOb through this. It's that I really want to be windows free but lets face it guys/gals, Windows is out there and there will always be people and companies that use it.  So a program like WINE might just become a necessity for Linux be mainstream.

---

### Post by Monster_user on 2006-05-24
Wine may be having trouble finding "Internet Explorer". If it is not in the '~/.wine/drive_c/' folder, or in a folder that is assigned a drive letter, then Wine can't find it.

I'm not sure which version of Winecfg you are using (I haven't installed it on Ubuntu). Which one of the following looks familiar? I'm used to the second one. Except for the non-english "Ok", and "Cancel" buttons.

[http://www.winehq.com/hypermail/wine-devel/2004/08/0257.html](http://www.winehq.com/hypermail/wine-devel/2004/08/0257.html)

[http://img.photobucket.com/albums/v328/thetargos/HowTo/Wine/winecfg_drive_advanced.png](http://img.photobucket.com/albums/v328/thetargos/HowTo/Wine/winecfg_drive_advanced.png)
[http://www.linuxquestions.org/questions/showthread.php?t=386621 - Google Image Search](http://images.google.com/imgres?imgurl=http://img.photobucket.com/albums/v328/thetargos/HowTo/Wine/winecfg_drive_advanced.png&imgrefurl=http://www.linuxquestions.org/questions/showthread.php%3Ft%3D386621&h=589&w=430&sz=36&tbnid=y1uyKUnFgwWwsM:&tbnh=132&tbnw=96&hl=en&start=4&prev=/images%3Fq%3Dwinecfg%26svnum%3D10%26hl%3Den%26lr%3D%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official_s%26sa%3DN)


In the list box, with C:, and D: etc, you have to make sure that either '/' or '~' is assigned to a drive. In both of the above images, "Z:\" is the drive letter assigned to '/'.

After that, you may need to do two things.

1st. For older versions of Wine, you will need to install "**dcom98.exe**" from the Microsoft.com website. In order to install most anything. It will result in Wine being detected as Windows 98 though.

2nd. You wil then have to install the 98 version of IE.

---

### Post by tamarku on 2006-05-24
Okay, maybe that is the part I am missing.  I'm thinking I have installed everything.  I  do have the folders and I find the IEXPLORE.EXE file but when I type the command a new window opens and just displays a White background.  No IE6.

---

### Post by nalmeth on 2006-05-25
There is a special way to install IE
[http://patrick.spacesurfer.com/ie_wine_install.html](http://patrick.spacesurfer.com/ie_wine_install.html)
This howto looks ok
There's also wine extension's called winetools, and another whose name escapes me...

---

### Post by cskeide on 2006-05-25
[QUOTE=tamarku]Okay, maybe that is the part I am missing.  I'm thinking I have installed everything.  I  do have the folders and I find the IEXPLORE.EXE file but when I type the command a new window opens and just displays a White background.  No IE6.[/QUOTE]
I had the exact same problem. IE6 doesn't seem to be working with the newest version of wine. I removed wine and installed version 0.9.9 from the dapper repositories, and it works fine.

---

### Post by Scunizi on 2006-05-25
Try looking for or googling IES4linux.  You'll come up with a site that has a script to install IE6, 5.5 & one other.  You'll be able to pick one of the options or all of them.  It will also put a startup icon on the desktop!

---

### Post by Monster_user on 2006-05-25
[QUOTE=nalmeth]There is a special way to install IE
[http://patrick.spacesurfer.com/ie_wine_install.html](http://patrick.spacesurfer.com/ie_wine_install.html)
This howto looks ok
There's also wine extension's called winetools, and another whose name escapes me...[/QUOTE]

It has been a LONG time since I installed IE. I forgot about the DLLOverides.

---

### Post by tamarku on 2006-05-25
I found the ies4linux website and downloaded it.  In the instructions it says to "run" the ies4linux script.  Can someone tell me how to do that?  I downloaded it and put it in its own folder but I can't seem to run the script. Any help on this?

---

### Post by Monster_user on 2006-05-25
Right-click on the script, and select the "Permissions" tab. Make sure that all of the Exec checkboxes are selected.

Then either double-click the file, and select "Run in a Terminal.

Or

Open a terminal, (Applications -> Accessories -> Terminal) and "cd" to the "ies4linux" folder, and then run it using a Dot, and a slash before the name. 

./ies4linux

---

### Post by hollywoodb on 2006-05-25
First off, do NOT use winetools with newer (0.9.x) versions of WINE.

See the Winetools section [here.]("http://www.winehq.org/site/download")

> Note: WineTools only recommended if installation or operability of Windows software failed on pure Wine. Since WineTools radically alters your Wine configuration please do not report bugs in programs with WineTools installed. Instead contact the author of WineTools


Check out [Frank's Corner]("http://frankscorner.org/") for some decent WINE howtos

---

### Post by tamarku on 2006-05-25
Ok, still no go.  When I run the Shell Script for ies4linux a bunch of errors scrolled on my screen telling me certain directories don't work and such.  Well, I am abandoning the windows (this is what I wanted to do anyway).  I'm pressing my work that if they expect me to work from home they need to come up with a linux compatible version or by me another machine for home.  It just means that I don't have to do the 12 to 14 hour days.  Anyway, thanks everyone for all the responses.  Anyone interested in telling me how to purge my system of all the wine/winetools and stuff?

---

