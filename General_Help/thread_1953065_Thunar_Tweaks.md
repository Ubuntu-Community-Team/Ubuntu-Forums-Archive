---
title: "Thunar Tweaks?"
date: 2012-04-05
forum: General Help
---

### Post by SlugSlug on 2012-04-05
Am new to xubuntu,

I'd like to make Thunar similar to nautilus.  

- Tab browsing 
- Remember folder view  (I like certian folders list some icon)

- I would also like it to hide folders again once closed, for example in nautilus I show hidden close browser and when I re-open the hidden files are hidden again.

Thanks

---

### Post by brainwash on 2012-04-05
The features you mentioned are on the wish list for thunar, which you can find here:

[http://wiki.xfce.org/wish_list#thunar](http://wiki.xfce.org/wish_list#thunar)

So the developers might implement them at some time. Meanwhile you could install nautilus and run it with the "--no-desktop" parameter to avoid conflicts with the xfce desktop manager.

---

### Post by SlugSlug on 2012-04-05
> **brainwash said:**
>  Meanwhile you could install nautilus and run it with the "--no-desktop" parameter to avoid conflicts with the xfce desktop manager.

am a fussy bugger tho and like to keep things clean ;)

---

### Post by mike555 on 2012-04-05
There are a bunch of "custom actions" for Thunar , resizing images, terminal here, send-to , etc.

---

### Post by SlugSlug on 2012-04-05
yer they are & it even come with terminal here option by default. But it's just them 3 things I want now really

---

### Post by Dave_L on 2012-04-05
> **SlugSlug said:**
> Tab browsing

The Thunar developer has stated repeatedly that he's not going to implement that.

---

### Post by SlugSlug on 2012-04-06
Do many people use nautilus with xubuntu ? From what I read is seems quite messy

---

### Post by NTL2009 on 2012-06-10
> **SlugSlug said:**
> Do many people use nautilus with xubuntu ? From what I read is seems quite messy

I tried setting Nautilus as default in the Settings Manager - Preferred Apps - Utilities, but had some conflicts, and I read of problems (for me, thunderbird/ToneqQilla would not play the sounds I set, it just opened the directory they were in).  I also really like Nautilus features, and all the scripts I have, so I really wanted PLACES, and my DIRECTORY MENU in the panel to open Nautilus.
 
**Here's my compromise solution:**

In Thunar, go to Edit/Configure Custom Actions (mike 555 mentioned this earlier). Create a new action:

NAME: "Open Nautilus FM here" (or whatever). 
COMMAND: [FONT="Courier New"]nautilus %f[/FONT]
Go to "Appearance Conditions" tab and check everything.

That's all. So now, I use PLACES, and my DIRECTORY MENU to get to where I want with Thunar, and once there, if I want the features in Nautilus, I can just right-click that custom action. I think this is 'safe' in terms of conflicts.

I made one to open as root also, just sub: [FONT="Courier New"]gksudo nautilus %f[/FONT]

or for Thunar as root: [FONT="Courier New"]gksudo thunar %f[/FONT]

more examples here: 

[http://thunar.xfce.org/pwiki/documentation/custom_actions](http://thunar.xfce.org/pwiki/documentation/custom_actions)


-NTL2009

---

### Post by celem on 2012-09-30
The "**Resize and email images**" custom action did not work for me as described at [http://thunar.xfce.org/pwiki/documentation/custom_actions]("http://thunar.xfce.org/pwiki/documentation/custom_actions")

I had to put quotes around $COLS here:
```
if [ -z "$COLS" ]; then
```

Also, the email command was not located as defined. I substituted some script from another program of mine and now it works correctly. My modified version of /usr/local.bin/thunar-resize-sendto is:
```

#!/bin/bash
#input to this is a list of files to send.
# depends on thunar, ImageMagick and Zenity
TMP=/tmp/thunar-pics
LOG=/tmp/thunar-resize-sendto.log
MARKER=/tmp/thunar-resize-sendto.marker
#SENDTO="/usr/lib/thunar/thunar-sendto-email"
SENDTOCMD=`grep Exec /usr/share/Thunar/sendto/thunar-sendto-email.desktop`
SENDTOEXEC=`echo ${SENDTOCMD:5}`
SENDTOEXEC=`echo ${SENDTOEXEC// %F/}`
SIZES="320x200 640x480 800x600 1024x640"
DISCMD="zenity --list --text=\"Select Size\" --checklist --column=Select --column=New --hide-header --print-column=ALL"
# Find unused tmp dir
if [ -e $MARKER ]; then
  CUR=$(cat $MARKER)
else
  CUR=1
fi
if [ 1 == $CUR ]; then
  CUR=0
else
  CUR=1
fi
echo "$CUR" >$MARKER
TEMP="${TMP}$CUR"
mkdir -p $TEMP
rm -rf $TEMP/*

for s in $SIZES; do
  if [ -z "$COLS" ]; then 
    COLS="$s "
  else
    COLS="$COLS 0 $s"
  fi
done
SIZE=$($DISCMD $COLS)
echo "CUR=$CUR SIZE=$SIZE" >$LOG

for f in "$@"; do
  n=$(basename "$f") 
  echo "item '$f'->$TEMP/$n" >>$LOG
  convert $f -resize $SIZE "$TEMP/$n"
  FILES="$FILES $TEMP/$n"
done
$SENDTOEXEC $FILES

```

---

