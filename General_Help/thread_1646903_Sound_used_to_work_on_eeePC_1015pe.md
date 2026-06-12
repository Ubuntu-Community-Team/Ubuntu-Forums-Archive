---
title: "Sound used to work on eeePC 1015pe"
date: 2010-12-16
forum: General Help
---

### Post by Loyus on 2010-12-16
EDIT : I tried to reboot several times, and the sound worked once. So my problem is that when I boot Ubuntu, sometimes the sound works (you can tell it from the logon screen), sometimes it doesn't, nada.

I like Ubuntu, but it will be useless to me if I have to reboot several times to get sound. Can anybody help me ? 

I installed Ubuntu in dual boot alongside Windows 7 yesterday, this on an Asus 1015pe netbook. I did all the updates, so I'm now on 10.10 and 35-23-generic version. (and GNOME)

The sound used to work fully, I could even Skype yesterday, but it is now broken. Actually, it worked this morning as well, as I got my computer out of hibernation. But when I tried to Skype, the mic wasnt working anymore, so I had to go back to Windows 7 to make my call.

And when I tried to go back to Ubuntu, there was no sound at all anymore. I tried to reboot, same problem. 

I tried to run the ´´ubuntu-bug audio´´ command in terminal, it didnt solve anything. I checked everything, and if I boot Ubuntu from the USB the sound works fine.



Thank you.

---

### Post by cariboo on 2010-12-16
Check alsamixer, in a terminal to make sure all the volume controls are turned up. Open an Applications->Accessories->Terminal and type:

```
alsamixer
```

you should see something like the screen shot. Use the tab and arrow keys to navigate and turn the volume up and down, once you have the settings to where you want them, press esc to exit, and then type:

```
sudo alsactl store 
```

to store the changes you have made.

---

### Post by Loyus on 2010-12-16
Thank you, I'll try it as soon as I get soundless reboot and keep you up to date.

---

### Post by Loyus on 2010-12-16
Ok, one problem is that my microphone doesn t work in Skype even tho the speakers do.

I went to alsa mixer and did as you said, tried to raise the "front mic boost" bar which was to zero. Executed sudo alsactl store, but it didn't change anything.


I ll reboot now to try alsamixer when the sound doesnt work at all.

---

### Post by Loyus on 2010-12-16
Alright, the sound seems to be stabilized. Speakers and mic all fine.

Thank you.

---

### Post by Loyus on 2010-12-17
Ok, I managed to reproduce the problem in a consistent way.


Sometimes, the sound won't work even when everything is perfect in alsamixer. It can happen in several ways :

Step 1 - Sound works perfectly on a) Windows 7 OR b) Ubuntu
Step 2 - Restart the computer and launch Ubuntu :
                   -  a) Sound doesn't work 
                   -  b) Sound works
Step 3 - If sounds doesn't work, restarting the computer as many times as I want WON'T fix it. The only way to fix it is to actually shut down entirely the computer and turn it on again before launching Ubuntu.

Sound will always work under Windows 7. Typically, sound stops to work when X or Hibernation crashes in Ubuntu and I have to restart. If I don't turn off the computer, it won't work. It won't work if I restart from Windows 7 either.

Machine: Asus eeePC 1015pe with EFI partition for Boot Booster. Usually, the Boot Booster won't be activated after a crash in any OS.

**SOLUTION: Turn off entirely the computer and boot again to get the sound back.**

---

