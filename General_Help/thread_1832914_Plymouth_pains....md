---
title: "Plymouth pains..."
date: 2011-08-25
forum: General Help
---

### Post by Aurauxis on 2011-08-25
Hello everyone! I just came by to seek for help on some problems am a currently facing. For unknown reasons, Plymouth appears to have messed up a bit. For the sake of keeping things simple, it looks a bit like this: 
[ATTACH]200767[/ATTACH]
Yeah, I "gimped" the image to look like what it does while booting. I believe its a first. I have nothing even remotely "KDE" on my system yet I have that weird Kubuntu. I've tried the ugly boot fix script, different themes, but I just can't seem to change it. The boot log files weren't any good either. Looking at the real thing almost hurts my eyes and really irritates me for some reason. What do you suggest I do?
P.S. I am not a beginner. I am fairly experienced and couldn't really find a better place to start this thread.
UPDATE:[ATTACH]200768[/ATTACH][ATTACH]200769[/ATTACH] After rummaging through a pile of trash from the dodgy corner of my sister's room, I was able to retrieve a dusty old 3 MP camera. We can clearly see (sort of) the abnormal colors and logos appearing on the display before our very own eyes.

---

### Post by Aurauxis on 2011-08-26
(bump!)
Could someone please help?

---

### Post by Aurauxis on 2011-08-28
Final bump, and I will stop about there.

---

### Post by Aurauxis on 2011-08-29
(sigh!)
Okay... bye. I'll keep this thread subscribed so if anyone had any ideas...

---

### Post by HarrisonNapper on 2011-08-29
I believe there's a plymouth config application in the repos. Another thing that might be worth doing is to dpkg-reconfigure plymouth, but I haven't ever tried doing that to plymouth, so hopefully we'll get someone to ditto that strategy as something that is safe to do. I don't see anything wrong with it and it might be worth a try anyway, but possibly disastrous.

---

### Post by stinkeye on 2011-08-29
I don't know what you have done but you may find a solution [**_[COLOR="DarkRed"]here[/COLOR]_**]("http://www.khattam.info/howto-change-ubuntu-pinkpurple-plymouth-boot-screen-to-any-color-you-like-2010-11-09.html#comment-108482029").
I used this Howto to change the Plymouth background to black.

---

### Post by F.G. on 2011-08-29
so, i had a problem with my dad's laptop where the screen would go green randomly, and often during boot. it was (still is) a hardware issue and it goes away with some jiggling of the power supply, or opening and closing the lid fixes it. i mention it because it looks just like your pictures.

---

### Post by Aurauxis on 2011-08-30
Thank for all the help.
Stinkeye's solution has gotten me somewhere. Editing a few conf. files manually allowed me to change it back to the Ubuntu Text (it looks much brighter and pinkier than usual but were at least getting somewhere). I still haven't been able to get a graphical boot working.

---

### Post by stinkeye on 2011-08-30
This is the fix I used for displaying text instead of logo.

gksudo gedit /etc/default/grub

add the line
```
GRUB_GFXPAYLOAD_LINUX="[COLOR="Magenta"]1680x1050[/COLOR]"
```
using your [COLOR="magenta"]native desktop resolution[/COLOR]

then run
```
sudo update-grub
```

---

### Post by Aurauxis on 2011-09-01
I don't think that did anything. It all looks the same. Note that my operating system is on an external hard drive and I carry it with me to other desktops that have different monitor resolutions.

---

### Post by stinkeye on 2011-09-01
Try 800x600

---

### Post by Aurauxis on 2011-09-13
Hmmm...

---

### Post by fractalman on 2011-09-13
not sure if this thread will help....  i used the application 'start up manager' and fixed my plymouth  see post #9

[http://ubuntuforums.org/showthread.php?t=1742944](http://ubuntuforums.org/showthread.php?t=1742944)

---

### Post by oldos2er on 2011-09-13
Thread moved to General Help.

---

### Post by Aurauxis on 2011-09-14
I have Startup Manager already. It appears that this is some sort of glitch. Perhaps some sort of a reset will be able to fix the issue. Apologies for being a pain.

---

### Post by Aurauxis on 2011-09-25
(bump!)
Any way I could reset Plymouth or something? Maybe its a driver issue.

---

### Post by Aurauxis on 2011-09-29
Come on...

---

### Post by stinkeye on 2011-09-29
Eileen?

---

### Post by oldos2er on 2011-09-29
Have you searched launchpad.net for any relevant bugs? If you can't find anything there I suggest you file a bug yourself. Unfortunately the forums don't always provide answers 100% of the time.

---

### Post by stinkeye on 2011-09-29
You could try reinstalling 
```
plymouth-theme-ubuntu-logo
```
in synaptic.

or

try some other themes
search in synaptic for
```
plymouth-theme
```

After you install a theme run
```
sudo update-alternatives --config default.plymouth
```
to choose your default theme


and then run
```
sudo update-initramfs -u
```

---

### Post by Aurauxis on 2011-10-06
I have tried a reinstall. I will file a bug soon. But I run 10.10 which is outdated no?

---

### Post by oldos2er on 2011-10-06
10.10 is supported until April 2012.

---

### Post by Aurauxis on 2011-10-30
No good... still.

---

