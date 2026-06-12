---
title: "Hoary array 6, ATI Radeon 9800 SE, X.org and Alsa"
date: 2005-03-06
forum: General Help
---

### Post by b_west on 2005-03-06
I'm fairly new to Linux, love Ubuntu and tend to be able to find what I need when I have a problem, but this is one of the rare times I must make a post -- and hopefully it may assist someone else as well.

I'm using Hoary from the Array 6 CD download (gnome;2.6.10-4-386 kernel) and have two major problems:

I have an ATI Radeon 9800 SE video card with 128 MB -- but I can't seem to get direct rendering to activate. As such all interactive 3d environments are choppy and unusable.

I've tried all the work-arounds I could find in the Ubuntu forums and elsewhere. Nothing worked until I found the vanilla solution in the post at the following address:

[http://www.linuxquestions.org/questions/history/294150](http://www.linuxquestions.org/questions/history/294150) 

While the America's Army gameplay was awesome :) , problem two arose -- the sound would not initiate with the game --except on rare occasions immediately after reboot. :-? 

I tracked this to the difference between OSS and Alsa mixers. Alsa was installed but wouldn't mix the sound between the desktop and the game and, thus, no in game sound. I figure initiating the game before the desktop took sound control were the only times it would work in gameplay.

It was during the Alsa troubleshooting that I just really screwed things up and finally opted to........ reinstall -- no big deal 'cause it was a new install anyway and I could just repeat the vanilla for the fglrx functionality... right?

I've now spent a whole day just trying to duplicate whatever I had done before to absolutely no success. I've gone through how-to after how-to, mixed processes, used the vanilla, used synaptic, configured XFree86 and copied information into xorg.conf.... and to no avail. ](*,) 

Here's are of SOME of the how-to's I've tried:
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto) 
[http://ubuntuforums.org/showthread.php?t=15990&highlight=ati+driver+install](http://ubuntuforums.org/showthread.php?t=15990&highlight=ati+driver+install) 
[http://ubuntuforums.org/showthread.php?t=3567&highlight=ati+driver+install](http://ubuntuforums.org/showthread.php?t=3567&highlight=ati+driver+install)
[http://ubuntuforums.org/showthread.php?t=13226&highlight=ati+driver+install](http://ubuntuforums.org/showthread.php?t=13226&highlight=ati+driver+install) 
[http://www.stanchina.net/~flavio/debian/fglrx-installer.html](http://www.stanchina.net/~flavio/debian/fglrx-installer.html) 

I've spent so much time and gone through so many how-to's I'm desperate and I've got no problem with reinstalling if necessary.

Thanks to all who reply!

(I apologize if this is a double-post -- I saw the content of the forums and realized my original post may have been placed wrong.)

---

### Post by b_west on 2005-03-06
I've got a full workaround in the forums at the following address

[http://ubuntuforums.org/showthread.php?t=18343](http://ubuntuforums.org/showthread.php?t=18343)

Best of luck to ya!

---

