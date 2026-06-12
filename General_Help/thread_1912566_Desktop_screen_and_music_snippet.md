---
title: "Desktop screen and music snippet"
date: 2012-01-20
forum: General Help
---

### Post by Silvernail on 2012-01-20
When Ubuntu's desktop screen appears the is a short snippet of music played. I would like to change that. 

On this forum, what words do I search for to see if its been done before.

Thanks
D

---

### Post by Silvernail on 2012-01-21
I still don't know what words to search for but I stumbled upon the answer to my needs.
On my labtop, I have installed 11-10. It has an elk as a choice for the desktop background. The login sound bite did not fit with the image. I wanted an elk bugling.

If you will look here:
```

/usr/share/gnome/autostart/libcanberra-login-sound.desktop

```
It will show you that 'desktop-login' is the name of the sound bite.
```

[Desktop Entry]
Type=Application
Name=GNOME Login Sound
Comment=Plays a sound whenever you log in
Exec=/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
OnlyShowIn=GNOME;
AutostartCondition=GNOME /desktop/gnome/sound/event_sounds
X-GNOME-Autostart-Phase=Application
X-GNOME-Provides=login-sound

```
The sound bite 'desktop-login' can be found here:
```

/usr/share/sounds/ubuntu/stereo/desktop-login.ogg

```
I downloaded a mp3 file of an elk bugling. Converted it to an 'ogg' file and renamed it to a short name. And placed it in the same directory as 'desktop-login.ogg'. Substituted the new name without the 'ogg' extention in 'libcanberra-login-sound.desktop' for 'desktop-login'.
Voila!

Use this if needed:
```

#!/bin/bash

## A Simple Bash Shell Script to Convert MP3s to Ogg Vorbis
## Submitted by rdjere on Mon, 01/09/2012
## @ http://djere.com/node/189

# The 2 lines below declare variables that store file names.
declare inputFileName
declare outputFileName

# Prompts user and reads file names
echo "Enter the input file name:"
read inputFileName
echo "Enter the desired output file name:"
read outputFileName

# Change the line below to reflect the directories where you keep the mp3 files that you want to convert
# and the resulting ogg files.
mpg321 /home/rdjere/mp3s/$inputFileName.mp3 -w raw && oggenc raw -o /home/rdjere/oggs/$outputFileName.ogg

```

---

