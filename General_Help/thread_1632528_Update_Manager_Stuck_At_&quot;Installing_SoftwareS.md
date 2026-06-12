---
title: "Update Manager Stuck At &quot;Installing Software/Setting up grub-pc&quot;"
date: 2010-11-28
forum: General Help
---

### Post by -kg- on 2010-11-28
It's been a long, long time since I've had any major problem with Ubuntu.  This problem has occurred on my desktop.  I'll give as much information as I know to give.

I did updates to my desktop tonight.  It downloaded all the software and started installing, then got to "Setting up grub-pc" and has been stuck there for an hour or two.  The operation before that was "Setting up grub common" which I assume successfully completed.

I have shut all processes down that were running (that I knew to shut down, like BOINC) and still no joy.  System monitor shows nothing happening (except for System monitor, of course).  It shows everything else sleeping, yet I'm showing between 94% and 99% CPU usage and 818.4 MiB (out of 999.5 MiB) of RAM usage.  It even shows update manager and update notifier sleeping.  Not only that, but I'm showing that I'm using 23.2% of swap, too.  I've never seen this machine use swap before.  I've never seen any of my machines use swap.

I've also noticed a few strange things running in the processes.  I notice that I have 4 instances of Python running and 2 instances of gksu.  And oh joy of joys...I just found out that I can't mount any other partitions!  I can't back anything up before shutting down. [IMG]http://brainformation.com/~cp11440/neo/images/smilies/eusa_doh.gif[/IMG] ](*,)

My desktop is home built, with an ASUS MB, AMD Athlon 64 3200+ processor, 1 GB RAM, 3 hard drives...2 IDEs, the first (and boot) of which is 400 GB, the other 160 GB...and a 1 TB SATA drive.  I have two OSes...Ubuntu and Ubuntu Studio (Ubuntu "owning" the bootloader).  As an experiment, I tried running "sudo update-grub", but it wouldn't run.

I fear I'm stuck as far as installing any tools for troubleshooting.  Naturally, Synaptic won't run, since Synaptic is already running as a result of the Update Manager.  I do have access to Software Center, but don't know whether I'd be able to install anything.  I'm stuck with what I already have.

I'm going to let it run the rest of the night and see if it might correct itself, but I'm not too hopeful at this point.  If I can't get it to finish normally, I'll have to force it closed and hope for the best.  At any rate, the computer is still usable at this point, and before I do anything rash, I'll have saved what I can save before shutting it down (if I can! [IMG]http://brainformation.com/~cp11440/neo/images/smilies/eusa_pray.gif[/IMG] ).

If worse comes to worst, I'll have all my files saved elsewhere, and I'll just reinstall, though I'd rather not.  I have quite a bit invested in this installation that I can't replace, including a whole slew of Rosetta@Home work units which I doubt I can "save and reintroduce."  Not a big thing, but......

