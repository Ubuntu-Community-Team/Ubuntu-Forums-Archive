---
title: "Ubuntu 9.10 Issues"
date: 2010-02-03
forum: General Help
---

### Post by dubble on 2010-02-03
Hi all,
 
I just started using Linux and decided to install the latest Ubuntu 9.10 on my new Zotac Mag mini pc. Installation was nice and easy, but i have a few issues. I installed the latest nvidia driver 190.xx 
 
1. I turn of my visual effects from normal to none, but i don't get a dialog box to save the setting. I clearly see a difference when i turn off/on visual effects, so i know it works, but doesn't save, so every time i restart the computer i have to turn visual effects off. Do i have to reload compiz?
 
2. My desktop is over scan. I have to open Nvidia settings and reduce the overscan every time i reset the computer. I tried runing the sudo nvidia settings in terminal but always fails to save. I tried cuting and pasting the settings from the nvidia settings show details to xorg.conf but still doesn't work.
 
3. I installed gecko mplayer using the guide in this forum and tried playing a .mkv file. The video plays as if it's a slide show. The audio works fine. I installed xbmc and the video plays fine. Is there a setting that i have to adjust somewhere so that mplayer can play the file properly?
 
I am a newb to Linux, but can follow instuctions. Any help would be appreciated.

---

### Post by howefield on 2010-02-04
> **dubble said:**
> I turn of my visual effects from normal to none, but i don't get a dialog box to save the setting.

Try loading up gconf-editor and navigate to desktop > gnome > applications > window_manager and change the default to metacity.

To open gconf-editor, open a run box by pressing alt + F2 keys together and type gconf-editor. 
 
> 2. My desktop is over scan. I have to open Nvidia settings and reduce the overscan every time i reset the computer. I tried runing the sudo nvidia settings in terminal but always fails to save. I tried cuting and pasting the settings from the nvidia settings show details to xorg.conf but still doesn't work.

Try backing up your xorg.conf (rename it xorg.conf.backup or make a copy some place else) and then delete xorg.conf, run nvidia-settings and then save. 

From a terminal, (Applications > Accessories > Terminal) remove xorg.conf
```
sudo rm /etc/X11/xorg.conf
```
Then run
```
gksu nvidia-settings
```
Then save your settings to
```
/etc/X11/xorg.conf
```

If that doesn't work, revert to your backup. 
 
> 3. I installed gecko mplayer using the guide in this forum and tried playing a .mkv file. The video plays as if it's a slide show. The audio works fine. I installed xbmc and the video plays fine. Is there a setting that i have to adjust somewhere so that mplayer can play the file properly?.

Does it need to be mplayer that you use ?

VLC is a great player which will cope with just about anything you throw at it.

---

### Post by dubble on 2010-02-04
Thanks for the reply.  I decided to re-install Ubuntu 9.10 without dual boot.  This fixed my not being able to save settings.  I am not sure what happenned in the first install but i figured it didn't like re-partitioning the hard drive with win 7 installed.
 
As for the video overscan problem, i read somewhere else on this forum that it's a tv issue, not a nvidia issue.  Not an important issue considering my tv has vga input.
 
Is there a command line to retrieve/install vlc player, or should i just go to the website.
 
I am not currently at my linux computer, but i'll try it tonight.

---

### Post by howefield on 2010-02-04
> **dubble said:**
> Is there a command line to retrieve/install vlc player, or should i just go to the website.

You can install with Synaptic Package Manager or use the command line if your prefer.

```
sudo apt-get install vlc
```

This will give you version 1.02. 

The latest version is 1.05, if you wanted that, you would be best adding the repository or downloading the package from getdeb.net.

---

### Post by dubble on 2010-02-04
VLC does the same as any other player.   Is there a way to force the player to use the gpu to do the decoding?  Any way to reduce frames...  XBMC is doing something to make the video play fine.

---

