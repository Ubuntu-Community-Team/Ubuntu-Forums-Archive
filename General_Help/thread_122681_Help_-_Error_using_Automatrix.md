---
title: "Help - Error using Automatrix??"
date: 2006-01-28
forum: General Help
---

### Post by MJSOnline on 2006-01-28
Hi all.  

Ok when I ran automatrix to install frostwire it ran fine, installed no problem.  Then I went to Synaptic Package Manager to install Thunderbird email client.  Clicked on apply, installed, then came back with an error and this...

[B]W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
[/B]

Now what has happened and is it due to Automatix?  If it is due to Automatix, how do I get rid of the error and Automatrix?

Many thanks in advance. Matthew

---

### Post by GeneralZod on 2006-01-28
Those are more like warnings than errors, so Thunderbird should have installed correctly - can you verify that it is installed?

It looks like Automati*x* has added the mirrormax backports repositories to your sources.list, but that the mirror might be down.  Have you tried clicking "Reload" in Synaptic?

Edit:

Yep, that mirror's down - see [here](http://ubuntuforums.org/showthread.php?t=122548) for more details.

---

### Post by MJSOnline on 2006-01-28
Hi GeneralZod.  Thanks for getting back so quickly. 

I did a reload/refresh and got the following...

[B][http://ubuntu-backports.mirrormax.net/dists/breezy-extras/main/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/breezy-extras/restricted/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/breezy-extras/universe/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/breezy-extras/multiverse/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/multiverse/binary-i386/Packages.gz:) 404 Not Found[/B]

Thunderbird works fine.

Now is the **mirrormax.net** server down?  Does it go down a lot?  If its just a one off server fall over then it should work next time? If I want to install any other apps would the fault hinder that?

Thanks again. Matthew

---

### Post by GeneralZod on 2006-01-28
[QUOTE=MJSOnline]

Now is the **mirrormax.net** server down?  Does it go down a lot?  If its just a one off server fall over then it should work next time? If I want to install any other apps would the fault hinder that?

Thanks again. Matthew[/QUOTE]

I get the *impression* that it is now down for good, but have no way to substantiate that and am probably wrong :)

This particular error will only affect programs that you want to install from the [Backports](http://ubuntuforums.org/forumdisplay.php?f=47) project.

You can fix it by removing all lines containing an occurrence of "mirrormax" from your sources.list.  If you want to use Backports, then you can replace the "mirrormax" lines with these ones, taken from my own sources.list:

```

deb http://gb.archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse

```

In either case, remember to run

```

sudo apt-get update

```

afterwards (you'll need Synaptic to be closed during this whole procedure).

---

### Post by MJSOnline on 2006-01-28
Magic.  Thats great.  I am getting used to editing the soures list.  Thanks again. Matthew

---

