---
title: "Movie preview"
date: 2010-08-30
forum: General Help
---

### Post by aceofblackstar on 2010-08-30
I have  a ton of movie clips I saved on my hard drive.  They are usually .wmv and .mpg
The problem I am having is that I am unable to preview them. I have to click on them to see what they are.  All I get is a film Icon.  


 Ubuntu 10.04 LTS  - the Lucid Lynx
Default movie player is: Totem Movie Player 2.30.2

Thanks

---

### Post by rollin on 2010-08-30
Welcome to the forum!
I can't give an expert technical response, however from experience I can say that if you open a wmv file in totem it should prompt you to install some plugins. 
I usually get experience this when I play mp4s on a new install. Once the plugins are installed you get the small window I think you are looking for. 
If you're struggling keep posting and I'm sure we can get it fixed :)

---

### Post by Autodidact on 2010-08-30
Take a look at:
[http://ubuntuforums.org/showthread.php?t=432529](http://ubuntuforums.org/showthread.php?t=432529)

---

### Post by aceofblackstar on 2010-08-30
Thanks
The following sequence worked.
:)

sudo apt-get install libxine1-ffmpeg 

     rm -r $HOME/.thumbnails/fail
rm -r $HOME/.thumbnails/normal
killall -9 nautilus

---

