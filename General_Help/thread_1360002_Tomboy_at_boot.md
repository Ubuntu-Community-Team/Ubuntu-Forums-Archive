---
title: "Tomboy at boot"
date: 2009-12-20
forum: General Help
---

### Post by 2roombas on 2009-12-20
Hi... I've searched for this, yes, but I've found no easy answer, so I thought I'd ask here. You all have been so very helpful whenever I hit a bump while learning about this awesome OS in the past. Thank you!:)

I want to make Tomboy Notes start at boot. I do already have Tomboy added to the panel, however this still requires me to run it every time. I would like Tomboy to just start up automatically, so that it just sits there in the tray and when I click its icon it displays a list of notes.

I know it's via System > Preferences > Start Up Applications, but what/where is the command line that I need to add?

---

### Post by NFblaze on 2009-12-20
The command to launch Tomboy Notes is *tomboy*.

By the way you can always search for terminal commands of a program by using:

"apropos" or "man -k"

such as

[I]man -k tomboy
apropos tomboy[/I]

This will quickly scan the summary of the manpages of program for a match of the following phrase.

---

### Post by 2roombas on 2009-12-20
Thank you, but I found the answer to my question right after I posted on here.  It was locatesd in File System/usr/bin.  

I added Tomboyin System>Preferences>Start Up Applications, rebooted and viola... it is now auto-started at boot and sitting in my notification tray, ready to just rt-click and pick a note without first opening the "browse all notes" window.:)

---

