---
title: "Hardware/Software issues."
date: 2012-01-22
forum: General Help
---

### Post by Digi984 on 2012-01-22
So after going back to Windows(and being reminded clearly of why I hate it.) I want to give Ubuntu another try, but I am having the same problems, mainly with hardware.  

I am running 
AMD Athlon Dual Core X2 6000+  3.00GHz
Nvidia Gforce 9600 GT
4GB RAM


Problems I have when using Ubuntu are primarily games.  Games I play and the problems I have are as followed.

World of Warcraft: Won't utilize video card and will only run game on minimum(or near minimum) settings.

     -Ventrillo/Mangler: Won't recognize my microphone, I can hear people but no matter the setting, the mic won't work

     -Curse Client: Won't install, freezes up right after accepting EULA.  

Dragon Age Origins: Just simply won't install, I have tried using just wine as well as the third party software(Play on Linux, ect).  Setup gets to where you have to accept the EULA but the screen is just blank and won't proceed.

Pretty much anything from Steam: Runs very slowly and video is choppy at best.


Other than the issues with games and support applications I do like Ubuntu/Linux and am trying to learn it but having essentially half of my usage hindered is frustrating.  

Are there solutions to these issues or perhaps is there a different distro I should use for games?  I would really prefer to avoid dual booting.

Any help would be appreciated

---

### Post by NightFoxyarrith on 2012-01-22
So I guess you use wine to run these programs, and that can indeed make the programs run slowly or have issues. There are some things you can try. First one is install the most recent nvidia driver. Use this guide to do so:
 [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
Next, you can try Playonlinux, which is basicly wine with a GUI that automaticly tries some workarounds for some games and programs. 
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)
And you can always check other users experience with these programs on the wine appdb. 
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Digi984 on 2012-01-22
> **NightFoxyarrith said:**
> So I guess you use wine to run these programs, and that can indeed make the programs run slowly or have issues. There are some things you can try. First one is install the most recent nvidia driver. Use this guide to do so:
 [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
Next, you can try Playonlinux, which is basicly wine with a GUI that automaticly tries some workarounds for some games and programs. 
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)
And you can always check other users experience with these programs on the wine appdb. 
[http://appdb.winehq.org/](http://appdb.winehq.org/)


Is there a way to install the games without using wine?  Wine causes alot of headaches so avoiding it would be nice.  I have tried POL before and experience the same issues.

---

### Post by NightFoxyarrith on 2012-01-22
There's no way to install windows games without wine, you can however try some linux games. You' ll find a lot of free games in the ubuntu software center. If you're looking to buy games try desura (it's a steam alternative for linux).
[http://www.desura.com/](http://www.desura.com/)
By the way, through playonlinux you should try disabling glsl shaders in the options, this sped up lots of games for me.

---

### Post by Digi984 on 2012-01-22
> **NightFoxyarrith said:**
> There's no way to install windows games without wine, you can however try some linux games. You' ll find a lot of free games in the ubuntu software center. If you're looking to buy games try desura (it's a steam alternative for linux).
[http://www.desura.com/](http://www.desura.com/)
By the way, through playonlinux you should try disabling glsl shaders in the options, this sped up lots of games for me.


Problem with POL is it doesn't even make it through the install process for my games.  Either freezes up or goes blank or just crashes.   I have tried disabling glsl shaders but no noticeable improvements.

---

### Post by NightFoxyarrith on 2012-01-22
Then I'm sorry to say this but you might have to wait for wine developers to fix it, if it ever gets fixed. Running non-native code is a complex thing, and since windows programs keep on evolving, wine will probably never be perfect. But since microsoft recently dropped .net for windows 8 and encourages developers to write their apps in javascript (which is cross-platform) maybe things will become easier for linux users.

---

### Post by Digi984 on 2012-01-22
> **NightFoxyarrith said:**
> Then I'm sorry to say this but you might have to wait for wine developers to fix it, if it ever gets fixed. Running non-native code is a complex thing, and since windows programs keep on evolving, wine will probably never be perfect. But since microsoft recently dropped .net for windows 8 and encourages developers to write their apps in javascript (which is cross-platform) maybe things will become easier for linux users.


Okay.  It's just strange because the games are marked as high performance with wine..so obviously some people are getting them to work.

---

### Post by NightFoxyarrith on 2012-01-22
I know but since wine is really complex there's a different level of performance on different hardware. Are you sure you have the newest nvidia driver? You can always try to download the newest one from the nvidia site, that gave me better performance as well on one of my machines.

---

### Post by Digi984 on 2012-01-22
> **NightFoxyarrith said:**
> I know but since wine is really complex there's a different level of performance on different hardware. Are you sure you have the newest nvidia driver? You can always try to download the newest one from the nvidia site, that gave me better performance as well on one of my machines.


Well they didn't have a linux driver on the site for my card.  I tried using the windows one but had the same problem as with curse, it freezes up at the EULA, but I did go through the steps of the earlier link you gave.

---

### Post by NightFoxyarrith on 2012-01-22
They do have a linux driver for the nvidia 9 series, you can find it here [http://www.nvidia.com/object/linux-display-amd64-290.10-driver.html](http://www.nvidia.com/object/linux-display-amd64-290.10-driver.html) (this is the 64-bit desktop driver, if this is a laptop or 32-bit system, use their search: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) and select 9 series or 9m series, and linux 32-bit or 64-bit as operating system).

---

