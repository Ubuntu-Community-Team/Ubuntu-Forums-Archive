---
title: "Installing nothing but another desktop environment"
date: 2011-05-13
forum: General Help
---

### Post by Spitted on 2011-05-13
Hi
I'm running a regular installation of Ubuntu 10.10 with Gnome. I would like to try LXDE and other desktop environment, BUT without installing the entire Lubuntu.
Last time I tried something like that, I installed the kubuntu-desktop package which came with a ton of software I didn't want. I couldn't even remove it easily, so I followed a tutorial which made me remove some of the software I had BEFORE messing with KDE. :|
So what I'm asking is simple - is there a standalone package that installs nothing but another desktop environment? I also want to be able to remove it with a simple apt-get remove.

Thank you.

---

### Post by varunendra on 2011-05-13
You need to install lxde metapackage from the repositories. Or, in the terminal:
```
sudo apt-get install lxde
```

Installing a metapackage installs a whole group of included packages. But their removal, I'm afraid, is not so easy. Removing a metapackage only removes that one package, and not the other ones it installed. You'll have to check the metapackage's properties to see which packages it installed/changed, then will have to remove/change them manually. An easier approach would be to keep a log of installed/removed/changed packages when it displays it right before applying the changes in Synaptic. Then you can use this log to revert the changes later if required.

But anyway, I don't think the removal is going to be as easy as "apt-get remove <a single package>". (of-course you can include the names of all the packages included in the log, making it 'one-step' but lengthy command!)

---

### Post by Spitted on 2011-05-14
Thank for the help. I checked the lxde metapackage and it includes some stuff that are irrelevant. For example, it includes leafpad which is a text editor. How is that an integral part of a desktop environment?
Is there a package that contains really bare lxde, xfce and kde desktop environments and absolutely nothing else? If not, how come?

---

### Post by varunendra on 2011-05-15
> **Spitted said:**
> Thank for the help. I checked the lxde metapackage and it includes some stuff that are irrelevant. For example, it includes leafpad which is a text editor. How is that an integral part of a desktop environment?
Is there a package that contains really bare lxde, xfce and kde desktop environments and absolutely nothing else? If not, how come?
Yes, specific applications are integral parts of specific desktop environments. As such, leafpad is not irrelevant, just a lightweight substitute to gedit. :)

I think you are confusing 'themes' or 'window managers' with desktop environments. This post should clear all your doubts (thanks to robin (dixiedancer)): [http://ubuntuforums.org/showpost.php?p=10653379&postcount=11](http://ubuntuforums.org/showpost.php?p=10653379&postcount=11)

Imp. quotes from the above post:
> .......
A [COLOR=SeaGreen]**desktop environment**[/COLOR] on the other hand *includes*  a window manager [COLOR=DarkRed]**but also includes stuff like panels, applets, and  applications that are designed to work best in that particular desktop  environment (that's called *integration*)**[/COLOR].
....
....
[COLOR=DarkRed]**_Each of the desktop environments has it's own set of applications  that work best in their "native" environment. That is called  "integration_."**[/COLOR] ....
....
.... Here's are some of the applications listed according to the  desktop environment they are native to:

_CD Burners_:
K3B - [COLOR=Navy]KDE[/COLOR]
Brasero - [COLOR=Sienna]Gnome[/COLOR]
Xfburn - [COLOR=Blue]Xfce[/COLOR]

_File managers_:
Konqueror - [COLOR=Navy]KDE[/COLOR]
Nautilus - [COLOR=Sienna]Gnome[/COLOR]
Thunar - [COLOR=Blue]Xfce[/COLOR]
PCManFM - [COLOR=DeepSkyBlue]LXDE[/COLOR]

_Music Players_:
Amarok - [COLOR=Navy]KDE[/COLOR]
Rhythmbox - [COLOR=Sienna]Gnome[/COLOR]
Exaile - [COLOR=Blue]Xfce[/COLOR]
LXMusic - [COLOR=DeepSkyBlue]LXDE[/COLOR]

A personal advice: read the full post of robin. It is a long one but very interesting and very-very informative.

As for the 'bare-bone' thing, I believe it's very simple: just install your favourite desktop environment, then strip out everything unwanted or unnecessary;
or,
just select the metapackage in synaptic - this will select the whole group - then manually deselect unwanted packages (making sure you don't break any dependencies).

Hope it serves what you desire. :)

---

### Post by Spitted on 2011-05-15
I get it now :P I have been confused between DE and WM. Your post and robin's cleared that up for me. Thanks a lot!

I think the next step for me, in order to understand exactly which part is responsible for what, is to install and configure manually a system like Arch. Ubuntu doesn't really force me to get to the bottom of things.

---

