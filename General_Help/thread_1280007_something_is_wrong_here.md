---
title: "something is wrong here"
date: 2009-10-01
forum: General Help
---

### Post by bd41 on 2009-10-01
Im trying to install the ati driver from the ATI websites for my graphics card

It keeps asking me to run in terminal as super user. Ive used Sudo and i even opened up a root terminal. Still asking for super user...

---

### Post by BQAggie2006 on 2009-10-01
Have you tried:
```
sudo su
```

---

### Post by scragar on 2009-10-01
Try running```
sudo -i
```And running it them. Be sure to drop out of root when you're done though.

PS: is there any reason you are downloading and installing the driver manually and not using something like envy?

---

### Post by bd41 on 2009-10-01
> **scragar said:**
> Try running```
sudo -i
```And running it them. Be sure to drop out of root when you're done though.

PS: is there any reason you are downloading and installing the driver manually and not using something like envy?

whats envy?

---

### Post by Slim Odds on 2009-10-01
All time most informative title ever......

---

### Post by scragar on 2009-10-01
> **bd41 said:**
> whats envy?

[quote=http://albertomilone.com/nvidia_scripts1.html]"Envy" is an application for Ubuntu Linux and Debian written in Python and PyGTK which will:
1) detect the model of your graphic card (only ATI and Nvidia cards are supported) and install the appropriate driver. However automatic detection can be overridden with the "Manual installation"
2) install the right driver for your card and all the required dependencies
3) configure the Xserver for you
[/quote]
In other words it installs official graphics drivers for you.
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

