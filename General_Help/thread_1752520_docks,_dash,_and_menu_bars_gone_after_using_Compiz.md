---
title: "docks, dash, and menu bars gone after using Compiz with 11.04"
date: 2011-05-07
forum: General Help
---

### Post by dminli on 2011-05-07
I upgraded from ubuntu 10.10 to 11.04 without any problems.
I noticed the stretchy windows desktop effect was no longer available with the Unity desktop and I wanted to enable it.
I installed the Compiz Configuration Settings Manager via the Software Center.
I opened CCSM and successfully enabled the stretchy windows effect.

I then decided to enable the Desktop Cube: the then menubar display became garbled and illegible, and the desktop froze.

I restarted and now, whenever I login, I have a desktop with only my files and folders and nothing else: no menu bars on the windows, no dock or dash.

I was able to create a Launcher gnome-terminal so I can access the terminal to try to fix this.

Please help me try to restore the original settings before installing CCSM.

---

### Post by brentini on 2011-05-07
The following two commands fixed this issue for me.

```
gconftool-2 --recursive-unset /apps/compiz-1 
unity --reset
```I hope it works for you too. I am new to Unity and didn't like it at first, but I kinda like it now...

Cheers,

Brentini

---

### Post by dminli on 2011-05-09
Thank you very much!  The two commands appear to have restored everything (minus the cool desktop effects).

After entering the commands, the terminal is stuck with the message:
``(<unknown>:9269): dee-WARNING **:Transaction from com.canonical.Unity.ApplicationsPlace.GlobalGroupsModel is in the past. Ignoring transaction.''

Was this seen when using these commands before?

Thanks again!

---

### Post by brentini on 2011-05-09
No, I didn't see that but maybe I missed it. I'm glad you were able to get your desktop back with that.

Cheers, my friend!


EDIT: now that I think about it,  I did not see that output, but I did notice that the global toolbar now worked with the places menu, which did not appear before. So all of my bookmarks for windows were back at that point! I am liking Unity more and more and plan to do a clean install soon just to be sure that I won't have anymore of these issues, Lord willing.

The output you saw has to do with the global menu. Do you also now have that menu, where you did not before?


Brentini

---

### Post by nacef on 2011-05-16
thank you for the tip
but it worked at first and when i close the terminal it get back again like before
do i need to run this command in sudo mode and thak you

---

