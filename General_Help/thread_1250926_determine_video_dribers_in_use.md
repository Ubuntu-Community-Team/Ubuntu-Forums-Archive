---
title: "determine video dribers in use"
date: 2009-08-27
forum: General Help
---

### Post by Wim Sturkenboom on 2009-08-27
For the fun, I installed UNR 9.04 on a Dell laptop M2300. It works but when I tried to enable desktop effects, it said thatd esktop effects could not be enabled. So I assume that a generic driver is currently in use. Trying to determine which driver is in use for the video card.

lspci indicates a nVidia Quadro FX360M
grep on dmesg or /var/log/messages does not reveal anything related to nVidia
/etc/X11/xorg.conf only shows 'configured device'

synaptic shows that a lot of nvidia stuff is installed
the hardware drivers 'menu option' states that no proprietary drivers are installed.

[COLOR="Blue"]So which command can I use to find out which driver is used?[/COLOR]

Next step would be to install restricted drivers and as far as I know it's nowadays a 'menu option' but I haven't found that option yet in the 'menu'. [COLOR="Blue"]So where do I find it?[/COLOR] I know it has been mentioned here on the forums but don't seem to be able to find it.

---

### Post by P4man on 2009-08-27
its a good question how you determine the driver in use. Id like to know that as well :). If xorg.conf doesnt mention any, its a safe bet you are using the opensource nv driver, but there must be a way to confirm that, easier than:

```
 cat /var/log/Xorg.0.log
```

(though that should give you the info if you know where to look).

Anyway, im guessing the hardware driver app isn't recognizing your Quadro. But the nvidia driver does support it, so you should be able to install it:

```
sudo apt-get install nvidia-glx-180 nvidia-180-modaliases
```

---

### Post by P4man on 2009-08-27
oops, you havent the app yet?
maybe it does just work.
System > administration > hardware drivers

---

### Post by Wim Sturkenboom on 2009-08-27
Thanks for the reply

I just realized that I could check the log ](*,) There is a line *loadmodule: "nv"* and a number of lines starting with *(II} NV* and (II) NV(0)

So I assume that it implies the generic NV driver.

In the 'menu option' hardware drivers I don't have an option to add them; the icon also shows a lock (not sure what that implies).

*nvidia-180-modaliases* is installed according to synaptic, but if so, why not the nvidia-glx-180; I mean, what is the use of modaliases (whatever that might be) without the driver?



PS just ran *sudo apt-get install nvidia-glx-180* and get the error *E: Couldn't find package nvidia-glx-180*.
Can a proxy be the possible cause of this (connect through a Windows system that I can not configure)?

---

### Post by P4man on 2009-08-27
As far as I know, modaliases lets you determine what videocard you have. I guess it makes sense to include that even without the driver (so "hardware drivers" can determine what videocard you have).

That "lock" thing is kinda weird though. Not sure what it means, can you perhaps post a screenshot?

---

### Post by Wim Sturkenboom on 2009-08-27
Thanks for the explanantion of modaliases.

See attached screenshot for the lock

---

### Post by P4man on 2009-08-27
oh.. that lock :) Sorry, I should have thought of it :) Its just the icon, its always like that. Its a reference to the "restricted" drivers. What happens when you click it though?

---

### Post by Wim Sturkenboom on 2009-08-27
It starts the 'application', searches for drivers and displays that there are no 'proprietary drivers'.

---

### Post by P4man on 2009-08-27
Then go ahead and install nvidia-glx-180

---

### Post by 3rdalbum on 2009-08-27
In the "Administration" panel, go to Software Sources and make sure the top four checkboxes are enabled. Close the program. Then reload the package list by opening Synaptic and clicking Reload, and now you should be able to find nvidia-glx-180 (or the Hardware Drivers program should be able to see it now).

Apparently your card works with the 180 driver, so I'm surprised it isn't being offered to you automatically.

---

### Post by P4man on 2009-08-27
> **Wim Sturkenboom said:**
> 
PS just ran *sudo apt-get install nvidia-glx-180* and get the error *E: Couldn't find package nvidia-glx-180*.
Can a proxy be the possible cause of this (connect through a Windows system that I can not configure)?

Oops, I missed that, our messages crossed. Do what 3rdalbum suggested (enable multiverse and restriced). Its possible the proxy is a problem, but after adding those sofware sources, let it reload the repo's (it will prompt you to do so on close), and if there is a problem with the proxy, you will see it then.

---

### Post by P4man on 2009-08-27
if it turns out you need to configure it for the proxy, then go to system > adminstration > synaptic package manager.

In synaptic > settings > preferences > network

