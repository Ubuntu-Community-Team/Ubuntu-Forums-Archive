---
title: "so I want to try KDE but I have some questions"
date: 2006-03-20
forum: General Help
---

### Post by weasel fierce on 2006-03-20
I think Im ready to jump into trying out KDE and kubuntu, but I have some questions first.


If I figure I dont like it, can it be easily removed through synaptic / apt-get ?

Can KDE app's run under Gnome and vice versa ?
Principally Epiphany, GAIM, openoffice, abi-word and XMMS (though Im going to try out Amarok ,since I've heard a lot of good things about it)

Are there any potential complications I should be aware of ? (using Breezy here, without any real modifications, I think)

To install it, do I simply pick the Kubuntu-desktop package ? It seems to be the "default package deal" and thats pretty much what Im after. A decent selection of good KDE app's and whatnot.

EDIT: Will I be able to use Synaptic, while in KDE or is it different ?



Thanks in advance guys!

---

### Post by Sutekh on 2006-03-20
[QUOTE=weasel fierce]I think Im ready to jump into trying out KDE and kubuntu, but I have some questions first.


If I figure I dont like it, can it be easily removed through synaptic / apt-get ?
[/QUOTE]Yes you can, using these threads

If you want to keep the kubuntu-desktop and remove the ubuntu-desktop

[Ubuntu Forums - HOWTO Completely remove the ubuntu-desktop meta-package]("http://www.ubuntuforums.org/showthread.php?t=96046")

If you want to remove the kubuntu-desktop and keep the ubuntu-desktop

[Ubuntu Forums - HOWTO Completely remove the kubuntu-desktop meta-package]("http://www.ubuntuforums.org/showthread.php?t=96048")

[QUOTE=weasel fierce]
Can KDE app's run under Gnome and vice versa ?
Principally Epiphany, GAIM, openoffice, abi-word and XMMS (though Im going to try out Amarok ,since I've heard a lot of good things about it)
[/QUOTE]To start there isn't no such thing as a GNOME/KDE app.  So you can run applications in either desktop environment.  (You don't need GNOME or KDE at all to run applications if you wish)

There are applications that make use of particular libraries and theme engines, which comes with KDE, which may lead people to think that they are KDE applications.  KDE doesn't need to be installed to run these apps, just the relevant libraries.

[QUOTE=weasel fierce]
Are there any potential complications I should be aware of ? (using Breezy here, without any real modifications, I think)
[/QUOTE]Well there should be none.  In my experience I create a new user that I use for using KDE.  

[QUOTE=weasel fierce]
To install it, do I simply pick the Kubuntu-desktop package ? It seems to be the "default package deal" and thats pretty much what Im after. A decent selection of good KDE app's and whatnot.

EDIT: Will I be able to use Synaptic, while in KDE or is it different ?[/QUOTE]Yes, all your applications will be available in either desktop environment.  Synaptic will be there in KDE for you to use.

---

### Post by Barrakketh on 2006-03-20
> **weasel fierce]If I figure I dont like it, can it be easily removed through synaptic / apt-get ?[/quote]
Not really.  kubuntu-desktop is like ubuntu-desktop: nothing more than a meta-package.  It defines a bunch of dependencies that form the base desktop (just as if you had installed Kubuntu to begin with) and installs them.  Uninstalling kubuntu-desktop will only remove that package and nothing it depends on.  The same is true for ubuntu-desktop.

That said, if you really want to remove it later you can, or you can just leave it installed.  The previous poster posts two threads about how to remove them, but that doesn't take in to consideration whether you had any of those packages installed prior to installing (k)ubuntu-desktop.

> Can KDE app's run under Gnome and vice versa ?
Principally Epiphany, GAIM, openoffice, abi-word and XMMS (though Im going to try out Amarok ,since I've heard a lot of good things about it)
Yes.  You don't require the full blown desktop for any KDE or GNOME applications said:**
> Are there any potential complications I should be aware of ? (using Breezy here, without any real modifications, I think)
There is a possibility that some applications will associate themselves with certain filetypes, but it shouldn't be a problem.  It's an easily fixed problem if it does happen, and uninstalling the offending application (in case you *really* hate it) will also fix it.  

I have both KDE and GNOME installed side by side in case anyone else that I let use my computer wants to use GNOME, and I haven't had any problems.  The only thing you might notice is that your KMenu might need tidied up a bit.  Some things like gnome-games I remove from the menu because I don't play games :P

> To install it, do I simply pick the Kubuntu-desktop package ? It seems to be the "default package deal" and thats pretty much what Im after. A decent selection of good KDE app's and whatnot.
Yes.  Kaffeine is much better than Totem IMO, but it's worth installing the kaffeine-xine package instead of using gstreamer.  Obviously, nothing is 

> EDIT: Will I be able to use Synaptic, while in KDE or is it different ?
You can use Synaptic if you want, but you can also use the package manager that Kubuntu ships with called Adept.  A lot of people seem to have a preference for Synaptic once they get used to it, so you can stick with it if you choose.

---

### Post by weasel fierce on 2006-03-20
You guys are awesome !

Thanks!

---

### Post by Adrian on 2006-03-21
[QUOTE=weasel fierce]
If I figure I dont like it, can it be easily removed through synaptic / apt-get ?
[/QUOTE]

If you use **aptitude** instead of **apt-get** you will be able to remove it easily.

To install:
```

sudo aptitude install kubuntu-desktop

```

To remove:
```

sudo aptitude remove kubuntu-desktop

```

---

### Post by Randomskk on 2006-03-21
When you start using KDE, consider trying Kopete instead of gAIM, and indeed amaroK instead of xmms - they are the KDE programs for IM/music, and I've found them to feel more polished and go more with the rest of KDE than gAIM and xmms :D

---

