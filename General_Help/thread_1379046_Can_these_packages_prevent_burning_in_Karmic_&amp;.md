---
title: "Can these packages prevent burning in Karmic &amp; Lucid"
date: 2010-01-12
forum: General Help
---

### Post by ankspo71 on 2010-01-12
Hi,

I am doing some detective work again... after I found out I can't burn cds (again) on a 3rd dvd writer drive. Yes three.

I was talking amoung a few members here who could not burn cds last night. After all that talk of burning cds, I had the urge to burn one too. To my surprise, I was unable to burn cds again. I got mad again so I just finished a fresh reinstall of lucid (testing) and all of a sudden I can burn a cd again. I decided to install lastfm and pysdm, so I have something to do while I try to burn a cd, and the burn in brasero worked without a hitch. So lastfm and pysdm checks out ok.

Anyways, here is the list of applications that I normally install. Can anyone pinpoint anything that has the potential to prevent me from burning cd's? The reason why I am asking here is because I can't waste that many cds testing the possibility of burning after each and every package I install.

My common applications:
lastfm emerald compizconfig-settings-manager miro banshee parcellite audacity vlc mozilla-plugin-vlc cgmail thunderbird-gnome-support thunderbird moonlight-plugin-mozilla thunar sun-java6-jre sun-java6-plugin build-essential alltray wallpaper-tray keepassx sound-juicer gufw pysdm gparted gnome-color-chooser ubuntu-restricted-extras bum (never actually used it yet) wine1.2 playonlinux unrar p7zip-full p7zip-rar nautilus-open-terminal wine1.2 playonlinux fdupes easytag fslint soundconverter

My usual games to pass some time:
xmoto criticalmass chromium-bsu pinball trackballs gnome-hearts gnome-mastermind sdl-ball foobillard billard-gl

Medibuntu:
libdvdcss2 w32codecs googleearth

----
Here are the things that I have tried to do to be able to burn cds:

[LIST]
[*]Reinstalled Karmic and Lucid (a few times) (but also added the packages in the above list immediately)
[*]Tried gnome xfce kde and openbox desktops.
[*]Tried k3b brasero gnomebaker xfburn and deepburner in wine
[*]Tried burning at the lowest speeds possible
[*]Tried burning by command line to check for errors (no errors)
[*]All gui burning software reported no errors
[*]Tried several different distributions /OS's with my drives (they all worked)
[*]Tried three different DVD burners
[/LIST]
So you can see I tried just about everything I could do. Without any errors I can't get much help or even report a bug at launchpad. Up until now I thought it was either a problem with my VIA based motherboard becoming incompatible with Ubuntu Karmic and Lucid, or perhaps something wrong with the drivers that are being supplied to my computer. My original link is below which includes my hardware (including 2 of the dvd drives) and the third reported as a USB storage device (Liteon EZDub USB dvd writer).
[http://ubuntuforums.org/showthread.php?t=1305501&highlight=kk+final](http://ubuntuforums.org/showthread.php?t=1305501&highlight=kk+final)

More specs:
[http://www.motherboardpro.com/BIOSTAR-P4M900-M4-Motherboard-VIA-P4M900-Intel-Socket-478-Micro-ATX-p-424.html](http://www.motherboardpro.com/BIOSTAR-P4M900-M4-Motherboard-VIA-P4M900-Intel-Socket-478-Micro-ATX-p-424.html)
Plus, 2 GB RAM, Nvidia 8400GS, Intel Pentium 4 3.0ghz, 4gb of swap.
My memory tests are good, as well as my cd images to install karmic and Lucid.

My thoughts that I might have some type of problem with either medibuntu stuff or ubuntu-restricted-extras. What do you think it is? Thanks for making it through this long post.

(Edit: I forgot to say I was able to burn cd's from 8.04 to 9.04 easily, but not since the day karmic was released)

---

### Post by ankspo71 on 2010-01-12
Update:
I installed every package on my list *except* ubuntu-restricted-extras or anything from medibuntu. I am able to burn a cd with brasero :D

Then I installed Google Earth (5.1.3533.1731) from the Google Earth homepage and flashplugin-nonfree (10.0.42.34) from Synaptic Package Manager. I am still able to burn a cd with brasero :D  

It looks like my burning problem might have been with something from medibuntu or ubuntu-restricted-extras. It could have been the codecs or something. The only thing I didn't do yet was install anything in wine or playonlinux. 

I hope this stays working because this has been a real headache. I'm using Lucid now btw.

---

