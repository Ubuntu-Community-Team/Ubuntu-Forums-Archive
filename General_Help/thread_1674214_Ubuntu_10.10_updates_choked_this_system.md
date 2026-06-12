---
title: "Ubuntu 10.10 updates choked this system"
date: 2011-01-23
forum: General Help
---

### Post by quadproc on 2011-01-23
I am looking for ideas or an explanation of what happened to this system during an update.  Here are the details:

I had a fresh version of Ubuntu 10.10 installed in its own partition and it seemed to be running OK. I decided to get all of the updates for it so I fired up the Update Manager.  I decided to get everything so I left all of the selections checked.  Then I started it updating and observed that was going to download more than 200 MB so I went away for a while.

In normal operation I get about 80K bytes/sec download speed due to my internet connection speed.  This allows the system to loaf along and the CPUs typically report only about 2 to 7 percent usage.

I had a few other things running before I started the updates: a terminal, the system monitor, and Firefox.  I had ssh connected from another machine.

When I returned to the system I found that the progress bar showed about 2/3 done and the update manager was announcing the name of one of the packages, I don't recall which.  I noticed that the system monitor was not scrolling but it was not showing much CPU usage.  I watched things for about a minute and did not see any change.  I thought that something had crashed during the updates and I started to figure out what to do about that.  Then I noticed that the system monitor had scrolled just a tiny amount - the system wasn't completely dead.  So I watched it for a while longer and it scrolled another tiny amount.  The mouse and cursor were operating normally so I fired up _top_ in the terminal.  This ran, although slowly, and it reported that most of the CPU time was going to gnome and to Xorg but no entry showed more than about 27%  usage. (This system uses an Intel 950 with 8 processors.)

I spent a couple of minutes wondering what was going on and wondering what I should do.  Suddenly, the system monitor started to scroll at normal speed and the graphs were typical.  Apparently, whatever was wrong had cleared itself.  The updates proceeded normally and finished.  The system seemed to be running normally.

I was concerned that something may have been corrupted so I booted from an older release from a different partition.  That version worked OK.

I rebooted from the newest, updated version and the boot seemed to proceed normally up through the time when the system played the drumroll associated with login.  However, instead of getting a login screen I had only the purple splash display with 5 red dots and nothing was changing; there was no login box.  Since I could not log in, I reset the system and booted from an older release and this worked OK.

The next time that I booted the updated 10.10 release, it worked like it should.

When the system was choked up, it was acting like it was extremely busy and did not have enough CPU time to update the display.  But the cursor moved as it usually does, without hesitation or jerkiness.

I am not running the proprietary fglrx driver; whatever the 10.10 install provided is presumably what I am using.  This system has two ATI HD4870 graphics cards because I want to run crossfire mode.

Questions:

Has this happened to anyone else?

Does anyone know what the system was doing when it almost froze?

Any other thoughts or insights?

Thanks.

quadproc

---

### Post by ajgreeny on 2011-01-23
It just sounds like one of those strange but totally undiagnosable problems that occur very occasionally at boot time.

If the system continues to run without problems, I would not worry too much.  Keep an eye on cpu% for a while, and make sure you keep updating as new packages appear, and I suspect you should be fine.

---

