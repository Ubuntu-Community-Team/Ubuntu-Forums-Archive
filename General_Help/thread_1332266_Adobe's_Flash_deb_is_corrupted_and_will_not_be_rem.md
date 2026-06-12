---
title: "Adobe's Flash deb is corrupted and will not be removed..."
date: 2009-11-20
forum: General Help
---

### Post by Udibuntu on 2009-11-20
> E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


Got this message while trying to install Flash on a an AAO751 with 9.10 reinstalled. Previous installation worked fine with Flash.

UM can't remove the corrupted file...

Please help!

---

### Post by slakkie on 2009-11-20
[http://blog.opperschaap.net/2009/11/13/upgrade-flash-on-ubuntu-after-a-release-upgrade/](http://blog.opperschaap.net/2009/11/13/upgrade-flash-on-ubuntu-after-a-release-upgrade/)


Enjoy

---

### Post by phillw on 2009-11-20
> **Udibuntu said:**
> Got this message while trying to install Flash on a an AAO751 with 9.10 reinstalled. Previous installation worked fine with Flash.

UM can't remove the corrupted file...

Please help!


It's long, it's involved - it gets scary, but it does work....  --->  [http://ubuntuforums.org/showthread.php?t=1305829](http://ubuntuforums.org/showthread.php?t=1305829)

Have a read through - there is a quick method that may well work for you posted near the end...

> Fixed the problem for me

sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
sudo dpkg-reconfigure adobe-flashplugin --force
sudo dpkg --purge --force-all adobe-flashpluginTry that 1st.

The longer solution, that I know works is .....

     ```

     cd /var/lib/dpkg
sudo cp available available.bad
sudo cp status status.bad
gksudo gedit available 
```
Copy and paste that, then ...

4b) remove all references to adobe-flashplugin Save/close.

Use the Search Find for the word adobe until you get a block like this ....

     Quote:
                                                 Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from the net.  It is a
 Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can
 use the Flash plugin.  This package currently supports the following browsers:
 Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
 Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
 konqueror-nsplugins is installed.
 .
 WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be
 downloaded from [www.adobe.com]("http://www.adobe.com/").  The distribution license of the Adobe flash
 plugin is available at [www.adobe.com]("http://www.adobe.com/").  Installing this Ubuntu package implies
 that you have accepted the terms of that license.
Homepage: [http://wiki.ubuntu.com/FlashPlayer9](http://wiki.ubuntu.com/FlashPlayer9)
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Description: Adobe Flash SWF Player ([http://www.adobe.com]("http://www.adobe.com/"))
Npp-File: libflashplayer.so
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Adobe Flash Player (installer)
Original-Maintainer: Bart Martens <bartm@knars.be>                                 
Delete it.

Then ..

     ```

     gksudo gedit status 
```
5b) remove all references to adobe-flasplugin. Save/close.

Do the same as above - looking for the same thing.

Then ..

     ```

     cd info 
```
Then..

     ```

     sudo rm -r adobe-flashplugin 
```
Now, I didn't find anything on my system in /var/lib/info  - so don't be worried if you don't !!


/edit Hmmm... I issued a sudo rm -r command - these are not good. PLEASE BE REALLY CAREFUL.

Regards,

Phill.

---

### Post by MiCK.ca on 2009-11-20
Yes purging works. But i recommend getting Ubuntu Tweak and run the "application cleaner" part of Tweak. It is a nice GUI for removing all the old orphan files that are left behind. it cleans the cache, Config and packages stored. even after a purge there is still some "non-flash" dependencies. Clean them and try again. It's important to rid the config files so the new install has no reference.

---

### Post by Udibuntu on 2009-11-20
Dag Slakkie, thanks - you pointed me to the right solution.

But, instead of coding and messing with sensitive files I took the easy way - just opened "software sources", looked for what looked like the Partner http and enabled it.

Flash is back on with better quality and better FPS than before, don't ask me why. No HD but Youtube works almost perfectly.

Thanks also for the other posters, I tried the first and most simple method and it worked.. if it breaks again then I'll dig deeper.

Thanks again,

udi

---

