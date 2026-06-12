---
title: "Yet another 64-bit Flash video issue post"
date: 2011-04-18
forum: General Help
---

### Post by FMAnimus on 2011-04-18
Hey everyone,
First off, I want to say that I'm completely new to Linux and Ubuntu, and I am absolutely loving it so far. Everything has worked like a charm since installation, but I'm still having a nagging issue getting embedded Flash videos to work on any website in Firefox 3.6. I've tried downloading Adobe 10, extracting it to the .mozilla plugin folder, removing Gnash and SWF, unlocking the ubuntu-restricted-extras, re-installing Adobe, installing Flash Aid, and I've gotten it to where websites aren't telling me I'm missing plug-ins or that I'm running an out-of-date Adobe (hooray!). However, in Youtube, the video is just showing as a blacked-out window with nothing on it, and on other websites like failblog.com, the video player will pop up, however clicking on Play does nothing, and there is an "X" in the middle of the window where the "Play" icon is normally located.
 
I'm running on 64-bit, and if anyone needs system specs, I can provide them. I've spent the last 3 days scouring the boards for fixes for this, and so far, none have worked entirely. I'm hoping someone has another suggestion or has experienced this as well. Thanks for your time everyone, I'm really glad to join the community!

---

### Post by garvinrick4 on 2011-04-18
Close all firefox running and copy and paste these one at a time in terminal:
```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
``````
sudo rm -f /usr/lib/mozilla/plugins/*flash*
``````
sudo rm -f ~/.mozilla/plugins/*flash*
``````
sudo rm -f /usr/lib/firefox/plugins/*flash*
``````
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
``````
sudo rm -rfd /usr/lib/nspluginwrapper
``````
sudo apt-get clean
``````
sudo apt-get install flashplugin-installer
```Will work for 64-bit machines. If you are trying to run 64-bit Native beta from Adobe it is a bit different at install. Let me know.

---

### Post by garvinrick4 on 2011-04-18
64-bit native from Adobe download to Downloads from adobe:
Do all the removing as in previous post instead of apt-get install flashplugin-installer
do these commands: These will extract the .tar.gz and then put in right directorys:
rick@rick-HP:~$ cd Downloads
rick@rick-HP:~/Downloads$ ls  (that is a lower case L)
flashplayer10_2_p3_64bit_linux_111710.tar.gz
super_tux_wallpaper_linux-800x600.jpg
rick@rick-HP:~/Downloads$ tar zxvf flashplayer10_2_p3_64bit_linux_111710.tar.gz
libflashplayer.so
rick@rick-HP:~/Downloads$ sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 
rick@rick-HP:~/Downloads$ sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/

---

### Post by FMAnimus on 2011-04-18
Thanks a ton, I'm going to give that a shot here shortly.  I'm not running anything beta, I'm trying to utilize the Adobe "Square" for 64 bit Linux.

---

### Post by garvinrick4 on 2011-04-18
> **FMAnimus said:**
> Thanks a ton, I'm going to give that a shot here shortly.  I'm not running anything beta, I'm trying to utilize the Adobe "Square" for 64 bit Linux. Should have no problem I run it also and actually use less processer glut that I
get with the stable flash in repo's. It is called a preview release by Adobe.
Has been very stable for me.

---

### Post by 3Miro on 2011-04-18
Ubuntu-restricted-extras is the default way to install flash Under Ubuntu. It seems that you tried other alternatives first and those did not work. You may not be able to get flash working, until you undo those "other" things first. The first 7 commands in garvinrick4's post aim to do exactly that.

---

### Post by FMAnimus on 2011-04-18
Hey guys,
I did everything line for line, and I'm still seeing the same things.  I really appreciate the help thusfar.  Do you have any other suggestions?

---

### Post by marl30 on 2011-04-19
Try the flash-aid plugin. I'm using 64 bit and flash-aid ensures that the 64 bit flash version is installed, plus it does some tweaks that causes flash to run very smooth even when playing high def videos. 

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by garvinrick4 on 2011-04-19
> **FMAnimus said:**
> Hey guys,
I did everything line for line, and I'm still seeing the same things. I really appreciate the help thusfar. Do you have any other suggestions?
Which one are you trying to install the one in ubuntu repo's flashplugin-installer
or the 64 bit downloaded in tar.gz from Adobe? 
 
EDIT: just saw previous post flash aid might be easiest for you. And it does have the Native 64 bit also or flashplugin-installer in its script.
Your choice give it a go.

---

### Post by Foxcow on 2011-04-19
I find that native 64 bit flash runs better than the flash installer that comes bundled with Ubuntu Restricted Extras.


[http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)

---

### Post by FMAnimus on 2011-04-19
Just finished executing Flash-Aid, and everything's working now.  Sorry for cluttering up the forum with a question that's been asked a million times.  I really appreciate the help; this is easily the most helpful computer community I have ever been a part of.  Thanks again!

---

