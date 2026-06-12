---
title: "How do I install adobe flash for Ubuntu 9.04"
date: 2009-07-04
forum: General Help
---

### Post by denz_el on 2009-07-04
hi all, 
I am pretty new to ubuntu, and i''ll like help in installing adobe flash player for Ubuntu 9.04.

---

### Post by wojox on 2009-07-04
```
sudo apt-get install adobe-flashplugin
```

---

### Post by denz_el on 2009-07-04
thank you,  will try it.

---

### Post by markharding557 on 2009-07-04
install ubuntu-restricted-extras this will install flash and other useful things as well.

---

### Post by lovinglinux on 2009-07-04
I recommend performing the instructions below, since you might already have another flash plugin installed that don't work properly. They will install the Adobe flash plugin and remove the others that might conflict with it.

> **lovinglinux said:**
> 
To remove conflicting flash plug-ins and install only the one from Adobe Open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree 
```



Also visit the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) for some additional Firefox tweaks and tips.

---

### Post by TrakerJon on 2009-07-04
What all these wonderful folks forgot to tell you is that you need the Medibuntu Repository.

Many of these installations require access to the Medibuntu Repository and enabling some additional software sources. Directions are on this site: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) or if you have Ubuntu 9.04 "Jaunty Jackalope" simply do the following from a terminal window:

sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

This post should help you overall [http://ubuntuforums.org/showthread.php?p=7418021]("http://ubuntuforums.org/showthread.php?p=7418021")

P.S. Installing ubuntu-restricted-extras is sometimes problematic I highly suggest installing things individually until you know how to fix broken packages.

---

### Post by Sef on 2009-07-04
> Many of these installations require access to the Medibuntu Repository and enabling some additional software sources. Directions are on this site: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

About the only thing that you need from Medibuntu is some DVD playback.   The rest can be installed through Add/Remove.   Applications > Add/Remove > Show: All Applications Available > Search:  Restricted > click on box next to Ubuntu Restricted Extras (or Kubuntu or Xubuntu depending on what os you installed) > click apply changes > apply > close.

>  	 		**Re: How do I install adobe flash for Ubuntu 9.04**
 		 	Code:
 	sudo apt-get install adobe-flashplugin 


That is not the correct way to install an application.   Before installing an application, you need to update the repositories, so you get the latest application versions from the repositories.  The correct code is this:

```
sudo apt-get update && sudo apt-get install name_of_program
```

However, you should tell them to use Add/Remove as it is easier and less intimidating to someone who is brand new or has not stated they want to use the Terminal.   The Terminal is very intimidating to many people.

---

### Post by michy99 on 2009-07-04
> **Sef said:**
> 
However, you should tell them to use Add/Remove as it is easier and less intimidating to someone who is brand new or has not stated they want to use the Terminal.   The Terminal is very intimidating to many people.

That is a matter of opinion. I have seen convincing arguments on both sides of the question.

---

