---
title: "Upgraded to 9.10 - Now I have no GUI"
date: 2009-10-30
forum: General Help
---

### Post by Vacman on 2009-10-30
The title explains it all. I don't even know where to begin with this one.

If I let it boot up normally, I see where it say Starting, but then I end up with a blank, black screen. If I hit ESC during biit-up - I do get a command line prompt if I boot into Recovery Mode.

Where to start? 9.04 worked great! Can I somehow go back? Is there a fix?

---

### Post by a20365354 on 2009-10-30
Type xorg in black screen and press <enter>.
If you can't type,press Ctrl+Alt+F1.
*Don't use numpad to enter username or password.
Maybe it work.

---

### Post by Vacman on 2009-10-30
No love... Blank, black screen - typed xorg, hit<enter> and nothing. Ctrl+Alt+F1 gives me a funky underscore cursor top left corner - typing there does nothing.

---

### Post by a20365354 on 2009-10-30
What display card you use?
What CPU you use?
More infomation can faster to solve the problem :)

---

### Post by njibo on 2009-11-01
I also have the same problem. I upgraded from Ubuntu 9.04 to 9.10. Everything went well until the reboot. I get the small Ubuntu logo and a black screen. I followed what you asked to do and still nothing.
I am running on an HP DV5Z with 4 Gig of RAM and an ATI Readon HD 3200 integrated card.

Please can you help?

Thanks!

William

---

### Post by njibo on 2009-11-01
I just solved my problem. This is what I did:

- I identified my video card (ATI READON HD 3200)
- I downloaded the Linux driver from the ATI side
- Copied the driver on a USB stick
- mounted the USB and installed the driver
- I then rebooted and I FINALLY GOT THE BEAUTIFUL COLORS OF 9.10

I noticed that lots of people have video card driver problems. I hope this would help!

---

