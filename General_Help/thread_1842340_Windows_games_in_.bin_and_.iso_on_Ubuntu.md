---
title: "Windows games in .bin and .iso on Ubuntu"
date: 2011-09-11
forum: General Help
---

### Post by Neoteros on 2011-09-11
I have 2 games for Windows i downloaded some time ago, and in order to install them, when i had Windows, i mounted their .iso or .bin image on Daemon. I want to play these games on Ubuntu. I know there are some programs that could help me, but being a total n00b, i just don't know how to proceed. Can someone enlighten me with a step by step guide or something? Please *__*

---

### Post by donpeter06 on 2011-09-11
You can try wine. You can install it from synaptic,also crossfire is a better choice but you gotta pay inorder to download and use it. A better choice is Wine.But not all games work on it.

---

### Post by Toz on 2011-09-11
**Wine** ([http://www.winehq.org/]("http://www.winehq.org/")) is the windows compatibility later that allows windows applications to run on linux. You can read all about it at that link.

You should then head over to [http://appdb.winehq.org/]("http://appdb.winehq.org/") and search for the games that you have so that you can see how supported they are and whether they will run properly under linux (not all games or apps can and some may need extra "tweaking").

You can use an application like **furiusisomount** ([http://www.marcus-furius.com/?page_id=170]("http://www.marcus-furius.com/?page_id=170")) to mount the files and make them accessible ala Daemon Tools in Windows. To install it, look for it in the software center, or from the command line:
```
sudo apt-get install furiusisomount
```

There are some front-ends for Wine that make it easier to install and manage Windows apps and games. Playonlinux ([http://www.playonlinux.com/en/]("http://www.playonlinux.com/en/")) is one such frontend. To install it, look for it in the software centre of from the command line:
```
sudo apt-get install playonlinux
```(it will also install the required wine files)

Or, you are free to directly install **wine** and manipulate them directly. To install wine, look for it the software centre or from the command line:
```
sudo apt-get install wine
```
But you might find this a little challenging if you are new to Linux. Using a front-end like PlayOnLinux would be much easier.

Feel free to post back the names of the games that you have and maybe we can provide you with some specific advice for those games.

---

### Post by Neoteros on 2011-09-11
@ Toz: My games are Victoria II, Mount&Blade: Warband, and Europa Universalis III.

I will try to do as you suggested, thanks for the advice.

---

### Post by Toz on 2011-09-11
> **Neoteros said:**
> @ Toz: My games are Victoria II, Mount&Blade: Warband, and Europa Universalis III.

**Mount&Blade: Warband** is directly installable via PlayOnLinux. Look for it in the Games subsection of PlayOnLinux.

**Victoria II** is not directly supported by PlayOnLinux but has favourable results listed at wineHQ ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=21110]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=21110")). You could try installing it through PlayOnLinux using the "Install a non-listed program" link.

**Europa Universalis III** is not directly supported by PlayOnLinux and has mixed results listed at wineHQ ([http://appdb.winehq.org/objectManager.php?sClass=application&iId=4478]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=4478")). You could try installing it through PlayOnLinux using the "Install a non-listed program" link.

One more piece of advice: you may want to upgrade your version of PlayOnLinx. The one in the ubuntu repositories is out of date. To do so, have a look at the "Ubuntu" section of [http://www.playonlinux.com/en/download.html]("http://www.playonlinux.com/en/download.html"). If your using Natty (11.04) the command line instructions would be:
```
wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
sudo wget http://deb.playonlinux.com/playonlinux_natty.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux
```

Good luck.

---

### Post by Neoteros on 2011-09-11
thanks, i'm off to get the latest PlayOnLinux. 

The only problem is, i can't seem to install Wine correctly... the instructions on the site are a bit complicated. (can't access the Software Sources thing here [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu) in order to download the PPA, may be because information's out of date)

I also want to know what is the best iso and bin mounter around, the ones i tried, including furius, don't open mine... maybe it's because i installed Wine like **** though...

---

### Post by _d_ on 2011-09-11
> **Neoteros said:**
> The only problem is, i can't seem to install Wine correctly... the instructions on the site are a bit complicated.

First add the Wine repo to your sources list via terminal or Software Sources:

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```

Then update your package listings, which I usually like to run twice to make sure:

```
sudo apt-get update
```

And then depending on which version of Wine you want, you can either install latest stable:

```
sudo apt-get install wine1.2
```

or development

```
sudo apt-get install wine1.3
```

After Wine and any other packages are installed, simply run this command via terminal (or use the Wine menu - Configure Wine) to configure Wine:

```
winecfg
```

---

### Post by Neoteros on 2011-09-11
Guys, thank you for coping with my noobness, i'm finally starting to get a grasp on the terminal's use... a question though, i seem to remember that Wine's already included on PlayOnLinux? My problem's 50% gone, all because of you. I love you, no homo XD

---

### Post by Toz on 2011-09-11
> **Neoteros said:**
>  a question though, i seem to remember that Wine's already included on PlayOnLinux? 
Yes, if the app/game is supported by PlayonLinux, then the correct version of wine will be automatically installed and setup as part of the game installation process.

---

### Post by Toz on 2011-09-11
> **Neoteros said:**
> I also want to know what is the best iso and bin mounter around, the ones i tried, including furius, don't open mine... maybe it's because i installed Wine like **** though...

I always use the command-line to mount stuff. It works something like this:
1. Create a mount point (only once):
```
mkdir ~/mnt
```
2. Mount the iso:
```
sudo mount -t iso9660 -oloop /path/to/iso/file /home/<user>/mnt
```
3. Go to the mount point and view the contents:
```
cd ~/mnt
ls
```
...or use your file manager.

4. To unmount when you're done:
```
sudo umount /home/<user>/mnt
```

---

### Post by Neoteros on 2011-09-13
i tried to run some games, but they crash ("couldn't find any compatible Direct3D devices") if this problem is solved, i think they'll run properly, since the intros ran as smoothly as silk. What should i do to fix the problem? Seems related to DirectX

---

### Post by mastablasta on 2011-09-13
> **Neoteros said:**
> i tried to run some games, but they crash ("couldn't find any compatible Direct3D devices") if this problem is solved, i think they'll run properly, since the intros ran as smoothly as silk. What should i do to fix the problem? Seems related to DirectX
 
 
intro usually has nothing to do with a game but is a movie file of some sort. 
 
avoid directx - use opengl in games config settings. if this is not possibel there is a way to install directx9 via wine. more on this on wine homepage.

---

### Post by Mark Phelps on 2011-09-13
That error message could also mean that your current video driver does not support DirectX -- which is, I believe, the case with the default open-source drivers.

If you don't know the make and model video card, open a terminal and enter "lspci".  Look for the line containingb "VGA" -- and post the results back here.

If you are unfortunate enough to have one of the "legacy" ATI cards, or one of the older Intel chips, there is no current DirectX support for those -- and you won't be able to run the games.

---

### Post by Neoteros on 2011-09-15
^

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 16)
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

---

