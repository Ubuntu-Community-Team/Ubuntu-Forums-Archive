---
title: "network manager has to be started manually"
date: 2012-06-15
forum: General Help
---

### Post by Old Woman on 2012-06-15
I've just performed a minimal install of lubuntu 12.04.  Wired ethernet connection works fine, however when using a wireless dongle the network does not set up at boot, and I have to start the network manager manually via the terminal. How can I get it to start up automatically?
Thanks!

---

### Post by SDX0 on 2012-06-15
The LXDE Wiki says you could add the command to start the network manager to ~/.config/autostart if you only want it to start automatically for one user or /etc/xdg/lxsession/LXDE/autostart if you want it to start automatically for all users.

---

### Post by Old Woman on 2012-06-15
> **SDX0 said:**
> The LXDE Wiki says you could add the command to start the network manager to ~/.config/autostart if you only want it to start automatically for one user or /etc/xdg/lxsession/LXDE/autostart if you want it to start automatically for all users.

Directory /etc/xdg/lxsession/LXDE doesn't exist. Should I create a directory? I've tried adding the command to /etc/xdg/lxsession/lubuntu/autostart. It didn't make any difference. What exactly should I write?
Thanks again.

---

### Post by nothingspecial on 2012-06-26
From the [[COLOR="Blue"]wiki[/COLOR]]("https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_I_can_autostart_a_program_when_logging_into_Desktop")



> 

How I can autostart a program when logging into Desktop

First you need to copy a .desktop -file to your .config folder's autostart folder.
```

cp /usr/share/applications/urxvtd.desktop ~/.config/autostart/
```

After copying we need to activate the starting from menu: Menu -> Preferences -> Desktop Session Settings

Please note that the directory may need to be created first:
```

mkdir ~/.config/autostart
```

for a PCManFM window

```
leafpad ~/.config/autostart/pcmanfm.desktop
```

and change

```
Exec=pcmanfm %U
```

to

```
Exec=pcmanfm
```

Alternative method

Make the directories "lxsession/Lubuntu/autostart" in "~/.config/"

```
mkdir -p ~/.config/lxsession/Lubuntu/
touch ~/.config/lxsession/Lubuntu/autostart
```

Then edit the file with the name of the applications you want to start, one per line. Example:

```
pcmanfm
sylpheed
chromium-browser
```

---

