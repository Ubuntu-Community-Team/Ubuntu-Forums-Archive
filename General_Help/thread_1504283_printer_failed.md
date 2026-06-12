---
title: "printer failed"
date: 2010-06-07
forum: General Help
---

### Post by choochoousmc on 2010-06-07
Got Ubuntu installe last week. Everything seems to be working fine.
Printed a test page on printer twice, printed both times.
Today it won't print. The print scheduler comes up with warning not connected.
Have epson stylus nx515, set up as wireless.
under system>administration>Printer  the main window shows connected to local host.
The url appears to be correct. It just won't print.

I just tried it from my windows computer and it printed fine.
So the problem is between Ubuntu and the printer.

any ideas?  If I have to use a terminal window to make changes, provide all the commands I would need, as I'm not upto date on those commands.
thanks

---

### Post by choochoousmc on 2010-06-09
I really dislike forums. You post a question, and then as it scrolls backward after time as new questions are introduced, it is a PIA to find it again.

However,
I have resolved my own question.
I thought back to a few months ago to a problem with my windows computer that was 
similar.
I checked that. Sure enough this time it happened to be the same problem

---

### Post by akxiii on 2010-07-05
> **choochoousmc said:**
> I really dislike forums. You post a question, and then as it scrolls backward after time as new questions are introduced, it is a PIA to find it again.

However,
I have resolved my own question.
I thought back to a few months ago to a problem with my windows computer that was 
similar.
I checked that. Sure enough this time it happened to be the same problem

I have the same printer, and it seems to work fine. When you go to select a driver try the nx400. The 515 driver works for me, but others have had success with the nx400 driver as well.

Does it just fail over wireless or plugged in as well?

---

### Post by choochoousmc on 2010-07-25
> **akxiii said:**
> I have the same printer, and it seems to work fine. When you go to select a driver try the nx400. The 515 driver works for me, but others have had success with the nx400 driver as well.

Does it just fail over wireless or plugged in as well?

I'm Marking this thread as solved because I figured it out.
Ubuntu does NOT automatically rescan for the printer if there has been a power outage.
I use a linksys wireless router, and if power is cut off it sometimes reassigns the ip address to the printer.
When it does that I have to manually reassign the ip in Ubuntu.
Plus I've noticed Ubuntu takes a VERY long time to actually communicate with the printer.

---

### Post by bakegoodz on 2010-07-25
Go to the "Search" menu drop down and choose "Find All Your Threads".
Also when your question has been solved goto the lower red "Thread Tools" menu and choose "Mark as Solved"
 That should help with your forum frustration

---

### Post by Bkidiooo on 2010-07-25
Hmmm... that seems to be quite the problem your having,
1. He you checked the drivers- maybe they need updating

I had a problem similar with the connection of my wired brother mfc-240c and in the end i had to take ownership of a file (40-libsane. rules to add a prompt at the end so my scanner would work... not sure if its any help to you

Good Luck Though!!! :p

---

