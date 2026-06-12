---
title: "Making cursor themes work in compiz"
date: 2010-08-20
forum: General Help
---

### Post by vince2678 on 2010-08-20
CC is now complete (didn't have access to the internet for 3 days so I couldn't upload  it) but its working fine. Tested it out with an ISO and it works perfect.
Rename to .deb and install it. Even though it says 11.04 - it works on any system with a problematic version of compiz. It is also harmless on a system without compiz although it does depend on it. 
[ATTACH]192967[/ATTACH]

---

### Post by exe0 on 2010-08-21
I get this message after running:

```

exe0@exe0-desktop:~$ gnome-appearance-properties

(gnome-appearance-properties-compiz-cursors:5928): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties-compiz-cursors:5928): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

```

My cursor theme still does not change. 

I'm running Ubuntu 10.04 with all the latest updates.

---

### Post by vince2678 on 2010-08-21
```
                                                                         **Bug Description**

   
   Binary package hint:  gnome-control-center
 Warnings while enabling compiz via gnome-appearence-properties.
 <stdout>
Checking for Xgl: not present.
xset q doesn't reveal the location of the log file. Using fallback  /var/log/Xorg.0.log
Detected PCI ID for VGA:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture  size (4096): Passed.
Checking for Software Rasterizer: Not present.
Checking for nVidia: not present.
Checking for FBConfig: present.
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present.
 <stderr>
(gnome-appearance-properties:5294): Gdk-CRITICAL **:  gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
 (gnome-appearance-properties:5294): Gdk-CRITICAL **:  gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
 (gnome-appearance-properties:5294): Gdk-CRITICAL **:  gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
 (gnome-appearance-properties:5294): Gdk-CRITICAL **:  gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX  1.3 is not supported!  This is an application bug!
 (gnome-appearance-properties:5294): Gdk-CRITICAL **:  gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap  format, disabling YV12 image format
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when  GLX 1.3 is not supported!  This is an application bug!


```The text above is just output from gnome-appearance-properties and compiz.Ignore it, it is probably irrelevant.  If it fails, try installing the package in a livecd environment to see if it works. The package works fine on my system; I have never updated any packages so most of them are as they were at installation. If it still fails try the following:
```

sudo ln -s /usr/share/icons/default /usr/share/icons/compiz-cursors/default
sudo chmod 777 -R /usr/share/icons/default


```
I'm not sure if this works.:confused: But try it anyway.

---

### Post by exe0 on 2010-08-22
I'm still getting the same messages, but after restarting the changes worked. Thanks

---

### Post by jrb114 on 2010-09-19
Thanks, I had to do a 
[code]
killall compiz
compiz &
[\code]
even after logging out and in again, but it worked perfectly.

---

### Post by mrinehart93 on 2010-09-19
The .deb posted above only helped me change my cursor back to the default... but now I can't change it to anything.

---

### Post by vince2678 on 2010-09-27
Check  :
1) You are running compiz.
2) You are not running 10.10 or anything below 10.04 (< 10.04 have not tested on)
3)  if the /usr/share/icons/compiz-cursors directory is populated with files that match
    the name of the available or needed cursor theme(s)
4) Check in the /usr/share/icons/compiz-cursors directory and take a look at the theme file USING A TEXT EDITOR and check the name of the cursor     theme you want to change to.
5) Make sure you DID NOT update gnome-control-center after installation of THIS package (this breaks it!). Update gnome-appearance-properties BEFORE installing this package.
6) Make sure you are running GNOME.

---

### Post by msrinath80 on 2010-09-27
You folks do realize that installation of a specific cursor theme in Debian/Ubuntu is complete only after you do a:

sudo update-alternatives --config x-cursor-theme

and select the new theme?

---

### Post by vince2678 on 2010-10-03
> **msrinath80 said:**
> You folks do realize that installation of a specific cursor theme in Debian/Ubuntu is complete only after you do a:

sudo update-alternatives --config x-cursor-theme

and select the new theme?

That's exactly what this package does:```


#!/bin/bash
IS_COMPIZ_RUNNING=$(pstree | grep -io compiz) #copies the output of 'pstree | grep -io compiz' to variable IS_COMPIZ_RUNNING
ICONSDIR=$(ls $HOME/.icons)
ICONSDIRII=$(ls $HOME/.icons/default)
TEMPFILEGAP=$(tempfile -p 1) #make temporary file and give a prefix of 1
TEMPFILEGAPII=$(tempfile -p 2) #make temporary file and give a prefix of 2
TFCURSOR_THEME=$(gconftool-2 --get /desktop/gnome/peripherals/mouse/cursor_theme) #gconf key that has the current cursor name
USR=/usr/share/icons/compiz-cursors
echo $TFCURSOR_THEME > $TEMPFILEGAP
/usr/bin/gnome-appearance-properties-compiz-cursors %F
CURSOR_SIZE=$(gconftool-2 --get /desktop/gnome/peripherals/mouse/cursor_size) #Cursor size
gconftool-2 --type integer --set  /apps/compiz/general/allscreens/options/cursor_size $CURSOR_SIZE
CURSOR_THEME=$(gconftool-2 --get /desktop/gnome/peripherals/mouse/cursor_theme)
echo $CURSOR_THEME > $TEMPFILEGAPII #check below

mkdir $HOME/.icons #should fix this later
mkdir $HOME/.icons/default #should also fix this
cp $USR/$CURSOR_THEME $HOME/.icons/default/index.theme 

if [ "$IS_COMPIZ_RUNNING" == "compiz" ]; then #check if compiz is running. MIGHT or MIGHT NOT work, depends on the program pstree in package psmisc
    diff $TEMPFILEGAP $TEMPFILEGAPII || /usr/bin/compiz --replace; #restarts compiz
else exit;
fi

rm $TEMPFILEGAP $TEMPFILEGAPII #remove temporary files
```If you did not know, what that command does is link your current theme file to /usr/share/icons/default/ to make all X apps know about it. This package does the same thing, only without you having to type in the command.

---

### Post by ben2talk on 2011-05-10
This isn't working in Natty - I can't now change my cursors with compiz enabled despite trying to find workarounds, and making sure that my cursor is listed as /usr/share/icons/default as an 'Inherit=Obsidian' as well as in gconf-editor.

works fine in Metacity.

---

### Post by vince2678 on 2011-05-15
I'm looking into your problem. I should be done in no time :). JUst check here for a new package.

---

