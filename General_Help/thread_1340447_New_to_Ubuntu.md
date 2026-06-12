---
title: "New to Ubuntu"
date: 2009-11-28
forum: General Help
---

### Post by Gingerjoe on 2009-11-28
hey.

New User to ubuntu, so far really enjoying it, Just getting round the way to install items ect, atm ive got a internet cable connected straight to the p.c, & its working fine, but its for my xbox, my Wireless card is in the computer, but doesnt work, Just wondering if anyone could help me install it? its a belkin Wirelesss G plus desktop card,  54G 125 highspeed, also Im trying to get hold of Wine so I can install photoshop, if someone could help out & do a idiot guide to for me. would well appreacite it! haha. Tar.

---

### Post by mechro on 2009-11-28
Wine is available as a package from Ubuntu's repositories. Go to **System > Administration > Synaptic Package Manager** and search for Wine.

---

### Post by Gingerjoe on 2009-11-30
ahh sweet tar! I found it before but it wouldnt let me download anything, but then ubuntu updated & it let me, Any idea on getting the wireless card to work?

---

### Post by 3rdalbum on 2009-11-30
What is the output of the commands:

```
lsusb
lspci
```

Once we know what chipset the card uses, we might be able to help you find a driver.

---

### Post by Wandels on 2009-11-30
Download these files and install:

[LIST]
[*][http://packages.ubuntu.com/jaunty/misc/ndiswrapper-common](http://packages.ubuntu.com/jaunty/misc/ndiswrapper-common)
[*][http://packages.ubuntu.com/jaunty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/jaunty/misc/ndiswrapper-utils-1.9)
[*][http://packages.ubuntu.com/jaunty/net/ndisgtk](http://packages.ubuntu.com/jaunty/net/ndisgtk)
[/LIST]
Then go to System > Administration > Windows Wireless Drivers > Add
Now find the right .INF file for your driver/system.

---

### Post by audiomick on 2009-11-30
Gimp is not quite photoshop, but nearly, and worth a look.

---

### Post by mechro on 2009-11-30
> **Gingerjoe said:**
> Any idea on getting the wireless card to work?

Sorry, can't help you there. I'm still using wires.

Try posting another thread about your wireless problem but give it a title something like "Belkin Wireless Not Working". Mention your Belkin card info again and mention what version of Ubuntu you're using.


Edit: I see somebody's helping so ignore my comment about new thread.

---

### Post by john newbuntu on 2009-11-30
Here's the place to start:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by Mark Phelps on 2009-11-30
If you've installed Wine simply to use Photoshop, unless you're using a really old version of Photoshop, you're wasting your time.

See the Wine App Compatibility page below:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=17]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=17")

---

### Post by 3rdalbum on 2009-11-30
> **Wandels said:**
> Download these files and install:

[LIST]
[*][http://packages.ubuntu.com/jaunty/misc/ndiswrapper-common](http://packages.ubuntu.com/jaunty/misc/ndiswrapper-common)
[*][http://packages.ubuntu.com/jaunty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/jaunty/misc/ndiswrapper-utils-1.9)
[*][http://packages.ubuntu.com/jaunty/net/ndisgtk](http://packages.ubuntu.com/jaunty/net/ndisgtk)
[/LIST]
Then go to System > Administration > Windows Wireless Drivers > Add
Now find the right .INF file for your driver/system.

...which does not always work (not all drivers are compatible with ndiswrapper), and will definitely not work if there are already native drivers attempting to handle the wireless card. They would need to be removed first; and for that we need to know what chipset it is.

Also, the packages you linked to are from 9.04. They won't necessarily work with 9.10.

---

### Post by Wandels on 2009-12-01
Sorry, I just know it worked for me.

---

