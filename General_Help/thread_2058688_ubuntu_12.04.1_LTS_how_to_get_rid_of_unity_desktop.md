---
title: "ubuntu 12.04.1 LTS how to get rid of unity desktop?"
date: 2012-09-16
forum: General Help
---

### Post by psihokiller4 on 2012-09-16
I've just upgraded my Ubuntu from 10.04.3 LTS to Ubuntu 12.04.1 LTS
and I've encountered BIG problems and found out those 10 "top" features is pretty much all you can do [http://www.omgubuntu.co.uk/2012/04/10-things-to-do-after-installing-ubuntu-12-04](http://www.omgubuntu.co.uk/2012/04/10-things-to-do-after-installing-ubuntu-12-04)

WTF how do I open terminal
WTF how do I even open synaptic

how do I even open wine
how do I open many stuff

it's Basic more options in BIOS than here must I really format my PC cuz of this ?!?!?!??!?!?!?!?!

I WANT my old GNOME desktop BACK ;(


EDIT:
thread name:
from BIG problem how to open normal stuff?



SOLVED with this:
[B][http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)
[/B]thank you very much

---

### Post by micahpage on 2012-09-16
The leap from one to the other is massive different.
I assume you are currently in Unity as the default desktop, however I forgot how to do anything in it as I abandoned it long ago.

I think in Unity, the top-left, is the dash, and you just type what you want terminal, etc. If you want to attach it to the taskbar on the left, you just click-hold-move it over to the taskbar from the dash

---

### Post by psihokiller4 on 2012-09-16
yeah there's dash home but there's only

old files I opened,
text editor, help, Thunderbird mail, movie player, rhythmbox music player

and that's all

so how do I get rid of this to get to normal

how did you got rid of Unity?

---

### Post by micahpage on 2012-09-16
there should be a textbox, where I typed in everything i wanted, which will pop up an icon for related items.

There should also be tabs for categories, i think at the bottom or to the right of the dash screen, which will pop up icons of the related category.

> how did you got rid of Unity?
I just installed numerous desktops and forced myself to learn them as opposed to Unity. KDE, Gnome 3 (gnome-session), etc.

I still have Unity installed but I never go into it.


> so how do I get rid of this to get to normal
I think by default it shows your previous programs you opened. There should be a textbox/category tabs though to open everything.

---

### Post by psihokiller4 on 2012-09-16
thank you very much at least I've got in to synaptic

installing gnome desktop
were searching for gnome 3 but couldn't find it as a test how it would be

---

### Post by GreatDanton on 2012-09-16
If you would like to get rid of unity desktop (IMO) is to switch to another *buntu, such as Xubuntu or Lubuntu. They look the same as old gnome 2.

---

### Post by micahpage on 2012-09-16
> were searching for gnome 3 but couldn't find it as a test how it would be

gnome 3 is called gnome-session

```
metulburr@ubuntu:~$ sudo apt-cache search gnome-session
[sudo] password for metulburr: 
gnome-session - GNOME Session Manager - GNOME 3 session
gnome-session-bin - GNOME Session Manager - Minimal runtime
gnome-session-canberra - GNOME session log in and log out sound events
gnome-session-common - GNOME Session Manager - common files
gnome-session-fallback - GNOME Session Manager - GNOME fallback session
metulburr@ubuntu:~$ 

```

---

### Post by micahpage on 2012-09-16
also if you feel the need to use unity, you can tinker with it to appear more "normal" per se

add right click "open in terminal"
```
sudo apt-get install nautilus-open-terminal
```

change global menu bar (move menu bars back to the windows)
```
#get rid of global menu bars and put back in windows
sudo apt-get remove appmenu-gtk3 appmenu-gtk appmenu-qt
restart

#reverse and get global menu bar back
sudo apt-get install appmenu-gtk3 appmenu-gtk appmenu-qt
restart


for firefox:
Tools -> Add-Ons disable Global menu bar integration extension
```

move min, max, close buttons to the right instead of left
```
gconftool-2 --set /apps/metacity/general/button_layout \
 --type string "menu:minimize,maximize,close"
```

add taskbar launcher
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

```

add right click desktop launcher
```
sudo apt-get install gnome-panel
sudo apt-get install nautilus-scripts-manager
gksu nautilus
Now you need to go to==> usr/share/nautilus-scripts
create a new documentcalled &#8220;create_launcher&#8221; (You can use any name) make it execuatable (You can do 	this right clik then premissions tab)
Now you need to open this document and add the following line:
gnome-desktop-item-edit --create-new ~/Desktop
Open nautilus scripts manager then just put a check mark in the box that says active.(From dash board 	enter nautilus to open nautilus scripts manager)
nautilus -q
when restart should have scripts -> Create LAuncher
```

missing title menu bars
```
sudo apt-get install metacity
metacity --replace

OR TRY:
sudo apt-get install compizconfig-settings-manager
1) change values in GUI

