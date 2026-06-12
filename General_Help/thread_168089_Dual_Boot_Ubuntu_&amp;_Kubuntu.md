---
title: "Dual Boot: Ubuntu &amp; Kubuntu"
date: 2006-04-29
forum: General Help
---

### Post by reubadoob on 2006-04-29
Ok I've searched and searched and haven't found exactly what I'm looking for so  I figured it was time to post. 

**Here's the situation:**
 I installed Ubuntu complete over Windows XP. And I'm not ashamed of it. Too many problems and I got tired of it. Not before I burned my files to a DVD-ROM though. ;) So now I have Ubuntu, I enjoy it but to me it's lacking that GUI that I feel I'm missing. 

**So here are the questions: **
I have Ubuntu installed and is there a simple way to create a partition to install Kubuntu onto my hard drive? Emphasis on **SIMPLE**. I haven't really installed anything in Ubuntu that I can't re-install within Kubuntu within a couple of hours at the most. Would it be better/more effiecient to un-install Ubuntu, then install Kubuntu?

**Summary:**
Ubuntu installed
Want Kubuntu
Partition **OR** Over-Write

Thanks guys for all your help and support/suggestions. 

By the way I'm downloading the Kubuntu install/live DVD onto my brothers Windows Box for later burning. I saw threads that said its posible to install Kubuntu from within Ubuntu or something like that. If that's possible I'd really like to free up some bandwidth here at home.

---

### Post by gingermark on 2006-04-29
If you're confident Kubuntu will be more your thing, then a fresh install might be ideal,

