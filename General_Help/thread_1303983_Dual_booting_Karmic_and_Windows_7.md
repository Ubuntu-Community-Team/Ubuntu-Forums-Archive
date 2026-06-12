---
title: "Dual booting Karmic and Windows 7"
date: 2009-10-28
forum: General Help
---

### Post by dwally89 on 2009-10-28
Hi,

There seems to be about a million articles on this, but I can't seem to get a final answer. 
i)   Is it possible to dual-boot Karmic and Windows 7
ii)  Is it any harder to do than dual booting with Vista
iii) Are there any specific things I need to know before I do it?

Thanks

---

### Post by Monotoko on 2009-10-28
I have Karmic and 7 duel booting at the moment

Karmic picked up Windows 7 and added it to my GRUB fine, so it is no harder than a vista/ubuntu duelboot

Install 7 then Karmic and you should be fine ^.^

~Monotoko

---

### Post by dwally89 on 2009-10-28
How about installing Windows 7 after Karmic?

---

### Post by Zoot7 on 2009-10-28
Installing 7 after karmic shouldn't be a problem, just direct it to whatever partition you want to put it and install it, but the you'll have to re-install Grub to the MBR, and because it's GRUB 2 there's a new method for that. See here to do it from a liveCD.
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) from LiveCD

Sometimes Windows doesn't play particularly nice when dual booting it with something else, but assuming 7 behaves the same as Vista you should be okay.

---

### Post by dwally89 on 2009-10-29
OK thanks, I'll let you know how it goes.

---

### Post by mitch_77 on 2009-11-01
> **Monotoko said:**
> I have Karmic and 7 duel booting at the moment

Karmic picked up Windows 7 and added it to my GRUB fine, so it is no harder than a vista/ubuntu duelboot

Install 7 then Karmic and you should be fine ^.^

~Monotoko

Hi folks, sorry for jumping in but i kind of have the same question.

@Monotoko
did you install 7 with that 200 mb hidden partition? cause i read somewhere that someone was having problem and grub couldn't see 7 or (even worse) it did see it but then no boot into windows because of that.
i just downloaded KK and wanted to install it along with w7. it would be great if it was like before (vista/ubuntu)...without the need to reinstall windows (i just set it as i want with all my sw and updates).

thanks,
mitch

---

