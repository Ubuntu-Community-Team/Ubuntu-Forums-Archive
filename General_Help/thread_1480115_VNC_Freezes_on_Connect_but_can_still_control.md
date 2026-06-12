---
title: "VNC Freezes on Connect but can still control"
date: 2010-05-11
forum: General Help
---

### Post by Kai Summers on 2010-05-11
OK, so I have 2  computers with Ubuntu 10.04, when I VNC to the computer I want to  control I get the first frame but no subsequent frames. However I can  still control the computers mouse and action on anything I want to but I  need to be in the same room to see the screen I am VNC'ing to, this  sort of defeats the point of VNC as I would like to be able to control  the computer from any room in the house.

Any thoughts as to what might be going on here?
 		                   		  		  		 		 			 				__________________

---

### Post by davewill on 2010-05-11
turn off compiz - set graphics effects to none.

---

### Post by Kai Summers on 2010-05-12
I didn't even think of that - thank you! Problem sorted...Can't emphasize enough how much of a legend you are right now!!!

---

### Post by davewill on 2010-05-12
If you do a little more digging, you can make VNC work with Compiz/effects enabled, but in my opinion - the performance degradation of compositing thru VNC isn't worth it.

Glad it's working for you now

---

### Post by Vijay.Saraff on 2010-09-20
> **davewill said:**
> If you do a little more digging, you can make VNC work with Compiz/effects enabled, but in my opinion - the performance degradation of compositing thru VNC isn't worth it.

Glad it's working for you now

Can you point me to how I can get compiz + vnc to work? I found [http://ubuntuforums.org/showthread.php?t=1470156](http://ubuntuforums.org/showthread.php?t=1470156), and something about -noxdamage to the vncserver but I have no idea how to do that. 

This is a headless server, and such needs vnc (or remote X?), and  I want to be able to use docky (which requires compositing!). You think it's a bad idea though? Any other ideas?

---

### Post by Vijay.Saraff on 2010-09-21
Anyway I solved by setting appearance effects to NONE (i.e. disable compiz)

then using gconf-editor set /apps/metacity/general/compositing_manager

i also set the xdamage setting (though I don't know if that solved the problem) /desktop/gnome/remote_access/disable_xdamage

and voila now vnc works with compositing and gnome-do w/ docky theme. Though the vnc is slow like you'd mentioned, but the desktop is fast.

---

