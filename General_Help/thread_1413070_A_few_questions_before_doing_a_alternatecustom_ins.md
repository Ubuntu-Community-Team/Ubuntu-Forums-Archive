---
title: "A few questions before doing a alternate/custom install."
date: 2010-02-22
forum: General Help
---

### Post by Linuxperiment on 2010-02-22
EDIT: This thread can be closed now. Thanks!

---

### Post by akakingess on 2010-02-22
> **Linuxperiment said:**
> Hi everyone. I'm stuck between picking which Ubuntu I want to use for a custom "alternate" install. I have a LOT of questions and I'm not the most adept with Linux, so please be nice :)

I have a few generic questions about various versions of Ubuntu.

1. Which version of Ubuntu is the most stable and has the least bugs? It's between these three: 8.04 LTS, 8.10, and 9.04. Logically 8.04 should be the most stable since it has been out the longest and has the longest support cycle, but if fixes are made in 8.04 aren't they supposed to be fix in 8.10 and so on? I do not want to use 9.10 as it was very buggy for me and I'll never go to it again :D

2. The laptop hardware is AMD Athlon Neo MV-40 and ATI Radeon X1250. Which version of the alternate install am I supposed to use for this? Intel x86 or AMD64? I'm not sure what the difference is.
That is the difference between 32-bit and 64-bit hardware. I am not sure about MV-40, but you should check if it is 64-bit and if so, go with that install.  I would suggest 9.04, of course I am also running 9.10 without too many issues, so I guess it's either hit or miss.

> **Linuxperiment said:**
> 3. I have a list of applications I want to install through the cli, but I don't know EXACTLY what to type to install them (IE: sudo apt-get install [application]). Does anyone have a site or something that has a list of them? If not, can anyone tell me what they are for this list:

GIMP
Opera
FileZilla
aMule
Azureus
Skype
Flash Player
Thunderbird
Pidgin
XChat IRC
Adobe Reader
OpenOffice Writer
OpenOffice Calc
VLC Media Player
Brasero CD/DVD Creator
Multimedia Codecs
True Type Fonts
Java
BleachBit

Thank you in advance for any information I can get.
All of these I think are available within Synaptic Package Manager except maybe Opera which you should be able to get from their site as download.

---

### Post by Linuxperiment on 2010-02-22
> **akakingess said:**
> All of these I think are available within Synaptic Package Manager except maybe Opera which you should be able to get from their site as download.

Yeah but if I'm doing an alternate install using the cli I'm going to be typing out everything I want to install so I might as well get those over with.

Also, I'm just trying to find a stable/not buggy version of Ubuntu to run. Is there any actual concrete evidence of which ones have the least bugs?

---

### Post by ankspo71 on 2010-02-22
Hi,
If you prefer to install applications by command line and you don't know the file names to install them, then your best bet is to use:
```
apt-cache search program-name
```if you would like more details on a package:
```
apt-cache show program-name
```for more information on apt-cache and apt-get, see:
```
man apt-cache
``````
man apt-get
```If you are going for a larger sized desktop. then you might want to include ' synaptic ' to make installing packages easier.
Oh yeah, sometimes you need to update your repositories before you can start installing anything:
```
sudo apt-get update
```An easy way to learn what package you need ahead of time is to go inside synaptic package manager, search for a package name, then look at it's dependencies. For example, if you looked at the meta-package named 'ubuntu-desktop', you would see that it uses 'update-manager' to get updates, 'jockey-gtk' as the hardware driver manager, and 'gdm' as the display manager, 'file-roller' as the archive manager, and so on.
Hope this helps some.

---

### Post by Linuxperiment on 2010-02-22
I have never done an alternate install before, but I've looked at tutorials at random sites that always use the cli. I'm wondering, with an alternate install, do I actually have to use the cli/terminal or can it be done through a graphical interface? Or, is there a way I can install a base system + synaptic package manager then just install all of these programs?

