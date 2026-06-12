---
title: "unnecessary updates and apps?"
date: 2006-06-15
forum: General Help
---

### Post by jamesrw on 2006-06-15
I am running Gnome in 6.06, software update is telling me to update KDE applications which I don't even use. WHY ARE KDE apps installed on my Gnome environment? How can I make sure to remove any unnessary KDE apps wasting my precious HD space? Is it okay to remove all KDE apps if there are any installed?? (search KDE, or K, in synaptic and remove apps)??

---

### Post by aysiu on 2006-06-15
If KDE applications are installed, you probably installed them.

If you want to get rid of KDE, try this:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by eqisow on 2006-06-15
As the aysiu said, if you are running any KDE apps such as amaroK, k3B, etc. then that is why you have kde packages installed. These programs rely on them.

---

### Post by eth on 2006-06-15
[QUOTE=eqisow]As the aysiu said, if you are running any KDE apps such as amaroK, k3B, etc. then that is why you have kde packages installed. These programs rely on them.[/QUOTE]

so be extremely careful before making anything really silly ;)

---

### Post by gamma on 2006-06-15
Why not try banshee? Or if you like the amaroK interface (shudder) there's a Gnome equivilent out there. I forgot the name though, but I'm sure someone has heard of it.

---

### Post by Ramses de Norre on 2006-06-15
I think you mean Listen ;)

---

### Post by elamericano on 2006-06-15
Hang on a second. It wants to add kcontrol and kicker, both of which would be useless without the kde desktop. Stupid dependencies if you ask me. I was expecting kde library updates only.

Then there's linux-386, linux-image-386. Hmmm, do I want rebuild everything that I compiled by hand? No. Not today.

Is there an easy way to make updates ignore certain packages... forever?

---

### Post by bruce89 on 2006-06-15
[QUOTE=elamericano]
Is there an easy way to make updates ignore certain packages... forever?[/QUOTE]
Use Synaptic's Force Version and Lock Version, both in the Package menu.
[QUOTE=gamma]Or if you like the amaroK interface (shudder) there's a Gnome equivilent out there. I forgot the name though, but I'm sure someone has heard of it.[/QUOTE]
[Exaile]("http://www.ubuntuforums.org/showthread.php?t=159879")

---

### Post by aysiu on 2006-06-15
[QUOTE=elamericano]
Is there an easy way to make updates ignore certain packages... forever?[/QUOTE] Yes, uninstall the offending packages.

---

### Post by elamericano on 2006-06-15
Will do ;-)

Is there a way do uninstall the updater? What's that package called?

---

### Post by aysiu on 2006-06-15
```
sudo aptitude remove update-notifier
```

---

### Post by elamericano on 2006-06-15
Thanks aysiu,

It's true, There's no way to make update-notifier shut up:

[https://launchpad.net/distros/ubuntu/+source/update-notifier/+bug/14728](https://launchpad.net/distros/ubuntu/+source/update-notifier/+bug/14728)

---

### Post by FredB on 2006-06-15
Well, and what will you do if there is any big security update ?

And I am using only one KDE based software... K3B ;)

---

### Post by elamericano on 2006-06-15
[QUOTE=FredB]Well, and what will you do if there is any big security update?

And I am using only one KDE based software... K3B ;)[/QUOTE]
Yeah, I was just kidding, but it did help to know the package name. And my one kde package...

kpatience! :-)

I intend to install more (kvpnc was a nice vpn client, for example), but that's all I have now, which made it a little annoying to get 5 updates. It would indeed be nice to hide updates you know you don't want until the next time they are updated.

---

