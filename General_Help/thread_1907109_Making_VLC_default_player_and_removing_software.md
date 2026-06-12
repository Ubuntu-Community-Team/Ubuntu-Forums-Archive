---
title: "Making VLC default player and removing software"
date: 2012-01-10
forum: General Help
---

### Post by charlescarroll1 on 2012-01-10
I'm running Ubuntu 11.10 with Gnome 3. I've gone to System Settings > System Info > Default Programs and set VLC as the default program for audio and video, however whenever I open a video file it opens with Totem Movie Player. 

I've considered uninstalling Totem, but I get the message 

```
To remove Movie Player, these items must be removed as well: 
The Gnome Desktop Environment - essential components
``` along with a couple plugins.

The last time I removed extra software and I got that message about Gnome essential components, when I rebooted, Ubuntu wouldn't load - it just sat at the load screen. I'm not sure if it this problem was related to the uninstall of some programs, but I'd also like to figure out how to remove software I don't use like Epiphany or Totem without it possibly screwing up my system.

So my questions are:
1) How can I make VLC the default video player, aside from going to Default Programs?
2) How can I uninstall unnecessary software without breaking my system?

Thanks!

---

### Post by charlescarroll1 on 2012-01-10
Okay, I figured out how to make VLC the default program. I right-clicked on a video file and selected Properties>Open With and selected VLC as the default player. Still odd that it didn't work under system settings>default programs.

I still have the issue of the possibility of removing unnecessary programs and breaking my system.

---

### Post by QIII on 2012-01-10
You may have to repeat that process for other file types.

As for your other question, the short answer is that you can't.  Some software is part of the metapackage for your DE or for other packages and removing them will remove the rest.

---

### Post by mc4man on 2012-01-10
> **charlescarroll1 said:**
>  Still odd that it didn't work under system settings>default programs.

I still have the issue of the possibility of removing unnecessary programs and breaking my system.

As far as the 'default' for music & video in System settings - really not much value in those settings, each one is tied to just 1 filetype - 
The default Music app just sets the app chosen as default for audio/x-vorbis+ogg
The default Video app sets the app chosen as default for video/x-ogm+ogg

In regards to removing totem & it's plugins, normally there should be no issue & nothing else removed. Are you using a straight up Ubuntu install or some other *ubuntu & or ppa's?

You could run this command & if needed post the results - note it only simulates, nothing is removed.

```
sudo apt-get -s purge totem
```

Example here on 12.04
> sudo apt-get -s purge totem
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  totem* totem-mozilla* totem-plugins*
0 upgraded, 0 newly installed, 3 to remove and 35 not upgraded.
Purg totem-plugins [3.0.1-0ubuntu12]
Purg totem-mozilla [3.0.1-0ubuntu12]
Purg totem [3.0.1-0ubuntu12]


Myself don't use totem but do use the totem-mozilla browser plugin so I leave totem installed.

As far as Epiphany (browser), I'm not aware that it is default installed in Ubuntu so if you installed it you can certainly remove it. If it's part of some non-standard  or *ubuntu install then probably something you should mention..

---

### Post by charlescarroll1 on 2012-01-11
I'm attempting to remove it from both Ubuntu Software Center and Synaptic. When I try to uninstall from Synaptic I get "To be removed: Gnome-core".

I installed Ubuntu 11.10 and then installed Gnome 3. I'm not sure if these programs came with the Gnome 3 installed. I did not install Epiphany. I think it came with the Gnome 3 installation.

I'd like to run that command if I was sure it wouldn't land me with a broken Ubuntu.

---

### Post by mc4man on 2012-01-11
gnome-core is just a meta-package, similar to ubuntu-desktop. In other words it contains basically nothing, just has quite a number of dependencies that are installed when you install it & nothing is removed if you remove it or cause it to be removed by uninstalling one of it's dependencies like totem or epiphany-browser, ect.
[see here]("http://packages.ubuntu.com/oneiric/gnome-core/filelist")
> 
I'd like to run that command if I was sure it wouldn't land me with a broken Ubuntu. 


As I said the command only **simulates** what would happen

I'm sure you have your reasons for installing gnome-core in the first place, not something I'd do here, if I wanted to use gnome-shell I'd just install it or any other app desired.

Note that gnome-core installs gdm while 11.10 uses lightdm by default, possibly your prior issue came from removing gdm & not switching back to lightdm before restarting ..?

---

### Post by charlescarroll1 on 2012-01-11
It must have installed when I installed gnome 3 because I didn't install it intentionally. 

When I was running the install, I selected gdm instead of lightdm. I figured "light" as in lite, and lite as in having less... I had/have no idea what it is. Is lightdm better? If so, how do I select it?

When I ran that command you suggested, it said gnome-core was removed in the text. As I said, the only thing I'm worrying about is Ubuntu not starting once I remove it.

---

### Post by charlescarroll1 on 2012-01-13
So, if I'm running Gnome 3 and remove "gnome-core", it shouldn't prevent the OS from starting and loading the gnome desktop?

---

### Post by mc4man on 2012-01-21
> **charlescarroll1 said:**
> So, if I'm running Gnome 3 and remove "gnome-core", it shouldn't prevent the OS from starting and loading the gnome desktop?
correct

---

### Post by charlescarroll1 on 2012-01-22
> **mc4man said:**
> correct

I removed Totem along with Gnome Essential Components (gnome-core) and it does exactly what it did a month ago. Ubuntu just sits at the load screen.

I let it sit there for a half an hour with no change.

HOW DO I FIX THIS?!??

---

### Post by mc4man on 2012-01-23
The removal of the metapackage(s) would not be the main cause of your failure to to restart into a session (ubuntu ?)
Again it's likely your use of gdm if you are still using ?

Ex.  - set up as you've **posted**
> $ sudo apt-get purge totem
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome* gnome-core* totem* totem-mozilla* totem-plugins*
0 upgraded, 0 newly installed, 5 to remove and 63 not upgraded.
After this operation, 3,080 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 266477 files and directories currently installed.)
Removing gnome ...
Removing gnome-core ...
Removing totem-plugins ...
Removing totem-mozilla ...
Removing totem ...
Purging configuration files for totem ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for menu ...


A restart using lightdm no issue at all.

Repeating the whole deal with gdm as the dm - a restart then logged into unity-2d here instead of ubuntu (unity-3d
So do you have a fallback session available? (unity-2d or gnome-session=fallback

Assuming you're still _using gdm & haven't removed the lightdm package_

Boot to the recovery mode, at the 1st screen choose the remount option.
When done, at the new option screen choose the root prompt option. In the console go 
```
 sudo dpkg-reconfigure gdm
```
Switch to lightdm, when done then go sudo reboot

---

