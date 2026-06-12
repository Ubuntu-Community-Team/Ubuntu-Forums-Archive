---
title: "Virtual box no keyboard"
date: 2011-01-24
forum: General Help
---

### Post by qwertyjjj on 2011-01-24
When I load XP in VirtualBox it starts off with the keyboard working.
However, if I leave my computer for 10mins the Ubuntu computer/screensaver lock comes in.
When I then go back to my VirtualBox I cannot select the CTRL-right to activate the keyboard. The mouse still works correctly but I cannot type anything.
Any ideas on what to do?

---

### Post by JKyleOKC on 2011-01-24
> **qwertyjjj said:**
> Any ideas on what to do?Have you installed the Guest Additions in the XP system? If you have, you should not need to use right-control to get the keyboard back from the guest system. Just move the mouse pointer out of the XP screen into the host area, and that should unlock the screensaver.

I had something similar happen yesterday, and I could not get the screensaver's images to go away until I used the "host" key (right-ctrl by default but I've changed mine to the menu key, so that both ctrl keys work normally at all times). I had not yet installed the guest additions into a brand-new XP machine I was creating. As soon as the XP machine released the mouse back to the host, the screensaver went away. Once the Guest Additions are installed, it's all automatic...

---

### Post by qwertyjjj on 2011-01-24
> **JKyleOKC said:**
> Have you installed the Guest Additions in the XP system? If you have, you should not need to use right-control to get the keyboard back from the guest system. Just move the mouse pointer out of the XP screen into the host area, and that should unlock the screensaver.

I had something similar happen yesterday, and I could not get the screensaver's images to go away until I used the "host" key (right-ctrl by default but I've changed mine to the menu key, so that both ctrl keys work normally at all times). I had not yet installed the guest additions into a brand-new XP machine I was creating. As soon as the XP machine released the mouse back to the host, the screensaver went away. Once the Guest Additions are installed, it's all automatic...

Yes, guest additions are installed but it's not the mouse that is the problem but the keyboard.
It will not recognise the keyboard once Ubuntu has gone into screensaver/lockdown mode. I enter the Ubuntu password to log back in and after that the Vbox will only recognise mouse clicks.

---

### Post by JKyleOKC on 2011-01-25
The only thing I can suggest for this situation is that possibly the keyboard is still hooked to the guest when you enter the password, and some character in the password is being interpreted as a hotkey by the guest. Next time it goes into screensaver, try moving the mouse completely away from the guest; this should unhook both mouse and keyboard from the guest. Then type the password to unlock, move the mouse back into the guest area, and see if the keyboard now works.

If it doesn't, then I'm lost! Perhaps someone else will have some ideas... If it's a USB keyboard connection, possibly it's becoming disconnected from the guest. I read somewhere yesterday that setting up a USB filter for keyboard or mouse had disabled the filtered connection so this might be a clue...

---

