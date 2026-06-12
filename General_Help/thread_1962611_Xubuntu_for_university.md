---
title: "Xubuntu for university"
date: 2012-04-21
forum: General Help
---

### Post by Tombgeek on 2012-04-21
I'm not entirely sure where to put this thread, so sorry if it's in the wrong place.

Anyway, I used to be here a long while ago. I previously used Ubuntu 9.10 and 10.04, but then I moved to Windows 7 and stopped using Ubuntu altogether (mostly due to my preferred software being Windows exclusive).

But anyway, that was in 2010. I recently applied for university and I'm planning ahead. I'm going to study BSc Computer Science and I'm thinking of dual booting Windows 7 and Xubuntu 12.04 for my 3-year-course (using Windows for my personal stuff and Xubuntu as a programming OS). Would you recommend I use Xubuntu? As far as I know, I'll be using IDEs like Netbeans and Eclipse.

The reason I don't want to use pure Ubuntu is because I'm really not a fan of Unity. It's not bad, but it makes me unproductive (I tried Ubuntu 11.04 in Virtualbox).

---

### Post by linuxcss on 2012-04-21
Same here on the unity, we like xubuntu 11.10 ... overall snappier than 9.10 gnome 2 too

---

### Post by raja.genupula on 2012-04-21
well but we have a option named as Gnome 3 and one more thing is Ubuntu 12.04 have Gnome-classic too . 

Xubuntu you can use as you wanted .you can use it for programming , no problems with that .

---

### Post by Tombgeek on 2012-04-21
> **raja.genupula said:**
> well but we have a option named as Gnome 3

I tried Gnome 3. A friend of mine gave me Fedora to try in a VM. I can't honestly say that I was impressed with Gnome 3 -- I definitely prefer Gnome 2.

> **raja.genupula said:**
> one more thing is Ubuntu 12.04 have Gnome-classic too.

Really? I thought the devs abandoned it. Now I might consider getting pure Ubuntu if I can fall back on Gnome 2. However, I do like the low memory usage of Xfce.

> **raja.genupula said:**
> Xubuntu you can use as you wanted .you can use it for programming , no problems with that .

Will there be any compatibility issues with an IDE like Netbeans on Xfce over other environments like Gnome or KDE? Sorry, I'm not a very experienced Linux user.

---

### Post by raja.genupula on 2012-04-21
> Will there be any compatibility issues with an IDE like Netbeans on Xfce over other environments like Gnome or KDE? Sorry, I'm not a very experienced Linux user.

No problem , it will be fine .:) . you can use Xubuntu for the development .

---

### Post by metulburr on 2012-04-21
I had the same issues with unity. You can configure unity to be more normal. Google search cmds for configuring unity. They all work in 12.04 beta as i have done them already. But here are a few.  

global menu bar back to normal:
```
#get rid of global menu bars and put back in windows
sudo apt-get remove appmenu-gtk3 appmenu-gtk appmenu-qt
restart

#reverse and get global menu bar back
sudo apt-get install appmenu-gtk3 appmenu-gtk appmenu-qt
restart


for firefox:
Tools -> Add-Ons disable Global menu bar integration extension
```window manager btns to the right:
```
gconftool-2 --set /apps/metacity/general/button_layout \
 --type string "menu:minimize,maximize,close"
```create a taksbar launbcher:
```
home/metulburr/.local/share
#create folder applications

#name <filename>.desktop

input in file: (example)
'''
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec= java -jar SKMCLauncher.jar
Name=SKMCLauncher Minecraft
Icon=/home/metulburr/.minecraft/icon.png
'''

```reset unity:
```
unity --reset
```add a create launcher to right click:
```
sudo apt-get install gnome-panel
sudo apt-get install nautilus-scripts-manager
gksu nautilus
Now you need to go to==> usr/share/nautilus-scripts
create a new documentcalled &#8220;create_launcher&#8221; (You can use any name) make it execuatable (You can do     this right clik then premissions tab)
Now you need to open this document and add the following line:
gnome-desktop-item-edit --create-new ~/Desktop
Open nautilus scripts manager then just put a check mark in the box that says active.(From dash board     enter nautilus to open nautilus scripts manager)
nautilus -q
when restart should have scripts -> Create LAuncher
```remove overlay scroolbar:
```
sudo apt-get remove overlay-scrollbar
```

---

### Post by raja.genupula on 2012-04-21
please wait for 4 days and try Ubuntu 12.04 . I have seen posts which are saying that Ubuntu 12.04 Unity will be the answer to the problems which , Ubuntu users have faced with Ubuntu Unity in previous releases . 

Thank you .:)

---

### Post by TheForkOfJustice on 2012-04-22
1. I think Lubuntu has a lower memory usage than Xubuntu. Haven't seen a comparative benchmark but the last time I used Xubuntu it felt just as resource-hogging as Gnome2.

