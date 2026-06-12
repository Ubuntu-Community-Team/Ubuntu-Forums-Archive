---
title: "What did you do to trim your system?"
date: 2006-02-17
forum: General Help
---

### Post by DonQuixote on 2006-02-17
I like to run a system without a lot of unneeded, and unused programs and processes.  However, being new to Linux, I have no idea what is needed, nor how to remove it if I knew it was not needed! :)

I'd like to know how you (the reader) have decreased boot time, response time, and basically fine tuned your system.

Thanks!

---

### Post by Lord Illidan on 2006-02-17
You might want to install xfce for a start..

Enable all the repos...
then

```
sudo apt-get install xubuntu-desktop
```

---

### Post by DonQuixote on 2006-02-17
What IS xfce?

---

### Post by gingermark on 2006-02-17
[QUOTE=DonQuixote]What IS xfce?[/QUOTE]

Short answer: Stripped down version of gnome.

It's another Desktop Environment, it has it's own utilities to set things up, it's own text editor, and sort of it's own file manager (it uses ROX).

I'm not a fan myself, but a lot of folks like it.

Have a look at [http://www.xfce.org/](http://www.xfce.org/) for a sense of it. And xubuntu-desktop is a meta package for a full desktop experience.

As far as KDE goes, there are some tips for optimising performance [here](http://wiki.kde.org/tiki-index.php?page=Performance%20Tips).

---

### Post by Lord Illidan on 2006-02-17
XFCE is a lightweight window manager like Gnome and KDE..It doesn't have all the eye candy, but it is more speedy.

For more info about gnome, kde, xfce, enlightenment (all window managers), look at [www.wikipedia.org](www.wikipedia.org)

I recommend you learn more about Linux before trying to optimise your system with things like initng, removing startup scripts and the like. This forum is a good start as any.

Have you read the documentation : [UserDocumentation - Ubuntu Wiki]("https://wiki.ubuntu.com/UserDocumentation")

---

### Post by aysiu on 2006-02-17
If you like KDE, try this: ```
sudo apt-get update
sudo apt-get install kpersonalizer
kpersonalizer
``` Then walk through the "wizard." When you get to the "Eye candy-O-Meter," select "fewer effects." See screenshot for more details.

---

### Post by Adrian on 2006-02-17
Here is a wiki page about KDE optimization:
[http://wiki.kde.org/tiki-index.php?page=Performance%20Tips](http://wiki.kde.org/tiki-index.php?page=Performance%20Tips)

---

### Post by ekarni on 2006-02-17
Yeah, I did some cleaning along those lines.  (However, unlike in Windows, having the extra stuff floating around isn't going to affect boot times - there's no registry here to get bloated!  I just did it because I like my computer tidy...)

Anyway, step one was spending 45 minutes looking at the installed packages (there's a filter for it in Synaptic) and unmarking everything that I knew I wouldn't be using.  Step two:  grab *deborphan* or *gtkorphan* (graphical) and run it.  This will show packages that were installed to satisfy dependencies that no longer exist.  I get some packages showing that I think I still need (i.e. codecs), but so far I've removed some stuff that showed up there without sideffects.  

Last thing, if you're running the "386" kernel on reasonably modern hardware you can try switching to the "686" version.  I haven't gotten around to doing this, but it's on my list.

---

### Post by dbw on 2006-02-23
ekarni - that is a great suggestion, I just ran through it muyself.  Additionally, i3dmaster wrote a pretty great [howto]("http://ubuntuforums.org/showthread.php?t=89491&referrerid=48700") about removing unneeded services at boot time.  If you want to get serious,  you could try to recompile your kernel, eliminating unneeded services.  I didn't notice a big difference here, but it is fun, and gets you into the real guts of your software.  It also will not damage your system in any way, as long as you do not foolishly uninstall your old kernel.    tseliot wrote a pithy and excellent [howto]("http://ubuntuforums.org/showthread.php?t=85064&referrerid=48700") on the subject.

---

