---
title: "aMule minimizing to tray icon -- How can I do this?"
date: 2012-09-04
forum: General Help
---

### Post by MrsUser on 2012-09-04
Hello dear Ubuntu users,

I am using Ubuntu 12.04 (64-bit) and I'm wondering if there is a possibility to minimize aMule to the tray, so that it disappears from the launcher. I tried the option 'Enable Tray Icon' in aMule preferences, but that doesn't have any effect.

Does anyone know a solution to this?

---

### Post by Vaphell on 2012-09-04
my arguably old version of amule (ubu 10.04) has another checkbox below the 'enable tray icon' option, 'minimize to tray'. When it's enabled, minimizing window makes it dissapear from the dock.

---

### Post by kostkon on 2012-09-04
Follow the instructions [here]("http://shuffleos.com/791/dconf-editor-show-selected-app-icons/"). Just add 'amule' in the list.

---

### Post by MrsUser on 2012-09-05
> **kostkon said:**
> Follow the instructions [here]("http://shuffleos.com/791/dconf-editor-show-selected-app-icons/"). Just add 'amule' in the list.
Thank you. Now at least I have the tray icon. Hint: When adding aMule to the whitelist, it has to be all in lowercase ('amule', not 'aMule') -- see screenshot attached.
However, aMule is still appearing in the launcher even when minimized  and 'Minimize to Tray Icon' is checked in aMule preferences. But I want aMule to disappear from the launcher when minimized. Is this even possible? Or is aMule too outdated for Unity compatibility?

[[IMG]http://i.imgur.com/qIPaHs.png[/IMG]]("http://imgur.com/qIPaH")


_EDIT:_
**I found the solution.** It's simple, just didn't see it straight away :-)
Once aMule is in the tray, aMule can be hidden from Unity's launcher by simply double-clicking the tray icon. Or, alternatively, just right-click the tray icon and choose 'Hide aMule' from the dropdown menu. Accordingly, you can double-click again or choose 'Show aMule' when aMule is hidden from the launcher. Thanks a lot for your help!

---

