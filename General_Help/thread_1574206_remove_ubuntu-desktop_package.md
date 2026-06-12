---
title: "remove ubuntu-desktop package?"
date: 2010-09-13
forum: General Help
---

### Post by jfreak_ on 2010-09-13
So i am converting to openbox and don't need most of the baggage that comes along with the standard desktop. But most of these packages list ubuntu-desktop as a dependency. So is it safe to remove ubuntu-desktop (Not going to upgrade to maverick) ? 
You guys know of any other resource crunching services that can be removed? ( Currently openbox at idling is at 130 mb Ram and I know that this number can be reduced)

---

### Post by Jesus_Valdez on 2010-09-13
I know that is safe to remove the ubuntu-desktop package, and I would love to know about the other thing, I just removed Ubuntu One and Evolution.

---

### Post by wojox on 2010-09-13
> **jfreak_ said:**
> So i am converting to openbox and don't need most of the baggage that comes along with the standard desktop. But most of these packages list ubuntu-desktop as a dependency. So is it safe to remove ubuntu-desktop (Not going to upgrade to maverick) ? 
You guys know of any other resource crunching services that can be removed? ( Currently openbox at idling is at 130 mb Ram and I know that this number can be reduced)

Sure. Ubuntu-desktop is a metapackage. You could always try here as well [Modest Spec or Barebones Installation of Ubuntu]("http://www.psychocats.net/ubuntu/minimal")

---

### Post by wilee-nilee on 2010-09-13
On this website you can get the whole list of Ubuntu to remove and just have open box. Be careful at the end of any of these lists is the desktop that is intended to be installed, don't include that.
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

I have just defaulted to a random page look through the options in the left panel.

Sort of a unusual way of getting the package list for the distro-desktop you want to remove

---

### Post by jfreak_ on 2010-09-13
> **wojox said:**
> Sure. Ubuntu-desktop is a metapackage. You could always try here as well [Modest Spec or Barebones Installation of Ubuntu]("http://www.psychocats.net/ubuntu/minimal")
Nah i am already on a 6 month old install and it will be too much of a bother to re-install. So basically want to keep removing unneeded packages, like cups(don't have a printer), evolution, samba etc

---

### Post by wojox on 2010-09-14
Evolution you have to be careful with

```
sudo apt-get remove evolution evolution-common evolution-couchdb evolution-exchange evolution-indicator evolution-plugins evolution-webcal
```

I use CUPS and Samba

---

### Post by jfreak_ on 2010-09-14
You have any idea what the guys at crunchbang and peppermint(openbox) have done to keep their usage well below 100mb?

---

### Post by snowpine on 2010-09-14
> **jfreak_ said:**
> You have any idea what the guys at crunchbang and peppermint(openbox) have done to keep their usage well below 100mb?

They start with a minimal install and build up, rather than starting with a full install and stripping down.

Also, RAM use depends on a number of factors, the biggest being how much RAM you have available. 100mb is a lot if your computer only has 128mb, but if you have 1gb or more, it is nothing. :)

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by mike555 on 2010-09-15
This is what I did ;
Uninstall using the package manager (mark for complete removal)

- bluez
- bluez-alsa
- bluez-cups
- bluez-gstream
- britty
- compiz
- compiz-core
- computer-janitor
- empathy
- empathy-common
- espeak
- espeak-data
- evolution
- evolution-common
 - evolution-data-server (but not data-server common)
- evolution-webcal
- f-spot
- g-brainy
- gwibber
- gwibber-service
- indicator-me
- indicator-messages
- mono-2.0-gac
- python-ubuntuone
- python-ubuntuone-client
- python-ubuntuone-storageprotocol

- shut down , wait a minute then start ... you will see much less memory usage.

 - then you can install some lighter apps, like ; gnote ,  mirage , gufw , abiword , Thunderbird , ubuntu-tweak ,etc.

---

### Post by masuch on 2012-05-02
> **wilee-nilee said:**
> On this website you can get the whole list of Ubuntu to remove and just have open box. Be careful at the end of any of these lists is the desktop that is intended to be installed, don't include that.
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

I have just defaulted to a random page look through the options in the left panel.

Sort of a unusual way of getting the package list for the distro-desktop you want to remove

thanks for URL.

---

