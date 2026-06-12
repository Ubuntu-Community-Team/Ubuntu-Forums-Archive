---
title: "Back to &quot;Defaults&quot;"
date: 2009-11-12
forum: General Help
---

### Post by AeroCross on 2009-11-12
Well, hello there, happy users.

I was just wondering if any of you knew how to restore your packages to default in a 9.10 installation. After installing a load of stuff on my laptop, I haven't been able to keep track of everything I've installed (especially metapackages, they make your life wonderful and hell).

For instance, I've installed the php5 metapackage, but when I want to unninstall it, it doesn't uninstall everything it installed. Same for apache, and their libs, etc.

I don't think sudo apt-get autoremove --purge does the trick, when unistalling metapackages..

So, I was wondering if I could do some radical stuff like setting the packages the their defaults, like only installing the packages that come with the installation.

Any ideas?

---

### Post by philinux on 2009-11-12
Look up the deborphan package on google and it's in the repo. Use it carefully.

Not sure if the computer janitor could help, worth a try too.

mind you the file sizes involved are likely to be small.

---

### Post by Andreas1 on 2009-11-12
[this]("http://ubuntuforums.org/showthread.php?t=947865") thread might be interesting for you, albeit the unsatisfactory conclusion being that there is no 100% solution. deborphan does treat "soft" dependencies differently than apt-get for example. somewhere there is still information missing.

---

### Post by AeroCross on 2009-11-12
Well, Computer Janitor didn't do squad, but I really didn't raise my hopes with it.

The deborphan package looks kinda interesting, but I don't think it'll do the work.
The other thread seems like it'll do more harm than good.

I just don't know why apt-get autoremove doesn't do the job. The --purge command also fails a lot of times.

---

### Post by Andreas1 on 2009-11-12
> **AeroCross said:**
> Well, Computer Janitor didn't do squad, but I really didn't raise my hopes with it.

The deborphan package looks kinda interesting, but I don't think it'll do the work.
The other thread seems like it'll do more harm than good.

I just don't know why apt-get autoremove doesn't do the job. The --purge command also fails a lot of times.

i think i can explain that:

```
packageA
  depends on packageB
  recommends packageC

apt-get install packageA
  installs packageA, packageB, packageC

apt-get remove packageA
  removes packageA

apt-get autoremove
  removes packageB

--> packageC remains

```

also: did you try deborphan *-an*? (i don't really remember how it worked but i remember having toyed around with those options)
EDIT: CAREFUL, i just tried it out again and among the packages in the list were core system components, i guess that was not it, sorry :-(

---

### Post by AeroCross on 2009-11-12
> **Andreas1 said:**
> i think i can explain that:

```
packageA
  depends on packageB
  recommends packageC

apt-get install packageA
  installs packageA, packageB, packageC

apt-get remove packageA
  removes packageA

apt-get autoremove
  removes packageB

--> packageC remains

```

also: did you try deborphan *-an*? (i don't really remember how it worked but i remember having toyed around with those options)

Great explanation - I'd keep that in mind when installing packages.
I haven't tried deborphan, I'll try it later. Gotta document myself a lil' first. Any reccomendation when trying? It check packages installed BEFORE installing deborphan?

---

### Post by Andreas1 on 2009-11-12
> **AeroCross said:**
> It check packages installed BEFORE installing deborphan?

I'm not sure what you mean but i think the answer is no.

---

### Post by AeroCross on 2009-11-12
What I meant was:

Does deborphan works with previously installed packages? Or with packages installed after deborphan was installed?

I'm not sure If I'm making myself clear. But oh well, I'm gonna try later - thank you all for your help =)

---

### Post by kio_http on 2009-11-12
```
sudo apt-get purge package 
```

then

```
sudo apt-get install package
```

or you can delete the config files in your homefolder

e.g

```
rm -rf /home/youruser/.firefox
```

[COLOR="Red"]Caution:[/COLOR]Take care with rm -rf you could loose data if not handled properly see [this]("http://ubuntuforums.org/showthread.php?t=1301269") and [this]("http://ubuntuforums.org/showthread.php?t=332453")

---

### Post by Andreas1 on 2009-11-12
> **AeroCross said:**
> What I meant was:

Does deborphan works with previously installed packages? Or with packages installed after deborphan was installed?

I'm not sure If I'm making myself clear. But oh well, I'm gonna try later - thank you all for your help =)

i think the former. any other way would imply deborphan monitoring apt, which i can hardly imagine.

---

### Post by winotree on 2009-11-12
I'm thinking this will help -- at least it let's you know what's there as default.  How you get it back to that state should be a matter of deleting or restoring packages, don't you think?  Good luck with this!!  :D

[http://cdimage.ubuntulinux.org/daily-live/current/karmic-desktop-i386.manifest](http://cdimage.ubuntulinux.org/daily-live/current/karmic-desktop-i386.manifest)

---

