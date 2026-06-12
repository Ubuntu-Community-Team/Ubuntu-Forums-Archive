---
title: "Installed software now computer wont boot"
date: 2009-07-03
forum: General Help
---

### Post by gunnerjamesr on 2009-07-03
I recently installed some applications from [http://cantthinkofa.com/platforms/linux/remuxing-mkv-for-the-xbox-360.html/comment-page-1](http://cantthinkofa.com/platforms/linux/remuxing-mkv-for-the-xbox-360.html/comment-page-1) which lets you convert .mkv file to mp4 or something, but thats going off subject.  Anyway after installing the programs i restarted my computer as it said to do but now it wont start up properly.  It goes through all the usual processes and just before it gets to the screen where you enter your user name and password a little timer comes up and just stays there.  Then the only thing i can do is shut the computer down by holding the button.

Is there anyway of fixing this problem like removing the applications?

Thanks

---

### Post by DeMus on 2009-07-03
> **gunnerjamesr said:**
> I recently installed some applications from [http://cantthinkofa.com/platforms/linux/remuxing-mkv-for-the-xbox-360.html/comment-page-1](http://cantthinkofa.com/platforms/linux/remuxing-mkv-for-the-xbox-360.html/comment-page-1) which lets you convert .mkv file to mp4 or something, but thats going off subject.  Anyway after installing the programs i restarted my computer as it said to do but now it wont start up properly.  It goes through all the usual processes and just before it gets to the screen where you enter your user name and password a little timer comes up and just stays there.  Then the only thing i can do is shut the computer down by holding the button.

Is there anyway of fixing this problem like removing the applications?

Thanks


```
Reboot the computer
```
When you come at the GRUB menu choose the second option: Failsafe mode
```
Log in
``` (when possible of course)

Then type:
```
sudo apt-get update && sudo apt-get remove mkvtoolnix bbe mplayer normalize-audio mpeg4ip-server
```

This should uninstall what you have installed from the website you mentioned.

Hopefully it is enough to get rid of the stuff which is blocking your computer to boot normally.

---

### Post by gunnerjamesr on 2009-07-03
Hi, I tried doing as you said but I'm afraid it still doesn't want to start properly.  Not sure what's wrong with it.

---

### Post by philcamlin on 2009-07-03
try booting into safe mode or whatever its called in ubuntu 

[http://ubuntuforums.org/showthread.php?t=915948](http://ubuntuforums.org/showthread.php?t=915948)

---

### Post by philcamlin on 2009-07-03
> **Clearence said:**
> Yes philcamlin is right.

I had the same problem but fixed it by restarting the system in safe mode.  ):P


thanks :) and its called failsafe not safe mode for anyone who wants to know :D :popcorn:

---

### Post by moster on 2009-07-03
If you need to convert videos in some standard formats, you should look at this app. I do not know much easier GUI solution :)
[http://handbrake.fr/]("http://handbrake.fr/")

---

