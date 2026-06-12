---
title: "no internet connection"
date: 2011-01-31
forum: General Help
---

### Post by michaelalmond on 2011-01-31
I have loaded Ubuntu studio onto an older computer. Seems to work fine but I cannot get an internet connection. Any advice appreciated.

---

### Post by TeoBigusGeekus on 2011-01-31
Wired or wireless?

---

### Post by stinkeye on 2011-01-31
Network Manager is disabled by default in Ubuntu Studio 10.04.
See here to fix: [**_[COLOR="DarkRed"]UbuntuStudioNetworkSetup[/COLOR]_**]("https://help.ubuntu.com/community/UbuntuStudioNetworkSetup")

---

### Post by michaelalmond on 2011-02-01
Thanks I''ll try that then.

---

### Post by michaelalmond on 2011-02-02
> **stinkeye said:**
> Network Manager is disabled by default in Ubuntu Studio 10.04.
See here to fix: [**_[COLOR="DarkRed"]UbuntuStudioNetworkSetup[/COLOR]_**]("https://help.ubuntu.com/community/UbuntuStudioNetworkSetup")
Tried that page you suggested - managed to load one of the .deb packages. The other three would not load.

Error:Dependency is not satisfiable: libnm-glib2
(>=0.8.1 -beta3 -git_20100626t172728.44d2f9c)

I must be doing something wrong
Thanks anyway.

---

### Post by stinkeye on 2011-02-02
Take a note of the dependency and install that package first.
I think it's in the same folders.
ie the network-manager and network-manager-applet folders.

---

### Post by michaelalmond on 2011-02-05
Thanks. Managed to install the packages. Network Manager has appeared, ticked enable networking but networking remains firmly disabled. I have read that Ubuntu is plagued with network connection problems. Is it worth continuing?

---

### Post by stinkeye on 2011-02-05
> **michaelalmond said:**
> Thanks. Managed to install the packages. Network Manager has appeared, ticked enable networking but networking remains firmly disabled. I have read that Ubuntu is plagued with network connection problems. Is it worth continuing?
Did you follow the second part, after you installed the packages, on the help page I posted?

The only problems I'm aware of are with some wireless cards.
Ubuntu studio is just plain ubuntu setup to give you the best enviroment for
audio and video production with all the packages included in the iso.
You can download and run any of the applications in a normal Ubuntu install.

---

### Post by michaelalmond on 2011-02-06
Yes, I've configured the connections several times - still no joy.
The networking card I'm using is a Realtek, 1839C - I think

---

### Post by Spyderkid on 2011-02-06
Have a look on here

[http://www.google.co.uk/url?sa=t&source=web&cd=2&sqi=2&ved=0CBsQFjAB&url=http%3A%2F%2Fwww.opendrivers.com%2Fcompany%2F2358%2Frealtek-free-driver-download.html&ei=B6ROTdHQGN2qhAeep9DNDg&usg=AFQjCNFWvGJBgJRib7hA1V6-703uh4KEZA](http://www.google.co.uk/url?sa=t&source=web&cd=2&sqi=2&ved=0CBsQFjAB&url=http%3A%2F%2Fwww.opendrivers.com%2Fcompany%2F2358%2Frealtek-free-driver-download.html&ei=B6ROTdHQGN2qhAeep9DNDg&usg=AFQjCNFWvGJBgJRib7hA1V6-703uh4KEZA)

---

### Post by stinkeye on 2011-02-06
Is that wired or wireless and have you had it working with an Ubuntu install?

---

