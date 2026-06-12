---
title: "Trying to get JW player to work under firefox"
date: 2009-08-01
forum: General Help
---

### Post by MonkeyCoffeeBeans on 2009-08-01
I've recently upgraded to 9.04 and soon realized that i could no longer watch streaming video from JW players. Instead there is a new player / image that appears. 

[http://img35.imageshack.us/img35/3772/jwplayer01.jpg](http://img35.imageshack.us/img35/3772/jwplayer01.jpg)

Would anyone by chance know how to correct this? 

I have Installed Adobe Flash Player on Firefox. Youtube works just fine along with megavideo players. Only JW player seems to be effected.

Thank you.

---

### Post by arrow432 on 2009-09-02
I've got the same problem as you and don't know what to do. Please write a tip for us, any advice ... 
Thanks in advice ;)

---

### Post by gatos on 2009-09-07
Hmmm
I am also using 9.04, but have no issues with JW player. I am not an expert, but I too installed Adobe Flash Player. I have also installed the codecs for the default Totem Movie Player. Try installing GStreamer and see if it makes a difference

---

### Post by s.l.i.m on 2009-09-28
Hi,

I'm the fourth to have that problem. So please who have a solution help us.

---

### Post by s.l.i.m on 2009-09-28
I have found a solution : 
( i just needed the read the                           **[B]Sticky:**[/B]                                      [COLOR=#008c00]**[all variants]**[/COLOR]                          [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")[SIZE=5][SIZE=1][COLOR=darkred][COLOR=Black]in the Multimedia & Video section )
[/COLOR][/COLOR][/SIZE][/SIZE]> 
[CENTER][SIZE=5]**[COLOR=darkred]--TROUBLESHOOTING--[/COLOR]**[/SIZE] 
[/CENTER]
 
[CENTER][SIZE=3]**[COLOR=DarkRed]ADOBE FLASH PLAYER[/COLOR]**[/SIZE][/CENTER]


On occasion, installing Adobe Flash Player and/or watching online Flash streams successfully isn't as simple as it might ordinarily be. If you have tried installing it already, and are having issues, read on. First of all, please disable any ad-blocking Firefox extensions you have installed, such as Adblock Plus, as they can sometimes interfere with the Flash content you actually want to see. If you are still having issues after disabling the extension(s), you should now completely purge Adobe Flash Player from your system, along with any other packages which may be interfering with it, reinstall only Adobe Flash Player, restart your web browser, and then test Flash performance again. Will both 32-bit and 64-bit users copy and paste this command into the terminal:

**sudo apt-get purge adobe-flashplugin flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree**

Still no joy? I would suggest following the instructions below for your particular Ubuntu version and architecture.

[CENTER]**[COLOR=DarkRed]UBUNTU FAMILY 8.04+ USERS ONLY[/COLOR]**[/CENTER]


**[COLOR=DarkRed]Note:[/COLOR]** You can safely install the Ubuntu package (flashplugin-nonfree), or a Deb archive over the top of the Tar installation method at a later date - I've tested it several times. There's absolutely no need to remove any of the manually installed files, as they will simply be overwritten.

First of all, copy and paste the following command into the terminal and remove the package installed by Ubuntu:

**sudo apt-get purge flashplugin-nonfree**

**[COLOR=DarkRed]32-Bit Users Only:[/COLOR]** Those of you running the 32-bit version of Ubuntu can install the Flash Player plug-in by selecting and downloading the Deb archive in the drop-down menu on [this page]("http://get.adobe.com/flashplayer/") of Adobe's site, then executing it and entering your root password when prompted.

**[COLOR=DarkRed]32/64-bit Users:[/COLOR]** Alternatively, 32-bit users can download the Tar archive from the [same link]("http://get.adobe.com/flashplayer/") provided above and follow my instructions below. If you're a 64-bit Ubuntu user, download the Tar archive of the 64-bit Flash Player plug-in from the bottom of [this page]("http://labs.adobe.com/downloads/flashplayer10.html") to your desktop.

Once downloaded, simply open the Tar archive, look for a file named "libflashplayer.so", copy that file to your desktop, then both 32-bit and 64-bit users execute the following command in the terminal:

**sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so**

You may now restart your web browser and use the plugin.
...


It worked for me by the first operation.

---

