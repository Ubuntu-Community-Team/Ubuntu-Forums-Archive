---
title: "White screen of death, Ubuntu 11.10"
date: 2011-10-15
forum: General Help
---

### Post by bibble235 on 2011-10-15
When the signon screen kicks in the screen goes white. You can enter the password and sign back in but no screen is visible it is just white however it does sign back in.

Iain

---

### Post by effenberg0x0 on 2011-10-15
I really don't know if you're talking about the DM or login at a VT.
I will guess it's lightdm. But still I don't know which session you have selected.
I also don't know if its a vga issue, as I don't know which VGA you have and if you installed opensource or proprietary drivers, etc.

Being generic, we can try a broad approach:

Maybe you can go to a VT with Ctrl+Alt+F1 to F6 and login.
Or you can boot and select recovery in grub.
Then run:

```
sudo service lightdm stop
sudo service gdm stop
sudo killall -s KILL /usr/bin/X
sudo apt-get remove --purge gdm
sudo apt-get install --reinstall lightdm
sudo dpkg-reconfigure lightdm
sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo reboot now

```

Effenberg

---

### Post by marin123 on 2011-10-15
Try pressing Ctrl+Alt+F1, log in with your username and type unity --replace. Then press Ctrl+Alt+F7 and Unity should restart.

---

### Post by bibble235 on 2011-10-15
Thanks all upgrade to 11.10 did fail around the themes area. Perhaps something caused all this. Tried unity --replace but did not work. Will download 11.10 (64-bit) and reinstall, Unity is starting to make linux like Windows! ouch.

---

### Post by bibble235 on 2011-10-17
Re-install with the 64-bit 11.10

I have not changed themes just the default install.

Screens still come up white. I think it is after the lid has been put down and left overnight. I have noticed you can type in the password and you are logged back on so it is a display issue.

This is an F500 compaq with 6100 nvidia card. Also some of the screen are white when maximized. E.g. Thunderbird has an all with content window with no panes being displayed.

---

### Post by The Bane on 2011-10-19
Having same issue on a desktop. After leaving my PC for a brief period I returned to find a WSOD with only a pointer visible after moving mouse. Assumed it was an issue of the password enabled screen saver. Frustrated I powered off the system and went to work. I did not attempt a 'blind' login, and will try this as a work around until I find a suitable fix.

Is there a resolution for this currently that anyone is aware of?

The Bane

---

