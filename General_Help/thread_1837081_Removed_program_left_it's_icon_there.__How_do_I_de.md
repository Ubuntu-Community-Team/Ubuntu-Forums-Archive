---
title: "Removed program left it's icon there.  How do I delete it?"
date: 2011-09-01
forum: General Help
---

### Post by pretty_whistle on 2011-09-01
It's icon is still showing up in the "applications" button on the launcher.

How can I delete it?

:confused:

---

### Post by pretty_whistle on 2011-09-01
I still need an answer since I haven't figured it out myself.

---

### Post by Enigmapond on 2011-09-01
It would help to know what icon exactly...what programme, how you installed/uninstalled said programme. A little more information is necessary.

---

### Post by pretty_whistle on 2011-09-01
> **Enigmapond said:**
> It would help to know what icon exactly...what programme, how you installed/uninstalled said programme. A little more information is necessary.

I've got several actually where I uninstalled the program but the icon's still there.  One program is Evolution.

---

### Post by Enigmapond on 2011-09-01
Ok...well with evolution, just open the terminal and do:

```
gksudo nautilus
```

Then Navigate to File System
/usr/share/indicators/messages/applications
Delete the evolution file. You will need to reboot.

---

### Post by Bobhuber on 2011-09-01
> **pretty_whistle said:**
> It's icon is still showing up in the "applications" button on the launcher.

How can I delete it?

:confused:
right click - remove

---

### Post by sauerpauer on 2011-09-01
There are two preferred methods of removing programs in Ubuntu (just removing the icon won't actually remove the program).

If you want to be cool and use the command line (Applications > Accessories > Terminal, or just search apps for "terminal", depending on which desktop you are using), you can copy the following into the terminal: ```
sudo apt-get remove evolution
```
Alternatively, you can open the Ubuntu Software Center or Synaptic Package Manager, search for evolution, and remove it there.

That should remove any indicators as well.

---

### Post by pretty_whistle on 2011-09-01
> **sauerpauer said:**
> There are two preferred methods of removing programs in Ubuntu (just removing the icon won't actually remove the program).

If you want to be cool and use the command line (Applications > Accessories > Terminal, or just search apps for "terminal", depending on which desktop you are using), you can copy the following into the terminal: ```
sudo apt-get remove evolution
```Alternatively, you can open the Ubuntu Software Center or Synaptic Package Manager, search for evolution, and remove it there.

That should remove any indicators as well.
I did the last option.  The icon's still there.

---

