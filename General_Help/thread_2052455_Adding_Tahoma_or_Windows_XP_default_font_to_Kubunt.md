---
title: "Adding Tahoma or Windows XP default font to Kubuntu 12.04"
date: 2012-09-03
forum: General Help
---

### Post by manuleka on 2012-09-03
I'm trying to find a way of installing Tahoma on to Ubuntu...

I've been fiddling around with a variety of Linux Distros and i notice that the fonts aren't as clear as Windows... 

I'm currently with Kubuntu 12.04.1 and running Windows XP on VM... i would really like to see the type of fonts Windows XP has on my Kubuntu Desktop

i came across this page:
[http://panic83.livejournal.com/19679.html](http://panic83.livejournal.com/19679.html)

but have no clue on how to apply the script or commands on terminal...

---

### Post by mastablasta on 2012-09-03
did you install kubuntu-restricted-extras package found in repository (use Muon to find& install it)?
 
it should include MS fonts.

---

### Post by manuleka on 2012-09-03
> **mastablasta said:**
> did you install kubuntu-restricted-extras package found in repository (use Muon to find& install it)?
 
it should include MS fonts.

yes i did, but Tahoma doesn't appear to be there... should it be in it?

---

### Post by ajgreeny on 2012-09-03
I suspect that the way you see fonts on your display is more related to the setup of your font display, and I have no idea how you can change that in Kubuntu, I'm afraid. Have a good search around the configuration options for the system similar to those in Ubuntu with gnome 2 (not sure about gnome 3 as I don't use it at the moment) See screenshot of gnome 2 options.

However to answer your question about the site you linked to you need to copy this:-
```
#!/bin/bash
[ ! -f /usr/share/fonts/truetype/msttcorefonts/tahoma.ttf -o ! -f /usr/share/fonts/truetype/msttcorefonts/tahomabd.ttf ] &&
wget [http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IELPKTH.CAB](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IELPKTH.CAB) &&
cabextract -F 'tahoma*ttf' IELPKTH.CAB &&
mkdir -p /usr/share/fonts/truetype/msttcorefonts/ &&
mv -f tahoma*ttf /usr/share/fonts/truetype/msttcorefonts/ &&
chmod 644 /usr/share/fonts/truetype/msttcorefonts/tahoma* &&
fc-cache -v &&
rm -f IELPKTH.CAB &&
echo "Installed Tahoma" 

```to a text editor and save it as font.sh in your home.  Now make it executable with command ```
chmod +x font.sh
```You can now double click it to run it in terminal (or you can in gnome, not sure about KDE) and it should install tahoma for you.  If double clicking it in your file manager does not run it or even give you the option to do so, open a terminal and use command ```
/home/$USER/font.sh
```

PS:  I have no idea if this script works, as I have not tried it having already got tahoma.ttf on my system.  I have no idea where it came from, but I do have the msttcorefonts installed, so it could be from there, but I also have many fonts from old windows applications that I think I copied across many years ago.  However I reiterate my comment about font rendering that I made at the start of this post; do search around to see if yu can improve the looks of your current fonts.

---

### Post by manuleka on 2012-09-03
thanks ajgreeny :)

now i have tahoma... and yet it still doesn't look at nice on Kubuntu as Windows... When i was using Mint i quite like the interface and layout... i changed to Kubuntu because i find the Ubuntu Forum to be more promptive and helpful in assisting me as a learner on Linux

Now i just feel like falling back to LinuxMint...

---

### Post by black veils on 2012-09-03
maybe try this: ```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

```

here is the source: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

it has some MS fonts

i would think you must have this installed already, or you wouldnt be able to play dvds etc (?)

---

### Post by black veils on 2012-09-03
as for smoothness of your fonts, you need to alter anti-aliasing

---

### Post by manuleka on 2012-09-03
> **black veils said:**
> as for smoothness of your fonts, you need to alter anti-aliasing

thanks... i think it's more of the coloring that would help make the fonts a bit more clearer - not too sure, but am going through the themes/icons/color settings and see if i can come across something that would help

cheers

---

