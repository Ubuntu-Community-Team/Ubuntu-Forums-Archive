---
title: "Ubuntu Server nonGUI doesn't know GUI installed, so can't uninstall the GUI"
date: 2009-12-13
forum: General Help
---

### Post by MKVCrazy on 2009-12-13
I have Ubuntu Server 9.10 and I've installed the GUI using the following command.
```
apt-get install ubuntu-deskop
```
As you can see that's the standard installation and I even install NX server so I can connect to the GUI through NoMachine (!M).

But now I want to uninstall that standard version because I want it to reduce as much as resources usage possible since it's a server. So I go and type the following command in my SSH tunnel.
```
apt-get remove ubuntu-desktop
```

Guess what, it says "ubuntu-desktop is not installed so nothing to remove". I am even using the GUI version at the time I did this. It doesn't see the installed ubuntu-desktop so I cannot install my lightweight version of ubuntu :(

How can I uninstall it?

EDIT: I've did searches and found how to uninstall ubuntu-desktop but they only say to use the following command:
```
apt-get remove ubuntu-desktop
```

But mine doesn't see it's installed so I cannot follow those articles.

---

### Post by mac9416 on 2009-12-13
Hey, MKVcrazy,

ubuntu-desktop is what's called a meta-package. It does not contain any software itself, it simply depends on other packages. So when removing ubuntu-destop you are not removing the dependencies, only the metapackage.

So how do you get rid of ubuntu-desktop dependencies? Unfortunately it's not very easy. After removing ubuntu-desktop, you'll need to find the packages that ubuntu-desktop depends on by running 'apt-cache show ubuntu-desktop'. Then you will either have to 'apt-get remove' the entire list of dependencies, or select the packages you know you want to remove.

I have spent a lot of time slimming down the default Ubuntu install on my machine by removing ubuntu-desktop and its dependencies. It is rather time-consuming if you don't want to remove *all* the dependencies.

Good luck!

---

### Post by MKVCrazy on 2009-12-14
Hi, no there's nothing I want from the GUI package. I want it back like I first installed the Ubuntu Server non-GUI. Is there a all in 1 step for this?

---

### Post by mac9416 on 2009-12-14
If I was better at BASH, I could probably do it in one line. However, Python is more my cup of tea. 

I haven't been able to test this thoroughly (because I kinda want to hang on to some of those packages) but I'm fairly sure it will work. Just save the code on your server as a .py file, make it executable, and run it as root.

```
#!/usr/bin/python

import commands

packages = ''

for line in commands.getoutput('apt-cache show ubuntu-desktop').split('\n'):
    if line.startswith('Depends: '):
        packages += '%s ' % (' '.join(line[9:].split(', ')))
    elif line.startswith('Recommends: '):
        packages += '%s ' % (' '.join(line[12:].split(', ')))
        
print 'Packages to be removed:\n%s' % (packages)
answer = 'n'
answer = raw_input('Are you sure you want to remove these %i packages? [y/N] ' % (len(packages))).lower().strip()

if answer == 'y':
    print 'Removing packages...',
    status, output = commands.getstatusoutput('apt-get remove -y %s' % (packages))
    if status == 0:
        print ' Done.'
    else:
        print ' Failed.'
        print '=== Output: ===\n%s\n===============' % (output)
else:
    print 'Abort.'
```

Disclaimer: this code works with APT as root - very dangerous. Read and try to understand what the code does and consider carefully before running it. I am not responsible for any havok wreaked.

Disclaimers aside, this should make removing ubuntu-desktop fairly easy.

Good luck!

---

### Post by MKVCrazy on 2009-12-15
Hi, I tried the script. It removed 2813 packages. Below is the result of the script. There's no drop down menus in under "System". I'm impress how it removes many packages just by a little of work but not as I want exactly.

What I'm trying to gain is, let's say when I first installed the Ubuntu Server non-GUI it has 1000 packages then goes upto 1300 packages when the GUI is installed. I want to go back to the 1000 packages.

It's just not possible beside reinstall or there IS a way(s) to do what I've mentioned above?

---

