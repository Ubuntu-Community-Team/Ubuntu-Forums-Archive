---
title: "Grub Background Image Help"
date: 2010-05-24
forum: General Help
---

### Post by UbuNoob001 on 2010-05-24
Hi all,
    I am trying to make an image to use as background on Grub as per [HTML]https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming[/HTML] 

I edited the beginning of  ***/etc/grub.d/05_debian_theme  ***from the first to the second "code quote" as below. 

Question: I am still recieving the same standard Grub screen (black background w/ white text). What else do i need to change in that file? 

Original ```
source /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"
  COLOR_NORMAL="black/black"
  COLOR_HIGHLIGHT="magenta/black"
```

to 

 ```
source /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
  WALLPAPER="/usr/share/images/grub/Apollo_17_The_Last_Moon_Shot_Edit1.png"
  COLOR_NORMAL="black/black"
  COLOR_HIGHLIGHT="magenta/black"
```

Many thanks

---

