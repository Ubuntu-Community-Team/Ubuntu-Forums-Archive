---
title: "monitor out of sync during boot and shutdown (also shutdown hang)"
date: 2010-06-30
forum: General Help
---

### Post by ccheath on 2010-06-30
when my pc boots and shuts down my monitor goes into 'input out of range' mode for a bit between the gui and the text only phases of boot/shutdown.

is there a way to fix this? or where to start troubleshooting?

also, when it shuts down it hangs after coming back to the text only part... after just one line of text.

any ideas?

---

### Post by dcstar on 2010-07-01
> **ccheath said:**
> when my pc boots and shuts down my monitor goes into 'input out of range' mode for a bit between the gui and the text only phases of boot/shutdown.

is there a way to fix this? or where to start troubleshooting?
........

Change the resolution in /etc/default/grub.

I have found that **burg** works better in this area than grub2.

---

### Post by ccheath on 2010-07-01
> **dcstar said:**
> Change the resolution in /etc/default/grub.

I have found that **burg** works better in this area than grub2.

thanks for the suggestion... i forgot to check what it's doing in there

any idea as to why it won't shut down?  

i tried a hibernate and got a similar hang (different text on the screen and more lines), but after about 15 seconds it eventually shut off the computer...

---

### Post by ccheath on 2010-07-01
> **dcstar said:**
> Change the resolution in /etc/default/grub.

I have found that **burg** works better in this area than grub2.

thanks for the suggestion... i forgot to check what it's doing in there

any idea as to why it won't shut down?  

i tried a hibernate and got a similar hang (different text on the screen and more lines), but after about 15 seconds it eventually shut off the computer...

---

### Post by ccheath on 2010-07-01
[EDIT saved for future use]

---

