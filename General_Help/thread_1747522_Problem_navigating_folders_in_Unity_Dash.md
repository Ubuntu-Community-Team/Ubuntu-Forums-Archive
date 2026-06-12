---
title: "Problem navigating folders in Unity Dash"
date: 2011-05-02
forum: General Help
---

### Post by darkcloak on 2011-05-02
I upgraded to 11.04 with pretty much no issues.  But, I do have one:
     When I opened "Files and Folders" in Dash and clicked on a .jpg image, a GNOME-looking dialogue popped up asking me which program I wanted to use to displayed the image.  So, I went to make sure that opening an image on my desktop had the correct results.  It did, and opens in Eye of Gnome.  Yay.  
     Well, I messed up and made a typo, and now when I try to click on ANY folder or file in Dash, it says that it can't find the program "E" (which was my mistake/typo/whatever/I didn't finish typing and had a twitch or something xD).  I cannot figure out how to set Dash to open [x file] with [x program]... anyone else know about that?

---

### Post by garvinrick4 on 2011-05-02
Right click on file and say open with other pick the program you want to open with and check the box that says always open this type of file with this program.

---

### Post by darkcloak on 2011-05-02
Mm, I tried it, but it's as I feared.  It's something specific in the Dash settings.  If I do it outside of Dash, it opens.  If I do it inside Dash, it says, "Failed to execute default File Manager" (which I'd assume would be Nautilus).  And I can't find the Dash configuration files...

---

### Post by mc4man on 2011-05-02
> **darkcloak said:**
> Mm, I tried it, but it's as I feared.  It's something specific in the Dash settings.  If I do it outside of Dash, it opens.  If I do it inside Dash, it says, "Failed to execute default File Manager" (which I'd assume would be Nautilus).  And I can't find the Dash configuration files...
I don't believe there is any config, files & folders just uses whatever is the default for that filetype - nautilus for folders, the install default or whatever you've set for any other particular type of file 

The r. click > open with other application -  'remember this..' option should change the default, maybe d. check with a r. click > _properties_ > open with  (try changing from that properties  dialog box to another choice and back.

---

### Post by darkcloak on 2011-05-02
Dash doesn't seem to have a right click for the icons, only the menus, unless I'm missing something (which is entirely possible, because this is my first day with 11.04).  Any icon I click on that isn't an application gives me the error about not being able to open the default file manager.  I shall keep trying.  ^_^

---

### Post by mc4man on 2011-05-02
For the moment forget about the dash and or places
R. click, ect.  on any .jpg file and see what the default is.

Also maybe run this in a terminal  and post what's in the file, if anything

```
gedit ~/.local/share/applications/mimeapps.list
```

Have you used any other file managers other than nautilus, either in 11.04 or the prev. install you upgraded from

---

### Post by darkcloak on 2011-05-02
Hmm.  A year or so ago, I was running Xmonad and Enlightenment, both of which I loved.  And somewhere along the way I was using Thunar.  And I sometimes use Fluxbox.

Here's the output:

> [Added Associations]
application/x-ms-dos-executable=wine.desktop;file-roller.desktop;wine-extension-ini.desktop;gedit.desktop;openoffice.org-writer.desktop;
application/x-object=gedit.desktop;
application/x-pkcs7-certificates=gedit.desktop;
application/x-lha=nautilus-browser.desktop;
inode/directory=nautilus-folder-handler.desktop;Thunar-folder-handler.desktop;vlc.desktop;exo-file-manager.desktop;nautilus-browser.desktop;
x-scheme-handler/file=exo-file-manager.desktop
x-scheme-handler/trash=exo-file-manager.desktop
audio/mpeg=vlc.desktop;

[Default Applications]
audio/mpeg=vlc.desktopI still don't see the typo I made in the added applications.  I accidentally got "Eye" (I originally thought it was just "E") into the "Run a custom command" box.  I was going to type "Eye of Gnome" for some god-awful reason (I'm chalking it up to being tired), when I know better.  So now, when I click on folders/images in Unity, it says it can't find the program "Eye".  I feel as though I'm missing something *really* simple.  :)

---

### Post by mc4man on 2011-05-02
open mimeapp.list again and add this line to bottom 
 
```
image/jpeg=eog.desktop
```


While you're there you could delete some other lines (you could actually remove all the lines in the [Added Associations] section

So mimeapps.list looks like this (or less
> [Added Associations]
application/x-ms-dos-executable=wine.desktop;file-roller.desktop;wine-extension-ini.desktop;gedit.desktop;
application/x-object=gedit.desktop;
application/x-pkcs7-certificates=gedit.desktop;
application/x-lha=nautilus-browser.desktop;
audio/mpeg=vlc.desktop;

[Default Applications]
audio/mpeg=vlc.desktop
image/jpeg=eog.desktop 


---

### Post by darkcloak on 2011-05-02
Hmm.  Well, that still didn't effect Unity.  This is odd.  However, I right-clicked on a folder and saw the option to open with "File Manager".  This was just from my desktop.  When I did, it threw up that message about, "Eye (No such file or directory") like it does in Unity.  So I went to my /usr/share/applications directory and found two instances of "File Manager". 
     One is nautilus, the other reads, in its properties, "exo-open --launch FileManager %U" which I found has to do with XFCE (as per my looking around, so maybe I'm wrong).  That's the one that throws up the error I'm trying to get rid of in Unity.

---

### Post by darkcloak on 2011-05-02
Ah HA!  It seems it was only that I needed to remove exo-utilities and Thunar.  I suppose I can reinstall them later if I want/need to.  But this seems to have solved my issue.  Thank you!! ^_^  Oh dear.  Er... I don't know how to mark this as [SOLVED].  I create many threads. xD

---

### Post by mc4man on 2011-05-02
Excellent - I was going to give you a link to this thread (still will), I've never used XFCE before so didn't put the exo's in your mimeapps together with that

Anyway it appears XFCE can cause a direct issue with unity if even installed
[http://ubuntuforums.org/showthread.php?t=1747534](http://ubuntuforums.org/showthread.php?t=1747534)

---

