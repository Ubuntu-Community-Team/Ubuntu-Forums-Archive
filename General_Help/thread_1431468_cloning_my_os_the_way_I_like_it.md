---
title: "cloning my os the way I like it"
date: 2010-03-16
forum: General Help
---

### Post by spiky001 on 2010-03-16
I want to reinstall karmic set it up the way i like it install what i want uninstall what I dont set up passwords and all settings, Am I correct in thinking Clonezilla will do this? I then want to create an iso so I can just load disc in reinstall (if ever needed) and have pc up and working from that disc, or dose clonezilla create the iso so then I just have to burn it

---

### Post by J V on 2010-03-16
nope...

I suggest you make a script (below is my personal sample, edit BEFORE you use) and back up your /home...

```
#! /bin/bash
# Install stuff
sudo apt-get update
sudo apt-get --force-yes install simple-ccsm gedit-plugins apg ghex gmountiso glade gnome-schedule gtk-recordmydesktop iat preload sun-java6-jre sun-java6-plugin unrar playonlinux avant-window-navigator ubuntu-restricted-extras blender startupmanager clamtk cheese handbrake-gtk gimp nautilus-gksu
# 64 flash
if [ `uname -m` = "x86_64" ]
then
    sudo apt-get remove flashplugin-nonfree
    wget "http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz"
    tar -xzf "libflashplayer-*.so.tar.gz" --directory "~/.mozilla/plugins"
    rm -f "libflashplayer-*.so.tar.gz"
fi
# Stop annoying beep
echo "blacklist pcspkr" | sudo tee -a /etc/modprobe.d/blacklist
echo "Bleep disabled"
# Shortcuts
gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_terminal "Super_R"
echo "Terminal is right super"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom0/action "xkill"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom0/binding "<Control><Alt>X"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom0/name "Kill Application"
echo "Kill app is ctrl + x"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom1/action "gnome-system-monitor"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom1/binding "<Shift><Control>Escape"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom1/name "System monitor"
echo "System monitor is ctrl + shift + esc"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom2/action "nautilus /"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom2/binding "<Control>Space"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom2/name "Filesystem"
echo "Filesystem is ctrl + space"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom3/action "gksudo nautilus /"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom3/binding "<Shift><Control>Space"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom3/name "Administrator filesystem"
echo "Admin filesystem is ctrl + shift + space"
setxkbmap -option terminate:ctrl_alt_bksp
echo "Restart X is ctrl + alt + backspace"
# skype
cd /tmp
if [ `uname -m` = "x86_64" ]
then
    wget http://www.skype.com/go/getskype-linux-beta-ubuntu-64
elif [ `uname -m` = "x86_64" ]
then
    wget http://www.skype.com/go/getskype-linux-beta-ubuntu-32
fi
sudo gdebi skype-ubuntu*.deb
rm -f skype-ubuntu*.deb
cd
cd /tmp
wget http://www.mvps.org/winhelp2002/hosts.txt
cat hosts.txt | sudo tee -a /etc/hosts
rm -f hosts.txt
cd
gconftool-2 --set --type bool /apps/update-notifier/auto_launch false
gconftool-2 -set --type bool /apps/indicator-session/suppress_logout_restart_shutdown true
ccsm&
```And backup your compiz settings too...

---

