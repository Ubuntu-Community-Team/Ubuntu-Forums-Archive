---
title: "strange problem after disabling/ enabling usplash"
date: 2010-08-16
forum: General Help
---

### Post by Richard85 on 2010-08-16
So I wanted to get rid of the usplash deal because I'd gotten used to the straight text boot up, so I did exactly


- edit with #sudo nano /etc/default/grub
- change line "splash" to "nomodeset noplymouth"
- save and close nano
- run #sudo update-grub

Afterwards, when I shutdown or come back from suspend, I see a screen that can only be described as the screen you see when the NES would not properly read a game cartridge.

I then changed the nomodeset noplymouth back to splash but when I shutdown or restart , I still see the wacked out NES screen.

Does anyone have a clue what I could do? Maybe reinstall something?

Any help and suggestions would be greatly appreciated!

---

### Post by cantormath on 2010-08-16
[http://ubuntuguide.net/startup-manager-an-gui-tool-for-managing-grubusplash-and-splashy](http://ubuntuguide.net/startup-manager-an-gui-tool-for-managing-grubusplash-and-splashy)

---

### Post by Richard85 on 2010-08-17
Still seeing crazy NES screens...

---

