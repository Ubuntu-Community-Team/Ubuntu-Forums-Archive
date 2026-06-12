---
title: "Update 3.5.6 killed Firefox"
date: 2009-12-20
forum: General Help
---

### Post by Tosa on 2009-12-20
Hi all!

I've just updated to Firefox 3.5.6. through synaptic and I don't have Firefox any more!

All I get is an empty window without menu bar, status bar, anything! Starting FF from terminal doesn't give any info...

Any help will be greatly appreciated.

---

### Post by leandromartinez98 on 2009-12-20
Very strange. Try removing it and reinstalling.

---

### Post by squaregoldfish on 2009-12-20
If that fails, try removing your firefox profile - it's in ~/.mozilla/firefox. Move it somewhere safe, and see what happens. If Firefox works, you can re-import your bookmarks from the old profile.

If it still fails, try removing your plugins in the same way - ~/.mozilla/plugins.

Steve.

---

### Post by Tosa on 2009-12-20
Thanks for the answers.

I've already try reinstalling it without any help.

Removing ~/.mozilla/firefox didn't help either, but there is no ~/.mozilla/firefox

I still get only a window decoration without any app in it. :(

---

### Post by Tosa on 2009-12-20
Since nothing helped, i decided to go MS way: I rebooted...

And all of a sudden Firefox works again.. :confused:

---

### Post by lovinglinux on 2009-12-20
I get those all the time when I'm developing extensions for Firefox and reload it for testing. I don't know why it happens, but it looks like an extension problem.

---

### Post by grepnix on 2009-12-20
Same thing happened to me. Reboot sorted it...

---

### Post by lovinglinux on 2009-12-20
> **grepnix said:**
> Same thing happened to me. Reboot sorted it...

For me too, btw.

---

