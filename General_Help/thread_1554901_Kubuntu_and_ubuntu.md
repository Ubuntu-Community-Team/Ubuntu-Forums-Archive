---
title: "Kubuntu and ubuntu ?"
date: 2010-08-17
forum: General Help
---

### Post by binarylife on 2010-08-17
Can I have Kubuntu As a session ? 
thanks

---

### Post by sydbat on 2010-08-17
> **binarylife said:**
> Can I have Kubuntu As a session ? 
thanksSure. You can install all the different, supported desktop environments through Synaptic or via apt-get. 

I have my 3 favourites (Ubuntu, Kubuntu and Xubuntu) installed and go into each when I get the hankering. 

Just log out and back in, choosing which desktop you want.

---

### Post by mitsios on 2010-08-17
When logging in, on the bottom of the screen you will see you have options between Gnome/KDE. Gnome is the window manager used in Ubuntu, and KDE the window manager used in Kubuntu.

---

### Post by Dustin2128 on 2010-08-17
yup, just apt-get kubuntu/lubuntu/xubuntu-desktop. The rest of the wms don't have ubuntu after them.

---

### Post by binarylife on 2010-08-17
Thanks all =) I love linux!

---

### Post by mitsios on 2010-08-17
> **binarylife said:**
> Thanks all =) I love linux!
That's the spirit!

---

### Post by binarylife on 2010-08-17
> **mitsios said:**
> That's the spirit!

Yup:) , but HowTo install it form the Synaptic exactly please ):??

---

### Post by sydbat on 2010-08-17
> **binarylife said:**
> Yup:) , but HowTo install it form the Synaptic exactly please ):??System > Administration > Synaptic, type in (one at a time) kubuntu, xubuntu, lubuntu, whatever other DE in the search window and choose "install". Any/all dependencies will show up.

---

### Post by binarylife on 2010-08-17
> **sydbat said:**
> System > Administration > Synaptic, type in (one at a time) kubuntu, xubuntu, lubuntu, whatever other DE in the search window and choose "install". Any/all dependencies will show up.


thanks a lot..! : )

---

### Post by alaukikyo on 2010-08-17
> **Dustin2128 said:**
> yup, just apt-get kubuntu/lubuntu/xubuntu-desktop. The rest of the wms don't have ubuntu after them.

after 

sudo apt-get install kubuntu-desktop 

