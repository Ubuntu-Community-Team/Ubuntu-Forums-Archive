---
title: "Minimal Gnome Installation - Questions/Advice"
date: 2011-05-25
forum: General Help
---

### Post by Cheesemill on 2011-05-25
Hi there guys.

I'm trying to install a minimal Gnome setup without any of the usually installed apps. Last time I tried this it worked fine but that was a couple of years ago (see [this thread]("http://ubuntuforums.org/showthread.php?t=1156254") if you're interested).

The closest I've got so far is to install a CLI system from the alternate install CD and then run:

```
sudo aptitude update
sudo aptitude -y full upgrade
sudo aptitude -y install xorg gdm gnome-core plymouth-theme-ubuntu-logo ubuntu-artwork jockey-gtk network-manager synaptic

```
The problem is that one of these packages (I think that it's gnome-core) installs Epiphany, Evince, Evolution, Gwibber and Ubuntu One which I don't want.

Any ideas on how to get a minimal system installed without these apps?

---

### Post by Off Topic on 2011-05-25
I did it on 3 of my machines by installing Ubuntu Server 10.10 and then run.

```
sudo apt-get install xorg gdm gnome-core synaptic gcc gnome-system-tools gnome-app-install gnome-nettool gdebi
```

Only my main PC has a full Ubuntu 10.10 Desktop install,  the other PC and netbook have the 10.10 server as described above, and my server is 11.04 with the above installed.

---

### Post by Cheesemill on 2011-05-25
Sorry Off Topic, that's still no use.

I've just tried your method and it still installs the apps that I don't want.

Can anyone tell me if there is a way that I can tell aptitude to always ignore certain packages even if they are dependancies?

Basically I need to install gnome-core but without installing any of the following packages:

```
epiphany-browser
epiphany-browser-data
evince
evince-common
evolution
evolution-common
evolution-data-server
evolution-data-server-common
evolution-plugins
evolution-webcal
gwibber
gwibber-service
gwibber-service-facebook
gwibber-service-identica
gwibber-service-twitter
ubuntuone-client
ubuntuone-control-panel
ubuntuone-control-panel-gtk
```

---

### Post by Zero2Nine on 2011-05-25
> **Cheesemill said:**
> Sorry Off Topic, that's still no use.

I've just tried your method and it still installs the apps that I don't want.

Can anyone tell me if there is a way that I can tell aptitude to always ignore certain packages even if they are dependancies?

Basically I need to install gnome-core but without installing any of the following packages:

```
epiphany-browser
epiphany-browser-data
evince
evince-common
evolution
evolution-common
evolution-data-server
evolution-data-server-common
evolution-plugins
evolution-webcal
gwibber
gwibber-service
gwibber-service-facebook
gwibber-service-identica
gwibber-service-twitter
ubuntuone-client
ubuntuone-control-panel
ubuntuone-control-panel-gtk
```

These packages are part of gnome-desktop-environment and not of gnome-core if I'm right (am checking them in Synaptic now) however gnome-core does advise gnome-desktop-environment. Is it possible to install gnome-core without gnome-desktop-environment?

---

### Post by satanselbow on 2011-05-25
are you actually installing them and then having to start again?

You can always "test" packages out from the terminal and the "apt-get -s" switch like:

```
sudo apt-get install -s ubuntu-desktop
```As said above - ubuntu desktop is basically a branded gnome-desktop - I don't think there is any reason why (ie it won't break) if you just pull evince/evolution off if you don't need them... one of the 1st things I do on a new install - well evolution anyway ;)

gnome-core still installs evince / evolution etc btw

---

### Post by aeiah on 2011-05-25
it may be the case that evolution is too integrated in gnome (isnt it related to the calendar?)

try ```
sudo apt-get install -s --no-install-recommends gnome-core
```

the -s, as mentioned above, tests.

but really, are you that bothered about gnome? xfce is very similar, or if you know what packages you want you could just use openbox etc

i use openbox+tint2+thunar and miss nothing from gnome. they all do the same kinda thing as eachother.

---

