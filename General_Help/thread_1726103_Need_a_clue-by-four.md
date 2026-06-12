---
title: "Need a clue-by-four"
date: 2011-04-10
forum: General Help
---

### Post by SeanTater on 2011-04-10
I setup a Multiterminal/multiseat X, using one of the Community Documentation pages as a general roadmap. I was shocked to find that it actually worked, but there were some problems, most of which I managed to overcome with tweaks here and there. (Info available, but I doubt it's relevant.) But there is one that's been plaguing me for weeks. I thought I finally fixed it a few minutes ago (yippee!), and it seems like I'm in the home stretch here, <facetious> but there's just one itty bitty little issue. </facetious>

The issue is, when I type, it shows up in a terminal too. (One of the Ctrl-Art-F*, /dev/tty* terminals, even if it's not showing) Of course, getty was on, and since the first thing I always do is log in, I log into the terminal too and start unwittingly typing commands. *It was a long time before I realized why everything I typed was executed twice.* So I moved all of the tty* files out of /etc/init and rebooted. **Poof!** No more duplicated commands! :D
Well that's only half of it. Everything I send is going to X.org's stdin too, from what I can see. The way I know is that the CTRL-* triggers, such as CTRL-C, send signals to X. CTRL-C and CTRL-Z are particularly annoying since I really find those useful in the graphical world, but they crash/freeze X instantly. :p

So the bottom line is:

**How on earth do I stop my input from going to all of these terminals? Why did they go there in the first place?**
or at least plan B:
**Can I get X to ignore SIGINT and SIGSTOP?**

---