### Post by mac9416 on 2009-12-15
Well, the only way I can think of getting back to the 1000 packages is to look back at the APT logs and see what packages were installed with ubuntu-desktop. I am not sure what log would contain that info, but you might check /var/log/apt/term.log.

---

### Post by MKVCrazy on 2009-12-15
The very first log record was started 13 Dec, 09. That's not the day I install the GUI. So I don't think it has the GUI installation logs in it :S

---

### Post by lewisforlife on 2009-12-15
This should do the trick, however, since you have probably already removed a bunch of them, you will probably keep getting a message saying "so-in-so file is not found and can't be removed".  You can them remove those packages from the list, and then run it again.

```
sudo apt-get remove acpid alacarte alsa-base alsa-utils anacron apmd bc ca-certificates checkbox-gtk consolekit cups cups-bsd cups-client cups-driver-gutenprint dc dcraw desktop-file-utils doc-base eog evince fast-user-switch-applet file-roller foomatic-db foomatic-db-engine foomatic-filters gcalctool gconf-editor gdebi gdm gedit genisoimage ghostscript-x gnome-about gnome-app-install gnome-applets gnome-control-center gnome-icon-theme gnome-media gnome-menus gnome-nettool gnome-panel gnome-power-manager gnome-session gnome-session-canberra gnome-system-monitor gnome-system-tools gnome-terminal gnome-themes-selected gnome-themes-ubuntu gnome-utils gstreamer0.10-alsa gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gtk2-engines gtk2-engines-pixbuf gucharmap hal inputattach language-selector launchpad-integration lftp libgl1-mesa-glx libgnome2-perl libgnomevfs2-bin libgnomevfs2-extra libpam-ck-connector libsasl2-modules libxp6 metacity nautilus nautilus-sendto notify-osd openprinting-ppds pcmciautils pnm2ppa pulseaudio pulseaudio-esound-compat rarian-compat readahead rss-glx screen screensaver-default-images seahorse smbclient software-properties-gtk ssh-askpass-gnome synaptic system-config-printer-gnome tangerine-icon-theme ttf-bitstream-vera ttf-dejavu-core ttf-freefont ubuntu-artwork ubuntu-sounds unzip update-manager update-notifier usplash usplash-theme-ubuntu wireless-tools wpasupplicant x-ttcidfont-conf xdg-user-dirs xdg-user-dirs-gtk xkb-data xorg xscreensaver-data xscreensaver-gl xterm yelp zenity zip
```

Disclaimer: same as above, I am not responsible if this messes anything up, please make sure you actually want to remove this list of packages before running.

---

### Post by mac9416 on 2009-12-15
Even that command will not fully remove the packages installed by ubuntu-desktop, though it will remove about 10 packages that my script did not.

About the log, apparently it only saves so many installation records, then writes over them.

Interesting... Perhaps removing the dependencies of gnome-desktop-environment would get you closer to being GUI-free.

```
sudo apt-get remove gnome-core alacarte brasero cheese deskbar-applet dmz-cursor-theme ekiga epiphany-browser gnome-www-browser evince evolution evolution-data-server fast-user-switch-applet file-roller gcalctool gconf-editor gdm gnome-backgrounds gnome-about gnome-keyring gnome-media gnome-menus gnome-netstatus-applet gnome-nettool gnome-power-manager gnome-screensaver gnome-system-monitor gnome-system-tools gnome-network-admin gnome-themes gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-alsa gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-tools gtk2-engines gucharmap seahorse sound-juicer swfdec-gnome totem-gstreamer totem-xine totem-plugins vinagre vino zenity libgnomevfs2-bin libgnomevfs2-extra libgnome2-perl desktop-base gksu gnome-accessibility fam gnome-games
```

Once again, look that list over and be very certain you want to part with those packages before hitting enter.

---

### Post by MKVCrazy on 2009-12-15
I did a reinstall of the Ubuntu Server and now I'm good with 800 installed :)

---

### Post by mac9416 on 2009-12-15
OK, good. Sorry it took a reinstall to get things straightened out, but sometimes that's the best way to go.

Best of luck!

---

