---
title: "How can I change the default screen brightness?"
date: 2009-07-13
forum: General Help
---

### Post by mbux on 2009-07-13
Is there anyway I can change the screen brightness my laptop starts-up with?

---

### Post by ajgreeny on 2009-07-13
The ones I've seen always start the same as they were when shutdown.

---

### Post by mbux on 2009-07-13
Well, not quite. I like to run my screen on the lowest brightness, but it always starts up on the highest brightness. It doesn't save the brightness setting on a fresh start. I would like to know a way to change the brightness it starts up with.

---

### Post by 456 on 2009-08-03
Hi mbux,

Have you tried setting the brightness options in the power management program?

Accessed via: System - Preferences - Powermanagement.

I've just fixed my laptop after getting annoyed that the screen kept adjusting to 50% brightness on battery power.

All the best,

456

---

### Post by mikewhatever on 2009-08-03
> **456 said:**
> Hi mbux,

Have you tried setting the brightness options in the power management program?

Accessed via: System - Preferences - Powermanagement.

I've just fixed my laptop after getting annoyed that the screen kept adjusting to 50% brightness on battery power.

All the best,

456

That's irrelevant to the OP's question.

Hi mbux,

there is not gui for changing the default brightness in Ubuntu/Gnome, but you can do it with gconf-editor.
Press alt+f2, type gconf-editor, in the window that opens, navigate to /apps/gnome-power-management/backlight, and change the value of brightness_ac to your liking.

---

### Post by mike555 on 2009-08-03
I have an Acer monitor and it has settings on it for brightness , I set mine for the "text" setting witch is less bright .

---

### Post by Tipped OuT on 2009-08-03
I would think the brightness is controlled by the monitor, not the operating system. This is weird because my brightness always saves.

---

### Post by mikewhatever on 2009-08-03
It is usually the case, that there are control buttons on the panel of the monitor to control brightness, etc. However, you don't have these on laptops, so an alternative way is needed.

---

### Post by Tipped OuT on 2009-08-03
> **mikewhatever said:**
> It is usually the case, that there are control buttons on the panel of the monitor to control brightness, etc. However, you don't have these on laptops, so an alternative way is needed.

Yes, you use the special keys on your laptop.

Function Key + Brightness Up Key/ Brightness Down Key

You don't use your operating system to do this.

---

### Post by Hobgoblin on 2009-08-03
> **Tipped OuT said:**
> Yes, you use the special keys on your laptop.

Function Key + Brightness Up Key/ Brightness Down Key

You don't use your operating system to do this.

Those functions keys operate via the operating system.

On laptops the screen brightness is set by software.

---

### Post by mikewhatever on 2009-08-03
> **Hobgoblin said:**
> Those functions keys operate via the operating system.

On laptops the screen brightness is set by software.

+1. Try deleting the operating system and see if the brightness control keys still work.

---

### Post by Tipped OuT on 2009-08-03
> **Hobgoblin said:**
> Those functions keys operate via the operating system.

On laptops the screen brightness is set by software.

Well that's weird because I can change my brightness when the laptop is booting the BIOS, hasn't even loaded an operating system yet. Matter of fact, I can change it whenever I want, even after Windows crashes and locks up. As long as it has power. *sigh*

Anyways, I hope the OP solves his case with the suggestions.

---

