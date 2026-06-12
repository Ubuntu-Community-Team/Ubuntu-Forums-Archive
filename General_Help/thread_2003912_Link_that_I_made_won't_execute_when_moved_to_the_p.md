---
title: "Link that I made won't execute when moved to the panel(gnome2)"
date: 2012-06-14
forum: General Help
---

### Post by p3aul on 2012-06-14
I created a script to to pass two file names to ffmpeg in order to extract the audio from the video: The script works fine and I usuall run it from a directory were I have a flv file I want to strip the audio from. It places the audio created in the same directory as the flv file. I wanted to be able to run it from the top panel in gnome 2 so I createwd a link and drug it to the panel. Now when I click on it it wont run. I get this error:

---

### Post by p3aul on 2012-06-14
I forgot! Here is the script:
```

#!/bin/sh
echo Enter full input file name
read I
echo Enter full output file name
read O
ffmpeg -i "$I" -vn -f wav "$O"
```

---

### Post by mc4man on 2012-06-15
I don't have or use gnome2 anymore so not sure what you mean by 'linked'
What you want is a launcher (.desktop) that runs your script in a terminal.

so if using gnome2 there should be a r. click on the desktop option, 'create launcher' or something like that. If so then set the command as either /path/to/scriptname or just scriptname if it's in a bin in your path
Pick an icon, name, & choose 'run in terminal' 

Otherwise just create a .desktop, save, right click on > properties > permissions & set as executable,  then drag on to panel ( you can then dispose of the .desktop as you choose

```
gedit ~/Desktop/flv2wav.desktop
```
Here's a basic launcher, edit blue to whatever you want, adjust red to match your scriptname if in a bin folder in your path or do a full path to scriptname, ect
```
[Desktop Entry]
Type=Application
Version=1.0
Terminal=true
Icon=[COLOR="Blue"]/usr/share/icons/hicolor/scalable/apps/nautilus.svg[/COLOR]
Name=[COLOR="Blue"]Flv2Wav[/COLOR]
Comment=[COLOR="Blue"]extract audio from flv[/COLOR]
Exec=[COLOR="Red"]flv2wav[/COLOR]
```

---

### Post by p3aul on 2012-06-15
Mc4man:
I guess I'm just dense, but I can't make sense of your post.
I've created the launcher, it just won't do anything. It should open a terminal and ask for input. Here is one that does just fine. I can't see the difference.

```
#!/bin/bash
echo "*** Converting between the different temperature scales ***"
echo "1. Convert Celsius temperature into Fahrenheit"
echo "2. Convert Fahrenheit temperatures into Celsius"
echo -n "Select your choice (1-2) : "
read choice
 
if [ $choice -eq 1 ]
then
    echo -n "Enter temperature (C) : "
    read tc
    # formula Tf=(9/5)*Tc+32
    tf=$(echo "scale=2;((9/5) * $tc) + 32" |bc)
    echo "$tc C = $tf F"

elif [ $choice -eq 2 ]
then
    echo -n "Enter temperature (F) : "
    read tf
    # formula Tc=(5/9)*(Tf-32)
    tc=$(echo "scale=2;(5/9)*($tf-32)"|bc)
    echo "$tf = $tc"
else
    echo "Please select 1 or 2 only"
    exit 1
fi
echo -n "
-->  Press any key to exit "
read echoice

exit 0
```

---

### Post by mc4man on 2012-06-15
"I've created the launcher, it just won't do anything"
A launcher is a .desktop file, so if you actually created a launcher then - 
open gedit, drag & drop your 'launcher' in to the gedit window & post the contents

---

### Post by p3aul on 2012-06-16
Ahh, this has been such a hassle to get working I just put the sh file in my nautilus-scripts folder. Now all I have to do is right click in the dir that my flv is located and choose the sh file. This work pretty well.
Thanks for your help!
Paul

---

