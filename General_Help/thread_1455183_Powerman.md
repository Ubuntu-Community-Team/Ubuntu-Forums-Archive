---
title: "Powerman"
date: 2010-04-15
forum: General Help
---

### Post by seandude on 2010-04-15
Somehow powerman got uninstalled.  I've reinstalled it, only it needs to be configured.  Does anyone know how to do it?  I've looked at the man page for it (man powerman.conf) and I don't understand it.

---

### Post by WinterRain on 2010-04-15
What do you plan on doing with powerman? 

From synaptic: "[I]It is suitable for remote operation in data centers or
computer cluster environment.[/I]"

No offense meant, but if you don't understand the man pages, then this app probably isn't for you.

---

### Post by seandude on 2010-04-15
I use it for suspending my computer from the command line with:

`pm -suspend`

Or putting it into hibernation:

`pm -hibernate`

And no offence taken at all.

---

### Post by 3rdalbum on 2010-04-15
> **seandude said:**
> I use it for suspending my computer from the command line with:

`pm -suspend`

Or putting it into hibernation:

`pm -hibernate`

And no offence taken at all.

You shouldn't need to configure anything. If the pm-suspend and pm-hibernate commands tell you to install Powerman, then install it and you should be able to use those commands.

---

### Post by seandude on 2010-04-15
I try it, and this is what it tells me:

[FONT="Courier New"]Usage: pm [action] [targets]
-1,--on targets      Power on targets
-0,--off targets     Power off targets
-c,--cycle targets   Power cycle targets
-q,--query-all       Query power state of all targets
-Q,--query targets   Query power state of specific targets
[/FONT]

---

