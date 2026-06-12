---
title: "Slow Loading After Login"
date: 2011-01-06
forum: General Help
---

### Post by Jackson Tan on 2011-01-06
Hi all!

I am kinda having some emerging issue, but a brief search yields no solution (maybe I'm using the wrong keywords), so I hope someone can help me out here.

Usually, after logging into Ubuntu through the GUI, Ubuntu will start reading the hard disk, presumably to load certain configuration files. However, after several months, this process gets longer and longer. Now it may take up to two minutes before Ubuntu is done meddling with my hard disk. It's not as if the GUI is not responding; I can open up Terminal or Rhythmbox, but it takes comparatively longer than if the system is idling. In fact, it gets so bad that, if I were to run Firefox while this is occurring, Firefox will become greyed out (i.e. not responding) for a while.

This occurs both to my laptop and PC. However, it is user-specific, i.e. a fresh new user will not experience this problem. Similarly, if I were to do a fresh install (wiping out the user configuration files), the problem will go away. This of course suggests to me that it's some configuration files that clutter up the login process after repeated use. Given that I typically shut down my laptop/PC once I'm done using it (which means on average I'll login about three times a day), it may explain why it becomes a problem for me.

So is there anything I can do about it? I'd like to avoid a clean install as much as possible.

---

### Post by fabricator4 on 2011-01-06
> **Jackson Tan said:**
> However, after several months, this process gets longer and longer. Now it may take up to two minutes before Ubuntu is done meddling with my hard disk. 

You say a clean user account does not suffer from this problem so I agree that it is likely to be some kind of configuration problem.  Are you doing some hefty re-configuration of the GUI or installing lots of extra programs that might loading some components at login?

Maybe work with your clean user account for a while, and when you get to a point with it that starts to slow down, figure out what you installed or changed that may have caused it.

Maybe think about cleaning up your main user account - delete any unused programs and run Computer Janitor (under System-Administration) and see if that helps.

How much memory are you working with?  A machine with not much memory available is going to have a lot more trouble loading lots of components at login.

You could try working with a different GUI for a while and see if that helps.  Gnome is more resource hungry that others, but I've never personally found it a major issue.

Kind of reminds me of some of the Windows machines I used to see when I worked in the industry.  I was given the job of speeding them up but you had to turn them on and go have lunch while they did their thing.  There'd be widgets and applets all over the place, plus things like menu bars, update programs and stuff for IE that always got loaded at boot. ](*,)

Chris.

---

### Post by Jackson Tan on 2011-01-06
Hi Chris,

Thanks for the reply!

I don't change the GUI much... nothing more than changing background picture, changing Nautilus icon/list zoom, and a few shortcut icons at the top panel as well as the System Monitor. I doubt that'll create the issue I'm facing. So is memory, since I have > 2 GB for both laptop and PC.

Note that this is a progressive thing... it's kinda like the loading time creeps one second longer every few days.

Program settings could be a likelier cause, though I don't install that many other programs and I typically clean them up if they are untouched after some time. I initially thought Ubuntu One was the culprit, but then I remembered the problem existed on my PC before I had it. Is there a way to see which process is responsible for accessing the hard disk, much like how System Monitor can show which program is using the most CPU?

I used to have the problem of Nautilus taking incredibly long to load the list of files, especially pictures. It turns out to be a problem of an incredibly huge thumbnail cache, generated when I churned out large quantities of pictures to create animations. After deleting them, things went back to normal (I actually went further and disabled media preview). I wonder if I'm facing a similar problem here.

I certainly hope it's not because I shut down my systems all the time. That'd be ironic since I do so on the reason that Ubuntu boots up in a flash!

---

### Post by fabricator4 on 2011-01-06
> **Jackson Tan said:**
> Program settings could be a likelier cause, though I don't install that many other programs and I typically clean them up if they are untouched after some time. I initially thought Ubuntu One was the culprit, but then I remembered the problem existed on my PC before I had it. Is there a way to see which process is responsible for accessing the hard disk, much like how System Monitor can show which program is using the most CPU?

Not that I'm aware of, though I do use a program called GKrellm which is a system monitor that you can leave running all the time. I changed the update rate to less than 10 per second which makes it inconsequential for even my slowest machines.  It splits the CPU time between "system" and "user" so it give you a good feeling for what the machine is doing at any time.  It will also show disk activity for individual partitions so I can see which disk is  actually getting the pounding - it would work well if your ~/ was on a different partition.  Don't worry about loading another program, GKrellm is about as efficient and useful as you could hope for... nice programming and very configurable. It actually loads up before the Gnome desktop on this 900SD which is hardly the fastest machine on the planet.

If you could somehow get the Gnome system monitor up and displaying processes by CPU load you might be able to see if something is hammering the system.

> **Jackson Tan said:**
> After deleting them, things went back to normal (I actually went further and disabled media preview). I wonder if I'm facing a similar problem here.

It's possible, and it would fit in with the problem creeping over time - as you put more images on the system, generating and indexing the thumbnails would take longer and longer. Simply because you disable the preview, it may not stop the module from doing it's biz at startup.  The module would still be getting loaded and maybe even active in the background.  Maybe it's one of the programs/modules you should think about cleaning out.

I understand the problems of thumbnails, being a photographer.  I can easily load a few hundred images from a session and "DSCFXXXX" doesn't tell you much except the sequence that they were shot in.  Add to this the requirements of thumbnails from camera RAW files and it gets a bit silly under Gnome. That "other" OS used to drive me nuts with its thumbnail.db files, but the basic concept is not so stupid as it might seem.

> **Jackson Tan said:**
> I certainly hope it's not because I shut down my systems all the time. That'd be ironic since I do so on the reason that Ubuntu boots up in a flash!

Absolutely not.  My 900SD can get booted many times a day, partly because I have to disable wifi/3G through  BIOS when I want to switch but also because it's the way I use the machine - as a very mobile book reader/browser/move player etc. Even though it's so slow, I still get a desktop in about 30 seconds or so.

Chris

---

### Post by Jackson Tan on 2011-01-07
The system monitor icon that displays a time-update of the processor load shows that the process "IOWait" is hovering around 50%. So that narrows down the problem (and it's 50% because I'm running both systems in dual-core, so I reckon only one CPU is needed to do the job).

Googling this brings up several recommendations, though it seems to happen more to servers than PCs/laptops. I'll see if I can work out the problem from there.

Thanks a lot for your help! I really appreciate them!

---

### Post by fabricator4 on 2011-01-07
> **Jackson Tan said:**
> The system monitor icon that displays a time-update of the processor load shows that the process "IOWait" is hovering around 50%. So that narrows down the problem (and it's 50% because I'm running both systems in dual-core, so I reckon only one CPU is needed to do the job).


Oh, now that rings a bell.  A very loud one as a matter of fact.  I've seen the exact same thing when I first upgraded to 10.04: The CPU was flogging at 100%, 50% on the dual core Toshi laptop. In fact, it happened on all three machines I regularly run Ubuntu on.

Along with this I was also having trouble with Update Manager. The window that asks for the user password (to allow system updates) wasn't displaying while the CPU was running at 100%. Closing update manager seemed to make the CPU problem go away, but the Clock cycles weren't being eaten up by Update Manager according to the system monitor.  I do recall the IOWait doing something strange however, which is what reminded me.

The problem went away after I'd been forced to kill and restart update manager a few times, so I forgot all about it.

A similar thing happened with the keyring authentication module as well.  I'd click on the "authenticate" button and nothing at all would happen except the CPU meter would go through the roof.  Sometimes I didn't get the dialogue box at all, but IOWait would be eating CPU. This one was the most puzzling when the dialogue box didn't even show up, or sometimes it would never appear in front of whatever window I had open at the time, and I'd only discover it when I closed some windows. From memory, the problem went away when I'd rebooted and managed to click the authentication button as soon as the window popped up and I put the password in.

Since those first few niggles 10.04 has been rock solid and I've seen nothing like it since.  It's possible there were some updates that fixed these problems (when I managed to get updater to run) but I offer this long winded story in the hope that it might give some clue as to what's happening on your machine.

Chris.

---

### Post by Jackson Tan on 2011-01-08
I've installed iotop, which is a command line system monitor type of program that monitors I/O. The culprit, not quite unexpectedly, was the Ubuntu One sync-daemon. Which means that the post-login slowness I experienced on my PC before it had Ubuntu One may be a separate affair.

I think I'll start haunting the Ubuntu One subforum to see if I can find a way around this.

Thanks for all the responses and suggestions!

---

### Post by claudios on 2011-01-21
I had the same problem.
Ubuntu used to start like a two years old windows xp installation hahaha
I had to wait a few minutes before being able to use the system because of the huge hard drive activity. 
I was not able to solve the problem and after a few months I decided to switch off ubuntuone and use just dropbox.
Powertop said "The program 'ubuntuone-syncd is writing to file 'ENCRYPTFS_FNEK_ENCRYPTED........' on /dev/sda5

---

