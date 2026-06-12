---
title: "Gnome Keyring"
date: 2010-06-09
forum: General Help
---

### Post by baker126 on 2010-06-09
Hi all...I have a quick question.  I switched to Kubuntu with the upgrade to Lucid.  After a couple updates, I started getting a "Gnome looking" unlock screen on my desktop at start-up.  I get the regular KDE keyring password request and a second that looks like the Gnome keyring.  I don't know how this happened.  I checked in Synaptic and found the gnome-keyring was installed.  Can I uninstall this or will that cause problems?  

Thanks for the help.

---

### Post by sleepitoff on 2010-06-09
You can remove it, yes, but you might also remove a couple apps you like if you do so.

---

### Post by baker126 on 2010-06-09
Is there any way to find out what apps are using the gnome-keyring prior to removing it?  I was trying to switch completely to KDE to give it a try...

---

### Post by ankspo71 on 2010-06-09
Hi,
I had gnome-keyring on my Kubuntu too (probably because I installed Synaptic Package Manager), so I uninstalled it just to see if it was safe to remove. Using the command **sudo apt-get remove gnome-keyring** only removed "gksu gnome-keyring software-properties-gtk". I also ran the command **sudo apt-get autoremove** and didn't it find any unwanted leftover programs. It looks safe to remove - to me too.
Hope this helps.
PS. Write down anything your system wants to remove so you can easily install them again, if needed.

---

### Post by jepong on 2010-06-10
actually i'm also asking the same question at the Kubuntu Forums ([http://kubuntuforums.net/forums/index.php?topic=3112312.0](http://kubuntuforums.net/forums/index.php?topic=3112312.0))

Also, you can remove libpam-gnome-keyring too.

---

### Post by baker126 on 2010-06-10
Beautiful...Worked like a champ!  Thanks for the quick reply!

---

