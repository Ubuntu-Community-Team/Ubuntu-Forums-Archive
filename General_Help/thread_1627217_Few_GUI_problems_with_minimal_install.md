---
title: "Few GUI problems with minimal install"
date: 2010-11-21
forum: General Help
---

### Post by Oxwivi on 2010-11-21
I installed a minimal Ubuntu with a complete functional GUI, but facing a few problems.
  
[LIST]
[*]nm-applet's icon won't show in the notification area, but I can  connect to wired internet fine. I am not able to configure my wireless  or VPN this way.
[*]gksu's authentication screen is different from the usual graphical  authentication - the screen turns gray as usual, but there are more  options like save password for this session or keyring. And most  importantly, **it won't accept my password no matter what**.
[*]And lastly, Gwibber seems to install no matter what, but there's not  a single package in my knowledge that I installed has anything related  to Gwibber.
[/LIST]
  I would welcome any help regarding these three issues. I did not  mention what packages I installed, because the list is long, but I will  do so if anyone requests.

  Thank you in advance!

[Posted in Ask Ubuntu as well.]("http://askubuntu.com/questions/14276/few-gui-problems-with-minimal-install")

---

### Post by Oxwivi on 2010-11-21
Additionally, if anyone can tell  me how to install restricted drivers on command line, instead of having  to install jockey-gtk it will be extremely welcome.

---

### Post by NightwishFan on 2010-12-03
Use jockey-text. It will complain about missing GTK or something, but it works. For example, to update the data base, check for drivers, list them, and the install one:

```
jockey-text -u
```
```
jockey-text -c
```
```
jockey-text -l
```
```
jockey-text -e nameofdriver
```

To remove a driver use:
```
jockey-text -d nameofdriver
```

---

### Post by Oxwivi on 2010-12-03
And I'm gonna need to install jockey-text for that, no doubt?

---

### Post by NightwishFan on 2010-12-03
Possibly. I am unsure. I never used it from a true minimal install (as I never had need of one).

---

### Post by Paqman on 2010-12-03
> **Oxwivi said:**
> 
[*]And lastly, Gwibber seems to install no matter what, but there's not  a single package in my knowledge that I installed has anything related  to Gwibber.


What desktop meta-package are you installing? And what other packages?

---

### Post by Oxwivi on 2010-12-03
No desktop meta-package. Want the whole package list I installed?

---

### Post by QLee on 2010-12-03
[QUOTE=Oxwivi]Additionally, if anyone can tell  me how to install restricted drivers on command line, instead of having  to install jockey-gtk it will be extremely welcome.[/QUOTE]
Generally speaking, from the CLI you would, apt-get install <package_name>, after doing an, apt-get update, to refresh the packages list to the latest versions. You need to know which package you want, though. If I was doing it, I would also do an, apt-get upgrade, after I did the, apt-get update, before I installed a new package.

---

### Post by Paqman on 2010-12-03
> **Oxwivi said:**
> No desktop meta-package. Want the whole package list I installed?

Yeah, go for it. For future reference, gnome-core is a good place to start. After that you really only need xorg, gdm, network-manager-gnome, indicator-applet-session and gnome-themes to have a pretty good desktop.

The script in my sig takes a lot of the tedious package research out of using the minimal install, btw.

---

### Post by Oxwivi on 2010-12-03
I've considered the script, but not knowing what packages it installs, and more important how to get the package on a minimal install to run it has put me off.

Anyway, here's the list:```
alacarte
alsa-base
alsa-utils
eog
evince
file-roller
gconf-editor
gdm
gedit
gnome-applets
     -control-center
     -session
     -panel
     -terminal
gstreamer0.10-alsa
             -plugins-base-apps
             -pulseaudio
gtk2-engines
    -pixbuf
indicator-applet-session
nautilus
notify-osd
pulseaudio
software-center
software-properties-gtk
system-config-printer-gnome
ubuntu-artwork
ubuntu-sounds
unrar
unzip
update-manager
update-notifier
wireless-tools
xorg
app-install-data-partner
empathy
firefox
firefox-gnome-support
hplip
indicator-messages
network-manager
plymouth-theme-ubuntu-logo
rhythmbox
totem
transmission-gtk
ttf-ubuntu-font-family
xul-ext-ubufox
```

---

### Post by Paqman on 2010-12-06
Your best friend is the site: [packages.ubuntu.com](packages.ubuntu.com). You can use it to research what the dependencies are for every package. Just from a quick look at your package list i've spotted several packages you don't need to install explicitly, since they're dependencies of others you're installing. There's probably quite a few more (i'm pretty sure you don't have to tell it to install pulse, for example).

As for you wifi problem, i'd suggest installing network-manager-gnome instead of plain old network-manager, as it includes all the keyring stuff you need for wifi.

Your Gwibber problem is because indicator-applet-session depends on the new "me-menu" (indicator-me) in Maverick, and that depends on Gwibber.

```
alacarte
alsa-base
alsa-utils
evince
file-roller
gconf-editor
gdm
gstreamer0.10-alsa
gstreamer0.10-plugins-base-apps
gstreamer0.10-pulseaudio
gtk2-engines
gtk2-pixbuf
indicator-applet-session
notify-osd
pulseaudio
software-center
system-config-printer-gnome
ubuntu-artwork
ubuntu-sounds
unrar
unzip
update-manager
update-notifier
xorg
app-install-data-partner
empathy
firefox-gnome-support
hplip
indicator-messages
network-manager-gnome
plymouth-theme-ubuntu-logo
rhythmbox
totem
transmission-gtk
ttf-ubuntu-font-family
xul-ext-ubufox
```

---

### Post by Oxwivi on 2010-12-07
Is your list all I need? What about the shutdown button that comes with Me-Menu?

---

### Post by Paqman on 2010-12-07
> **Oxwivi said:**
> Is your list all I need? What about the shutdown button that comes with Me-Menu?

The list I posted was just your one tidied up a little. The shutdown button is part of indicator-applet-session IIRC. If you wanted one that didn't have the me-menu (and therefore didn't come with Gwibber) you could try the vanilla Gnome one called indicator-applet. I've not actually tried that myself, but it'd be worth a go.

If in doubt start with the bare minimum:

gnome-core
gdm
xorg
indicator-applet(-session)
network-manager-gnome

(it'll be ugly though, you may want to chuck in a theme package of some flavour)

Then just add things as you find you need them.

---

### Post by Oxwivi on 2011-02-06
Sorry for the late [very] reply, didn't have the opportunity to try it out at all. My brother-in-law is using the bare-bones version you recommended, but the network icon still didn't show.

---

