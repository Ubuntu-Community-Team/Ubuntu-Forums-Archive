---
title: "Volume maximum at start up, any way to fix?"
date: 2011-08-03
forum: General Help
---

### Post by Wetmewhistle on 2011-08-03
I have a dual boot with windows 7 and ubuntu 11.04, I have installed this a couple times, so its not the first time it happens. My laptop is an acer 5678zg i think its called. I previously had 32 bit ubuntu and 64 bit now, same issue

When I boot up ubuntu, my volume is sat at maximum which is really annoying since I have the sound through hdmi pass through via onkyo receiver and loudspeakers. Even when I turn volume down, the volume meter is not at top, but at where it was last time, but the volume is still at top and decreases to whatever volume I had at last time at first click on volume down..

Any workaround on this issue?

---

### Post by pqwoerituytrueiwoq on 2011-08-03
```
pacmd set-sink-volume 0 3500
```add that to start up
i actually made my login sound run a script instead
```
#!/bin/sh
pacmd set-sink-volume 0 3500
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
exit

```

---

### Post by Wetmewhistle on 2011-08-03
thanks for the quick reply. Im bit newbie, but this looks like i need to post somewhere in the repository? or can I do this from terminal?

---

### Post by krytorii on 2011-08-03
> **Wetmewhistle said:**
> thanks for the quick reply. Im bit newbie, but this looks like i need to post somewhere in the repository? or can I do this from terminal?

For the first one, just paste into the terminal and press enter

Open gedit (or any text  editor), and paste the code in.

Save as a .ssh, then go to system settings, startup applications and click add. Give it a name, then go on browse, find the .ssh you just made and you should be all set to go

---

### Post by pqwoerituytrueiwoq on 2011-08-03
Run this command it will set the script of for you and add it to startup
```
echo "#!/bin/sh" > ~/.loginSound.sh;echo "pacmd set-sink-volume 0 3500" >> ~/.loginSound.sh;echo '/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"' >> ~/.loginSound.sh;echo "exit" >> ~/.loginSound.sh;echo "" > ~/.config/autostart/libcanberra-login-sound.desktop;echo "[Desktop Entry]" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "Type=Application" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "Name=GNOME Login Sound" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "Comment=Plays a sound whenever you log in" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "Exec=~/.loginSound.sh" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "OnlyShowIn=GNOME;" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "AutostartCondition=GNOME /desktop/gnome/sound/event_sounds" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "X-GNOME-Autostart-Phase=Application" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "X-GNOME-Provides=login-sound" >> ~/.config/autostart/libcanberra-login-sound.desktop
```if you need to adjust the volume settings at startup ```
gedit ~/.loginSound.sh
```just change the 3500 to a higher or lower number depending on what way you want the volume to go
if it does not work it is something that has changed since 10.04

uninstall:
```
rm ~/.loginSound.sh;rm ~/.config/autostart/libcanberra-login-sound.desktop
```

---

### Post by Wetmewhistle on 2011-08-04
Thanks for the help guys, I am still trying to sort i out. Its not just login sound btw, my bad. But whole volume is reset everytime i restart/shut off computer and is set on maximum when i start my pc again. 

I pasted this into terminal; pacmd set-sink-volume 0 3500

And got this message; 
Welcome to PulseAudio! Use "help" for usage information.

Not sure where to go from there

I also tried;

echo "#!/bin/sh" > ~/.loginSound.sh;echo "pacmd set-sink-volume 0 3500" >> ~/.loginSound.sh;echo '/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"' >> ~/.loginSound.sh;echo "exit" >> ~/.loginSound.sh;echo "" > ~/.config/autostart/libcanberra-login-sound.desktop;echo "[Desktop Entry]" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "Type=Application" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "Name=GNOME Login Sound" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "Comment=Plays a sound whenever you log in" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "Exec=~/.loginSound.sh" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "OnlyShowIn=GNOME;" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "AutostartCondition=GNOME /desktop/gnome/sound/event_sounds" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "X-GNOME-Autostart-Phase=Application" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "X-GNOME-Provides=login-sound" >> ~/.config/autostart/libcanberra-login-sound.desktop

But I just got the message in terminal;

bash: !/bin/sh": event not found

:confused:

---

### Post by mikejonesey on 2011-08-04
why not just use alsamixer; should save as defaults (i think);
```
alsamixer
```

---

### Post by fdrake on 2011-08-04
> **Wetmewhistle said:**
> Thanks for the help guys, I am still trying to sort i out. Its not just login sound btw, my bad. But whole volume is reset everytime i restart/shut off computer and is set on maximum when i start my pc again. 

I pasted this into terminal; pacmd set-sink-volume 0 3500

And got this message; 
Welcome to PulseAudio! Use "help" for usage information.

Not sure where to go from there

I also tried;

echo "#!/bin/sh" > ~/.loginSound.sh;echo "pacmd set-sink-volume 0 3500" >> ~/.loginSound.sh;echo '/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"' >> ~/.loginSound.sh;echo "exit" >> ~/.loginSound.sh;echo "" > ~/.config/autostart/libcanberra-login-sound.desktop;echo "[Desktop Entry]" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "Type=Application" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "Name=GNOME Login Sound" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "Comment=Plays a sound whenever you log in" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "Exec=~/.loginSound.sh" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "OnlyShowIn=GNOME;" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "AutostartCondition=GNOME /desktop/gnome/sound/event_sounds" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "X-GNOME-Autostart-Phase=Application" >> ~/.config/autostart/libcanberra-login-sound.desktop;echo "X-GNOME-Provides=login-sound" >> ~/.config/autostart/libcanberra-login-sound.desktop

But I just got the message in terminal;

bash: !/bin/sh": event not found

:confused:

post here your ~/.loginSound.sh and ~/.config/autostart/libcanberra-login-sound.desktop

```
less ~/.loginSound.sh
less ~/.config/autostart/libcanberra-login-sound.desktop

```

---

### Post by Wetmewhistle on 2011-08-10
> **fdrake said:**
> post here your ~/.loginSound.sh and ~/.config/autostart/libcanberra-login-sound.desktop

```
less ~/.loginSound.sh
less ~/.config/autostart/libcanberra-login-sound.desktop

```

I got this when pasted it in terminal



[Desktop Entry]
Type=Application
Name=GNOME Login Sound
Comment=Plays a sound whenever you log in
Exec=/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
OnlyShowIn=GNOME;
AutostartCondition=GNOME /desktop/gnome/sound/event_sounds
X-GNOME-Autostart-Phase=Application
X-GNOME-Provides=login-sound
X-GNOME-Autostart-enabled=false
(END)

---

### Post by Wetmewhistle on 2011-08-10
> **mikejonesey said:**
> why not just use alsamixer; should save as defaults (i think);
```
alsamixer
```

thanks, i tried this.

Master it seems like is at 0
headphone 100
speaker 81
pcm 100

i tried change the values last time to like 35, but it seems its reset itself

---

### Post by Ezraghast on 2011-08-29
If you're still having the same problem you can try this:
Open a terminal and type 
```
gksudo gedit /etc/pulse/daemon.conf
```
In the file that opens find the line that reads 
```
flat-volumes = no
```
and place a semi-colon and a space at its beginning so that it reads 
```
; flat-volumes = no
```
Save the file and reboot. Volume should now be as you set it before rebooting. I was having the same problem as you (even down to the onkyo receiver!) and this worked for me. I found the solution [here.]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/661885")

---

