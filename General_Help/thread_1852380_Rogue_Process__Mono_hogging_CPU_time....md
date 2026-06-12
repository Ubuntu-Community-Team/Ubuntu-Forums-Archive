---
title: "Rogue Process?  Mono hogging CPU time..."
date: 2011-09-30
forum: General Help
---

### Post by svtguy88 on 2011-09-30
I'm not sure where to post this, but I wanted to see what everyone thinks.  Long story short, I ran "top" and noticed a command called "mono" hogging lots of CPU time.  It was the top process, taking up over 100%.

I did a little googling, but I'm kind of at a loss.  It seems to be a compiler, of sorts?  I haven't installed much in the form of a dev environment on this machine, and certainly nothing .NET/Microsoft related (as some of the mono stuff seems to be for).  

I killall'ed it and it didn't come back yet.

What is mono, why do I have it, and why was it hogging CPU time?

---

### Post by yetiman64 on 2011-09-30
Do you run or have you run Banshee? It is a mono app, there are more than just Banshee but that is the first to come to mind. 

Others here will be able to explain this more in depth than myself, what I mainly know is there are a group of applications that come under the banner of "Mono Apps" that are used in Ubuntu.

---

### Post by An Sanct on 2011-09-30
mono is the Linux port of .net, so actually it is a framework.

[http://en.wikipedia.org/wiki/Mono_%28software%29](http://en.wikipedia.org/wiki/Mono_%28software%29)

---

### Post by directhex on 2011-09-30
> **pkmgarf said:**
> I'm not sure where to post this, but I wanted to see what everyone thinks.  Long story short, I ran "top" and noticed a command called "mono" hogging lots of CPU time.  It was the top process, taking up over 100%.

I did a little googling, but I'm kind of at a loss.  It seems to be a compiler, of sorts?  I haven't installed much in the form of a dev environment on this machine, and certainly nothing .NET/Microsoft related (as some of the mono stuff seems to be for).  

I killall'ed it and it didn't come back yet.

What is mono, why do I have it, and why was it hogging CPU time?

Mono is installed by default, because three default apps use it:

[LIST]
[*]Banshee
[*]Tomboy
[*]gBrainy
[/LIST]

If you're running any of those apps (especially Banshee, which is the only one of the three that ever does CPU-intensive background tasks) then that would explain it.

You might get a better answer with more detail - i.e. what exactly does "ps -ef | grep mono" return?

---

### Post by svtguy88 on 2011-09-30
Thanks for the replies.  It was Banshee.  I had tried to open a file with it, and then closed it, but mono must have stayed open in the background.

---

### Post by seawolf167 on 2011-09-30
It looks like you've got this solved - but I'll add that you may like *htop* better than *top*, and when you use it you can turn on displaying of the process trees to see what belongs to what.

```
sudo apt-get htop
```

---

### Post by An Sanct on 2011-09-30
> **seawolf167 said:**
> It looks like you've got this solved - but I'll add that you may like *htop* better than *top*, and when you use it you can turn on displaying of the process trees to see what belongs to what.

```
sudo apt-get htop
```

Can htop or top be bound to a GUI like form, like SuperKaramba or something? so that one can see "the bad boys" on desktop at any time without having to go to terminal?

PS. I will research htop tomorrow...

---

### Post by seawolf167 on 2011-09-30
Sure - you can use something like [Conky]("http://conky.sourceforge.net/"). I personally don't like manually setting it up though so I use [ConkyColors]("http://gnome-look.org/content/show.php/CONKY-colors?content=92328").

[Conky Wiki]("http://www.wikihow.com/Configure-Conky").
[Conky UbuntuForums Post]("http://ubuntuforums.org/showthread.php?p=6365702").

---

