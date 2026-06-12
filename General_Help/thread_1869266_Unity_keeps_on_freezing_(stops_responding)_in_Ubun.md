---
title: "Unity keeps on freezing (stops responding) in Ubuntu 11.10"
date: 2011-10-25
forum: General Help
---

### Post by kaustavdm on 2011-10-25
Hi all,

I'm having a strange issue since upgrading to Ubuntu 11.10. Unity keeps freezing from time to time. The UI stops responding altogether. No clicks or keyboard commands have any effect. It does not happen a specific interval or when any particular program runs. But it has happened atleast 10 times since I upgraded to 11.10. The upgrade, btw, had been smooth with no errors. 

When this freeze occurs, the only option left to me is to reset the computer. I didn't try falling back to console. I'll remember to try it next time and do a Unity restart. But still it is Unity causing the problem.

The reason I'm sure that it's Unity causing the problem is that on one such occasion, I was logged in through SSH to this computer from my laptop. I was able to perform commands and could reboot the computer.

Any idea, anyone?

Thanks.

Kaustav

---

### Post by xtremo on 2011-10-25
I did have a few instances of that, along with the menu bar appearing and disappearing at different times.

No doubt there is a solution to it, but I need this machine as a general workhorse for business....I don't have time to fiddle around with it.

So I just cut to the chase and put 11.04 back on.

---

### Post by diversecg on 2011-10-25
I just made a similar post, and I found the cause, compiz (go figure, always causes problems).  It appears that compiz or something related to it takes complete focus preventing any desktop interaction (usually happens switching screens with a alert/dialog that poped up somewhere in the background from any application)

solution: use Ctrl+Alt+F1 to get to terminal, login, then kill compiz:

sudo killall -KILL compiz

After that Ctrl+Alt+F7 brings back desktop (reorganizing itself as  compiz/unity starts again automatically) and everything appears to work  again

I think I will keep my other machine at 11.04 for now...  at least it is possible not to loose all your work...

---

### Post by kaustavdm on 2011-10-26
Just as I thought. Falling back to terminal would be an option. But after you kill compiz, doesn't it end all desktop effects with it? When compiz returns, does it reorganize itself successfully?

---

### Post by kaustavdm on 2011-10-26
Okay. So it happened again and diversecg's solution worked ([http://ubuntuforums.org/showpost.php?p=11392420&postcount=3](http://ubuntuforums.org/showpost.php?p=11392420&postcount=3)). Thanks.

---

### Post by diversecg on 2011-10-27
compiz does appear to return successfully after killing it, and the desktop does reorganize itself properly (at least for me).  The only issue I have noticed once was the workspaces swapped around (top left ended up bottom left) but otherwise all fine.

---

### Post by BillyBoa on 2011-10-27
Try to install or reinstall the video proprietary drivers. I had a similar problem and it was due to my ATI drivers.

---

### Post by kaustavdm on 2011-10-27
@diversecg
I seemed to face no problem with compiz and it returned. Even workspace switching worked fine. Not sure if I should report this as a bug.

@BillyBoa
I don't have any proprietary drivers installed. So it's a different case for me.

---

### Post by BillyBoa on 2011-10-27
Try to install the proprietary drivers (if any) because they work better. If not, maybe you have an installation problem. In such a case the easier way is to re install the system.

---

### Post by kaustavdm on 2011-10-28
I don't have any external graphics card installed. Ubuntu's drivers are good enough for my system. I don't need to install proprietary drivers. My computer works fine otherwise. If there's a glitch in compiz, I see no reason to go for a clean install. Maybe the glitch is that I don't have a graphics card. :P

---

### Post by merindol on 2012-01-31
Hi.

I updated to Nvidia 295 drivers (from Nvidia official web site) and it didnt help.

Then I updated Compiz with this PPA : [http://ppa.launchpad.net/vanvugt/compiz/ubuntu](http://ppa.launchpad.net/vanvugt/compiz/ubuntu)
and all is good so far. No freeze for an hour.

---

### Post by paulkiss on 2012-05-22
I had the same problem as the topic starter described. Ubuntu 12.04, Unity 3D, an ATI video card (Radeon X1600). Everything froze, the music player kept buffering music from a radio station but nothing worked. I had to downswitch to Unity 2D... but I'll try to switch back to 3D mode and try the trick with Ctrl+Alt+F1 in case everything freezes again, I didn't know about the console trick till this moment...

---

### Post by paulkiss on 2012-06-03
Ok, Ubuntu 12.04, Unity, Radeon X1600 vcard, occasional freezes still happen for no reason and "sudo killall -KILL compiz" don't really help much. Only rebooting (from TTY) gets things back to normal. So I switched back to Unity 2D.

---