```

remove overlay scrollbar
```
sudo apt-get remove overlay-scrollbar
```

reset unity
```
unity --reset
```

---

### Post by psihokiller4 on 2012-09-16
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

```

did you mean creating a file:
/home/username/.local/applications/.desktop

?

---

### Post by ajgreeny on 2012-09-16
If you really find the unity desktop too much to bear, you can change the DE to look at act very much like the old gnome 2 DE (gnome-classic) by following the various actions suggested in [http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) where many options to get something more like the DE you're used to are described.

I am using gnome-classic on my 12.04 install on a desktop machine which is my main computer, though the 12.04 is just a test-bed of 12.04, not my main OS.  It does, however, work very well once you get used to the very few differences and omissions, so read that thread well and give it a try; you may like it.

---

### Post by micahpage on 2012-09-16
> did you mean creating a file:
/home/username/.local/applications/.desktop

?
_____
oh i labeled it wrong, edited name of code

yes but not .desktop, in my example minecraft.desktop
/home/username/.local/applications/minecraft.desktop
the first code snippet created a file named:
minecraft.desktop
for example, in which would be adding your own launcher to the taskbar of unity

make it executable
after that you should be able to move it over to the taskbar, and use it as normal launcher for taskbar OR type in the dash for the name of file you made to get it also

the second code snippet under desktop launcher is for adding the right click create launcher for example the desktop

---

### Post by psihokiller4 on 2012-09-16
thank you very much that solved my problem :)

---

### Post by CaptainMark on 2012-09-16
Unity is still using Gnome3, the different desktop that your talking about is called Gnome-Shell, however if you want a more customisable desktop which can be made to resemble gnome2 I recommend cinnamon [http://cinnamon.linuxmint.com/?page_id=61](http://cinnamon.linuxmint.com/?page_id=61)

---

### Post by hawthornso23 on 2012-09-16
I prefer gnome classic which is gnome-fallback on compiz and which has the look and feel of gnome2. I find Gnome shell and Unity equally frustrating. 

However I am worried about the level of commitment to support this option in future. Ubuntu developers see it purely as training wheels for Unity refuseniks and would rather we were all using Unity. Gnome developers see it purely as a fallback mode for older hardware and would rather we all used gnome shell. The contunued functioning of this desktop depends on both groups continuing to support it. That support is grudging at best at present. Neither is strongly committed to continuing to support it and either one is quite likely to suddenly drop it without warning.

---

### Post by dcstar on 2012-09-17
People who really want to keep the old Gnome 2 environment should install Mate:

[https://wiki.archlinux.org/index.php/MATE](https://wiki.archlinux.org/index.php/MATE)

I have tried it and it is 95% functional as the old 10.04 desktop, but you lose some of the nice Ubuntu Themes and customisation.

In the end I just use Gnome 3 now and I have stripped away all the unnecessary Unity packages from my 12.04 system (don't remove **unity-greeter** or your system won't have a login screen!!!!).

---

### Post by CaptainMark on 2012-09-17
> **hawthornso23 said:**
> I prefer gnome classic which is gnome-fallback on compiz and which has the look and feel of gnome2. I find Gnome shell and Unity equally frustrating. 

However I am worried about the level of commitment to support this option in future. Ubuntu developers see it purely as training wheels for Unity refuseniks and would rather we were all using Unity. Gnome developers see it purely as a fallback mode for older hardware and would rather we all used gnome shell. The contunued functioning of this desktop depends on both groups continuing to support it. That support is grudging at best at present. Neither is strongly committed to continuing to support it and either one is quite likely to suddenly drop it without warning.
Well gnome and unity will from all future releases run on all hardware regardless of graphical capabilities so I would expect that gnome-fallback will drop to become nothing more than literally an emergency backup mode like low graphics mode back in the day

---

