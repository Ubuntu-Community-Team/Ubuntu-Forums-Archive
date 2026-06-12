---
title: "No panels after 1st Ubuntu KK install and update"
date: 2009-11-19
forum: General Help
---

### Post by Citizenpete on 2009-11-19
History of the missing gnome panels...

[SIZE=4]**Sony Vaio vs. new first install of Umbuntu  9.10**[/SIZE][I][SIZE=2][COLOR=Blue]

[/COLOR][/SIZE][/I]*[SIZE=2][COLOR=Blue]processor     [/COLOR][/SIZE]*           *[SIZE=2][COLOR=Blue]       Intel Pentium 4 2.8 GHz     [/COLOR][/SIZE]*                     *[SIZE=2][COLOR=Blue]Video Chipset []("http://www.dealtime.com/xWI?lid=1&fid=451&aid=538") [/COLOR][/SIZE]*                   *[SIZE=2][COLOR=Blue]       SiS651     [/COLOR][/SIZE]*               *[SIZE=2][COLOR=Blue]      Installed Memory     [/COLOR][/SIZE]*           *[SIZE=2][COLOR=Blue]       512 MB (DDR SDRAM)     [/COLOR][/SIZE]*[I][SIZE=2][COLOR=Blue]isplay                       17.5 in.  Flat Panel LCD     [/COLOR][/SIZE][SIZE=2][COLOR=Blue]
[/COLOR][/SIZE][/I]*[SIZE=2][COLOR=Blue]Video Out Ports     [/COLOR][/SIZE]*           *[SIZE=2][COLOR=Blue]       S-Video x 1     [/COLOR][/SIZE]*               *[SIZE=2][COLOR=Blue]      Audio Input     [/COLOR][/SIZE]*           *[SIZE=2][COLOR=Blue]       Microphone Jack    •        1 x Line In    •        Optical Digital In     [/COLOR][/SIZE]*               *[SIZE=2][COLOR=Blue]      Audio Output Type     [/COLOR][/SIZE]*           *[SIZE=2][COLOR=Blue]       Sound Card    •        Headphones    •        Line out     [/COLOR][/SIZE]*               *[SIZE=2][COLOR=Blue]      Video Input Type     [/COLOR][/SIZE]*           *[SIZE=2][COLOR=Blue]       TV Tuner     [/COLOR][/SIZE]**[SIZE=2][COLOR=Blue]Networking Type                       Integrated 10/100 Network Card    •        Integrated Wireless LAN     [/COLOR][/SIZE]*

This is an old Sony Vaio all in one intel p4 pc with 512 mb ram and a couple bad keyboard keys      I burned the iso image on to DVD+R off another windows pc and ran Ubuntu off the DVD first to test - it seemed to work to well so I installed to the HD --  it eventually installed from the DVD without errors. 

 Starting it u the first tim eit udated the OS and when the OS booted up I have NO MENUS -- i think the term is panels -- no panels -- just a empty desktop :cry:  I can get the right click menu up on the desktop.

I have NO MENUS / panels -- zero panels -- notta -- no top no bottom -- just an empty desktop   background 

  getting the right click mouse menu up, I was able to get Mozilla going through a right click menu selection for new backgrounds and then search for new backgrounds on line which launched mozilla firefox - thank god. thats how I got here.

Is there a keyboard shortcut to turn panels on ... When I ran UBUNTU from the DVD ISO image it ran fine ... when I  brought it up the first time from the HD install UBUNTU udated and NO panels to or bottom

by **wojox**
Code:     gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel 

successfully entered and rebooted - however did not fix -- now I have no controls on mozilla windows --  resize delete etc.
:confused:

wow - I figured out how to get my window controls back! I lost ability to change focus between windows and lost my min/max/close menu bar controls, but when I right click on the desktop and select the Change Desktop Background then select the Appearance preferences then Visual Effects and select Normal or Extra options [only to have them error out) - my windows controls come back -- BUT still no panels on the top or bottom ](*,) ... CLUE maybe

                     Originally Posted by **wojox**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8350540#post8350540")                 
                 [I]Maybe you need to reinstall gnome-panel:

     Code:
     sudo apt-get install gnome-panel 
