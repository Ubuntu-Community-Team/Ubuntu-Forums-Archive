---
title: "shared printer died"
date: 2010-01-31
forum: General Help
---

### Post by tapenick on 2010-01-31
I'm running Xubuntu 8.04.. have an HP printer hanging off of it that is shared.  Everything has been working fine for over a year now.  But now the Windows machine is not working the network.  There is a Ubuntu machine on the net that still prints.  Only thing I can think of that changed were upgrades?

I know there was the Fuse upgrade recently.. not clear on what that is but think it has something to do with permissions.. could that be it?  Sorry for the ignorance.. just guessing.

When I view the printer from the Windows (XP SP3) machine it does not have a 'Ready' status.  Printed from it a day or two ago.. so something recent.  

Okay I'll stop right there and hope for suggestions or more questions... thanks in advance.



Tom

---

### Post by quixote on 2010-02-02
It's probably not the upgrades, but sometimes the last program used to print something can set some flags that cause problems.  To see if that's the case, use CUPS admin:

open firefox or whatever browser you use.
Put "http://localhost:631/" (without quotes) in the address bar

It'll ask for your administrative login at some point.  For CUPS, the user is "root" and your primary user password.  (The same one you would enter to use sudo.)

Go to the printers tab and see if any of the printers are "stopped".  If so, start them.

And hope that helps....

More people have gone bald tearing their hair out over CUPS than any other single cause :p .

---

