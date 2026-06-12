---
title: "Keyboard shortcuts not working"
date: 2010-06-21
forum: General Help
---

### Post by PommieB on 2010-06-21
I don't think I could be much newer to Ubuntu (I only started using it properly an hour ago) and I'm having trouble with the keyboard shortcuts. Nothing happens when I press alt-f2 to run terminal, or ctrl-alt-tab to switch workspaces. I also cannot use the fn keys to dim the screen, change the volume etc

I'm dual booting at the moment using wubi, and I have a Vaio (VGN-CR11S).

Any help would be greatly appreciated!

---

### Post by Smart Viking on 2010-06-21
AFAIK, you use ctrl+alt+<arrow keys> to switch workspaces. 



About "alt+f2", it is probably compiz that is causing that, go into the compiz control center, and check off "Gnome Compatibility".

I hope this helped. :)

---

### Post by PommieB on 2010-06-24
> **Smart Viking said:**
> AFAIK, you use ctrl+alt+<arrow keys> to switch workspaces. 



About "alt+f2", it is probably compiz that is causing that, go into the compiz control center, and check off "Gnome Compatibility".

I hope this helped. :)

Thanks for that, but when I said I was new, I really wasn't kidding... How do I find the Compiz control centre? :S

---

### Post by jesuisbenjamin on 2010-06-24
If you go to System > Preferences > CompizConfig Setting Manager
In there you press button General Options, then select Key-Bindings tab.
Alternatively you can check System > Preferences > Keyboard Preference (but i believe Compiz should over-rule any key-bindings of the latter.

Hope this helps 
PS: Welcome to Ubuntu :)

---

### Post by PommieB on 2010-07-20
I finally solved this when it turned out that my 'Alt' key is called 'Mod5' for some reason. Reassigning all keyboard shortcuts sorted it out.

---

