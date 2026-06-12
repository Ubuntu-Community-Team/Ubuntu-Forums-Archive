---
title: "set visual effects from command line?"
date: 2011-03-12
forum: General Help
---

### Post by UncleBoarder on 2011-03-12
I've been searching for how to set Preferences - Appearance - Visual Effects from command line.

I'm not trying to launch the gui, I want it to set from CLI and then I want to check the GUI to confirm it did set properly... possible?

I've tried gconftool which shows me what windowmanager I'm running (note both "Normal" and "Extra" say I'm running "compiz" as my windowmanager.

I've tried gconftool-2 to set it but since both are already "compiz" I don't know how to differentiate between "Normal" and "Extra"

I have grep'd all of my .gconf directory and there doesn't seem to be any reference to "Normal" or "Extra" in any of my %gconf.xml files.

How can I change the Visual Effect setting from CLI?

---

### Post by gyussz on 2011-03-12
Had similiar problem this week. I wanted to disable every extra visual effects while running World of Warcraft. So when I run it:
```
metacity --replace &
```
And when I'm done and I want my previous settings:
```
compiz --replace &
```

Well, you can't switch with this method between Normal and Extra, only None and Extra, but maybe it helps a bit, so I wanted to share with you...

Have a nice day

---

### Post by Frogs Hair on 2011-03-12
I find no man page for visual effects or appearance , it may be included somewhere else , but I have not found it yet. All I know of is what gyussz posted.

---

### Post by UncleBoarder on 2011-03-12
No, that's not really what I'm looking for.  I'd seen that too.  Thanks though.  

As you said, that only switches between "None" and "Extra", my question is how do I switch between "Normal" and "Extra"?

Still looking for a solution...

---

