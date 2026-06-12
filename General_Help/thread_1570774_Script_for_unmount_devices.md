---
title: "Script for unmount devices?"
date: 2010-09-08
forum: General Help
---

### Post by inameiname on 2010-09-08
Can someone help me with a basic script on unmounting devices, as that option was removed in Ubuntu Lucid?

I'm aware I can possibly recompile the nautilus source and all that, but I think a much easier method would be to just add a script for such. 

Something basic, like this, but that includes ALL devices that can be unmounted (such as flash drives, external hard drive, and sd/xd cards), not just disc drives. Pretty much what the right click 'Unmount' option in nautilus used to be like:

```

#!/bin/bash
sudo umount /dev/sr0

```

---

### Post by ubulal on 2010-09-08
```

for d in /media/*; do
        sudo umount $d
done

```

Throws some error messages for dirs where's nothing mounted on.

---

### Post by inameiname on 2010-09-08
Thanks for the suggestion. I tweaked it to work as a nautilus-script:

```

#!/bin/bash

SUDO="/usr/bin/sudo"

if [ -t 1 ]; then
"$SUDO" "$@";
else
gksudo -- "$SUDO" "$@";
fi

for d in /media/*; do
        sudo umount $d
done

```Two questions:

- Why is sudo required to unmount here, when before, when it was part of nautilus's context menu, sudo wasn't required or ever asked, as all you had to do was right click the disc, flash, usb, sd card, or whatever drive, and select 'unmount'?

- When unmounting a disc drive, do these two work the same for it?:
```

sudo umount /dev/sr0

```and

```

for d in /media/*; do
        sudo umount $d
done

```

---

### Post by inameiname on 2010-09-08
I found a problem with that:

```

#!/bin/bash

SUDO="/usr/bin/sudo"

if [ -t 1 ]; then
"$SUDO" "$@";
else
gksudo -- "$SUDO" "$@";
fi

for d in /media/*; do
        sudo umount $d
done

```

It unmounts ALL drive, not just the one I right click. So if I had a disc drive mounted, a usb flash drive, and an external hard drive, it unmounts all of them.

Also, it seems to completely remove the flash drives from the normal nautilus pane view, so I can't simply mount it again if desired. Why is that?

To work as the old Nautilus right click 'unmount' did is my ultimate goal here.

---

### Post by ubulal on 2010-09-08
Sorry, I misunderstood.  I though your goal was to umount *everything*.

```

umount "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"

```

This *should*  umount only the selected drive.  I think gnome mounts removable media with your user id, so it should work without sudo.

---

### Post by ubulal on 2010-09-08
And regarding your question: when /dev/sr0 is mounted on /media/Something you can umount either the device file or the mount dir, both work.

---

### Post by inameiname on 2010-09-08
Thanks again for the suggestion. And the explanation on the use of sudo. Sadly though, this doesn't work:

```

#!/bin/bash

umount "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"

```

I've also tried this too:

```

#!/bin/bash

SUDO="/usr/bin/sudo" 

if [ -t 1 ]; then 
"$SUDO" "$@"; 
else 
gksudo -- "$SUDO" "$@"; 
fi 

sudo umount "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"

```

but still doesn't work. Never thought it'd be this hard to make a basic command to do what it used to do, unmount whatever I right click on the desktop and 'unmount'.

---

### Post by inameiname on 2010-09-08
Wow, I just happened to find a script and removed the 'finished' display that works! Google rocks! :P

Unmount.sh

```

#!/bin/bash
# unmount
# by kelfro
# tweaked by me

gksudo -k /bin/echo "Are You The Admin?"

BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`

sudo umount "/media/$BASENAME"

sudo rmdir "/media/$BASENAME"

exit 0

```Mount.sh

```

#!/bin/bash
# mount
# by kelfro
# tweaked by me

gksudo -k /bin/echo "Are You The Admin?"

BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`

sudo mkdir "/media/$BASENAME"

if sudo mount -o loop -t iso9660 $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS "/media/$BASENAME"
then
nautilus /media/"$BASENAME" --no-desktop
fi

exit 0
else
sudo rmdir "/media/$BASENAME"

exit 1
fi

```It seems to work for all devices, not just ISOs, as it seems to be what these are for.

---

### Post by ubulal on 2010-09-08
> **inameiname said:**
> Thanks again for the suggestion. And the explanation on the use of sudo. Sadly though, this doesn't work:

```

#!/bin/bash

umount "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"

```


Please change this to
```

#!/bin/bash

umount "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"  >/tmp/debug 2>&1

```

then try unmounting something and post content of /tmp/debug here.

---

### Post by ubulal on 2010-09-08
Okay I just tried it with nautilus on lucid.  Apparently there is no path given to the script for removable media, neither in $NAUTILUS_... nor in $*.  So it seems to be impossible for a script to know which drive/folder it should act on.

BTW, I have the standard "Unmount" entry in the context menu of removable media.  Tried it with DVD and USB stick. EDIT: Only when using the Tree view in the left side pane!  That's weird.

---

### Post by inameiname on 2010-09-08
Okay, so trying this:

```

#!/bin/bash
umount "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"  >/tmp/debug 2>&1

```

This is what was in that temp file:

```

umount: /media/New
is not mounted (according to mtab)

```

Odd, since it is mounted. Perhaps it's because how it mounts is not through sudo, but through the user, idk.

The other script I found on the net seems to work just fine, so that's good. Although, if you look at it, I don't see how it works for anything but iso files, as:

```

BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`

```

---

### Post by inameiname on 2010-09-08
So you still have the Nautilus "Unmount"? Interesting. I thought it was removed in the new nautilus. I know there is a patch that was included to remove it to clean up the three choices that most seemed to many for most in the original nautilus, but not sure which version in Lucid. I do know that what I use, Nautilus-Elementary, it is also in there as a patch, but in the one big Nautilus-Elementary patch that it gives. 

Oh well. It's funny how the script I found works, but the one you gave doesn't in Lucid. I've seen ones like yours before, and it should work.

---

### Post by ubulal on 2010-09-08
> **inameiname said:**
> Okay, so trying this:

```

#!/bin/bash
umount "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"  >/tmp/debug 2>&1

```This is what was in that temp file:

```

umount: /media/New
is not mounted (according to mtab)

```Odd, since it is mounted. Perhaps it's because how it mounts is not through sudo, but through the user, idk.


So your nautilus *does* set the variable.  That script which you said works does basically just

```

#!/bin/bash
sudo umount "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"

```

which should be enough for you unmount script.  So it was just the missing sudo.

> 
The other script I found on the net seems to work just fine, so that's good. Although, if you look at it, I don't see how it works for anything but iso files, as:

```

BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`

```

This constructs the name for the subdirectory in /media by stripping the trailing ".iso" from the ISOs file name.  Note the space before the dot.  But all that is unnecessary for your purpose.

---

### Post by inameiname on 2010-09-08
Oddly enough, neither of these work. Something in the script I found works, unlike these:

```

#!/bin/bash

sudo umount "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"

```

Or this one, which just prompts for sudo:

```

#!/bin/bash

SUDO="/usr/bin/sudo"

if [ -t 1 ]; then
"$SUDO" "$@";
else
gksudo -- "$SUDO" "$@";
fi

sudo umount "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"

```

---

### Post by inameiname on 2010-09-08
Would these be the same when it comes to unmounting any device:

```

BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`

```

```

BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS`

```

---

### Post by ubulal on 2010-09-08
> **inameiname said:**
> Would these be the same when it comes to unmounting any device:

```

BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`

``````

BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS`

```

Most of the time yes, as there aren't many drives with ".iso" as the last part of their title.