Sorry for all the newbie questions, I'm just trying to learn so I don't end up having a useless laptop.

---

### Post by ankspo71 on 2010-02-22
Hi,

"can it be done through a graphical interface? Or, is there a way I can install a base system + synaptic package manager then just install all of these programs?"

yes

The installation of Linux will install with a graphical interface, whether it will be a full ubuntu install or a cli only install. 

Here is the alternate cd in action [http://www.youtube.com/watch?v=IH7QQ3WHZBs](http://www.youtube.com/watch?v=IH7QQ3WHZBs)

If you choose the cli only option, it will use the graphical interface to install the base system, but it will not include a desktop. This is were the cli comes in. The easiest way to go about that is to get the desktop installed just after installing the base system.

If you would like gnome, the very basics that I am aware of is:
```
sudo apt-get install gnome-core gdm
```Xfce minimal:
```
sudo apt-get install xfce4 xdm
```You can optionally add ' synaptic ' to the list if you like.
Once you get a desktop and a display manager installed, reboot, then you can work from your desktop.

---

### Post by Luke Little on 2010-02-22
The "alternate install" wields an intuitive interface. After installing the "base," you would elect to install your preferred additional packages. 

Also, Hardy Heron is the most stable Ubuntu distribution,  but the differences in stability between the mentioned distributions are not material. I work on Karmic Koala.

---

### Post by Linuxperiment on 2010-02-22
Ok everyone. Thanks for the advice. I should probably do the base install with synaptic, then download everything from there. I wonder, will it be simple for me to get wireless once I get the base system down or will I have to do some "custom work" to get it? For example, if I install the network manager, will in intuitively find my wireless and work from there? Here's my current idea of the code for now after I do the basic install:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

```
sudo apt-get install xorg gdm acpi-support gnome-session gnome-menus gnome-panel 
gnome-applets gnome-volume-manager gnome-power-manager metacity nautilus compiz powernowd
gnome-screensaver xscreensaver menu gnome-utils gnome-system-tools libgnomevfs2-extra smbfs
gnome-app-install app-install-data-commercial update-manager update-notifier jockey-gtk 
network-manager-gnome synaptic
```

Then after this, I'll figure out the applications. Does this look okay? If I do all of this, will I have a good/basic desktop with wireless working? Or should I just do what you said and do this:

```
sudo apt-get install gnome-core gdm synaptic
```

and then install from the synaptics package manager from there? I'm not sure what gnome-core gdm includes, so please help clarify if either of the codes are ok.

EDIT: Tried to make the "code" look easier to read.

---

### Post by Linuxperiment on 2010-02-22
I guess I got my definitions/ideas confused. I posted a thread in the Installation/Upgrade section only to find out that I'm looking for a minimal install (supposedly). I'm sort of confused, but I'm still wondering if I should be using the alternate install CD or minimal install CD with thoes scripts. Any help? :)

---

### Post by akakingess on 2010-02-22
> **Linuxperiment said:**
> I guess I got my definitions/ideas confused. I posted a thread in the Installation/Upgrade section only to find out that I'm looking for a minimal install (supposedly). I'm sort of confused, but I'm still wondering if I should be using the alternate install CD or minimal install CD with thoes scripts. Any help? :)

You should be good with a normal install, this will automatically (it did for me anyway) install base+gnome (or whichever you choose) and from there you should be able to get all of your apps installed. Also, as far as the wireless goes, that could turn out to be the trickiest part, but hopefully it will see the wireless card/chipset upon install and all should be good, you will just have to select it from within the network manager, which also should default to being on the top bar within gnome. It should show available networks and you will just have to select yours and enter any keys necessary for your security on your router (not any different from a Windows network selection).

BTW: the more recent version you choose, the best chance you have of the wireless working out of the box, without having to connect and get an update (a semi catch-22 at which point quite a few people get frustrated, but I just had the same happen on a Windows install over the weekend).

---

