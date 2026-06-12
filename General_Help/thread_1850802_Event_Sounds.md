---
title: "Event Sounds"
date: 2011-09-27
forum: General Help
---

### Post by bestbets1 on 2011-09-27
Hi All (Again)

Sorry for the flood of questions recently(!) But this should be my last one for a while, then maybe I can do some learning myself. 

Anyway, how do you get the event sounds to play during logon, logoff etc in Kubuntu? I downloaded Canberra as suggested by Xubuntu, and sox plus gnome-audio and I can play the login/out sound found somewhere within the '/usr' directory. 
Sadly though, there are no options for these sounds, and I'd really like to hear them (there are even options for them in the appearance set of settings found in Settings Manager)

Is sound events really possible in Xubuntu?

---

### Post by seawolf167 on 2011-09-27
Login, logoff sounds should already be present under System -> Administration -> Sounds, then look for the Ubuntu System Sounds

---

### Post by Toz on 2011-09-27
> **bestbets1 said:**
> Hi All (Again)

Sorry for the flood of questions recently(!) But this should be my last one for a while, then maybe I can do some learning myself. 

Anyway, how do you get the event sounds to play during logon, logoff etc in Kubuntu? I downloaded Canberra as suggested by Xubuntu, and sox plus gnome-audio and I can play the login/out sound found somewhere within the '/usr' directory. 
Sadly though, there are no options for these sounds, and I'd really like to hear them (there are even options for them in the appearance set of settings found in Settings Manager)

Is sound events really possible in Xubuntu?

According to xfce developers, xfce doesn't have support for system sounds. See: [http://forum.xfce.org/viewtopic.php?id=5702]("http://forum.xfce.org/viewtopic.php?id=5702"). Since you've already tried downloading canberra, you've probably seen a number of the threads regarding possible workarounds (eg. [http://forums.debian.net/viewtopic.php?f=6&t=59522]("http://forums.debian.net/viewtopic.php?f=6&t=59522")). If you're using pre-11.10 (oneiric) you still have the flexibility to use GDM workarounds as per [http://ubuntuforums.org/showthread.php?p=3907604#post3907604]("http://ubuntuforums.org/showthread.php?p=3907604#post3907604"). In oneiric, gdm is replaced by lightdm and that functionality doesn't currently exist (or at least, I can't find it).

I currently have a login sound playing by creating a ~/.xprofile file, giving it executable permissions, with the following content:
```
canberra-gtk-play -f /usr/share/sounds/moblin/stereo/desktop-login.ogg
```(requires: libcanberra-gtk0 and moblin-sound-theme)

Since I'm currently testing 11.10, I've yet to find a way to play a logout sound.

---

### Post by bestbets1 on 2011-09-27
> **Toz said:**
> According to xfce developers, xfce doesn't have support for system sounds. See: [http://forum.xfce.org/viewtopic.php?id=5702](http://forum.xfce.org/viewtopic.php?id=5702). Since you've already tried downloading canberra, you've probably seen a number of the threads regarding possible workarounds (eg. [http://forums.debian.net/viewtopic.php?f=6&t=59522](http://forums.debian.net/viewtopic.php?f=6&t=59522)). If you're using pre-11.10 (oneiric) you still have the flexibility to use GDM workarounds as per [http://ubuntuforums.org/showthread.php?p=3907604#post3907604](http://ubuntuforums.org/showthread.php?p=3907604#post3907604). In oneiric, gdm is replaced by lightdm and that functionality doesn't currently exist (or at least, I can't find it).

I currently have a login sound playing by creating a ~/.xprofile file, giving it executable permissions, with the following content:
```
canberra-gtk-play -f /usr/share/sounds/moblin/stereo/desktop-login.ogg
```(requires: libcanberra-gtk0 and moblin-sound-theme)

Since I'm currently testing 11.10, I've yet to find a way to play a logout sound.

Thanks. Tried it in terminal, and got a skippy sounding file. I tried it with just the sounds I have in /usr/share/sounds/login.wav and got the following error message: 

"Murrine configuration option "gradients" is no longer supported and will be ignored."

Maybe I should report it as a bug in Xubuntu... Thats O.K. though.

---

### Post by Toz on 2011-09-28
> "Murrine configuration option "gradients" is no longer supported and will be ignored."

Go to your themes gtkrc file (/usr/share/themes/<theme>/gtk-2.0/gtkrc) and comment out the lines that have the "gradient" keyword in them.

What version of xubuntu are you using and which theme is your current theme?

---

### Post by bestbets1 on 2011-09-28
> **Toz said:**
> Go to your themes gtkrc file (/usr/share/themes/<theme>/gtk-2.0/gtkrc) and comment out the lines that have the "gradient" keyword in them.

What version of xubuntu are you using and which theme is your current theme?

I am using Xubuntu 11.04 Natty Narwhal and my current theme is NOX. I noticed that I'll need root permissions to save a copy of the file.
So do I just delete the 'gradient' part of a command or the whole command?-I don't want to mess anything up

---

### Post by Toz on 2011-09-28
Yes, you will need root privileges. I wouldn't delete anything, just comment out the affected lines by putting a **#** at the front of the line. (That way if you need to undo it, you can simply remove the #s)

Of course, if everything is working ok except for the error message, you could just ignore it.

---

