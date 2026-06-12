---
title: "Oneiric, ALT+TAB task switcher"
date: 2011-10-14
forum: General Help
---

### Post by Rodayo on 2011-10-14
Just installed oneiric last night and I'm not liking this new task switcher. 

1) I don't need a desktop option
2) I only want tasks from the current workspace to show up
3) I don't want tasks to be grouped together
4) I want to see what the window looks like, not the icon for the app

Is there anyway to change the settings for this?

Apologies if this has been posted already.

PS: seems windows+D doesn't minimize and show desktop. Is this a bug?

---

### Post by bbrg548 on 2011-10-14
I've gone back to Compiz's Shift Switcher. It's much more usable. Unity's default switcher is horrible, and the developer responses to this same complaint in LaunchPad have been less than encouraging. They've gotten fixated on the 'application-based' model and ignore the fact that users don't see *applications*, users see *_windows_*.

They've just barely acknowledged that the new switcher breaks the workspace paradigm. I don't think we'll see this issue addressed at all before 12.04, if then.

---

### Post by Rodayo on 2011-10-14
> **bbrg548 said:**
> I've gone back to Compiz's Shift Switcher. It's much more usable. Unity's default switcher is horrible, and the developer responses to this same complaint in LaunchPad have been less than encouraging. They've gotten fixated on the 'application-based' model and ignore the fact that users don't see *applications*, users see *_windows_*.

They've just barely acknowledged that the new switcher breaks the workspace paradigm. I don't think we'll see this issue addressed at all before 12.04, if then.

That's a shame. I like the new unity a lot, looks very elegant. But the task switcher was not thought out.

Can you tell me how to switch the compiz version? Can I continue to use Unity after switching over?

---

### Post by mpo on 2011-10-15
Before siwtching to an alternative (I would welcome the howto on that as well, anyone?) I would like to try customizing the current one more to my liking.

The only thing I would like to change at the moment is removing the ALT+1 key-binding to get the preview (which doubles somewhat already for ALT+TAB, then DOWN)

Does anyone know how to do that?

---

### Post by pbradaric on 2011-10-16
I completely agree with Rodayo. Here's one alternative.

1. Install "CompizConfig Settings Manager"
```
sudo apt-get install compizconfig-settings-manager
```
2. Open "CompizConfig Settings Manager" and go to "Desktop"/"Ubuntu Unity Plugin"/"Switcher" and disable "Key to start the switcher" and "Key to start the switcher in reverse"
3. Then go to (also in "CompizConfig Settings Manager") "Window Management" and check "Static Application Switcher" (this can possibly screw up your current display - don't worry, just reset the machine).

That's it, you should basically have the old switcher back - everything else "Unity" stays.

---

### Post by Rodayo on 2011-10-20
> **pbradaric said:**
> I completely agree with Rodayo. Here's one alternative.

1. Install "CompizConfig Settings Manager"
```
sudo apt-get install compizconfig-settings-manager
```2. Open "CompizConfig Settings Manager" and go to "Desktop"/"Ubuntu Unity Plugin"/"Switcher" and disable "Key to start the switcher" and "Key to start the switcher in reverse"
3. Then go to (also in "CompizConfig Settings Manager") "Window Management" and check "Static Application Switcher" (this can possibly screw up your current display - don't worry, just reset the machine).

That's it, you should basically have the old switcher back - everything else "Unity" stays.

Worked like a charm. Thanks alot!

---

### Post by punkprincess on 2011-12-31
This was very helpful! The new task switcher has been very annoying. Thank you very much for this work around :)

> **pbradaric said:**
> I completely agree with Rodayo. Here's one alternative.

1. Install "CompizConfig Settings Manager"
```
sudo apt-get install compizconfig-settings-manager
```
2. Open "CompizConfig Settings Manager" and go to "Desktop"/"Ubuntu Unity Plugin"/"Switcher" and disable "Key to start the switcher" and "Key to start the switcher in reverse"
3. Then go to (also in "CompizConfig Settings Manager") "Window Management" and check "Static Application Switcher" (this can possibly screw up your current display - don't worry, just reset the machine).

That's it, you should basically have the old switcher back - everything else "Unity" stays.

---