it gives the following output
> 

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: ark but it is not going to be installed
                   Depends: dolphin but it is not going to be installed
                   Depends: kde-window-manager but it is not going to be installed
                   Depends: kde-zeroconf but it is not going to be installed
                   Depends: kdebase-workspace-bin but it is not going to be installed
                   Depends: kdemultimedia-kio-plugins but it is not going to be installed
                   Depends: kdepasswd but it is not going to be installed
                   Depends: kdm but it is not going to be installed
                   Depends: khelpcenter4 but it is not going to be installed
                   Depends: klipper but it is not going to be installed
                   Depends: kmix but it is not going to be installed
                   Depends: konsole but it is not going to be installed
                   Depends: ksnapshot but it is not going to be installed
                   Depends: ksysguard but it is not going to be installed
                   Depends: ksystemlog but it is not going to be installed
                   Depends: language-selector-qt but it is not going to be installed
                   Depends: okular but it is not going to be installed
                   Depends: phonon-backend-xine but it is not going to be installed
                   Depends: plasma-desktop but it is not going to be installed
                   Depends: software-properties-kde but it is not going to be installed
                   Depends: systemsettings but it is not going to be installed
                   Recommends: akregator but it is not going to be installed
                   Recommends: amarok but it is not going to be installed
                   Recommends: apport-kde but it is not going to be installed
                   Recommends: apturl-kde but it is not going to be installed
                   Recommends: dragonplayer but it is not going to be installed
                   Recommends: freespacenotifier but it is not going to be installed
                   Recommends: gwenview but it is not going to be installed
                   Recommends: install-package but it is not going to be installed
                   Recommends: jockey-kde but it is not going to be installed
                   Recommends: k3b but it is not going to be installed
                   Recommends: kaddressbook but it is not going to be installed
                   Recommends: kamera but it is not going to be installed
                   Recommends: kate but it is not going to be installed
                   Recommends: kbluetooth but it is not going to be installed
                   Recommends: kcalc but it is not going to be installed
                   Recommends: kcm-gtk but it is not going to be installed
                   Recommends: kcm-touchpad but it is not going to be installed
                   Recommends: kdegraphics-strigi-plugins but it is not going to be installed
                   Recommends: kdepim-kresources but it is not going to be installed
                   Recommends: kdepim-runtime but it is not going to be installed
                   Recommends: kdepim-strigi-plugins but it is not going to be installed
                   Recommends: kdepim-wizards but it is not going to be installed
                   Recommends: kdesudo but it is not going to be installed
                   Recommends: kmag but it is not going to be installed
                   Recommends: kmail but it is not going to be installed
                   Recommends: kmousetool but it is not going to be installed
                   Recommends: knotes but it is not going to be installed
                   Recommends: konqueror but it is not going to be installed
                   Recommends: konqueror-nsplugins but it is not going to be installed
                   Recommends: kontact but it is not going to be installed
                   Recommends: kopete but it is not going to be installed
                   Recommends: korganizer but it is not going to be installed
                   Recommends: kpackagekit but it is not going to be installed
                   Recommends: kppp but it is not going to be installed
                   Recommends: krdc but it is not going to be installed
                   Recommends: krfb but it is not going to be installed
                   Recommends: ktimetracker but it is not going to be installed
                   Recommends: ktorrent but it is not going to be installed
                   Recommends: kubuntu-firefox-installer but it is not going to be installed
                   Recommends: kubuntu-konqueror-shortcuts but it is not going to be installed
                   Recommends: kubuntu-notification-helper but it is not going to be installed
                   Recommends: kvkbd but it is not going to be installed
                   Recommends: kwalletmanager but it is not going to be installed
                   Recommends: network-manager-kde but it is not going to be installed
                   Recommends: okular-extra-backends but it is not going to be installed
                   Recommends: openoffice.org-kde but it is not going to be installed
                   Recommends: plasma-widget-facebook but it is not going to be installed
                   Recommends: plasma-widget-folderview but it is not going to be installed
                   Recommends: plasma-widget-kimpanel but it is not going to be installed
                   Recommends: plasma-widget-kubuntu-feedback but it is not going to be installed
                   Recommends: plasma-widget-message-indicator but it is not going to be installed
                   Recommends: plasma-widget-quickaccess but it is not going to be installed
                   Recommends: plasma-widgets-addons but it is not going to be installed
                   Recommends: printer-applet but it is not going to be installed
                   Recommends: quassel but it is not going to be installed
                   Recommends: system-config-printer-kde but it is not going to be installed
                   Recommends: usb-creator-kde but it is not going to be installed
                   Recommends: userconfig but it is not going to be installed


---

### Post by alaukikyo on 2010-08-17
Just added this ppa and it worked :D
> ppa:kubuntu-ppa/backports

---

### Post by binarylife on 2010-08-17
Guys I did install kubuntu from synaptic and checked evey things connects with kubuntu ,  I'm now using kubuntu but I'm stuck in two problems ,
1) Can't Log Out from session!
2) No wireless connection !I am using ubuntu 10.04 lts
please help

---

### Post by uRock on 2010-08-17
> **binarylife said:**
> Guys I did install kubuntu from synaptic and checked evey things connects with kubuntu ,  I'm now using kubuntu but I'm stuck in two problems ,
1) Can't Log Out from session!
2) No wireless connection !I am using ubuntu 10.04 lts
please help
You may be better off starting a new thread as to catch the attention of the networking gurus.

---