[/I]
                                 hmmm...  

reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-panel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

:confused:


not feeling so good about blowing away my Xp off my hard drive #-o

anyone else hear about this :confused: I could not find the exact same prob  on the forum - reinstall - try again maybe

---

### Post by Citizenpete on 2009-11-20
Checked these posts out but  still no panels,,,

ttp://ubuntuforums.org/showthread.php?t=1326632&highlight=panels
gnome-session-save --logout

[http://ubuntuforums.org/showthread.php?t=1330592&highlight=panels](http://ubuntuforums.org/showthread.php?t=1330592&highlight=panels)
not applicable

[http://ubuntuforums.org/showthread.php?t=1329119&highlight=panels](http://ubuntuforums.org/showthread.php?t=1329119&highlight=panels)
tried before

[http://ubuntuforums.org/showthread.php?t=833101&highlight=panels](http://ubuntuforums.org/showthread.php?t=833101&highlight=panels)
SOME GOODNESS from sisco311xfce4-panellog out with the *Save session for future logins* option (select it from the shutdown menu).




this brings up the bottom panel [ had to install first in terminal)


created gnome terminal by selecting    create launcher     and adding    gnome terminal    as command

---

### Post by drs305 on 2009-11-20
You can try running these commands. They reset the panel settings to the defaults but I don't know if they will actually put them back in place:
```

gconftool-2 --recursive-unset /apps/panel
killall gnome-panel &

```

---

### Post by Citizenpete on 2009-11-20
still not working

---

### Post by drs305 on 2009-11-20
One more guess, then off to bed:

```

sudo apt-get install --reinstall gnome-panel
killall gnome-panel &

```

---

### Post by Citizenpete on 2009-11-20
no cracker

](*,)

---

### Post by Citizenpete on 2009-11-20
SO still no permanent panels. in my Karmic nightmare.


This command ...



xfce4-panel


does bring up the bottom panel so I know it is possible  :P  [ and that one panel does exist) but the bottom panel  goes away if I shut down or log out

Since installing Ubuntu Karmic with the update I have not yet seen the top panel -- not once.  Not a sausage. 

Is there a Karmic guru that can reach out and assist me,,, an Ubuntu deity who comes out and heels the wounds of embattled Karmic installs [-o<   OH Great and powerful Umbuntu support guru we beceach thee, help this Newbie and bring forth our daily panels!

---

### Post by blueridgedog on 2009-11-20
What version did you download?

---

### Post by Citizenpete on 2009-11-20
> **blueridgedog said:**
> What version did you download?
9.10 Karmic - the very latest DVD ISO and update available.  First time installing Ubuntu.

---

### Post by Citizenpete on 2009-11-20
> **blueridgedog said:**
> What version did you download?
Another user who was kind enough to reach out to me via email suggested that I potentially reinstall the desktop if nothing else works. 

ubuntu-desktop (sudo apt-get install --reinstall ubuntu-desktop)

---

### Post by P4man on 2009-11-20
did you test the DVD for defects? When you boot from the dvd you have that option. Id try that as I suspect a problem with the disc.

---

### Post by blueridgedog on 2009-11-20
> **Citizenpete said:**
> 9.10 Karmic - the very latest DVD ISO and update available.  First time installing Ubuntu.

There are a few download "flavors", Ubuntu should have panels, and you appear well on your way to debugging that.  The help differs if you have Ubuntu, Kubuntu or Xubuntu.

---

### Post by Citizenpete on 2009-11-20
Is there any terminal command to do a complete reinstall from Ubuntu archive?  My DVD drive is not functioning.

> **P4man said:**
> did you test the DVD for defects? When you boot from the dvd you have that option. Id try that as I suspect a problem with the disc.

---

