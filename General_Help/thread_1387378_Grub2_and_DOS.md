---
title: "Grub2 and DOS?"
date: 2010-01-21
forum: General Help
---

### Post by Amdahl1 on 2010-01-21
I'd like my old DOS6 partition to show up in the OS list for GRUB. I don't understand how to add it.

I have Ubuntu 9.10 with no menu.lst file so I think I have GRUB2. I tried a GUI config tool but it doesn't help me add to the list.

Can someone explain how to do this?

---

### Post by JC Cheloven on 2010-01-21
> **Amdahl1 said:**
> I'd like my old DOS6 partition to show up in the OS list for GRUB. I don't understand how to add it.

I have Ubuntu 9.10 with no menu.lst file so I think I have GRUB2. I tried a GUI config tool but it doesn't help me add to the list.

Can someone explain how to do this?

Open a terminal and try ```
update-grub2
```

---

### Post by Amdahl1 on 2010-01-21
It didn't like grub2 but update-grub responded with menu.lst not found, and asked to generate for me. Of course I said YES.

Perhaps I can make some progress now?

---

### Post by JC Cheloven on 2010-01-21
> **Amdahl1 said:**
> It didn't like grub2 but update-grub responded with menu.lst not found, and asked to generate for me. Of course I said YES.

Perhaps I can make some progress now?

Sorry, you have to run it with root permissions:```

sudo update-grub2
``` and supply your password when required (when typing it you won't see anything, it's normal).

---

### Post by Amdahl1 on 2010-01-21
Ok, I got the menu.lst, edited it, saved it, no problem... sort of

I re-ran the update-grub (as sudo) and it ran but I'm not getting any change in the boot list. ???? What's up?

---

### Post by JC Cheloven on 2010-01-22
If you are on Ubuntu 9.10, there should not be any menu.lst. It is a grub-legacy (as it is named now) file, and grub2 has a different structure. 

So (I think) you won't get anywhere editing a menu.lst file...

If your grub2 install is still there, "sudo update-grub2" should be able to catch the other Operating systems in your hard disk. I see [here]("http://en.wikipedia.org/wiki/GNU_GRUB") it supports DOS ;-)

Anyway, check [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Dayofswords on 2010-01-22
just wondering, but what do you use dos for?

---

### Post by Amdahl1 on 2010-01-22
Don't laugh.... I need it to run Star Commander to transfer .d64 images back to my [COLOR="Red"]Commodore 64[/COLOR]!

once you pull it together... the goal I have is to get my network up and running with Linux,XP,Dos,C64,and maybe an Apple IIc. (just for bragging rights of course)

---

### Post by Leppie on 2010-01-22
why did you start 2 threads on this?

can you not use a vm for dos?

---

### Post by Amdahl1 on 2010-01-22
I changed threads when I realized I was chasing the wrong issue. My bad...

The application, Star Commander, needs to have direct control of the printer port. Multitasking OS have a tendency to screw with it's timing while it tries to bit-bang data to the IEC serial databus. Sticking to DOS solves a lot of issues with the use of the application and it's requirements.

---

### Post by Leppie on 2010-01-22
and have you tried running it in wine?

---

### Post by Amdahl1 on 2010-01-22
The documentation on it states that the use of emulators will not resolve the issue. It's a problem with the OS doing too many things. To solve it the OS, be Linux or Windows, would need to halt all other processes. Which needless to say is against their very nature.

---

### Post by Leppie on 2010-01-22
> **Amdahl1 said:**
> The documentation on it states that the use of emulators will not resolve the issue. It's a problem with the OS doing too many things. To solve it the OS, be Linux or Windows, would need to halt all other processes. Which needless to say is against their very nature.
wine is not an emulator.
however, can you not make a bootable cd for this?

---

### Post by Amdahl1 on 2010-01-22
Sorry, I had the impression that software running inside a OS environment was limited to the handling of the hosting OS?:confused: But being new to Linux this may be an incorrect thought process. :( I know Linux can run multiple sessions at once but I never heard of it running independent OS simultaneously. I'll have to read up on Wine and DOSEMU further.

Ok, did some additional reading on Wine. So it doesn't emulate machine cycles, but it is still strapped to the multitasking processes that interfere with the IO timing that Star Commander is trying to maintain.
I think my best bet at this point is to just rebuild an old dos machine and keep it in the corner...

But THANKS to everyone for all the help! I have learned a lot in the last week!

---

### Post by Leppie on 2010-01-23
> **Amdahl1 said:**
> I think my best bet at this point is to just rebuild an old dos machine and keep it in the corner...
and running from cd or usb stick?

---

