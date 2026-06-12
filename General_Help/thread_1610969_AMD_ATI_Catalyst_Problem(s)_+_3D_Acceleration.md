---
title: "AMD ATI Catalyst Problem(s) + 3D Acceleration"
date: 2010-11-01
forum: General Help
---

### Post by Cadam92 on 2010-11-01
Ive updated the ATI Mobility Radeon 5800 series in the laptop, ASUS g73jh, automatically from ubuntu when it first started up. 

I then downloaded PlayOnLinux to be able to use Steam, I downloaded Counter Strike Source. The graphics went funny as there was white bars flashing when in game.

I closed the program and it told me I needed 3D acceleration, so I went to look at the ATI Catalyst Control, System > Preferences, but when I got to the directory there where two ATI Catalyst Control Panel and two ATI Catalyst Control Panel (Administrative), I cant open both and I dont find them under the Ubuntu Software Centre so i can remove it. 

So I now I dont know how to remove it and to see if it has anything for 3D Acceleration for Ubuntu.

---

### Post by 3Miro on 2010-11-01
If you have the ATI Catalyst Control Panel yo should already have 3D acceleration enabled. You can test that by opening a terminal and typing:
```
 glxgears 
```
this is a common test. You should get a number ii the hundreds or thousands (unless you have vsync, in which case it will match the monitor refreash rate).

As a general rule, ATI cards are bad for wine games. There is a new ATI driver for the 5xxx cards, which is supposed to work great, but it will not make it in Ubuntu until 11.04.

---

### Post by Cadam92 on 2010-11-01
get BadRequest, must be the ATI cause i cant remove the programs but its still stuck up i systems > preferences. should i reinstall linux? or is it going to do the same thing?

---

