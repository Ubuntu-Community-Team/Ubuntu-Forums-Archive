---
title: "adobe flashplayer for ubuntu 8.04+ installation problem"
date: 2010-01-13
forum: General Help
---

### Post by bobmac on 2010-01-13
Folks,

I've been trying to install Adobe flashplayer 8.04+ for ubuntu from the Adobe site.

I seem to be able to download it ok and it drops the installation file on my desktop.

However, the instructions for the .deb file don't seem to work. These instructions are:

1.Click the download link to begin installation. If a dialog box appears, follow the instructions to save the installer to your desktop. 
2.Save the .deb package to your desktop, and wait for it to download completely. 
3.Double-click on the .deb package and follow the instructions to complete installation. 
-or-
Issue one of the following commands from the terminal:
dpkg --install [filename].deb 
dpkg -i [filename].deb 
4.To verify the plugin is installed in Mozilla, launch Mozilla and choose Help > About Plug-ins from the browser menu. 

I've tried all three. The first opens a couple of dialogs which have an install button which I have tried to use to install it. The result is the following message:

dpkg -i '///home/calban/Desktop/install_flash_player_10_linux.deb' ;echo RESULT=$?
(Reading database ... 204208 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.42.34-1 (using .../install_flash_player_10_linux.deb) ...
Unpacking replacement adobe-flashplugin ...
Setting up adobe-flashplugin (10.0.42.34-1) ...

RESULT=0

with the dpkg --install [filename].deb 
dpkg -i [filename].deb 

commands all I get is a message telling me that the file doesn't exist and yep I navigate to the desktop via the monitor and enter the file name - install_flash_player_10_linux.deb

I'm anything but a linux/ubuntu expert so needless to say I'm baffled as to what I'm doing wrong.

Any help (printable :-) ) will be gratefully appreciated

Bob

---

### Post by Soul-Sing on 2010-01-13
you don't want flash nonfree from the ubuntu repositories?
via ===> synaptic packgemanager?
Or are you trying to install the flash nonfree for your 64 bit system?

---

### Post by etnlIcarus on 2010-01-13
> **leoquant said:**
> you don't want flash nonfree from the ubuntu repositories?
via ===> synaptic packgemanager?
Or are you trying to install the flash nonfree for your 64 bit system?
He's still running 8.04, which includes a very old version of flash player.

Easiest way to get Flash working is to download the latest tarball from adobe and extract the libflashplayer_10*.so file to your /home/<username>/.mozilla/plugins/ folder.

You can check which version is being detected by firefox by typing about:plugins into your address bar.

---

### Post by scouser73 on 2010-01-13
> **bobmac said:**
> Folks,

I've been trying to install Adobe flashplayer 8.04+ for ubuntu from the Adobe site.

I seem to be able to download it ok and it drops the installation file on my desktop.

However, the instructions for the .deb file don't seem to work. These instructions are:

1.Click the download link to begin installation. If a dialog box appears, follow the instructions to save the installer to your desktop. 
2.Save the .deb package to your desktop, and wait for it to download completely. 
3.Double-click on the .deb package and follow the instructions to complete installation. 
-or-
Issue one of the following commands from the terminal:
dpkg --install [filename].deb 
dpkg -i [filename].deb 
4.To verify the plugin is installed in Mozilla, launch Mozilla and choose Help > About Plug-ins from the browser menu. 

I've tried all three. The first opens a couple of dialogs which have an install button which I have tried to use to install it. The result is the following message:

dpkg -i '///home/calban/Desktop/install_flash_player_10_linux.deb' ;echo RESULT=$?
(Reading database ... 204208 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.42.34-1 (using .../install_flash_player_10_linux.deb) ...
Unpacking replacement adobe-flashplugin ...
Setting up adobe-flashplugin (10.0.42.34-1) ...

RESULT=0

with the dpkg --install [filename].deb 
dpkg -i [filename].deb 

commands all I get is a message telling me that the file doesn't exist and yep I navigate to the desktop via the monitor and enter the file name - install_flash_player_10_linux.deb

I'm anything but a linux/ubuntu expert so needless to say I'm baffled as to what I'm doing wrong.

Any help (printable :-) ) will be gratefully appreciated

Bob

[COLOR="Red"]**Installing Flash Player via the Adobe website**[/COLOR]

**1** - Go to [[COLOR="Red"]**Adobe Flash**[/COLOR]]("http://get.adobe.com/flashplayer/?promoid=BUIGP")

**2** - Select **.deb for Ubuntu 8.04+** from the drop down menu

**3** - Click **Agree & Install Now**

**4** - Select **Open With** **GDebi Package Installer** in firefox or save the file and install the **.deb** file that way

---

### Post by slakkie on 2010-01-13
> **etnlIcarus said:**
> He's still running 8.04, which includes a very old version of flash player.

Easiest way to get Flash working is to download the latest tarball from adobe and extract the libflashplayer_10*.so file to your /home/<username>/.mozilla/plugins/ folder.

You can check which version is being detected by firefox by typing about:plugins into your address bar.

Hardy has also version 10 available, it is even more current then Lucid, and equal to Karmic

```

apt-cache policy adobe-flashplugin
adobe-flashplugin:
  Installed: (none)
  Candidate: 10.0.42.34-2
  Version table:
     10.0.42.34-2karmic1 0
        300 http://archive.canonical.com karmic/partner Packages
     10.0.42.34-2 0
        990 http://archive.canonical.com hardy/partner Packages
     10.0.32.18-1karmic2 0
        300 http://archive.canonical.com lucid/partner Packages

```

Please have a look at the upgrade flash link in my sig. It will help you install flash from the partner repository.

---

### Post by bobmac on 2010-01-14
Many thanks to all who answered this query. I'll try it out and see how it goes - wish me luck 

Bob

---

