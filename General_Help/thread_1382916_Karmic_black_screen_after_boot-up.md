---
title: "Karmic: black screen after boot-up"
date: 2010-01-16
forum: General Help
---

### Post by FrankVdb on 2010-01-16
Hello everyone,

I've got a problem.

My Dell XPS M1330 laptop suddenly won't boot properly any longer. It boots up until after the Ubuntu sound, after that the screen goes black. I can't find any information about this particular problem.

I do have the impression that everything works (wireless network, sound) but the screen remains black. In the terminal I can access my hard drive, so the drive is ok.

I remember having played around with Compiz settings (using the settings manager) before closing down my system. My system closed down properly.

I have tried to dpkg-reconfigure xorg.conf in a terminal but it says that xorg.conf is not installed... I'm stunned.

Is there anyone who could help me? 

Thanks!

---

### Post by FrankVdb on 2010-01-16
Sorry, made a mistake. Obviously, it's xserver-xorg that needs to be reconfigured and not xorg.conf...

However, when I do a
sudo dpkg-reconfigure xserver-xorg
I don't get the chance to go through the settings, the terminal just sends me to the next line without any message!

---

### Post by ajgreeny on 2010-01-16
Try disabling compiz if you can get to anything on screen.

First try right clicking on the desktop and choosing Change desktop background.  Go to the Visual Effects tab and choose None.  If that is not possible, try Alt+F2 to see if a run dialog box appears. If so type metacity --replace then logout and login again to restart x.

If you can not get anything to show on screen, I don't know how you can disable compiz, other than sudo apt-get remove compiz but that's a bit of a sledgehammer to crack a wallnut, when I'm sure it must be possible to set the configuration in the cli if necessary.

By the way, that reconfigure command has been deprecated since ubuntu 8.10, I think, if not 8.04, and does not do anything any more.  If you write an appropriate xorg.conf it will be read and used by the system, but there is no such file in the default system any more.  Not very helpful in many cases but true, I'm afraid.

---

### Post by FrankVdb on 2010-01-17
metacity --replace in the terminal gives me an error:
Windowmanager error: Unable to open X display

Thanks for your info about xorg, I didn't know reconfiguring is no longer possible...

Removing compiz is indeed a bit drastic, I'll try to find another solution before I remove compiz.

Thanks for your help.

---

### Post by john newbuntu on 2010-01-17
Since you have a minimum OS and an apparent network connection, can you at least run "sudo apt-get install ubuntu-desktop"

---

### Post by FrankVdb on 2010-01-17
Got it sorted out, finally... 

It seems to be an nVidia problem with one of their drivers (version 185).

I found the solution here:
[http://ubuntuforums.org/showthread.php?t=1349553](http://ubuntuforums.org/showthread.php?t=1349553)

I had to revert to the default Karmic driver because the recommended nVidia driver (version 185) has a bug.

Now, I installed Karmic almost two months ago and never had a problem so I was stunned as to how this driver should suddenly cause problems. I was using Compiz as well, never had any problem. Was in Iceland last week for my work and there my laptop crashed. I was pissed to say the least...

This thing was driving me crazy. I thought it was a hardware issue. This is a problem laptop although it was not exactly cheap. It's a Dell XPS M1330 laptop has had its motherboard replaced because of overheating. In my dreams I was already spending an hour on the telephone again trying to get helped by the suckers at Dell. 

Obviously, my problem is not solved yet. I can no longer use either nVidia driver (173 or 185). Both are giving me the black screen.

Guess I'll have to look for a driver that does work properly.

---

### Post by FrankVdb on 2010-01-17
Ok I'm good again...

I installed the latest nVidia driver following this guide:
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

The version I installed is version 190 but the Gnome hardware driver interface claims that I'm on version 173 and is not even mentioning 190... 

Yet my system works again...

Thanks for your input guys!

---

