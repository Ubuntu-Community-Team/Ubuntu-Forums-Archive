---
title: "Why the heck don't I have a login window manager?"
date: 2010-03-06
forum: General Help
---

### Post by Rex Kekkonen on 2010-03-06
I just installed ubuntu and due to having a buggered CD and no option to burn another one I had to make a bootable USB stick via my netbook & UNetbootin. So I install this thing and I chose Gnome as the standard window manager when installing.

When it's done it boots into xfce instead and the login screen is not the regular one either. Another weird fact was that it said Kubuntu, then Xubuntu before coming to the login screen. Anyway I can choose Gnome there so I log into gnome and proceed to remove all this Xubuntu and Kubuntu stuff I can find. 

But I still can't change the login screen, I don't have a System > Preferences > Login Window to even choose from. I have a Login Screen though but all it shows is this unhelpful bit:

[img]http://xs.to/image-DCCC_4B923483.jpg[/img]

So, anyone know how I can get this piece of functionality restored? Maybe just some software that's missing I hope. I am pretty sure this is because I had to use the net installation.

---

### Post by Intrepid Ibex on 2010-03-06
I am 99% sure you didn't download a _Ubuntu_ live CD (maybe xubuntu?).

Also it seems you have xdm and not gdm set up. The "Login Window" menu will appear when you install gdm ('sudo apt-get install gdm' or search it with synaptic).

---

### Post by wojox on 2010-03-06
Easiest way would be to download Start Up Manager and then, go to the second tab, "Appearance," and select the usplash-theme-ubuntu entry from the "Usplash theme" section

---

### Post by Rex Kekkonen on 2010-03-06
> **Intrepid Ibex said:**
> I am 99% sure you didn't download a _Ubuntu_ live CD (maybe xubuntu?).

Also it seems you have xdm and not gdm set up. The "Login Window" menu will appear when you install gdm ('sudo apt-get install gdm' or search it with synaptic).

Hmm I chose Ubuntu 9.10 64-bit version from the USB stick creating program, and when I look at "About Ubuntu" from the system menu it tells me "You are using Ubuntu 9.10 - the Karmic Koala - released in October 2009 and supported until April 2011."

I ran the command you provided which says it's all up to date:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gdm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Intrepid Ibex on 2010-03-06
Allright then, like the funniest thing ever. To start using gdm you can execute this:
```
sudo dpkg-reconfigure gdm
```
**E:** and like select gdm from there.

---

### Post by Rex Kekkonen on 2010-03-06
> **wojox said:**
> Easiest way would be to download Start Up Manager and then, go to the second tab, "Appearance," and select the usplash-theme-ubuntu entry from the "Usplash theme" section

I'm afraid I just tried that and rebooted but the same old uggo login screen is still there... Maybe it would help if it was possible to take a screen shot of the login screen I am presented with?

---

### Post by Rex Kekkonen on 2010-03-06
> **Intrepid Ibex said:**
> Allright then, like the funniest thing ever. To start using gdm you can execute this:
```
sudo dpkg-reconfigure gdm
```
**E:** and like select gdm from there.

It gets funnier, when I do that it just thinks for a second, then returns me to the prompt.

---

### Post by wojox on 2010-03-06
Sorry Rex I was thinking Splash Screen not login. For login open a terminal and run this:

```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

Change your theme and background to what you want.

---

### Post by Rex Kekkonen on 2010-03-06
> **wojox said:**
> Sorry Rex I was thinking Splash Screen not login. For login open a terminal and run this:

```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

Change your theme and background to what you want.

I'm sorry but I do not see where I can change the login screen here:
[img]http://xs.to/image-1E28_4B923E87.jpg[/img]

---

### Post by wojox on 2010-03-06
Click on custom > Customize and make sure everything is set to Human. On backgrounds select the cranberryish background.

---

### Post by bumanie on 2010-03-06
Login manager changed in 9.10 - generally changing the themes won't work. But there is a 'hack' you can try is you wish. It's in [this]("http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html") thread.

---

### Post by Rex Kekkonen on 2010-03-06
Oh! So it's not a bug, it's a feature.

---

### Post by bumanie on 2010-03-06
Yes, it may be a retrograde feature in some peoples opinion, but it is there on purpose. It has been changed to assist with improving boot times, as far as I can work out.

---

### Post by MelDJ on 2010-03-06
you can also try: [https://launchpad.net/gdm2setup/](https://launchpad.net/gdm2setup/)

---

