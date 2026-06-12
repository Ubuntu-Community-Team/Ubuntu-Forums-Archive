---
title: "copy from Putty and paste to Remmina"
date: 2012-07-16
forum: General Help
---

### Post by smaring on 2012-07-16
I use Putty in Ubuntu 12.04 to manage my numerous ssh connections.  I don't have a problem selecting text in my Putty session with the left mouse button, and then pasting it elsewhere in Ubuntu, assuming I don't use the left mouse button again, by using <Shift>+<insert> or the middle mouse button.

However, that does not work when I try to paste into an RDP session with a remote Windows box in Remmina.  <Shift>+<insert> and <ctrl>+v (middle mouse button does nothing) both give the contents of the clipboard from the last <ctrl>+c, not the selected text in Putty.

It seems like the clipboard for Putty is a bit unusual, and fragile given that just about everything you do involves left clicking the mouse, which drops the Putty clipboard contents.

Is there a way to get the contents of the Putty style clipboard into the standard <ctrl>+c/<ctrl>+v clipboard?

---

### Post by Cheesemill on 2012-07-16
I've not used putty in a while (I'm 100% Linux) but can't you just right-click and select copy?

---

### Post by smaring on 2012-07-16
No, right click + paste inside Windows (in the Remmina RDP session) just pastes the contents of <ctrl>+c from before.

This is a Linux port of Putty.

If there is another ssh session manager that has a less esoteric copy/paste mechanism, I'd consider using it.  This is a game stopper for me.

---

### Post by Cheesemill on 2012-07-16
I've never understood why people use Putty when ssh is built into Ubuntu.
There's no need to use a dedicated SSH client, just use the ssh command from a terminal:
```
ssh user@IP_address
```You can then just use gnome-terminal's commands (ie right-click then copy).

---

### Post by smaring on 2012-07-16
I just installed ClipIt, and found I was able to have it save clipboards based on selection.  When I went to Remmina, selected the saved clipboard from the ClipIt history, and used <ctrl>+v, it WORKED!!!!

Huge kudos to ClipIt for saving the day!

:D

---