2. Unity sucks.  I agree as do many others. Follow these instructions to get the 'Gnome Classic' desktop environment option at the login screen:

[http://ubuntuforums.org/showthread.php?t=1859961](http://ubuntuforums.org/showthread.php?t=1859961)

It's not as customizable as the old classic Gnome interface (can't alter the panels or it's 'applets') but it has all the basics and the classic menu.

Hopefully 12.04 gnome-classic will have alterable panels and applets.  I have no idea why the hell they abandoned it.

---

### Post by ubuntu27 on 2012-04-22
> **raja.genupula said:**
> well but we have a option named as Gnome 3 and one more thing is Ubuntu 12.04 have Gnome-classic too.


> **Tombgeek said:**
> 
Really? I thought the devs abandoned it. Now I might consider getting pure Ubuntu if I can fall back on Gnome 2. However, I do like the low memory usage of Xfce.


Yep, you can use Gnome classic with Ubuntu 12.04:

[GNOME Classic in Ubuntu 12.04: It’s Like Nothing Ever Changed]("http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29")

I like both Ubuntu and Xubuntu.


I recommend you to try them using a Live USB or Live CD, and not a virtual desktop.

---

### Post by HermanAB on 2012-04-22
Linux is Linux is Linux...

XFCE is the desktop environment of Xubuntu.  Otherwise it is the same as regular Ubuntu.  Even Linus uses XFCE (on Fedora), so you'll be in good company.

---

### Post by Tombgeek on 2012-04-22
> **raja.genupula said:**
> please wait for 4 days and try Ubuntu 12.04 . I have seen posts which are saying that Ubuntu 12.04 Unity will be the answer to the problems which , Ubuntu users have faced with Ubuntu Unity in previous releases . 

Thank you .:)

A friend of mine at school asked me to download Ubuntu 12.04 for him, so I'll be downloading both Xu- and Ubuntu. Yes, I know that I can install Xfce on Ubuntu, but last time I tried that I had serious performance issues (and it installs software I didn't want, like Abiword). I'm first testing both OSs in a VM before I dual boot (I can't afford to mess with partitions while school is a priority at the moment. I had to reinstall Windows many times because of an issue I had trying to install another OS. Granted, it was Windows XP at the time and XP is a terrible OS).

> **TheForkOfJustice said:**
> 1. I think Lubuntu has a lower memory usage than Xubuntu.

My computer isn't so outdated that I need Lubuntu. While performance is a slight concern of mine, I just prefer the Xfce interface. At least the dock is at the bottom (which I cannot understand why Ubuntu devs have put it on the left; it's more logical at the bottom).

> **TheForkOfJustice said:**
> Haven't seen a comparative benchmark but the last  time I used Xubuntu it felt just as resource-hogging as Gnome2.

The difference is only slight. Like I said, it's more about the interface than the performance. At least it's not as bad as KDE.

> **TheForkOfJustice said:**
> 

2. Unity sucks.  I agree as do many others. Follow these instructions to  get the 'Gnome Classic' desktop environment option at the login screen:

[http://ubuntuforums.org/showthread.php?t=1859961](http://ubuntuforums.org/showthread.php?t=1859961)

It's not as customizable as the old classic Gnome interface (can't alter  the panels or it's 'applets') but it has all the basics and the classic  menu.

Hopefully 12.04 gnome-classic will have alterable panels and applets.  I have no idea why the hell they abandoned it.

I'm not so worried about the customization as I am the thing functioning. In fact, I had many issues with the panels in 10.04 (a frequent bug would keep on removing certain applets I added and no update to the point I stopped using Ubuntu fixed it). But I'll test both before I install anything on my hard drive.

Unity's problem is that, if they make the interface logical, Canonical could get attacked for "copying" Mac OSX. People who use the dock on the left or right in Mac OS are a small minority. Many, like myself, prefer the dock at the bottom. Also, the global menu bar doesn't help, which I hate as well. The only thing keeping me from buying a Mac (apart from Apple's claustrophobic control over the OS) is the global menu bar.

---

### Post by TheForkOfJustice on 2012-04-22
> **HermanAB said:**
> Linux is Linux is Linux...

XFCE is the desktop environment of Xubuntu.  Otherwise it is the same as regular Ubuntu.  Even Linus uses XFCE (on Fedora), so you'll be in good company.

In this case it does matter since he wants a low-resource desktop.  Desktop environments aren't created equally and I'm pretty sure LXDE is the best of the 'major' desktops.

I think IceWM is even cheaper but I hated the menu.  It doesn't have the looks or features of the others but it gets the job done. You'll probably end up customizing the menu yourself with the programs you want.

---

