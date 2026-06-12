---
title: "Can't get passed broken packages/dependencies"
date: 2012-04-15
forum: General Help
---

### Post by isaacj87 on 2012-04-15
Hello all,

I'm currently on Ubuntu 11.10 x86_64 and I was attempting to install Kubuntu/KDE packages. I've actually done this a few times (and removed Kubuntu as well), but somehow I screwed it up this time. I ran:

```
sudo apt-get install kubuntu-desktop
```

While apt-get was downloading the necessary packages, I realized I forgot to enable the kubuntu-backports PPA. I killed the process, enabled the PPA, and tried to keep going, but apt-get is stuck in some dependency hell.

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 kubuntu-desktop : Depends: ark but it is not going to be installed
                   Depends: dolphin but it is not going to be installed
                   Depends: kde-window-manager
                   Depends: kde-workspace-bin but it is not going to be installed
                   Depends: kdemultimedia-kio-plugins but it is not going to be installed
                   Depends: kdepasswd but it is not going to be installed
                   Depends: kdm but it is not going to be installed
                   Depends: khelpcenter4 but it is not going to be installed
                   Depends: klipper but it is not going to be installed
                   Depends: kmix but it is not going to be installed
                   Depends: konsole but it is not going to be installed
                   Depends: ksnapshot but it is not going to be installed
                   Depends: ksysguard but it is not going to be installed
                   Depends: language-selector-kde but it is not going to be installed
                   Depends: okular but it is not going to be installed
                   Depends: plasma-desktop but it is not going to be installed
                   Depends: plasma-netbook but it is not going to be installed
                   Depends: software-properties-kde but it is not going to be installed
                   Depends: systemsettings but it is not going to be installed
                   Recommends: akregator but it is not going to be installed
                   Recommends: amarok but it is not going to be installed
                   Recommends: apport-kde but it is not going to be installed
                   Recommends: apturl-kde but it is not going to be installed
                   Recommends: bluedevil but it is not going to be installed
                   Recommends: dragonplayer but it is not going to be installed
                   Recommends: gstreamer0.10-qapt but it is not going to be installed
                   Recommends: gwenview but it is not going to be installed
                   Recommends: jockey-kde but it is not going to be installed
                   Recommends: k3b but it is not going to be installed
                   Recommends: kaccessible but it is not going to be installed
                   Recommends: kaddressbook but it is not going to be installed
                   Recommends: kamera but it is not going to be installed
                   Recommends: kate but it is not going to be installed
                   Recommends: kcalc but it is not going to be installed
                   Recommends: kde-config-touchpad but it is not going to be installed
                   Recommends: kdepim-kresources but it is not going to be installed
                   Recommends: kdepim-runtime but it is not going to be installed
                   Recommends: kdepim-strigi-plugins but it is not going to be installed
                   Recommends: kdepim-wizards but it is not going to be installed
                   Recommends: kdesudo but it is not going to be installed
                   Recommends: kmag but it is not going to be installed
                   Recommends: kmail but it is not going to be installed
                   Recommends: kmousetool but it is not going to be installed
                   Recommends: knotes but it is not going to be installed
                   Recommends: kontact but it is not going to be installed
                   Recommends: kopete but it is not going to be installed
                   Recommends: korganizer but it is not going to be installed
                   Recommends: kpat but it is not going to be installed
                   Recommends: kppp but it is not going to be installed
                   Recommends: ksystemlog but it is not going to be installed
                   Recommends: ktorrent but it is not going to be installed
                   Recommends: kubuntu-firefox-installer but it is not going to be installed
                   Recommends: kubuntu-notification-helper but it is not going to be installed
                   Recommends: kvkbd but it is not going to be installed
                   Recommends: kwalletmanager but it is not going to be installed
                   Recommends: libreoffice-kde but it is not going to be installed
                   Recommends: muon but it is not going to be installed
                   Recommends: muon-installer but it is not going to be installed
                   Recommends: muon-notifier but it is not going to be installed
                   Recommends: partitionmanager but it is not going to be installed
                   Recommends: plasma-widget-facebook but it is not going to be installed
                   Recommends: plasma-widget-kimpanel but it is not going to be installed
                   Recommends: plasma-widget-networkmanagement but it is not going to be installed
                   Recommends: plasma-widgets-addons but it is not going to be installed
                   Recommends: printer-applet but it is not going to be installed
                   Recommends: qapt-deb-installer but it is not going to be installed
                   Recommends: quassel but it is not going to be installed
                   Recommends: rekonq but it is not going to be installed
                   Recommends: system-config-printer-kde but it is not going to be installed
                   Recommends: usb-creator-kde but it is not going to be installed
                   Recommends: userconfig but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


I've tried many things to get pass this: 

```
sudo apt-get install -f
```

...which didn't work. I also tried doing this:

```
sudo apt-get clean && sudo apt-get autoremove
```

...which also didn't clear things up. I also tried:

```
sudo dpkg --remove --force-remove-reinstreq kubuntu-desktop

```

...but that didn't work either. Fortunately, I'm still able to update my system and install any other packages as well, but I get no joy when trying to install Kubuntu. Is there any way to get around this?

---

### Post by 23dornot23d on 2012-04-15
You could try aptitude .... its good for some large dependency problems as it tries to work out other alternatives - each time you refuse its first set of dependency solutions - it will
come back with others ....

sudo apt-get install aptitude

sudo aptitude update

sudo aptitude install kde-full

post back any output ..... depends where you crashed out ..... on the downloading part
its not so bad ..... but beyond that - things tend to get into a mess quickly

---

### Post by isaacj87 on 2012-04-16
> **23dornot23d said:**
> You could try aptitude .... its good for some large dependency problems as it tries to work out other alternatives - each time you refuse its first set of dependency solutions - it will
come back with others ....

sudo apt-get install aptitude

sudo aptitude update

sudo aptitude install kde-full

post back any output ..... depends where you crashed out ..... on the downloading part
its not so bad ..... but beyond that - things tend to get into a mess quickly

Firstly, thanks for the prompt reply. I tried using aptitude, but the options it offered weren't any good (i.e. vital packages were going to be removed).

In any case, I think something was funky in the backports PPA. I just ran a repo refesh and everything is installing now. Go figure, as soon I make a thread, everything is working again... ;)

Thanks for the help!

---

### Post by 23dornot23d on 2012-04-16
Good to hear ..... your welcome .... ):P

---

