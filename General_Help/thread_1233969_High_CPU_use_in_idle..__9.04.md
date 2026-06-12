---
title: "High CPU use in idle..  9.04"
date: 2009-08-07
forum: General Help
---

### Post by Roig on 2009-08-07
I'm very confused, hope someone with more knowledge can help me here.. 

When I installed ubuntu 9.04 all was working very well. But since yesterday I am experiencing little locks when I do my tasks (playing a DVD, opening a website, playing music.. etc..). 

When I look to the gnome system manager I can see the high CPU usage and when the lock is happening. Just look that screenshot that shows my computer in idle for about 1 minute. Did you see the high CPU usage? Why? :S

If i look the process tab all is normal.. and when the CPU peak happens the process tab is normal too..

Anyone can give me some advice please? It's annoying having those peaks..

---

### Post by joe2012 on 2009-08-07
I've never used that UI, but if you go into the terminal and use *top* you can see all the processes and the percentage of the CPU they're using. You can always try using that if that UI doesn't already do it

---

### Post by kpkeerthi on 2009-08-07
Open a terminal and run **top** command. Post the screenshot of it when the cpu usage spikes.

---

### Post by NightwishFan on 2009-08-07
That seems fairly normal for Gnome-System-Monitor. It sometimes peaks 30% or so itself.

---

### Post by Roig on 2009-08-07
> **NightwishFan said:**
> That seems fairly normal for Gnome-System-Monitor. It sometimes peaks 30% or so itself.

I assure you that is not normal.. and the locks I experience when I play a .avi file or music either.. 

> Open a terminal and run top command. Post the screenshot of it when the cpu usage spikes.

Here i go, it's Xorg.. >_<

but.. why? :S


EDIT: When a peak happens Xorg I saw Xorg at 90% CPU usage for a second. This is when the lock happens too..

---

### Post by NightwishFan on 2009-08-07
I get xorg high cpu errors when I install Ubuntu (and once a Debian and Fedora) unknowingly using a bad media. Make sure the CD you used to install was burned correctly.

Also, if it was burned correctly: It does not seem like a compiz problem, oddly enough, so perhaps try to reconfigure your graphics in recovery mode. If you have a customized xorg.conf I would not do this though. If you do reconfigure, you will need to reinstall any proprietary drivers.

---

### Post by Roig on 2009-08-07
> **NightwishFan said:**
> I get xorg high cpu errors when I install Ubuntu (and once a Debian and Fedora) unknowingly using a bad media. Make sure the CD you used to install was burned correctly.

Also, if it was burned correctly: It does not seem like a compiz problem, oddly enough, so perhaps try to reconfigure your graphics in recovery mode. If you have a customized xorg.conf I would not do this though. If you do reconfigure, you will need to reinstall any proprietary drivers.

The problem began i think when I switched on the compiz effects, then I installed screenlets. But now i uninstalled screenlets and switched off all the effects and it's the same.. I didn't touch the xorg.conf file.

Well i don't know what i have to do.

EDIT!!

JUST LOOK: ... 98% usage.. WITH THE DEFAULT UBUNTU THEME AND NO EFFECTES ENABLED... :confused::popcorn:

---

### Post by NightwishFan on 2009-08-07
Try my suggestion to check the cd you used to install or use recovery mode to reconfigure the graphics.

---

### Post by Roig on 2009-08-07
> **NightwishFan said:**
> Try my suggestion to check the cd you used to install or use recovery mode to reconfigure the graphics.

The CD (And it's a Verbatim) it's ok I used it in my other PC's and 2 weeks ago and all is working very well. Reconfigure my graphics? How I can do it? :S

look my previous post xD 98% it's insane.. 

Thanks for your help.

---

### Post by NightwishFan on 2009-08-07
Boot into recovery mode at grub. If you do not see the selection screen, just push esc when it prompts you to. (Right before the 'splash').


Choose the Recovery Mode option and when the menu loads tell it to reconfigure the graphics/xserver then resume boot. You may need to reinstall any proprietary drivers.

The biggest culprit would be compiz though, which causes video lag in totem for me. It shows Compiz.real as the cpu eater not xorg, so your situation is different.

---

### Post by Roig on 2009-08-07
> **NightwishFan said:**
> Boot into recovery mode at grub. If you do not see the selection screen, just push esc when it prompts you to. (Right before the 'splash').


Choose the Recovery Mode option and when the menu loads tell it to reconfigure the graphics/xserver then resume boot. You may need to reinstall any proprietary drivers.

The biggest culprit would be compiz though, which causes video lag in totem for me. It shows Compiz.real as the cpu eater not xorg, so your situation is different.


Ok i did it, and then it messed up my xorg.conf file and I can't boot (black screen), then I reentered in recovery mode and in console i replaced the new xorg.conf file with the backup one so im now here :> 

The problem persists, and now i booted with the main ubuntu theme and no effects enabled.

Should I reinstall all the thing..? >_<

---

### Post by NightwishFan on 2009-08-07
;/ I would wait for a few suggestions before you reinstall. Sorry I could not help more. If I may ask what graphics hardware are you using?

---

### Post by Roig on 2009-08-07
> **NightwishFan said:**
> ;/ I would wait for a few suggestions before you reinstall. Sorry I could not help more. If I may ask what graphics hardware are you using?

No problem, thanks for your help. I'm using a ATI Mobility Radeon HD 3400 Series. i never had problems with it at all but well.. i don't know.

Hope more suggestions appear.

---

### Post by aesis05401 on 2009-08-07
Have you seen this thread ?

I don't know what they are testing, but you may want to find out:[http://ubuntuforums.org/showthread.php?t=1234012]("http://ubuntuforums.org/showthread.php?t=1234012").

---

### Post by Roig on 2009-08-07
I found this thread but i think it's not solved. I'm starting to think that this is a big bug in Xorg or something related with Xorg.

[http://ubuntuforums.org/showthread.php?t=1196603]("http://ubuntuforums.org/showthread.php?t=1196603")

---

### Post by NightwishFan on 2009-08-08
I hear ATI drivers have problems currently. Do you have high CPU usage using a live CD? If not then either your install is messed up or the driver you are using is installed wrong or is buggy.

---

