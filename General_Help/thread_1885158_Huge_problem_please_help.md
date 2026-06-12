---
title: "Huge problem please help"
date: 2011-11-22
forum: General Help
---

### Post by esg10 on 2011-11-22
I have Ubuntu 11.10 installed in my Computer. 

But, I really want to delete Ubuntu due to the fact that it does not play dvd s or Cds I always get an error for a cd. 

For DVD I get a blank cd rw. 

Most Cd's and DVDs I have burnt myself, But I have noticed that commercial cd's don't even get read. 

I have everything updated in my computer ... libdvdcss latest versions have tried all versions...

All I want is to be able to Watch a DVD AND Listen to MUSIC in UBUNTU. And I'm also a total Noob. I was told that Linux is better. And it sure is but this just kills it. I want to watch dvd and cds... please help me out. I have done everything I can and searched everywhere to fix this. = (

---

### Post by Hugh971 on 2011-11-22
Hello and welcome to Ubuntu Forums!

Ubuntu will not play DVDs out of the box as you have to use non-free codecs. Fortunately it is easy to enable it. Try running through the instructions in this guide.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by JC Cheloven on 2011-11-22
Hi again, esg10. Playing music cd's shouldn't be a problem. Let's see what we can do...

First, please see if my later answer to your previous post [here]("http://ubuntuforums.org/showthread.php?p=11481312#post11481312") is of any help.

Aditionally: your audio cd should be accesible to media players on /dev/cdrom. So try opening your media player and try to open that location within the options/menus the media player gives you. 

For example I use the VLC media player. In it, I can navigate to "media-> open disk", choose "audio cd" from there, and press play.

Hope this helps

EDIT: I also play commercial dvd's with VLC. If you have installed the medibuntu repository, and the packages libdvdread4 and libdvdcss2 (you said you have), you should find your dvd similary, under /dev/dvd. If dvd menus broke things (sometimes do), choose to "open without dvd menus".

---

