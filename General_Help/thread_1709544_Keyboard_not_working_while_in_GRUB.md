---
title: "Keyboard not working while in GRUB"
date: 2011-03-18
forum: General Help
---

### Post by Davidthewin on 2011-03-18
Already posted this in the new to Ubuntu section, so sorry if it seems like spam

In short, my keyboard does not work until Ubuntu has booted, I found the  error when I couldn't change option to boot from my Windows partition. I  have tried both PS2 and USB keyboards and my case speaker, which  usually beeps once just after being powered up did nothing, which is why  I suspect it is a hardware fault.

I left my computer off this morning, after getting onto Windows fine and  no one has had the opportunity to use my computer since I last did this  morning. I have seen a thread in which someone fixed the problem by  changing the keyboard setting from OS to BIOS, but I am not sure where  or how they did this.

Does anyone have any ideas? (Just a reminder that I'm near enough  completely new to Linux and the most I know about it is a few sudo codes  using sudo)

(I am using Ubuntu 10.04 LTS (I think it's the Lucid Lynx version, it's the only one I've seen around))

---

### Post by Davidthewin on 2011-03-18
I have seen some threads with a similar problem that recommended that the original poster restore his GRUB, would that work here?

---

### Post by MichaelGld on 2011-03-18
Check your BIOS settings. Usually it is accessible by pressing DEL when you hear the beep, if your keyboard is working at that point. If you can get in, search for a section regarding USB keyboard and mouse and make sure they are enabled. Save changes and reboot.

---

### Post by Davidthewin on 2011-03-18
> **MichaelGld said:**
> Check your BIOS settings. Usually it is accessible by pressing DEL when you hear the beep, if your keyboard is working at that point. If you can get in, search for a section regarding USB keyboard and mouse and make sure they are enabled. Save changes and reboot.

Can't use it at all until Ubuntu loads when GRUB automatically loads it.

---

### Post by Davidthewin on 2011-03-18
OK so I changed the GRUB settings to load Windows first automatically and it turns out that the keyboard doesn't work when loading Windows either. I read somewhere that in BIOS the keyboard control can be changed from BIOS to OS, could this be the problem in this case? And if so, how would I go about fixing it seeing as I can't use a keyboard until this point?

---

