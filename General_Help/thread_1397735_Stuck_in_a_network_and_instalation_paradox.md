---
title: "Stuck in a network and instalation paradox"
date: 2010-02-03
forum: General Help
---

### Post by ShadowMosesGreen on 2010-02-03
All I am trying to do is gain access to the internet and install wine.  Here's the problem.  Ubuntu won't recognize any drivers or networks.  And I do mean none.

This is what I get when I try to find drivers.
[http://i72.photobucket.com/albums/i161/Zeppelin5080/Screenshot.png](http://i72.photobucket.com/albums/i161/Zeppelin5080/Screenshot.png)

In order to gain a wireless network card driver and go into the network configuration to enable the driver, I figured I'd install Wine so I can use my network card driver CD to install the driver for it.  But here's the thing, I can't get Wine because I have no access to the internet.  And to gain access to the internet, I need wine.  How on earth do I go about getting either?  I'm stuck in limbo right now.

---

### Post by mikewhatever on 2010-02-03
As far as I know, wireless drivers don't work in wine, so even if you could get it, it would not help. If you are absolutely certain that you need Windows drivers, ndiswrapper is the program to install. I am not quite sure, but it may be on the live cd. It is somewhat rare these day, that you need to use ndiswrapper, as most wireless cards have native Linux drivers. If not sure, post your wireless card model.

---

### Post by ShadowMosesGreen on 2010-02-03
> **mikewhatever said:**
> As far as I know, wireless drivers don't work in wine, so even if you could get it, it would not help. If you are absolutely certain that you need Windows drivers, ndiswrapper is the program to install. I am not quite sure, but it may be on the live cd. It is somewhat rare these day, that you need to use ndiswrapper, as most wireless cards have native Linux drivers. If not sure, post your wireless card model.
I am absolutely aware that Linux is not Windows.  But, I am aware that a number of people have been telling me to get an installation program or use the terminal to install my network drivers.  After I tell them that there is no where it says to enable the network, they, without fail, tell me to get Wine, Aptitude, Adept or Synaptic by typing in sudo apt-get (whatever the program may be) and I tell them, "hey, I can't do that because I have no networks hooked up."  Or they tell me to go into the Software Center and I have to tell them that I have no networks.  Or they tell me to type sudo apt-get update and I have to tell they that I have no networks.  I been being told to get some installation program (using the internet) in order to install the network driver, and I obviously can't access the internet to get anything.  I am aware that Linux is not Windows.  I am aware that the Unix system is nothing Windows.  And the only thing about the card is that it's an 802.11 2.4Ghz Wirelss Adapter.  It doesn't say the brand name anywhere on the card but I do know that it's a zonet.  And it does not have the model either.

---

### Post by audiomick on 2010-02-03
If it is not a USB device, do
```
lspci
```
in the terminal. The network card should be listed there.

If it is a usb device, you should see it with
```
lsusb
```

Post the output of whichever is appropriate here. It could assist in helping you.

---

### Post by ShadowMosesGreen on 2010-02-03
> **audiomick said:**
> If it is not a USB device, do
```
lspci
```in the terminal. The network card should be listed there.

If it is a usb device, you should see it with
```
lsusb
```Post the output of whichever is appropriate here. It could assist in helping you.

Ok.  I have just started using Ubuntu and I am trying to learn more.  And I need step by step instructions.  Don't just say "open up terminal."  Tell me to go to the Ubuntu button > Application > Terminal.  Do you want me to open up terminal and type spci?

---

### Post by lisati on 2010-02-03
> **ShadowMosesGreen said:**
> Ok.  I have just started using Ubuntu and I am trying to learn more.  And I need step by step instructions.  Don't just say "open up terminal."  Tell me to go to the Ubuntu button > Application > Terminal.  Do you want me to open up terminal and type spci?

You're on to it. (btw, don't forget the "l" (small L), it's **lspci**)

---