One last try before I give up.  Try the "simple script" with gksudo instead of plain sudo.  That is:

```

#!/bin/bash
gksudo umount "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"

```

 Maybe sudo wants to ask for your password but doesn't have a terminal to display the prompt.  I think the gksudo -k /bin/echo "Are you admin?" in that other script is only their to cache the users credentials for the following plain sudos.

---

### Post by inameiname on 2010-09-08
Sorry, I'm afraid that doesn't work either. Oh, and the addition that I added at the beginning of your original script is what prompts for a sudo password. Without it, it doesn't work as you don't have sudo access.

Also, to your, "Most of the time yes, as there aren't many drives with ".iso" as the last part of their title," I still don't get why the ".iso" part inside the script that works, works with all types of devices, not just ".iso"'s. That doesn't make logical sense to me. But it works, so oh well.

---

### Post by ubulal on 2010-09-08
> **inameiname said:**
> Sorry, I'm afraid that doesn't work either.

Might try this if you like:
```

#!/bin/bash
gksudo umount "`echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"`"

```

> 
Also, to your, "Most of the time yes, as there aren't many drives with ".iso" as the last part of their title," I still don't get why the ".iso" part inside the script that works, works with all types of devices, not just ".iso"'s. That doesn't make logical sense to me. But it works, so oh well.

That script is supposed to be run on ISO files, lets say /store/image.iso.  That's what NAUTILUS_..._PATHS contains.  That basename command strips the leading path (/store/) and additionally the trailing .iso, the result is just "image", which is used as the name of the directory where the iso is to be mounted (/media/image).

When you run it on your removable media, the variable NAUTILUS_..._PATHS contains the mount dir, e.g. /media/FlashPen.  basename removes the leading path /media/ and the trailing .iso (nothing to be done here) which results in just "FlashPen".  This is the value of the variable $BASENAME which ist then used in
sudo umount "/media/$BASENAME"

That means it first removes /media/ from the path and then it adds it again.  It would fail if your removable media had a title like "FlashPen.iso" because nautilus would mount it on /media/FlashPen.iso but the unmount script would try to umount /media/FlashPen.  But who would name their external hard drive or flash stick "Movie Collection.iso"?

The problem which the above simple script hopefully solves is that NAUTILUS_SCRIPT_SELECTED_FILE_PATHS contains a *newline separated* list of selected files[1].  Your list contains only one entry (/media/FlashPen) but with a trailing newline, which the above script removes.

[1] [http://library.gnome.org/users/user-guide/2.27/gosnautilus-444.html.en](http://library.gnome.org/users/user-guide/2.27/gosnautilus-444.html.en)

---

### Post by inameiname on 2010-09-08
That works, thanks. Thank for all your help. Seems as though your script is the most efficient and cleanest to use. And, as you said, the other won't work on drives named funny. So it seems yours does EXACTLY what the original Nautilus one does, so you've solved my issue. Thanks again.

```

#!/bin/bash
# unmount
# ubulal

gksudo umount "`echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"`"

```It is unfortunate you have to put in your sudo, unlike the original Nautilus 'Unmount,' but not a big issue.


Also, shame I can't direct a nautilus-action to the path of this script, so it'll also be in the main directory of my context menu, so I can be even lazier and not have to go to my scripts folder for it. :P But since the icons for the drives aren't technically a file or a folder, it's not possible. Hehe

---

### Post by inameiname on 2010-09-08
Just for the heck of it, I added this script to Gnome-Look. Maybe others will find it useful.

[http://gnome-look.org/content/show.php?content=132354](http://gnome-look.org/content/show.php?content=132354)

---

### Post by ubulal on 2010-09-09
Glad it works.  You could try replacing "gksudo umount"  with "gvfs-mount -u" for a password-less umount ;)

---

### Post by inameiname on 2010-09-09
Sorry, but "gvfs-mount -u" instead of "gksudo umount" does not work. But thanks for the idea.

---

