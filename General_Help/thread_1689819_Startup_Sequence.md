---
title: "Startup Sequence"
date: 2011-02-17
forum: General Help
---

### Post by Chris Riley on 2011-02-17
I run Hardy 8.04 64 bit on an AMD desktop. Recently my installation has become 'quirky'. At startup the list of instructions and files scroll down the screen, I would rather it went straight to log-in screen as it used to do; when I request close-down, it takes several minutes for the graphic to appear to allow the selection of options.
From Gutsy, I remember a config file that can be edited to turn on/off the scrolling info at start-up, but don't know where to find it (I have startup manager loaded, but that has no effect).
I do not know why the screen hangs at close-down.
I would appreciate help.

---

### Post by quixote on 2011-02-18
If there's a problem or warning during boot up, it'll display all the text even if you've told it not to.  That's telling you there's a problem (I know, not hugely helpful because it goes by too fast to read), and the fact that it hangs a bit on shutdown is probably due to the same thing.  Whatever the quirky process(es) are, the system has to time out before it'll close them.

The options for no text on boot up is in /boot/grub/menu.lst.  It's the line that usually says "quiet splash" among other things.  The "quiet" bit means "no text".  I think you'll find it's still there.  It's being overridden because there's a problem.

As to how to fix the problem, that's another whole can of worms.  Somebody who knows more about it than I do should be able to give you some diagnostic commands you could run.  Did the problem appear after an upgrade?  After you installed some new software?  Anything else that might give a hint?

---

### Post by Chris Riley on 2011-02-20
Thanks for your response, Quixote. If I upgrade (online) to the next version of Ubuntu, will that sort any underlying problem simply by replacing the operating system? Or will the problem remain as the upgrade recovers all my personal settings?

As far as the when, I believe it was following an upgrade to Hardy.

---

### Post by quixote on 2011-02-20
Hard to say (for me) whether an upgrade would fix things or not.  Depends on whether the problem is in system files or somewhere in your /home settings.  The latter, as you say, would be carried over.

Just as a general attempt, you could tell it to fix broken packages and see if that helps. (Probably won't do a thing.) ```
sudo dpkg --configure -a
```

There's a log file called dmesg which retains all that bootup verbiage.  That would tell you where the problem was, if I knew enough about it to tell you what to look for, however ... :(.  I'll hunt around and see if I can find some general pointers as to diagnostics for this situation.

---

### Post by Chris Riley on 2011-02-24
[SOLVED]. I've upgraded to 10.04 LTS. The upgrade has cured the startup problem, and thanks for the advice.
The only reason I've stuck with Hardy for so long is because it is LTS; now I find that Lucid is also LTS.
Unfortunately I now get very jumpy graphics. This, I presume, is because there is no fglrx drivers for ATI graphics? I'll dig around, see if there's any way to tweak this.

---

### Post by quixote on 2011-02-24
Good to hear that installing 10.04 helped!  That's a really nice version.  I'd stick with it.  Even though Maverick (10.10) is very good, 11.04 (Natty) looks like a complete mess to me, and the problem with the non-LTS is you can't skip any of the versions.

ATI graphics can be a real bear.  I had a real fight with one of my older laptops before I could get it to work at all.  I believe, at this point, that if you get the right drivers, the problem is actually solved.  Search the forums for your computer model, ATI, and drivers.  I know I've seen this answered before.

---

