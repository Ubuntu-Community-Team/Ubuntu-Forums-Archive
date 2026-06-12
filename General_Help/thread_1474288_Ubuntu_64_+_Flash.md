---
title: "Ubuntu 64 + Flash"
date: 2010-05-05
forum: General Help
---

### Post by Tanner2007 on 2010-05-05
Myspace:

-Online now friends list dont show when I click instead shows all friends

Myspace built-in IM half the time does not
-make a sound
-show my messages to/from people
-opens more than 1 depending on how many tabs you have which never happens on windows or macs
-sometimes wont even open
-etc

Megavideos:
-I have to click, move, or close and reload it 100 times just to make the movie start and by then it wont even work some of the time

youtube:
same as megavidoes

All video sites:
Just randomly get grayed out where the flahs player shoudl be at nothign shows, ex, youtube, megavidoes,hulu, etc 


I have ubuntu 64 bit and have flash 10 I got off this site right here

[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html#comment-150888](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html#comment-150888)

Basically my flash on my ubuntu is on crack and very very unstable no matter how many times i uni-stall it and reinstall it it does the stuff I posted above + more I can't even remember 

what can i do? this is making it hard for me to browse the internet 

Please help thanks

---

### Post by Tanner2007 on 2010-05-05
Also to add on, i have dual screens lets say its on my primary screen a video of youtube, and I click full screen, it goes to the other screen and makes the entire thing full screen with black but the video its self size dont change and the seek bar is stretched across screen

---

### Post by mscout2004 on 2010-05-05
Tanner I had the same problems with flash so I followed the guide here  [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591) and it works fine now.

---

### Post by mscout2004 on 2010-05-05
Make sure you parse all old versions first like it says and have the right version of firefox.

---

### Post by McMichael96 on 2010-05-05
Flash doesn't work well on Ubuntu or Linux for that matter... It don't work well on Mac OSX or really any *nix OS. I think they should strip out flash from everything and replace it with HTML5. You can watch most YouTube videos in HTML5 (HTML5 Works great on pretty much any *nix OS) Just go to [http://youtube.com/html5](http://youtube.com/html5) and click on "Join HTML5 Beta" or "Join Beta"

---

### Post by WinterRain on 2010-05-05
> **McMichael96 said:**
> Flash doesn't work well on Ubuntu or Linux for that matter... It don't work well on Mac OSX or really any *nix OS. I think they should strip out flash from everything and replace it with HTML5. You can watch most YouTube videos in HTML5 (HTML5 Works great on pretty much any *nix OS) Just go to [http://youtube.com/html5](http://youtube.com/html5) and click on "Join HTML5 Beta" or "Join Beta"

Flash works fine if you get the right version. Even full screen flash works great for me.

Remove any flash you have installed, and get the 64bit flash file here [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

Then extract it and put it in /usr/lib64/mozilla/plugins and restart firefox. Works perfect for me.

If you are unsure how to do this, to extract the file, just right click and "extract here". Make sure it's on your desktop. Then do in terminal: (you can copy and paste it)
```
sudo cp ~/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins
```
Restart firefox, done.

---

### Post by Linuxforall on 2010-05-05
If you are installing x64 flash, make sure to remove nspluginwrapper if its still installed.

---

### Post by Tanner2007 on 2010-05-08
Sorry guys none of this is working, I unistalled flash and did it the way as on the amd64 post, and sites saying they have flash 64 bit limitation, so I had to redo that guide again  on the first post of mine and unistalled nspluginwrapper again and nothing full screen on youtube and etc still dont even work

---

