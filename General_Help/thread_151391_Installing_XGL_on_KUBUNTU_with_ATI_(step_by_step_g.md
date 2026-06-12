---
title: "Installing XGL on KUBUNTU with ATI (step by step guide)"
date: 2006-03-27
forum: General Help
---

### Post by duality on 2006-03-27
[COLOR="Red"]tutorial outdated, plz visit [http://compiz.ed3n.com/](http://compiz.ed3n.com/)[/COLOR]
 Or see other tutorials on this forum

---

### Post by duality on 2006-03-27
.

---

### Post by polaren on 2006-03-31
I followed the "how to" but it doesn't work! When i login i choose "Standardsession" but it loads gnome and not KDE with XGL. 

Ideas?

EDIT: I think i got i now, something had gone wrong with my xsession file and i created a new one! 

Thanks for the "How to" duality!

---

### Post by domino on 2006-04-01
I'm about to try this. For the sake of readability, please use the code tag instead the of the quote tags. You also might want to disable smiles just in case.

Thank for the this how to and polaren, please let us know how it's going with your install.

cheers!

Edit: Wouldn't it be easier if you already have Dapper Flight 6 on disk? I'm still pretty new at this, but can we make it read from the CD instead of doing a dist upgrade online (Step 8 )?

---

### Post by intrigue on 2006-04-04
thanks for the great guide!  I just installed dapper flight 5 and followed your guide to the T.  it installed beautifully.  My screen wiggles and rotates and everything, all very smoothly.

1. I've noticed a few annoying things however: When the default session loads now, it loads the KMix and Adept Notifier in TINY windows at the top left of the screen, instead of down by the clock. these windows cannot be closed.  
2.  After KDE has loaded, a dialog window shows up saying "The process for the system protocol died unexpectedly." and all i can do is hit OK.  

None of these would really bother me much, I understand its a dev build, 
3.  but I can't start Konquorer.  Thus I can't graphically browse anything on my system.

When i boot into the standard KDE setup everything works fine.

Is there some setting I could change to make it launch konquorer?  

Or would it be easier to install gnome? if so what kinda procedure am i looking at? I'm a linux n00b.

thanks for getting me this far anyway guys, this is farther than i was able to get in a week

---

### Post by Al3xanR0 on 2006-04-04
Simply ingenious!

---

### Post by lexxonnet on 2006-04-04
Has anyone got this working with an ATI 9600 Mobility?
I've tried this method from here: [http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)
 but it didn't work.

Besides, I've put in almost two whole days into trying to get zgl and compiz running, and the closest I got is getting xgl running, but compiz never did...

---

### Post by duality on 2006-04-05
[QUOTE=lexxonnet]Has anyone got this working with an ATI 9600 Mobility?
I've tried this method from here: [http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)
 but it didn't work.

Besides, I've put in almost two whole days into trying to get zgl and compiz running, and the closest I got is getting xgl running, but compiz never did...[/QUOTE]

You need to run compiz-gnome instead of compiz-kde, even if your using kde, because compiz-kde is not working atm.
Theres the description for this on my How To.

---

### Post by hater2win on 2006-04-08
> Preparing to replace xserver-xgl 7.0.0-0ubuntu3 (using .../xserver-xgl_7.0.0-0ubuntu5_i386.deb) ...
Unpacking replacement xserver-xgl ...
dpkg: error processing /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu5_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/Xserver.1x.gz', which is also in package xserver-xorg-core
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

That is the error I am getting, any ideas?

Also, standardsession doesn't show up for me at the login screen. Only KDE, failsafe, and default.

---

### Post by asdf25 on 2006-04-13
I just followed this guide, and it almost worked, I did get XGL running with the official Dapper packages. But when I upgraded to the packages from the [www.beerorkid.com](www.beerorkid.com) repository, it stopped working. Then I tried to get it to work for a while and gave up.

---

### Post by FlakJacket on 2006-04-13
I have a HP Pav ze5300 with an ATi Radeon IGP 340M.  Is this enough to run XGL? Also, what is compiz exactly?

Thanks,
Flak

---

### Post by uteck on 2006-04-15
Here are links to the main site for Compiz and xgl which explains everything very well.
[http://en.opensuse.org/Compiz](http://en.opensuse.org/Compiz)
[http://en.opensuse.org/Xgl](http://en.opensuse.org/Xgl)

---

### Post by meditans on 2006-04-21
[QUOTE=duality]
26:Type:     [COLOR="Red"]wget [http://metascape.afraid.org:13666/quinn.key.asc.gz](http://metascape.afraid.org:13666/quinn.key.asc.gz)[/COLOR]
27:Type:     [COLOR="Red"]zcat quinn.key.asc.gz | sudo apt-key add -[/COLOR]
[/QUOTE]I wanted just ask what can i do if when I try to do this
He answers he cannot found the page... (404 error)
I mean... can i found it elsewhere???
thanks...

Ciao
meditans

---

### Post by Gnuxprog on 2006-05-04
try this:
```

wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```

Further infos:

[http://www.beerorkid.com/compiz/]("http://www.beerorkid.com/compiz/")

:gnuxprog:

---

