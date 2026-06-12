---
title: "How do I COMPLETELY delete Wine?"
date: 2009-07-10
forum: General Help
---

### Post by ravenblackxxx on 2009-07-10
I use Intrepid Ibex (8.10). 

I've uninstalled Wine using the Add/Remove Applications tool 
AND gone into Synaptic Package Manager and marked Wine (and wine-dev, etc.) for complete removal (then applied changes, etc.) 
AND I've also deleted the hidden file in my home directory. (home/USERNAME/.wine)

**HOWEVER!**

Wine is still in my Applications menu. :mad: And it still shows all the Applications I installed on it for testing purposes, but do not need (which I KNOW I deleted) and is now just useless clutter. I want it* ALL gone*. What else can I do? 

Please and Thank you. ):P

---

### Post by wojox on 2009-07-11
Hey ravenblackxxx,

Right click on Applications and select Edit Menu.

---

### Post by DeMus on 2009-07-11
> **ravenblackxxx said:**
> I use Intrepid Ibex (8.10). 

I've uninstalled Wine using the Add/Remove Applications tool 
AND gone into Synaptic Package Manager and marked Wine (and wine-dev, etc.) for complete removal (then applied changes, etc.) 
AND I've also deleted the hidden file in my home directory. (home/USERNAME/.wine)

**HOWEVER!**

Wine is still in my Applications menu. :mad: And it still shows all the Applications I installed on it for testing purposes, but do not need (which I KNOW I deleted) and is now just useless clutter. I want it* ALL gone*. What else can I do? 

Please and Thank you. ):P


To remove it from the Applications  menu, do this:
Go to System > Preferences > Main menu
In the new window in the left column (titled menu) click on Applications
In the right column (titled Items) uncheck the box in front of Wine.
Close the Window.

---

### Post by ravenblackxxx on 2009-07-11
Should I delete the Desktop Configuration File in /usr/share/app-install/desktop?
Or would that just make it so I could never install Wine again?

--------------------EDIT------------------------

Ignore that.

---

### Post by ravenblackxxx on 2009-07-11
Oh. That worked. Thanks guys. Ignore my previous post. I didn't know you could do that...cool.

Thanks again.

---

### Post by Chronon on 2009-07-11
If you go to [FONT="Courier New"]**System > Preferences > Main Menu**[/FONT] you should be able to delete the menu entry.

===
Doh!  Way too late.

---

