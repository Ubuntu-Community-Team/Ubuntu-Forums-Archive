---
title: "Install Issues ..."
date: 2006-03-10
forum: General Help
---

### Post by wannabelinuxconvert on 2006-03-10
Hi,

I want a very basic version of Ubuntu installed to act as a mail server.

I thought I would install the general package, and then remove everything I didn't need like CUPS and Bluetooth support etc but it seems to want to either remove all sorts or nothing at all depending on what I select. 

I then thought I would just re-install the server package instead of the standard one, but I know this just gives you the terminal and I need a Desktop/Window Manager as I am still very new to Linux. 

So my question is, from the terminal after the server install, is it as easy as just doing 

```
apt-get install gnome
```

And if so, does this just install a very basic gnome package, or does it still install stuff like synaptic, CUPS etc !?

Any help/advice would be great.

Cheers

Mic

---

### Post by Aine on 2006-03-10
My confusion comes from you want a mail server..but you're going to install Gnome? If you're going to go the route of servers, you should do straight terminal with no X..X bogs the system down if you're going to have a pretty popular mail server and your PC can't handle it.

When you install ubuntu, you can do install -- server or something (it says the switch on the install screen where you just normally hit enter)

---

### Post by Sutekh on 2006-03-10
If you really want a light desktop check some of these options

Oh yes do a server install; in the way Aine suggests just type 'server' and hit Enter when the installer starts

[Ubuntu Wiki - Installation/Low Memory Systems]("https://wiki.ubuntu.com/Installation/LowMemorySystems")

Don't forget to check out other Ubuntu derivations; Xubuntu (!), UbuntuLite, and so on.

---

### Post by wannabelinuxconvert on 2006-03-10
Hi,

Thanks for the replies.

XFCE definetley seems the way to go ... but I have a couple of questions.

After installation and reboot, does it automatically boot into XFCE or will I need to start it from the terminal !?

Does XFCE have a login screen like Gnome, or is that another app I need to install !?

Thanks

Mic

---

### Post by Sutekh on 2006-03-10
[QUOTE=wannabelinuxconvert]Hi,

Thanks for the replies.

XFCE definetley seems the way to go ... but I have a couple of questions.

After installation and reboot, does it automatically boot into XFCE or will I need to start it from the terminal !?

Does XFCE have a login screen like Gnome, or is that another app I need to install !?

Thanks

Mic[/QUOTE]
No XFCE doesn't have a display manager like GDM is to GNOME.  XFCE is started by using startxfce4.  You can work that command into the startup procedure, but that's something I haven't looked into yet.  

You can also install a display manager like GDM or KDM.  Keeping in mind that all you are getting is that graphical login, so you have to weigh up that against the penalty in space, etc.

---

### Post by wannabelinuxconvert on 2006-03-10
Once again Sutekh thanks for the reply.

On the wiki page you suggested, it says to install 'WDM' so I thought that may be XFCE's eqiuvilent to Gnome's GDM.

So do you know if I'm able to replace 'WDM' with 'GDM' then and have a graphical login screen !?

Also, if this is the case, once I log in through the screen, will it then just drop straight to terminal where I would run the command startxfce4 !?

Thanks

Mic

---

### Post by Sutekh on 2006-03-10
> **wannabelinuxconvert]Once again Sutekh thanks for the reply.

On the wiki page you suggested, it says to install 'WDM' so I thought that may be XFCE's eqiuvilent to Gnome's GDM.[/QUOTE]I think that WDM is different display manager altogether.  As far as I know, XFCE doesn't have its own one.

Put it this way said:**
> 
So do you know if I'm able to replace 'WDM' with 'GDM' then and have a graphical login screen !?Absolutely its that easy.  Once again the GDM will probably take more memory than WDM.  

Maybe try the WDM and see if you like it, I've heard it isn't as pretty though, if you don't like it, completely uninstall it and install the GDM.  Up to you.

