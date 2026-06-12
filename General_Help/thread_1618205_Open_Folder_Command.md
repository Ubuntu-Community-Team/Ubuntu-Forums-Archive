---
title: "Open Folder Command"
date: 2010-11-10
forum: General Help
---

### Post by Rick B. on 2010-11-10
I incorrectly changed the command under Folder Properties to open all folders with the wrong program rather than the Ubuntu default program. I now can't open the folder properties screen using the right mouse button. How do I get back to the properties screen so I can change this back to the default open folder command? Thanks.

---

### Post by sikander3786 on 2010-11-10
From terminal type,

```
nautilus
```

Right Click any folder > Open with other Application > Select File Browser and check the box for Remember this application for folder files.

---

### Post by mc4man on 2010-11-10
Pick any folder -> r. click -> Open With - Other Application, scroll down and choose 'open folder'

Otherwise 
```
gedit ~/.local/share/applications/mimeapps.list
```

Find the line inode/directory= and either delete **the whole line** or add to front
```
nautilus-folder-handler.desktop;
```

Ex.
> inode/directory=nautilus-folder-handler.desktop;totem-xine.desktop;kde-pana.desktop;vlc.desktop;userapp-mplay-E15PIV.desktop;

---

### Post by guest5 on 2010-11-21
Thank You.  I may or  may not, now, install Rythmbox - as I normally use vlc for whatever OS I've got installed.  At least I can now see where the problem lies, and surely not the only one.

Thanks again.

---

### Post by garvinrick4 on 2010-11-21
> **guest5 said:**
> Thank You.  I may or  may not, now, install Rythmbox - as I normally use vlc for whatever OS I've got installed.  At least I can now see where the problem lies, and surely not the only one.

Thanks again. I have found if I open say VLC and then navigate to directory I want open be it video or music I never have problem of opening home folders in VLC by default. But as earlier post says to right click on any folder and choosing open with  and choosing file manager and checking to open with by default will quickly fix problem. Some say no that opening VLC or mplayer or whatever with right click on directory and choosing does not duplicate initial problem, but I can reproduce by doing so eventually at any given time, so I just open my media player and navigate to directory, just because it cuts any doubt about it happening again. And I also enjoy VLC it just works on everything I throw at it. Such a benign looking media application but huge on the inside.

---

### Post by mc4man on 2010-11-21
> some say ..right click on directory and choosing does not duplicate initial problem
It's the 'other application' sub menu that in 10.10 will always change the default for both files and folders if one fails to uncheck the "Remember this.... " box

(the box should either say it's changing defaults or not be enabled by default or not even be there at all - anything but the way it is now.

---

### Post by garvinrick4 on 2010-11-21
> **mc4man said:**
> It's the 'other application' sub menu that in 10.10 will always change the default for both files and folders if one fails to uncheck the "Remember this.... " box
 
(the box should either say it's changing defaults or not be enabled by default or not even be there at all - anything but the way it is now. Very good that explains the why
when I was opening ripped DVD's in VLC and the directory had both text files and .vob
video files, so I was confusing the hell out of media player and file browser of what should open what.
So always opened in path from media player. I see a lot of threads with this problem, it is like usual "user error".
If a directory has both text and media files of any format do not open whole directory go one more step and open the sub-directory and
problem go's away.
Mc4man thank you kindly. OP you should mark this thread as Solved.

---

### Post by pleech on 2011-01-20
[sikander3786]("http://ubuntuforums.org/member.php?u=806649") your a legend. 

Right Click any folder > Open with other Application > Select File  Browser and check the box for Remember this application for folder  files.

Works beautifully and is so simple......no more opening Rhythmbox.

Thanks so much.:D

---

