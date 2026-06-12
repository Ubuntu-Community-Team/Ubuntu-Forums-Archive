---
title: "sticks to panel on openning, new version of ubuntu and other ???"
date: 2010-07-31
forum: General Help
---

### Post by jleslie48 on 2010-07-31
Ok, so I just updated my ubuntu computer now things are different and I want to configure my computer differently but I can't figure out how to do it.  I'm hoping someone here can point me in the right direction. 

first off I have two monitors on my system.   I figured out how to activate the second monitor so that it is not just a duplicate of the first, so I got that far at least. 

Here are my questions 


1)  How can I tell what version of Ubuntu am I running?  the help doesn't have an about tag!!!

2) how can I change which monitor has the panel?

3) the big annoying thing  -  all of a sudden, when I open an application it is "stuck" to the panel and I can't unstick it, how can I unstick it, and even better turn off this god-awful feature?

4) bonus question:  I used to be able to switch workspaces with the wheel on the mouse but that is now disabled how do I get it back?

TIA, 

Jleslie48

---

### Post by jleslie48 on 2010-07-31
Ok, so I'm poking around a bit.  


1) forget the blue question mark on the panel, god know why it doesn't have it, but under System  --> about ubuntu   it tells me I'm ubuntu 9.10. 

2) you have to right click on **one of the thingies** **on the left **in the panel and there are different options for the panel than if you click on the blank space.   One of them is MOVE and another is LOCK PANEL.   God knows why you don't see these options when you right click on the blank space of the panel.  between these two options I was able to move my panel to the other window. 

3) now that I've moved my panel, I don't seem to be having a problem with the applications being "stuck" to the panel.   I'm thinking maybe its just that the control panel at the top (the orange/brown bar at the top of the window) was just behind the panel and inaccesible.  This was very annoying. Any further information on this would be appreciated. 

4) still outstanding.

---

### Post by howefield on 2010-07-31
> **jleslie48 said:**
> 1)  How can I tell what version of Ubuntu am I running?  the help doesn't have an about tag!!!

Open a terminal and type

```
lsb_release -a
```

> how can I change which monitor has the panel?

What model of graphic card do you have ?


> the big annoying thing  -  all of a sudden, when I open an application it is "stuck" to the panel and I can't unstick it...

Not sure about this.

> I used to be able to switch workspaces with the wheel on the mouse but that is now disabled how do I get it back?

Open gconf-editor (press Alt + F2 keys together and type gconf-editor and press run)

Navigate to apps > compiz > plugins > vpswitch > allscreens > options.
Change "next_button" value to "Button5" and "prev_button" to "Button4"

---

