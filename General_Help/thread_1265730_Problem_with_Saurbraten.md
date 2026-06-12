---
title: "Problem with Saurbraten"
date: 2009-09-13
forum: General Help
---

### Post by BubbaBlues on 2009-09-13
While playing Saurbraten , in the middle of the game it just freezes. My whole system just freezes and I can't do anything except reboot. Then everything is fine for a few minutes and then Bam! Freeze!  I wondered if anyone else has experienced this or has any idea why.  I have a gaming graphics card. Nvidia 9 series. and an athlon 64 4800 dual core.
:confused:

---

### Post by whitethorn on 2009-09-13
Have you tried installing newer nvidia drivers from their webpage?  I also had a problem similar to yours, it got a lot better after I installed the drivers, problem is with every kernel update you need to reinstall the drivers ...  Or keep using the old kernel.  

Another thing you might want to try, I haven't tried it yet cause so I don't know if it'll work (I just read about it).  Next time your pc freezes, Hold alt and printscreen and press "r"  which should release you keyboard from the x server, then crtl alt F1 to get into the terminal,

then log in, and either 

```
sudo reboot
```

or

```
sudo /etc/init.d/gdm restart
```

Which should restart your X server.  If nothing works  Hold alt + printscreen and press the following letters  with a couple seconds in between,  r e i s u b (busier backwards).  It's kinda like a low level reboot safer for you pc then holding the power button.

---

### Post by BubbaBlues on 2009-09-14
I don't think that is the problem because I was using PCLinux OS for a long time and I played Saurbraten all the time with no problems at all. But now that I'm using Ubuntu again, I installed the game and the whole game has a different look and feel, which is no big deal, I can get used to that but it just won't keep running.:confused:

---

### Post by whitethorn on 2009-09-14
Are you using compiz?  I had an issue with compiz and playing in fullscreen.  There's an option to play in a window which might help. What version of sauerbraten are you playing?  Trooper edition?

---

### Post by BubbaBlues on 2009-09-15
Whatever is in the Ubuntu repo. I installed with synaptic. I don't know how to get any other version. 
Oh and thanks for the reply!!

---

### Post by juancarlospaco on 2009-09-15
kill gnome-screensaver and then run the game

---

### Post by Rhubarb on 2009-09-15
> **BubbaBlues said:**
> Whatever is in the Ubuntu repo. I installed with synaptic. I don't know how to get any other version. 
Oh and thanks for the reply!!

You can always get the latest version of [sauerbraten]("http://www.sauerbraten.org/") from here:
[http://www.cubeengine.com/files.php4](http://www.cubeengine.com/files.php4)

As some others have said here, I recommend that you disable your screensaver, and turn compiz off (System --> Preferences --> Appearance --> effects tab, and select none).  Then sauerbraten should run fine for you.

---

### Post by BubbaBlues on 2009-09-15
Thanks everyone, I took it out of full screen mode and after an hour of play, NO PROBLEMS!  Now I'm groovin' again.:guitar:

---

### Post by whitethorn on 2009-09-15
You should download the newer version, all you need to do is unpack it to wherever.  cd to the folder and 

./unix_sauerbraten

The graphics are better and some different models.

---

