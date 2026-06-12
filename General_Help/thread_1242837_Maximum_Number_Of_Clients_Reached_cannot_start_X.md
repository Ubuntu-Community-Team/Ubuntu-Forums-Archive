---
title: "Maximum Number Of Clients Reached cannot start X"
date: 2009-08-17
forum: General Help
---

### Post by jimbo99 on 2009-08-17
I'm running KDE 4.3.  I installed it after the initial release from the PPA repositories.  I have had it updated a couple of times since.  I have been noticing that as I use the system it seems to become somewhat less stable.  As I have encountered the instability I investigated some. Today I think I found a contributing cause.  I don't say "the cause" because it could be indirectly the cause.

I'd learned that when you are having problems launching a program that you should launch it in a terminal window.  I would also try various programs to see if it is just a single one.  In this case it didn't matter which one.

The symptom is this.  After some use programs won't launch.  If I close every program out I can launch one.  If I reboot, all things are back to normal.  In the terminal window, when I have the problem, I would test by starting VLC or firefox, or even dolphin.

When I launch the program in a terminal I had been getting the message that the maximum number of clients reached cannot start X display...

I took some time to research it on the web.  There were quite a few reports, but as usual there were nearly no fixes. Discussion, but no cause settled on and no resolutions.

Today I decided to run the command lsof -c X (as root).  It listed over 200 instances of sockets left open.  Since there were no solutions I chose to do a bit more investigating and discovered that the System Monitor had just about the same number of Python instances listed.

I chose at that time to highlight them all and then chose to terminate them all at once.  After doing this I was able to open new programs.

I then began to test to see which program could be causing this and the only program that I had repeatedly used to do something with was Firefox.  I hadn't open 200+ web pages but I had been saving images from sites like Interfacelift.com.  I left the System Monitor open and I began to test by right clicking and choosing "Save Image As" from the context menu. Each time I saved an image a python entry created.  When the dialog box closed the entry remained.  I did this 10 more times and had 10 more entries.  I closed Firefox, everything related to firefox, and noticed that the python entries were still there.

I tested it with Firefox 3.5.2 and tested it with 3.0.0.13.  It doesn't matter which version, the same result occurs.

---

### Post by jimbo99 on 2009-08-17
This may be the wrong forum to post this thread as in moments I was bumped off the front page with only a couple views.  

Anyone have any suggestion on which forum it should be in?

---

### Post by jimbo99 on 2009-08-18
No one?  No suggestions?  No help?  I don't think I've ever received help from ubuntuforums.org.

---

