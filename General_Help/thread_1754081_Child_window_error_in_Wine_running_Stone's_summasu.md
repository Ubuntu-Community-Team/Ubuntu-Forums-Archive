---
title: "Child window error in Wine running Stone's summasummarum"
date: 2011-05-09
forum: General Help
---

### Post by GNUbee40 on 2011-05-09
I a m using Stone's Summa Summarum for accounting (Danish Program)
This program makes regularly use of child windows.
Now for 2nd time there is an error occurring. Certain child windows have stopped appearing. When starting the program from terminal the following error message appears:

> err:rebar:REBAR_MoveChildWindows EndDeferWindowPos returned NULL

A successful opening of a childwindow (or any window) returns somthing like the following.

> fixme:win:LockWindowUpdate (0x20030), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!

[I]
Reinstalling the Windows program does NOT help, so I reckon this must be some sort of X problem.[/I]
_**How can i reset the window positions in Wine???**_
So far total reinstall of Wine has been my only option. But if this error continues to show this would be quite bothersome.

There are other X problems with this program in conjunction with multiple desktop areas. Thus, when minimizing the SummaSummarum window it might dissapear from, say desktop area 3, and the button shows up in Area 1 instead. However, I can live with that.

Thanks in advance! :popcorn:

---

### Post by GNUbee40 on 2011-05-10
All right!

Here's what to do when having problems with those Child windows in Wine:

In your home folder press Ctrl+h to unhide hidden files and directories
Enter folder **.wine**
open the file **user.reg** with any text editor
find the section with the window settings which is appropiate - in my case *Summasummarum - Kontokort*
Erase the section - if you are scared just cut and paste it in an empty file
Save changes and restart the Windows program, Summasummarum in my case.
Voila Window settings are reset. :guitar:

---