But to be honest, if you have the net connection on your ubuntu box, it would be easier to open up Terminal, and do
```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

During the install you are asked if you want GDM or KDM - If you think you'll use KDE more often choose KDM.

Then, when the install is finished restart X (Ctrl+Alt+Backspace) and choose KDE under the sessions menu.

---

### Post by reubadoob on 2006-04-29
Its that simple?? What's the difference between GDM & KDM? I'm a n00b.

---

### Post by hollywoodb on 2006-04-29
You can just 'sudo apt-get install kubuntu-desktop' metapackage... it will install KDE with some extras and you can select to start KDE instead of Gnome at the graphical login prompt (GDM).

In my opinion there's really no point in dual-booting kubuntu & ubuntu.  They are the same system.  Same daemons, same kernel, etc etc.  Simply a different desktop.

If you do decide to have ubuntu-desktop (default) and kubuntu-desktop (kubuntu) installed side by side, chances are a lot of Gnome apps will show up in your KDE menu and a lot of KDE apps will show up in your Gnome menu.  If you don't like this behaviour both menus are easily editable.

---

### Post by mexlinux on 2006-04-29
GDM=Gnome Display Manager
KDM=KDE Display Manager

Don't worry, You simply select KDM

---

### Post by gingermark on 2006-04-29
[QUOTE=reubadoob]Its that simple?? What's the difference between GDM & KDM? I'm a n00b.[/QUOTE]
Yes, it's that simple, although you will have your menu populated with applications from both environments (which can be a bit cluttered).

In practical terms, If you select KDM you can shutdown your computer from within KDE - if you used GDM, you'd have to log out of KDE first, and then shutdown from the login screen. GDM allows you to shutdown from within GNOME, whilst using KDM would mean you'd have to log out of GNOME first.

In practice, it doesn't really matter which one you use, but if you think you might use KDE more than GNOME, then KDM would be a little more convenient.

---

### Post by Ensnared on 2006-04-29
Wether you use KDM or GDM really is only a matter of preference. You'll be able to configure KDM from the KDE control panel while GDM requires you to use the gdmsetup utility (which is installed along with gdm), but other than that, it doesn't really matter which one you use.

I only use KDE, but I'm using GDM for my login-manager, because the graphical greeter in GDM is simply too purty not to use ;) It requires a nice skin though, but there are [tons](http://art.gnome.org/themes/gdm_greeter/) of [those](http://www.gnome-look.org/index.php?xcontentmode=150) around to choose from :)

Of course, for all I know, KDM has gotten the same possibilities the GDM greeter since last time I checked. If that's the case, then KDM is better simply because of the control center configuration, but really - how often do you reconfigure your login-screen anyway? I know I hardly ever do that once I've set it up the way I like it ;)

---

### Post by reubadoob on 2006-04-30
[QUOTE=gingermark]Yes, it's that simple, although you will have your menu populated with applications from both environments (which can be a bit cluttered).
[/QUOTE]

That's kinda strange. How would you edit this from happening? Or is it possible to un-install the ubuntu desktop (default) all together?

[QUOTE=hollywoodb]
If you do decide to have ubuntu-desktop (default) and kubuntu-desktop (kubuntu) installed side by side, chances are a lot of Gnome apps will show up in your KDE menu and a lot of KDE apps will show up in your Gnome menu.  If you don't like this behaviour both menus are easily editable.[/QUOTE]

Now by "side by side" do you mean on seperate paritions or this going to happen just by installing the KDE desktop? I'd like to aviod clutter if at all possible. You said it was "easily editable" how would you go about that?

---

### Post by der_joachim on 2006-04-30
[QUOTE=reubadoob]That's kinda strange. How would you edit this from happening? Or is it possible to un-install the ubuntu desktop (default) all together?[/QUOTE]

I'd prefer my Gnome apps to show up in KDE and vice versa. Some KDE apps are better than their Gnome counterparts and since Firefox is a GTK app (GTK is the graphical lib behind Gnome), I'd be very confused if it were not in my KDE menu.


[QUOTE=reubadoob]Now by "side by side" do you mean on seperate paritions or this going to happen just by installing the KDE desktop? I'd like to aviod clutter if at all possible. You said it was "easily editable" how would you go about that?[/QUOTE]

Just install the KDE desktop. I do not remember about Gnome, but KDE uses the program KMenuEdit. You can easily find it in your control center (just like Windows) or your applications menu.

---

### Post by hollywoodb on 2006-04-30
[QUOTE=reubadoob]That's kinda strange. How would you edit this from happening? Or is it possible to un-install the ubuntu desktop (default) all together?[/QUOTE]

There are various threads on the forum about uninstalling ubuntu-desktop to look into

[QUOTE=reubadoob]Now by "side by side" do you mean on seperate paritions or this going to happen just by installing the KDE desktop? I'd like to aviod clutter if at all possible. You said it was "easily editable" how would you go about that?[/QUOTE]

On seperate partitions you'll have two Ubuntu installs, one with KDE (kubuntu-desktop) and one with Gnome (ubuntu-desktop).  Neither install will be aware of the other as far as desktop use goes.  By "side by side" I mean having kubuntu-desktop and ubuntu-desktop on the same partition, same installation.  Both desktops have a menu editor you can use to remove the apps you won't use.  The menus & menu editors for each desktop are completely seperate from a usage point of view, so you can edit KDE's menu to show apps you would only use in KDE and edit Gnome's menu to show apps you would only use in Gnome.  If you choose to keep both desktops you could even create a "Gnome" submenu in the KDE menu that contains your gnome apps if that's what you would like to do.

Also, KDE can set Gnome/GTK2 apps to look like KDE apps.  If there are apps present in ubuntu-desktop that you would like to use under kubuntu-desktop they won't look completely out of place.

---

### Post by reubadoob on 2006-04-30
I ran the following command:
[B]
sudo apt-get uninstall gnome[/B]

But I got this error:
[B]
E: Invalid operation uninstall[/B]


What's the right command line?

---

### Post by gingermark on 2006-04-30
it's 'sudo apt-get remove'.

But that won't do anything in this case, as gnome is a meta-package - one that points to others.

You could try the instructions in [this thread](http://ubuntuforums.org/showthread.php?t=96046) if you're trying to remove ubuntu. Otherwise, you'll have to remove the packages you don't want manually I'm afraid.

In the future, if you install any other metapackage, use aptitude instead of apt-get when you install it (so 'sudo aptitude install blah'). Then, if you want to remove it afterwards you can easily. (this is why I instructed you to install kubuntu-desktop that way, in case you changed your mind later).

---

### Post by sweet_as_an_elf on 2008-02-10
Thanks everyone for putting together this thread -- it has been immensely helpful!

---

