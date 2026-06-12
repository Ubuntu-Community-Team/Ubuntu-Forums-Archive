---
title: "Problem getting into BIOS with ps/2 keyboard"
date: 2009-11-05
forum: General Help
---

### Post by honestguvnor on 2009-11-05
I have bought a new small computer and installed ubuntu 9.10. The computer has no ps/2 sockets only usb ones and so I am using a converter for the keyboard. The keyboard works fine except in the early stages when trying to get into the BIOS or when trying to select from the grub screen. Hammering the keyboard with lots of Alt Ctrl Del has got me into the BIOS twice but I have yet to successfully move the grub selection.

Are such problems common with non-ps/2 socket PCs?

Is there another solution apart from buying another keyboard?

---

### Post by Giblet5 on 2009-11-05
This is Catch-22.

The BIOS is set to not provide Legacy USB Support, so your keyboard won't work during POST (self tests) - the point where it NEEDS to work in order to enter setup.

You can try hitting the Setup key (usually F2, Esc, or Del) about once per second after the initial beep (signals that self-tests have begun). It ***might*** go into setup mode.

When that doesn't work, you can try borrowing someone else's real USB keyboard and try that...

---

### Post by alphaniner on 2009-11-05
I've found that continually pressing a key (I choose NumLock) all the way until the GRUB menu gives me control there.  As for the BIOS, alternating between NumLock and Del - from the instant I power on the machine until I see 'entering setup...' - tends to be quite reliable.  Though sometimes I get into the BIOS and have no control there...

---

### Post by honestguvnor on 2009-11-05
Thanks for the input. If others are having the same problems I can live with it in the short term and add a usb keyboard to the Christmas shopping list.

---

### Post by Giblet5 on 2009-11-05
> **honestguvnor said:**
> Thanks for the input. If others are having the same problems I can live with it in the short term and add a usb keyboard to the Christmas shopping list.

I'll throw in a shameless plug for the Logitech G15 gaming keyboard. It provides an LCD display that one can use for displaying media info, cpu stats, etc, plus THREE BANKS of 18 programmable macro keys (64 in all).

---

