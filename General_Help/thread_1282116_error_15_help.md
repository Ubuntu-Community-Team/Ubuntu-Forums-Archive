---
title: "error 15 help"
date: 2009-10-04
forum: General Help
---

### Post by Bearded-flower on 2009-10-04
I was messing around with start up editor last night. i shut down my lappy and went to sleep this morning i went to reboot and it came up with error 15: file not found.
i searched the forums and i found how to fix it, edit the grub and change the hd(1,0) to hd(0,0) but when i hit "e: to edit the grub options it comes up with this:
```
eeid   7f770dbd-0cb3-4409-be79-0d0bc9e1a1ed
kernel   /boot/vmlinuz-2.6.28-11-generic root=UUID=7f770dbd-0cb3-4409-be79-0d0bc931a1ed ro quiet splash
/boot/intrd. img-2.6.28-11-generic
quiet
```

That was all hand typed >.<

so does anyone have any idea?

---

### Post by Bearded-flower on 2009-10-04
Im sorry to bump so early, i need to get onto ubuntu, i have past due assignments.
and alot of GFX for my mates forum.

---

### Post by Bearded-flower on 2009-10-04
BUMP
What does all that mean?
why is my grub messed up like that?

---

### Post by Bearded-flower on 2009-10-05
Bump

---

### Post by Bearded-flower on 2009-10-06
bump!

---

### Post by rcayea on 2009-10-06
Have you tried booting from disk and reinstalling grub?

---

### Post by Bearded-flower on 2009-10-06
:D a reply! and no no i havnt, how do i do that?
thanks

---

### Post by Bearded-flower on 2009-10-06
but i can boot into windoz fine though.

---

### Post by lindsay7 on 2009-10-06
Try this to reinstall grub.




1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type “sudo grub”. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

---

### Post by Bearded-flower on 2009-10-19
didnt work, ill post the exact code later cos i dont have my USB on me

---

