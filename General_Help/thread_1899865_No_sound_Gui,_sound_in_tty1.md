---
title: "No sound Gui, sound in tty1"
date: 2011-12-24
forum: General Help
---

### Post by xedth2 on 2011-12-24
So I installed Ubuntu 11.04 off the minimal disc.  I installed XFCE4 and thats working fine.  My only issue right now is if I have anything with sound playing I don't hear anything but if I hit ctrl-alt-F1 and go to, well any of the tty's I get whatever is playing.  For example I'll have VLC open playing a song and I don't hear anything but when I go to a TTY I can hear the song.  When I type aplay Front_Center.wav into a TTY it plays fine.  When I type it into a terminal on the GUI I get nothing until I switch to the TTY.  I installed PulseAudio Mixer GUI and all the levels are turned all the way under the master.  When I open the window I see two sliders moving together.  The little speaker button doesn't have a red X on it.  When I click set controls I only see a check box with master for its label.  

Here are the groups I'm in...
adm dialout cdrom plugdev lpadmin sambashare admin

I tried 
sudo usermod -a (UserName) -G audio
but got no output, I'm not sure what is going on.

---

### Post by xedth2 on 2011-12-24
This thread isn't solved hit the button on accident please respond I have no idea why this is doing this.

---