There you can configure your proxy.

This might also explain why "hardware drivers" isnt suggesting a driver.

---

### Post by Wim Sturkenboom on 2009-08-27
No longer behind the machine. Will give it a shot tomorrow.

PS repositories are enables if I remember correctly.

---

### Post by Wim Sturkenboom on 2009-08-28
Brilliant :( OK, after setting up the correct proxy details and updating the package list (all in synaptic), there was the nvidia-glx-180 driver.
Installed it through synaptic.

Rebooted the X-server and no UNR menus any more; only the 'topbar' with (at the left) the little Ubuntu logo (hide all windows and show home screen) and an update manager icon and at the right hand side battery, network, speaker and bluetooth icons and the date/time.

Changed driver in xorg.conf to nv and rebooted the Xserver but that did not do the trick.

Waiting for updates to download; might fix the issue (although I don't have much hope).

I will run an *apt-get remove* after the downloads are done; anything else to run to get the system back to it's 'working state'.

---

### Post by P4man on 2009-08-28
dont uninstall the drivers. It wont get your UNR interface back.
Do all updates. Then run (and if needed install first) desktop-switcher. It lets you switch beween the classic gnome interface and the UNR interface.

---

### Post by Wim Sturkenboom on 2009-08-28
I tried to install from commandline and desktop-switcher is already installed. How do I run it (from a console) or graphical environment (without menus)?

PS
I did remove *nv* from xorg.conf, rebooted and it still uses nv as the driver.
I did a *dpkg-configure xserver-xorg* but that did not solve it (maybe even screwed it up more).

---

### Post by 3rdalbum on 2009-08-28
> **Wim Sturkenboom said:**
> I tried to install from commandline and desktop-switcher is already installed. How do I run it (from a console) or graphical environment (without menus)?

PS
I did remove *nv* from xorg.conf, rebooted and it still uses nv as the driver.
I did a *dpkg-configure xserver-xorg* but that did not solve it (maybe even screwed it up more).

You should be able to press Alt-F2 and type "netbook-launcher" to restart the Netbook Launcher interface.

---

### Post by Wim Sturkenboom on 2009-08-28
I did a fresh install and ran the updates. Next I installed nvidia-glx-180 and the netbook menus disappeared after a restart of the x-server.

Ran *netbook-launcher* from alt-F2 and it does not do anything
Ran *netbook-launcher* from xterm and it gives an error
```

Xlib: extension "GLX" missing on display 0:0.
Unable to run Netbook Launcher; XServer appears to lack required GLX support

```
However, I'm not sure if I can run it from xterm.

Ran desktop-switcher from alt-F2 and it does not give me the menus back (classic or netbook).
Ran desktop-switcher from xterm and it displays
```

In classic mode: true
...
...
same Xlib message as above
...
...

```
and a couple of warnings and a critical error *panel_applet_frame_change_background:asset*

Rerunning it does not show the critical error

So stuck again (grumble grumble)

---

### Post by Wim Sturkenboom on 2009-08-31
Forgot my usb-stick today, so did a normal 9.04 install, refreshed the package list and ran the updates.

The hardware manager shows two nvidia versions (173 and 180) and the option to activate. Click activate and after autentication I get a little popup with a one-way sign (red circle with horizontal white bar).

Checked synaptic and nvidia-glx-180 is not installed. Decided to install and run the hardware manager again; this time it did not complain.

Tried to enable desktop effects and it still says that desktop effects could not be enabled.

Restarted x-server (<alt><printscreen>k) and I now have a message that Ubuntu is running in low graphics mode. 

The errors from /var/log/Xorg.0.log
```

EE EVO push buffer channel allocation failed
EE *** aborting ***
EE Failed to allocate EVO DMA push buffer
EE *** aborting ***
...
...
II Virtual screen size determined to be 1440x900
EE Failed to unmap EVO channel memory
EE Failed to tear down EVO channel

```

Clicking OK gave some options and I opted to generate a new configuration and after some more clicking on OK I now managed to end up with an unresponsive keyboard and a blank screen (screen goes into powersave mode) :(

Managed to switch it of and after a reboot stiil the blank screen but at least I can get to a console again with <ctrl><alt><F1>. It however is not happy (looks like refresh rates are a little wrong). Changed the driver in xorg.conf from nvidia to nv, rebooted and now it works again.

Some more research to do, but likely to give up on this one.

I specifically want the drivers from the repository as I don't want to go through the whole install story as published elsewhere on Ubuntu Forums.

---

### Post by Wim Sturkenboom on 2009-09-03
The machine is now gone to my boss and will get WinXP installed again.

---

