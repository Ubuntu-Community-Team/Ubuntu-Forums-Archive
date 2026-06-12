---
title: "Powernowd Question"
date: 2006-04-02
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-04-02
I currently have it disabled but what exactly does it do ? I know it controls cpu and voltage to save battery power but here is my question. Say I'm not doing anything and I'm running on battery power. It is keeping my cpu at 600 mhz out of my 2.2 ghz. Then I open an application, say swiftfox. Would my cpu stay at 600 mhz or would it go up ? It also only runs when it running on battery, not plugged in correct ?

---

### Post by stocksy on 2006-04-02
powernowd is brilliant because it is stupid - it just runs all the time, not caring whether you are running on battery or not.  Essentially, it just checks to see how busy your CPU is and if it's over 80% utilised, it ramps up the MHz.  When it drops down to <20% utilisation, it steps your CPU down again.  To quote the man page; *"What good is having a nice powerful laptop if  you can't  use it at full speed, even for a few seconds, while on battery power?"*

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=stocksy]powernowd is brilliant because it is stupid - it just runs all the time, not caring whether you are running on battery or not.  Essentially, it just checks to see how busy your CPU is and if it's over 80% utilised, it ramps up the MHz.  When it drops down to <20% utilisation, it steps your CPU down again.  To quote the man page; *"What good is having a nice powerful laptop if  you can't  use it at full speed, even for a few seconds, while on battery power?"*[/QUOTE]
So it is basically not worth using ?

---

### Post by David Corrales on 2006-04-02
It's really worth using. You'll use less battery power and the laptop will remain cooler.

Normal desktop pc's are like having a car and always stepping on the pedal to the end. Always 100% power and performance.
When you use powerdnow, you're basicaly giving as much gas as the system needs. If you need to process something that's heavy, then sure, go all the way to 100%, but for regular browsing and stuff like that, ~40% is more than enough :)

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=David Corrales]It's really worth using. You'll use less battery power and the laptop will remain cooler.

Normal desktop pc's are like having a car and always stepping on the pedal to the end. Always 100% power and performance.
When you use powerdnow, you're basicaly giving as much gas as the system needs. If you need to process something that's heavy, then sure, go all the way to 100%, but for regular browsing and stuff like that, ~40% is more than enough :)[/QUOTE]
Thanks I'll enable it. But will it give more CPU power if an app needs it ?

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=MasterChief1234]Thanks I'll enable it. But will it give more CPU power if an app needs it ?[/QUOTE]
WOW ! I used Bum to enable it at start up and start it now I can't even hear my fans which is nice. I'm going to unplug my AC cord and see my battery life.

Edit: I have 3:40 min battery life, that's compared to 1:40 before ! I don't usually use my laptop on the go but extra battery life is welcome.

Edit Again: I found that it controls CPU speed when nothing/very little activity is happening. I ran sudo apt-get update and then sudo apt-get upgrade and my CPU went above 60 % and at a peak 100 %. Then when I closed everything but firefox and System Monitor, my CPU usage was at 0-2 %. With powernowd disabled and everything but system monitor closed, I was getting 10-25 % CPU usage over nothing. Cool :)

---

