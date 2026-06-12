---
title: "Setting system wide settings with gsettings/dconf in 11.10"
date: 2012-01-06
forum: General Help
---

### Post by Christian Moeller on 2012-01-06
Hi,

Back in the "old" days of gconf I used to be able to configure system-wide mandatory settings for users from the command-line like this:

$ gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --type integer --set /apps/gnome-power-manager/timeout/sleep_computer_battery 600

This doesn't work anymore in Ubuntu 11.10 - obviously because power management now stores it's settings in dconf instead of gconf.

I've figured out so far, that I can change dconf-settings from the command-line like this:

$ gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-battery-timeout 600

... but this only applies for the user currently logged in.

I've read something about dconf profiles on the gnome wiki, but they refer to /etc/dconf/... a directory not present in my Ubuntu 11.10-installations.

Does anybody know how to set up mandatory and/or default values from the command-line in Oneiric?


Best regards,

Christian.

---

### Post by velmont on 2012-03-15
It seems to somewhat work at a lower level. I.e. I'm not able to switch user or lock screen when I press the buttons/menu entries for it both in Unity and in Gnome Shell, they don't really respond.

However, - the UI doesn't disappear.

And also, -- I haven't seen a place to make this permanent/mandatory yet. Or, well, I saw some of it - but it didn't seem to work.


Come any closer?

---

### Post by Losergamer04 on 2012-06-08
[This ]("https://live.gnome.org/dconf/SystemAdministrators")is the best explination I have seen for how dconf works. I'm currently working on implementing this right now. I'm currently using Ubuntu 12.04
 
From what I can tell, you need to do both gconf and dconf because some applications are not set up for dconf (bur from what I've seen, most are).

---