One bad thing...my nephew was using this computer for a couple of days.  He thinks he knows way more than I think he knows (he's 17), and ***Lord knows*** what he might have been up to!  He pressed a key on my keyboard that I've never used that required me to give my password to wake the computer up....not to worry, though...he'll ***never*** get my passwords! :P

Anyone have any ideas?  I'm (once again) at my wit's end.

---

### Post by sikander3786 on 2010-11-28
It might be asking about the Grub files to keep the previous one's or generate a new one. And that dialogue box might be hidden behind the update manager or something.... Well it is just a thought.

You won't be able to use Software Center or apt-get until update-manager is closed. They can't be run simultaneously.

But hopefully we'll be able to solve the problem for you. That happens and can be fixed. Believe me ;-)

What is the current position? Can you post a screenshot somehow?

---

### Post by -kg- on 2010-11-28
Oh, you bet I can, and thank you for the reply!  I'm used to being in your shoes, offering the help.

First, I took your suggestion.  I normally run Update Manager maximized, and never thought to look behind the window for a dialogue box.  No dialogue box, though.  It's not on another desktop, either...I have only one desktop.

Still the same status.  It's still stuck on "Setting up pc-grub," as shown by the screenshot below:

If you want the entire screen, it is the second screenshot:

I've moved both around, and there's no dialogue hidden behind them.  That's all I've got.  Need any more information?

---

### Post by -kg- on 2010-11-28
I'll give you fair warning...I'm going to hit the sack before too long.  It's 5:00 in the morning here, and I've been up all night with this.

I do appreciate any ideas you might have, though!  Thanks!

---

### Post by sikander3786 on 2010-11-28
I will not advise you to do anything silly here. If it is still stuck you can do whatever you prefer to. Quit the update-manger or reboot or whatever. But don't follow my advice ;-)

Thats upto you whatever you do.

However I would recommend to just quit the update-manger and then do a few commands like

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get upgrade
```

But don't blame me that I was the one involved in messing up your system :P

Hope you understand my situation.

---

### Post by -kg- on 2010-11-28
Oh, I absolutely understand your situation, and there will be no blame (except maybe for my nephew! [IMG]http://brainformation.com/~cp11440/neo/images/smilies/icon_lol.gif[/IMG] ).  As I said before, I'm more used to giving help than asking for it, and I completely understand the risks.

Thank you for your suggestions.  I hadn't (yet) thought along those routes, and they will give me another set of options to try before the ultimate solution...nuking the installation and starting over.  I've even thought of the option of saving my files using a Live CD, so that's no problem.  I was just frustrated last night and wasn't thinking completely clearly.

The first thing I'm going to do is stop the Updater (if it's still running...I'm on my laptop presently) and run your suggestions.  If that doesn't do it (and if Ubuntu is still running right), I'll start BOINC back up, set it to not accept new tasks, and run the tasks I have out before going any further.  Then I'll attack it with my "sledge hammer" (joke) and try my more risky maneuvers in an attempt to save it.

Anyway, I've got to get to it.  I've been having other problems lately, like all of the various Windows computers not being able to access the Internet via DSL...only Ubuntu can get through. [IMG]http://brainformation.com/~cp11440/neo/images/smilies/eusa_doh.gif[/IMG]

Meanwhile, if anyone else has other suggestions?

---

### Post by -kg- on 2010-11-28
Well sikander, I now certainly thank you for the suggestions.

I was able to shut down Update Manager, but unable to shut down the terminal window installing the packages (the window on the right in my screen shot).  To accomplish this, I logged out and logged back in, figuring that Ubuntu would be unlikely to require GRUB to accomplish it.

I then opened a terminal window and attempted to run the first of your commands, which prompted me with "you must run sudo dpkg --configure -a" so I figured I was in.  But when I ran that, it would not run, saying that "/var/lib/dpkg/lock" was open and asking if something might be using it.  I checked all the running processes under System Monitor, but could find nothing that was even accessing "/var", let alone down into the dpkg subdirectory.

So I deleted the lock file and pulled the terminal up again.  I ran the dpkg command again and this time it worked, but still froze up and wouldn't complete.  I played around with it and finally gave up.  I rebooted and booted into an Ubuntu Live USB I have (using PlOP boot manager on a floppy drive...my desktop won't boot into a USB drive)unaided).  I copied my entire /home directory over to storage, then attempted to boot into Ubuntu again via GRUB on the hard drive.

I didn't expect it to work, but it did!  I booted into Ubuntu, pulled up the terminal, found that it still required a "dpkg --configure" and this time it worked perfectly.  It finished installing the updates and, upon pulling up Update Manager and doing a refresh, found that all updates have been successfully installed.

:guitar:

I want to thank you again, my friend, for your suggestions, which ended up pulling my bacon out!  All I need to do now is reboot and finish the update (one of which was a newer kernel) and I can mark this thread as SOLVED!

[IMG]http://brainformation.com/~cp11440/neo/images/smilies/oldSite/coolthumb.gif[/IMG]

---

### Post by -kg- on 2010-11-28
Total success.  This ticket is now solved.

Thanks one more time, my friend!

---

### Post by sikander3786 on 2010-11-28
You are more than Welcome :-)

Glad to know that update-manager didn't bork your install :-)

Happy Ubuntu-ing!

---

### Post by mista2 on 2011-02-21
> **sikander3786 said:**
> You are more than Welcome :-)

Glad to know that update-manager didn't bork your install :-)

Happy Ubuntu-ing!

I have just had this problem happen at a client - except they rebooted before I could have a look, their system is borked now. It will boot, but services wont auto start (Bind9, Apache2, MySQL), and no response from the GDM - mouse wont move, keyboard wont work. I can SSH to the server and start other services manually, but the Gnome GUI is broken. GDM appears frozen after a restart.
Installation is a 10.4 system running in VMWare ESXi4.1, previously fully updated in January 2011. Updates this month seem to be causing a problem.

From what the user told me, the were seeing the update manager, the information saying grub-pc updating, but no other dialog. I Just ran the same update on another 10.4 system built at the same time, and got the same issue, only I was able to see a dialog to skip the grub-pc update and I was able to proceed OK.

---

