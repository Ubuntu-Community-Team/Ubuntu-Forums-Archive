---
title: "&quot;Strip down&quot; Ubuntu 10.04?"
date: 2010-08-26
forum: General Help
---

### Post by rubencouto on 2010-08-26
Hello!
 
I use a Toshiba laptop, with 256MB Ram.
This latest version of Ubuntu is starting to slow down the laptop, because it requires more Ram.
 
I would like to know if there is a way to "strip down" this version of Ubuntu, so that I don't have to chage distro in order to reduce the Ram usage.
 
Any ideas?
:)
Thanks in advance!
Ruben

---

### Post by Mze on 2010-08-26
from the info on [Ubuntu minimum system requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements"), you might have to try another version of Ubuntu. Xubuntu or Lubuntu

I'd go for Puppy Linux 5.0 - which is also based on Ubuntu

---

### Post by afrowildo on 2010-08-26
Before you try anything drastic, like uninstalling applications and components, you should try installing and running UbuntuTweak [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/). It gives you an immense amount of options with regard to streamlining your system.

Also, are you running a lot of applications at startup that aren't being shut down? I've come across an option before that makes Ubuntu remember what applications were running when it last closed down and open them again at startup, so they won't appear in your list of startup programs.

---

### Post by oaxacamatt1 on 2010-08-26
You should try the Netbook Ubuntu version.  I think it runs pretty well on my limited system.

[http://www.ubuntu.com/netbook](http://www.ubuntu.com/netbook)

Cheers,
M

---

### Post by Mze on 2010-08-26
The time that will be spent uninstalling applications on a 256 MB system will pretty much amount to just installing one of the other Ubuntu derivatives.

In my opinion, a time consuming process; even if faintly possible on a system that doesn't meet the minimum requirements for smooth running. 

But hey, this is what being geeky is about. Make the seemingly impossible possible on inadequate resources.

---

### Post by holycow131415 on 2010-08-26
Lucid Puppy 5.1 works with ubuntu repositories. Its not based on ubuntu.

[http://puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm](http://puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm)

---

### Post by snowpine on 2010-08-26
> **rubencouto said:**
> Hello!
 
I use a Toshiba laptop, with 256MB Ram.
This latest version of Ubuntu is starting to slow down the laptop, because it requires more Ram.
 
I would like to know if there is a way to "strip down" this version of Ubuntu, so that I don't have to chage distro in order to reduce the Ram usage.
 
Any ideas?
:)
Thanks in advance!
Ruben

256mb of RAM is borderline for any modern Linux distro (1gb is the recommended minimum for Ubuntu); a RAM upgrade would be your best option in the long-term.

Before you do anything drastic, you can try a lightweight windows manager or desktop environment with your current Ubuntu install. For example, if you want to try LXDE:

```
sudo apt-get install lxde
```

Log out and select Sessions->LXDE from the login screen.

---

### Post by rubencouto on 2010-08-27
Thanks all you guys for the input!!
 
I'll try some of these ideas. Maybe I'll start with the lxde idea. And then Ubuntu Tweak.
 
:)
Ruben

---

### Post by mike555 on 2010-08-27
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


 [IMG]http://i40.tinypic.com/14c402e.jpg[/IMG]

---

### Post by wojox on 2010-08-27
Don't strip it, build it. [ Modest Spec or Barebones Installation of Ubuntu]("http://www.psychocats.net/ubuntu/minimal")

---

