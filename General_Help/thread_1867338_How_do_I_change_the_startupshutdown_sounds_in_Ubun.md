---
title: "How do I change the startup/shutdown sounds in Ubuntu 11.10?"
date: 2011-10-22
forum: General Help
---

### Post by Thelinuxgeek on 2011-10-22
I want to change my startup and shutdown sound effects to the old Knoppix sound effects ( [http://barnettcomputerrepair.com/computers/knoppix-startup-and-shutdown-sounds/](http://barnettcomputerrepair.com/computers/knoppix-startup-and-shutdown-sounds/) ) but I don't know how to do this in 11.10. Any tips?

---

### Post by duke.tim on 2011-10-22
The startup sounds are located in /usr/share/sounds/ubuntu/stereo/

You could replace them with the Knoppix sounds.

use the ogg format :)

or find the config  ( /home/duke/.config/autostart )that looks like

> /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
and change it to
> /usr/bin/canberra-gtk-play --file=/usr/share/sounds/ubuntu/stereo/[filename].ogg


---

### Post by Thelinuxgeek on 2011-10-22
> **duke.tim said:**
> The startup sounds are located in /usr/share/sounds/ubuntu/stereo/

You could replace them with the Knoppix sounds.

use the ogg format :)

or find the config  ( /home/duke/.config/autostart )that looks like


and change it to

Thanks for the post. But how do I get Ubuntu to play a sound when it's shutting down? There's the logout sound but that doesn't play when the system is powering down.

---

### Post by duke.tim on 2011-10-23
I'm not sure about shutdown/logout sounds

[http://ubuntuforums.org/showthread.php?t=789858](http://ubuntuforums.org/showthread.php?t=789858)

Looks like you need to add the sound command to the shutdown script.
instead of aplay you could just use the
> /usr/bin/canberra-gtk-play --file=/usr/share/sounds/ubuntu/stereo/[filename].ogg

---

### Post by linuxinstalledfromhdd on 2011-10-23
> **duke.tim said:**
> I'm not sure about shutdown/logout sounds

[http://ubuntuforums.org/showthread.php?t=789858](http://ubuntuforums.org/showthread.php?t=789858)

Looks like you need to add the sound command to the shutdown script.
instead of aplay you could just use the

There is a way to change the sound theme on 11.04, but for whatever reason it is missing in 11.10. I would like to know how to easily change my sound theme too in 11.10.  Most users don't know how to work the command line to change their sound themes, so I don't know why Ubuntu decided to remove the sound theme configuration GUI. :(

---

### Post by dcstar on 2011-10-24
> **Thelinuxgeek said:**
> Thanks for the post. But how do I get Ubuntu to play a sound when it's shutting down? There's the logout sound but that doesn't play when the system is powering down.

That has been broken for about 3 years now, the "Fast shutdown" procedure kills off the X process that plays the Logoff sound before it gets a chance to begin.

People wanted a system that shutdown quickly, playing the Logoff sound was a casualty to achieve that end.

---

### Post by Thelinuxgeek on 2011-10-25
> **duke.tim said:**
> I'm not sure about shutdown/logout sounds

[http://ubuntuforums.org/showthread.php?t=789858](http://ubuntuforums.org/showthread.php?t=789858)

Looks like you need to add the sound command to the shutdown script.
instead of aplay you could just use the

Thanks for the link. Just what I was looking for!

---