[QUOTE=wannabelinuxconvert]
Also, if this is the case, once I log in through the screen, will it then just drop straight to terminal where I would run the command startxfce4 !?

Thanks

Mic[/QUOTE]
No.  

If you install a display manager then once you login through it, XFCE will start.  

If you don't install a display manager then when you booot the PC you will login at a command prompt and then use startxfce4.

---

### Post by wannabelinuxconvert on 2006-03-10
Really learning something today, thanks for all your help.

Final question I promise ;) 

I connect to the internet through a wireless usb connection ... through Gnome I setup this up through the networking option in the system menu by just highlighting the wlan0 interface, inputting the network name and selecting the DHCP option ... the interface then activates and hey presto I can get on the internet.

Can you give me some guidelines on how I acheive this through the terminal (or even if the server option installs the necessary wireless librarys!?) as I cannot do anything with apt until I've got internet access !?

Thanks

Mic

---

### Post by Sutekh on 2006-03-13
> **wannabelinuxconvert]Really learning something today, thanks for all your help.

Final question I promise  said:**
> OK sorry about the delay, I really know nothing about wireless, more so using XFCE

[QUOTE=wannabelinuxconvert]
I connect to the internet through a wireless usb connection ... through Gnome I setup this up through the networking option in the system menu by just highlighting the wlan0 interface, inputting the network name and selecting the DHCP option ... the interface then activates and hey presto I can get on the internet.

Can you give me some guidelines on how I acheive this through the terminal (or even if the server option installs the necessary wireless librarys!?) as I cannot do anything with apt until I've got internet access !?

Thanks

Mic

Try some of these links, I hope they can be of use

 - These two are good resources

[Ubuntu Wiki - WiFi Howto]("https://wiki.ubuntu.com/WiFiHowto")

[UDSF - Connection Managers]("http://http://doc.gwos.org/index.php/ConnectionManagers")


 - These two are some software I saw mentioned often

[Webmin]("http://http://www.webmin.com/index.html")

[http://xfce-goodies.berlios.de/packages.html]("http://xfce-goodies.berlios.de/packages.html")


 - An assortment of XFCE and wireless search results.

[Ubuntu Forums - Problems with wireless on a server install]("http://www.ubuntuforums.org/showthread.php?p=533314")

[Ubuntu Forums - Wireless setup on server install]("http://www.ubuntuforums.org/showthread.php?p=558422")

[Ubuntu Forums - Wireless networking questions]("http://www.ubuntuforums.org/showthread.php?p=603730")

[Ubuntu Forums - Into what config file do I put iwconfig commands?]("http://www.ubuntuforums.org/showthread.php?p=676487")

[Ubuntu Forums - XFCE wifi and WEP setup]("http://www.ubuntuforums.org/showthread.php?p=320167")

[Ubuntu Forums - Installed XFCE now what?]("http://www.ubuntuforums.org/showthread.php?p=57312")

[Ubuntu Forums - Changing network preferences in XFCE]("http://www.ubuntuforums.org/showthread.php?t=138135")


Sorry to heap it all on you, I need to get a WiFi card one of these days so I know what its like to get one working.  Good luck and I hope you get your WiFi working with XFCE!

---

### Post by wannabelinuxconvert on 2006-03-13
Hi,

Thanks for all the info but I've really had no luck what so ever.

I did manage to get the wireless networking running fine by booting up my mac-mini which also runs on Ubuntu and uses the same wireless usb adapter and copying the contents of the interfaces file from one to the other :mrgreen: 

However, I could not get either XFCE4 or Xubuntu working successfully ... it seems it does not like either my graphics card or my monitor, I couldn't figure out which but never saw a desktop, just lots of pink and yellow vertical lines !!

After several re-configure attempts with no success, I abandoned this, and re-installed Gnome.

I am now just looking at stripping out all the unwanted packages one by one to strip the system down to it's bare minimum for the server.

Thanks again

Mic

---

