---
title: "Shutdown issue"
date: 2006-02-22
forum: General Help
---

### Post by theironbadger on 2006-02-22
I don't know what I did but now I am having issues shutting down my computer.  I get a blank screen and sometimes I have to shut off the power to stop it.  This also happens when I go to restart Gnome.

Recent changes:  Used Automatix to install several things
                        Trying to get mouse pad to scroll, altered xorg.conf a bit
                        
Anyone have any ideas what I might have done?
(by the way, still no luck getting it to scroll)

---

### Post by Xian on 2006-02-22
[QUOTE=theironbadger]
Recent changes:  Used Automatix to install several things
                        Trying to get mouse pad to scroll, altered xorg.conf a bit
                        
Anyone have any ideas what I might have done?[/QUOTE]

Can you recall what you altered??

---

### Post by hod139 on 2006-02-23
Not a solution, but I also have this problem lately (on my laptop).  Sometimes it turns off, sometimes it doesn't.  I haven't had the time to investigate the problem, but at least I can confirm it.  I'm interested to hear if this a common recent problem.

---

### Post by theironbadger on 2006-02-23
Actually, the problem started before I tried to fix the touchpad.  So I think that Xorg.conf might not be to blame.  I believe that it happened almost immediatly after I installed the nVidia drivers with Automatix....  I'll try to find what else I installed with it and post it.

EDIT:  Here is the list installed with Automatix:
Firefox Plugins|Ctrl-Alt-Del|DVD Ripper|Mplayer with plugin|Bittorrent Clients|F irestarter|NVIDIA cards|Firefox 1.5.0.1

Media Players

I have uninstalled Azereus, Firestarter and Mplayer with plugin as they didn't work very well.

Other installs:  Skype, aMSN (hoping to get webcam to work in linux...)

---

### Post by Sp@z on 2006-02-23
This will have to do with the Nvidia drivers. I experianced the SAME issues you are having. What Video card are you running? I had a 5700 Ultra, and a couple of ppl with that card had simular issues. AFAIK it was never resolved.I ended up going BACK to the 7667 drivers. Even though my computer still would not shut down, it at least stopped all the running processes and when I restarted I didn't have to fsck everytime. Good Luck, sorry I have no solution, and I am not sure it is a bug as much as a hardware issue.

---

### Post by theironbadger on 2006-02-23
I thought so, I have G-Force FX 5200 I believe...  could you point me to somewhere I could go to get some help getting the drivers killed?

---

### Post by hod139 on 2006-02-23
I don't think it has to do with the Nvidia driver, since I have an ATI mobility Radeon X300, using the latest ATI drivers which I installed using [http://ubuntuforums.org/showthread.php?p=423589](http://ubuntuforums.org/showthread.php?p=423589).

---

### Post by Sp@z on 2006-02-23
[QUOTE=hod139]I don't think it has to do with the Nvidia driver, since I have an ATI mobility Radeon X300, using the latest ATI drivers which I installed using [http://ubuntuforums.org/showthread.php?p=423589](http://ubuntuforums.org/showthread.php?p=423589).[/QUOTE]
As for my case it was DEFINATLY the Nvidia driver...and the FX5xxx series. Ran great till I installed the nvidia drivers, and the Nvidia forums also confirmed the issue. I peronally also lean towards the Idea of it being an openGL setting that is enabled when updating drivers. I am too n00b to test properly though. Some OpenGL setting is not enabled when installing ubuntu,(Ut2004 wouldn't even run) but updating drivers through, Automatix, synaptic, or the guide in my siggy activates/installs something that borks the drivers somehow. If it is something OpenGL, then that would lead to the ATI issues.

---

### Post by Sp@z on 2006-02-23
[QUOTE=theironbadger]I thought so, I have G-Force FX 5200 I believe...  could you point me to somewhere I could go to get some help getting the drivers killed?[/QUOTE]
best thing to do is click the link Nvidia drivers in my siggy, the Nvidia forums no longer had the thread last time I looked. But maybe TSEliot can lead you in the right direction.

---

### Post by theironbadger on 2006-02-23
Thanks, found that link through the automatrix uninstall thread.  Already posted a question about it.  Sorry I didn't tell you before you posted.

Thanks

---

### Post by Sp@z on 2006-02-23
np, hope you have better luck than I did with this issue. :)

---

