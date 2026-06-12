---
title: "Upgrade from 9.04 to 9.10 makes console text tiny."
date: 2009-11-28
forum: General Help
---

### Post by geeknik on 2009-11-28
I thought that doing the "apt-get dist-upgrade" was enough to move from 9.04 to 9.10 once it was released, however, it wasn't. So on 4 of my Ubuntu Server 9.04 machines, I did the "do-release-upgrade" and all 4 of them were successfully however, the text on 2 of them is so small on my monitor, I can barely read it.

#1 - tiny text
#2 - normal pre-upgrade size
#3 - smaller than pre-upgrade but fine
#4 - tiny text

Like I said, these are server machines, no GUI, just text console, display output to a 24" LCD via 4 port KVM.  I checked the menu.lst and all of them are identical. I've tried the vga=ask and the disabling of the framebuffer, but the text size never changes. This is driving me insane and I just want my normal text size back. LOL.

*EDIT* All of the GRUB loading stuff is in a normal size text. It just gets adjusted to a tiny text when the login prompt appears...

---

### Post by gfreethy on 2010-01-01
I just installed 9.04 and I have the same problem..

---

