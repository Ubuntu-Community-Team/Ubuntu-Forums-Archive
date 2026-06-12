---
title: "Ubuntu Mini"
date: 2011-06-06
forum: General Help
---

### Post by antrock101 on 2011-06-06
Hello,

My first post here, my main knowledge is with CentosOS for our work servers, However we have a host of netbooks which I'm trying to create a minimal install for, I've managed to install and get a windows manager working after much debate. However I'm having a few key issues.

1: All Ubuntu branding needs removing eg splash screens replaced with company logo?

is this possible and does it break terms and conditions

2: Can I still use the Ubuntu repositories without break the t&c them?

3: I'm currently using lxde however i'm not keen on a DE i'd rather have a windows manager then something like thunar, can anyone reccomend a jazzy looking wm (i've currently looked at icewm and fluxbox)  Or if there is none can i possible install the gnome shell for instance without all the apps such as calculator?

4: I'm struggling to get wifi drivers, I know there availble as a regular install of ubuntu runs with no tweaking and i can connect

5: Are there any decent alternatives to WICD for my wifi connections

I know its possible to start with xubuntu but i feel making my own package list will help me learn alot more about linux.

Thanks for your help

Ant

---

### Post by seawolf167 on 2011-06-06
Here is a [walkthrough ]("https://help.ubuntu.com/community/Installation/LowMemorySystems")for installing a minimal system

#1. Not sure
#2. Not sure
#3. I like fluxbox, though you can always fall back on gnome2
#4. If you know drivers are available you should be able to simply search for them, download and install, else you can take a look [here ]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")if your card isn't supported
#5. The only alternative I'm aware of is [NetworkManager]("https://help.ubuntu.com/community/NetworkManager")

---

### Post by antrock101 on 2011-06-06
Thanks for the reply, I tried Flux box, wasn't a fan personally. Althought I may just need to read more about setting it up, I'm looking at enlightenment atm. Would I find all the wifi drivers online somewhere I'm not sure if there is a repository online I can search

---

### Post by seawolf167 on 2011-06-06
There is probably a repo somewhere that I'm not aware of, but you can always download and install them directly (a quick google search for you hardware name and model should do the trick). As an example, here are all the [Intel Wireless WiFi Link drivers]("http://intellinuxwireless.org/?n=downloads").

---

### Post by antrock101 on 2011-06-06
Found the issue, on kbuntu and ubuntu i have to go to System > Administration > Hardware Drivers to activate my drivers, is there a way to do this in terminal as mini does not have them.

On my distro i'm also looking to install the program hardware drivers and network manager but I am struggling to find the package names as there quite generically named programs

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **antrock101 said:**
> Found the issue, on kbuntu and ubuntu i have to go to System > Administration > Hardware Drivers to activate my drivers, is there a way to do this in terminal as mini does not have them.

On my distro i'm also looking to install the program hardware drivers and network manager but I am struggling to find the package names as there quite generically named programs

You could try Openbox PCLinuxOS?

---

### Post by antrock101 on 2011-06-07
I'd rather create my own if i'm honest

---

### Post by nothingspecial on 2011-06-07
Look at bhodi linux which is based on ubuntu

It comes with enlightenment, firefox, lxterminal, leafpad and er, that's about it. You get a nice looking de that you can install what you want on.

[http://www.bodhilinux.com/about.php](http://www.bodhilinux.com/about.php)

---

### Post by antrock101 on 2011-06-08
I have a weird issue, I install ubuntu server not choosing any type of install and selecting f4 at the start for minimal. It boots up fine, I install xorg and e17 along with slim and remastersys. However when I reboot sometimes it seems to boot up in some really dumbed down gnome wm and I have no idea why :S I thought I got rid of most of it

---

### Post by seawolf167 on 2011-06-08
> **antrock101 said:**
> I have a weird issue, I install ubuntu server not choosing any type of install and selecting f4 at the start for minimal. It boots up fine, I install xorg and e17 along with slim and remastersys. However when I reboot sometimes it seems to boot up in some really dumbed down gnome wm and I have no idea why :S I thought I got rid of most of it

When you installed xorg, i.e.

```
sudo apt-get install xserver-xorg xserver-xorg-core
```

what did you install for a window manager after that?

---

### Post by antrock101 on 2011-06-08
yeah although xorg is the only thing I installed

---

### Post by antrock101 on 2011-06-08
sudo apt-get xorg
sudo apt-get e17
sudo apt-get dolphin
sudo apt-get remastersys
sudo apt-get jocky-gtk
 
this is the list

---

### Post by seawolf167 on 2011-06-08
> **antrock101 said:**
> yeah although xorg is the only thing I installed

My guess would be the "dumbed down" gnome-type window manager is one that was available by default without you specifying your own window manager to install and use (like fluxbox, openbox, etc.)

---

### Post by antrock101 on 2011-06-08
oops sorry I ment xorg and e17 are the only things, I was wondering if remastersys or jockey-gtk (the ubuntu hardware manager) would have installed them.
 
I've tried uninstalling all gnome desktop with no luck, I'm very confused why it's even installing

---

### Post by antrock101 on 2011-06-08
Just another thought is enlightenment using any gnome components, this is really confusing me

---

### Post by antrock101 on 2011-06-08
ok i've installed slim and i'm trying to resolve it by changing what starts up, in slim.conf i added session e17 and removed gnome. in xinitrc I added exec enlightment_start

still booting gnome, i'm really lost now

---

### Post by antrock101 on 2011-06-09
heads up for people trying this, jockey-gtk installs gnomes, jockey-common work however, Now I just have to find the package to open .deb and change splash screens and i'll be happy

---

