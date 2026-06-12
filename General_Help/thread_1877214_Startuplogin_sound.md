---
title: "Startup/login sound"
date: 2011-11-07
forum: General Help
---

### Post by jmacx81 on 2011-11-07
Since I have upgraded to 11.10 I have had no startup or login sounds. I have tried to fix this but it hasn't stuck. Any suggestions?

---

### Post by BillyBoa on 2011-11-07
Our friend Andrei gives some ideas about tweaking of 11.10
[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

*good job in Aphganistan

---

### Post by jmacx81 on 2011-11-07
I looked through this but I didn't see any info on the Sounds.

---

### Post by BillyBoa on 2011-11-07
Check in autostart items if the sound is missing. In the link is explaining how.

---

### Post by jmacx81 on 2011-11-07
well in there is shows that gnome-sound-applet.desktop is there

---

### Post by ReptilianShadow on 2011-11-07
It *should* run 
```
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
```
on startup (open startup applications), and it does run, but for some reason the sound doesn't play.

You could instead just play the .ogg file directly at startup.
Install some .ogg player like ogg123
[http://manpages.ubuntu.com/manpages/gutsy/man1/ogg123.1.html]("http://manpages.ubuntu.com/manpages/gutsy/man1/ogg123.1.html")
```
sudo apt-get install vorbis-tools
```
then this line to run at startup:
```
ogg123 /usr/share/sounds/ubuntu/stereo/desktop-login.ogg
```
(Untested as a startup command, but should work)
Not fixing it, but a quick work around.

---

### Post by jmacx81 on 2011-11-08
> **ReptilianShadow said:**
> It *should* run 
```
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
```
on startup (open startup applications), and it does run, but for some reason the sound doesn't play.

You could instead just play the .ogg file directly at startup.
Install some .ogg player like ogg123
[http://manpages.ubuntu.com/manpages/gutsy/man1/ogg123.1.html]("http://manpages.ubuntu.com/manpages/gutsy/man1/ogg123.1.html")
```
sudo apt-get install vorbis-tools
```
then this line to run at startup:
```
ogg123 /usr/share/sounds/ubuntu/stereo/desktop-login.ogg
```
(Untested as a startup command, but should work)
Not fixing it, but a quick work around.

I would suggest not doing this, it crashes the startup and reverts to text mode. Then when you get that problem corrected the command then doesn't stick so still no start up sound :(

---

### Post by ReptilianShadow on 2011-11-12
A crash? That's... odd. I tested it on Unity 3d (default) desktop session, Ubuntu 11.10, no crash for me. Have you tried running just the "ogg123 [file.ogg]" command in terminal instead of in startup list? 

Or, are you changing something other than "GNOME Login Sound" in "Startup Application Preferences"?

Should edit this:

[IMG]http://i1184.photobucket.com/albums/z324/ReptilianShadow/Screenshotat2011-11-12011010.png[/IMG]

I'm really surprised it would crash like that, not sure what the cause would be, perhaps add a delay to the sound (sleep 3;ogg123 [file.ogg])?

---

### Post by jmacx81 on 2011-11-13
well it didn't change in the start up apps. I have updated it and will post a yes or no next time I can reboot.

---

### Post by Cyclane on 2011-11-13
Do you have sound after login?
In previous releases of ubuntu, upstart would load alsa too late (for my system). So I would login before the sound was fully loaded and this resulted in the login sound not working. If I waited a few seconds before logging in everything worked fine. 11.10 fixed this for me.

So my question, what happens if you wait a few moments before logging in?

---

### Post by jmacx81 on 2011-11-14
Yup I have sound after logging in but even if I wait 10 minutes before logging in I still get no log in sound.

---

