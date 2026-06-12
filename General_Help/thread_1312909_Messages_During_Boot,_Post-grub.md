---
title: "Messages During Boot, Post-grub?"
date: 2009-11-03
forum: General Help
---

### Post by moore.bryan on 2009-11-03
I know this was asked before in some other thread, but for the life of me I can't find it...

There are a number of messages which only briefly appear on my screen between boot selection in grub and the xsplash screen; I'm *very* interested in seeing them. I've search all the /var/log's, but nothing in any of them... suggestions aside from "take a picture of the screen with my digital camera?" ;-)

---

### Post by squaregoldfish on 2009-11-03
Try the dmesg command - I think that's what you're looking for.

Steve.

---

### Post by moore.bryan on 2009-11-03
Already did... no dice.

---

### Post by NFblaze on 2009-11-03
I cant really remember right now but I believe if you edit your grub at boot hitting the 'e' key and removing the 'quiet' and 'splash' argument that it will boot with all that information displayed, at the moment my internet is "backed up" and I cant access the grub wiki.

---

### Post by moore.bryan on 2009-11-03
Tried that trick too, but it scrolls too quickly for me to get a handle on what the error is. I was hoping there was a single file which contained that scrolling info... not sure why it's not that simple, to be honest.

---

### Post by Too Late on 2009-11-03
Removing the 'splash' option just removes the splash screen, but removing the 'quiet' option produces much more lines to the output. So let the 'quiet' stay there and remove only the 'splash'.

edit: You can also try to see them by going to tty1 (by pressing Ctrl+Alt+F1) and using Shift+PageUp to scroll. However, the scrolling doesn't work on my computer. To get back to the normal X, press Ctrl+Alt+F7.

---

### Post by squaregoldfish on 2009-11-03
Just a random thought to throw into the mix: if you're nimble with your fingers, you might try the Scroll Lock key. You're unlikely to see it all, but you might at least get an idea of what's in there.

Steve.

---

### Post by moore.bryan on 2009-11-04
> **Too Late said:**
> Removing the 'splash' option just removes the splash screen, but removing the 'quiet' option produces much more lines to the output. So let the 'quiet' stay there and remove only the 'splash'.
Tried this one too... :-(
> 
edit: You can also try to see them by going to tty1 (by pressing Ctrl+Alt+F1) and using Shift+PageUp to scroll. However, the scrolling doesn't work on my computer. To get back to the normal X, press Ctrl+Alt+F7.
**This** was an interesting approach; never really thought of it. Alas, nothing... just "[~5]".
> **squaregoldfish said:**
> Just a random thought to throw into the mix: if you're nimble with your fingers, you might try the Scroll Lock key. You're unlikely to see it all, but you might at least get an idea of what's in there.

Steve.
Hmm... this one I might need to try.

---

### Post by philinux on 2009-11-04
From what I see on my pc it looks like a much smaller version of the grub menu.

Very fleeting.

---

### Post by moore.bryan on 2009-11-04
I have some information about a ureadahead error I want to pass along to the developers...

---

