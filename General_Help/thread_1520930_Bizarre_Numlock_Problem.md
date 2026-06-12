---
title: "Bizarre Numlock Problem"
date: 2010-06-30
forum: General Help
---

### Post by klytu on 2010-06-30
I've been having a strange issue with Kubuntu 10.04 64-bit. The first time (and *only* the first time) I press the shift key on my keyboard, the numlock light on my keyboard turns off! At first I thought that the numlock was also being toggled off when this happens, but in fact it isn't. It's not a critical issue or anything like that; I can simply tap the numlock key twice and the numlock light then stays for the rest of the session. I have Ubuntu 8.04 32-bit and Windows Vista installed as well and I don't have this issue running either of those.

Things I've tried to correct this include: playing around with the keyboard settings for the numlock (turn on, turn off, leave unchanged), checking the standard keyboard shortcuts for conflicts, playing around with the keyboard layout settings on the "advanced tab" of that(didn't try all of these, just the ones that seemed relevant - current layout is "Generic 105-key (Intl) PC"). Behavior hasn't changed.

Does anyone have any ideas on how I might go about troubleshooting this to figure out why it happens?

Brief system specs: Intel D975XBX2 motherboard, Intel E6600 processor, Radeon X1650 video card, 4GB ram, Saitek Eclipse II usb keyboard, kernel 2.6.32-22

---

### Post by dabl on 2010-06-30
Huh!

I have the same mobo and 4GB of RAM, although the rest of my hardware is different.  I have never noticed that odd behavior, but I'll try it tonight when I'm home.

Meanwhile, can you boot a Live CD and see if it is the same?

---

### Post by klytu on 2010-07-02
> **dabl said:**
> Huh!

I have the same mobo and 4GB of RAM, although the rest of my hardware is different.  I have never noticed that odd behavior, but I'll try it tonight when I'm home.

Meanwhile, can you boot a Live CD and see if it is the same?

Same issue with Live CD.

---

### Post by dino99 on 2010-07-02
check the bios setting, is numlockx installed ?

---

### Post by simosx on 2010-07-02
It's quite strange.

Do you have an Ubuntu LiveCD? There might be something related to GNOME or KDE.

You can see in ~/.xsession-errors any relevant messages, or in /var/log/Xorg.0.log.

---

### Post by klytu on 2010-07-02
> **dino99 said:**
> check the bios setting, is numlockx installed ?

Thanks for the input, but the BIOS settings aren't the issue. I don't have numlockx installed.

---

### Post by klytu on 2010-07-02
> **simosx said:**
> It's quite strange.

Do you have an Ubuntu LiveCD? There might be something related to GNOME or KDE.

You can see in ~/.xsession-errors any relevant messages, or in /var/log/Xorg.0.log.

Thanks for the tip. Unfortunately, so far I haven´t found any clues in the logs as to what was going on.

However, I think I may be on to something. I think the numlock issue is related to the keyboard layouts settings (in the Regional & Language submenu of System Settings). Reason: the behavior stopped when I disabled keyboard layouts and logged off then back on. However, with keyboard layouts disabled I can´t type a double-quote character! In fact I have to type a single quote (´) character twice to get the single quote character to appear in text. Maddening!

I guess I´ll have to do some more digging and just live with the issue until I can figure out exactly what´s triggering it.

---

### Post by Chame_Wizard on 2010-07-02
You also fix it in the system settings.

---

### Post by klytu on 2010-07-03
> **Chame_Wizard said:**
> You also fix it in the system settings.

I don't understand what you mean. What does "it" refer to?

---

### Post by L_V on 2010-10-14
[_Bug #658991 in linux (Ubuntu): “Keyboard numlock function upside down”_](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658991)

Bug identified, but not yet solved.

---

