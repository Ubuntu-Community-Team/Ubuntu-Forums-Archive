---
title: "What happened to Unmount?"
date: 2010-09-05
forum: General Help
---

### Post by coldraven on 2010-09-05
Hi Guys, maybe it's too early in the morning or I have gone senile but what happened to the Unmount option when I right click on a Desktop CD icon in 10.04?
I only wanted to make an ISO image and K3B says it cannot unmount the CD. I don't want to Eject it thank you. Ah! I have a clever idea! I will add Mount Manager to the panel. Mount Manager should be called Eject Manager because that is all it does!!
Even Krusader seems to have lost its ability to unmount a device.
What's going on? :roll:

---

### Post by inameiname on 2010-09-05
They removed it. It sucks. I miss it immensely. Now I'm forced to open Disk Utility to unmount anything. The right click link was much easier.

---

### Post by dcstar on 2010-09-05
> **inameiname said:**
> They removed it. It sucks. I miss it immensely. Now I'm forced to open Disk Utility to unmount anything. The right click link was much easier.
"They" were the Nautilus developers:
```
* Mon Apr 26 2010 Tomas Bzatek <tbzatek@redhat.com> - 2.30.1-2
- Do not show Unmount when showing Eject/Safe removal
As of nautilus-2.30.1-2, the Unmount option was removed. You could always unmount it from a terminal command line if you really need to.
```

If you want you can downgrade Nautilus to the previous version to regain that functionality:

