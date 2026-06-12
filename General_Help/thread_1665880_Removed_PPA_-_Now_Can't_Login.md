---
title: "Removed PPA - Now Can't Login?"
date: 2011-01-12
forum: General Help
---

### Post by porkchop_001 on 2011-01-12
Hi Guys,

So all I did was go into Software Sources, selected the PPA for the program I wanted to remove (I forget what it was called now - Synabolus or something...it was a desktop search program), then went into Ubuntu Software Centre and removed the applicable entries there.

Now when I boot up into Ubuntu it asks for my password (which it never use to do) and when I enter the password it just keeps looping to the password screen.

Any ideas? Thanks

---

### Post by celldweller1591 on 2011-01-12
press Ctrl+alt+F1 and login as root. Then try : 

> apt-get install -f 
dpkg --configure -a 

---

### Post by porkchop_001 on 2011-01-13
Hi cell,

Sadly that didn't do anything. I've attached the screenshot for reference purposes.

Allow me to clarify again as when I made the original post I was in a rush to go out:

I was removing a PPA entry for a program I no longer use (it was 'Synapse' - I couldn't remember that before). Once they were gone from the Software Sources I proceeded to the Ubuntu Software Centre to see if they had disappeared from the updates list. They hasn't - so I removed all four entries, and then restarted my machine.

What happens is that once I arrive on the login screen (which never use to happen as I had set it to auto login as myself) and I enter my password, the screen goes blank, then arrives back at the login screen again - once more asking for my password.

I don't see what's gone wrong here. It's essential I get back into my things as I have University exams approaching and I really needs to get some files.

Any further help would be greatly appreciated.

[http://img641.imageshack.us/i/img00184201101131859.jpg/](http://img641.imageshack.us/i/img00184201101131859.jpg/)

---

### Post by porkchop_001 on 2011-01-13
Never mind - I just booted with the Live CD, grabbed my files, and did a clean format. I was planning on re-formatting soon either way.

Thanks anyway Cell - appreciated.

---