[http://packages.ubuntu.com/search?suite=karmic-updates&searchon=names&keywords=nautilus](http://packages.ubuntu.com/search?suite=karmic-updates&searchon=names&keywords=nautilus)

You need to install the **libgnome-desktop-2-11** package as well as the nautilus (1:2.28.1-0ubuntu3) & nautilus-data (1:2.28.1-0ubuntu3) packages.

No guarantees that doing this won't break other things in your system, but they seem to work in mine as a test.

---

### Post by inameiname on 2010-09-05
Haha, yeah, Nautilus was the culprit. Nah, I don't think a downgrade would be best for me. Basically, it's either having the unmount or losing my Nautilus-Elementary...and for me, it's not at all a toss up. :P

---

### Post by garvinrick4 on 2010-09-05
> **inameiname said:**
> Haha, yeah, Nautilus was the culprit. Nah, I don't think a downgrade would be best for me. Basically, it's either having the unmount or losing my Nautilus-Elementary...and for me, it's not at all a toss up. :P

```
sudo umount /dev/sr0
```

---

### Post by mc4man on 2010-09-05
If you want this option in lucid it's quite simple to rebuild the current lucid-updates nautilus version with the hide unmount patch disabled
semi described here
[http://ubuntuforums.org/showthread.php?t=1563345](http://ubuntuforums.org/showthread.php?t=1563345)


@ inameiname
Took a look at the ppa for Nautilus-Elementary sources,   the nautilus source used doesn't hide unmount and his debian folder has no patch set like ubuntu.

As it turns out the 'hide unmount' code  is inside of his one big nautilus-elementary patch so it's quite doable, though you'd need to manually revert those changes after the patch is applied, then continue the build of the ppa source.

(a little complicated - but still could be done - don't know if it's worth the effort compared to the regular nautilus which, as mentioned, is quite simple.

Edit : not that hard, a widescreen monitor makes it easy to do. If inclined could try to explain if you get hung up

(will have to give ne a shot for a bit..

---

### Post by arvevans on 2010-09-05
It is possible to make a desktop icon/command that will do the "unmount" function for you.  Just save the command suggested by garvinrick4, as a shell-script in an executable file.  Save that file in some good place ($HOME/bin is a good place).  Then go the the Menu Editor and add this as a new command in the menu. Once you have that new menu item, you can also add the icon to your top-bar for quick access to unmount a specific device.

NOTE:  It would be possible for some enterprising individual to write a shell-script that looked for all the mounts, then presented these as a list for unmounting.  Adding that to the menu and it's icon to the top-bar would make a readily available universal unmounter tool.

---

### Post by inameiname on 2010-09-07
Yeah, I agree with arvervans, a desktop shortcut would be easiest.

Anyway, I appreciate your suggestion; I don't know if it'd be worth the effort either. Of course, if I really did want it, doing it with Nautilus-Elementary is FAR more worthwhile for me than using the plain old, ordinary Nautilus. I'd give up way too much if I were to do that. :P But thanks. Nice to know the culprit, and that it's possible. Maybe there will be an easier way down the road.

What would be nice as an alternative is perhaps a nautilus-action, that works not only for disc drives, but for usb and media card devices as well.

---

### Post by inameiname on 2010-09-07
Just for fun, I decided to look into the nautilus-elementary code. This is how I get it (I hope this is correct):

STEP 1. Get source and install needed dependencies
Get nautilus source
apt-get source nautilus
Install needed dependencies (these are needed for compiling)
sudo apt-get build-dep nautilus
 
 STEP 2. Edit Nautilus source
nautilus-2.31.1/debian/patches/nautilus-elementary-2.30.1-rev91.patch
(but not sure where it is)

STEP 3. Compile and install
 Move to nautilus source root (this dir contains configure file)
 cd..
 Then configure, compile, install
 ./configure --prefix=/usr
 make
 sudo make install


Thus, I seem to have the how-to just fine. It's the finding the exact line of code in nautilus-elementary's big update that confounds me. I know in the normal nautilus it's easy to find the right one, as it's number 16, but since nautilus-elementary just has one big patch, I don't know where inside it.

UPDATE:

Downloading the original 2.30.1 and nautilus-elementary's 2.31.1, I think I've found the same inputs of number 16 patch in the original nautilus that you can comment out for it to have the unmount, inside the nautilus-elementary big patch. Seems it starts at line 28164. Now, do I edit all of it out, or just portions? Not sure.

---

### Post by inameiname on 2010-09-07
Here are those two files, the one from the original nautilus, and the other from nautilus-elementary. Maybe somebody could give me info on just what to comment out in the nautilus-elementary version. Might it be removing the "-" lines, which I'm guessing means they were removed? What about the "+" ones? There are two that I can remove the "+" sign in it. Would that do anything?

---

### Post by inameiname on 2010-09-07
So these are the lines in the nautilus-elementary patch that I've uncommented the (-) parts, line numbers 28164-28210:

```

@@ -7782,10 +7827,6 @@ file_should_show_foreach (NautilusFile
         *show_eject = TRUE;
     }

    if (nautilus_file_can_unmount (file)) {
        *show_unmount = TRUE;
    }

     if (nautilus_file_can_mount (file)) {
         *show_mount = TRUE;

@@ -7805,6 +7846,12 @@ file_should_show_foreach (NautilusFile
         *show_stop = TRUE;
     }

+    /* Dot not show both Unmount and Eject/Safe Removal; too confusing to
+     * have too many menu entries */
+    if (nautilus_file_can_unmount (file) && !*show_eject && !*show_stop) {
+        *show_unmount = TRUE;
+    }
+
     if (nautilus_file_can_poll_for_media (file) && !nautilus_file_is_media_check_automatic (file)) {
         *show_poll = TRUE;
     }
@@ -7852,10 +7899,6 @@ file_should_show_self (NautilusFile
         *show_eject = TRUE;
     }

    if (nautilus_file_can_unmount (file)) {
        *show_unmount = TRUE;
    }

     if (nautilus_file_can_mount (file)) {
         *show_mount = TRUE;
     }
@@ -7874,6 +7917,12 @@ file_should_show_self (NautilusFile
         *show_stop = TRUE;
     }

+    /* Dot not show both Unmount and Eject/Safe Removal; too confusing to
+     * have too many menu entries */
+    if (nautilus_file_can_unmount (file) && !*show_eject && !*show_stop) {
+        *show_unmount = TRUE;
+    }
+
     if (nautilus_file_can_poll_for_media (file) && !nautilus_file_is_media_check_automatic (file)) {
         *show_poll = TRUE;
     }

```And this line, line 33807-33814:

     }
     if (mount != NULL) {
         *show_eject |= g_mount_can_eject (mount);
        *show_unmount = g_mount_can_unmount (mount);
+        *show_unmount = g_mount_can_unmount (mount) && !*show_eject;
     }
 }


Now I'll build the debs and see what happens.

---

### Post by inameiname on 2010-09-07
It's not working. Ah well. Worth a try. For some reason it installed 2.30 and not the same version of nautilus as nautilus-elementary was already. All I changed was that one file, I don't get it.

---

### Post by inameiname on 2010-09-08
FOR THOSE INTERESTED IN A WORKING SCRIPT THAT DOES THE SAME THING AS WHAT NAUTILUS'S 'UNMOUNT' USED TO DO, HERE IT IS. JUST ADD TO YOUR '~/.gnome2/nautilus-scripts' folder:

Oops...it didn't add it correctly. It is in the next post below:

---

### Post by inameiname on 2010-09-08
Unmount.sh (it does prompt you for a sudo password though, but that's not a huge issue):

```

#!/bin/bash
# unmount
# ubulal

gksudo umount "`echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"`"

```

---

