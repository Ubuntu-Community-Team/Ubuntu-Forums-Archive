---
title: "Computer will no longer start up after replacing the CPU."
date: 2009-07-27
forum: General Help
---

### Post by anthony62490 on 2009-07-27
I really need to learn when to leave well enough alone. I think I got myself into a mess of troubles.

My current CPU is OLD and does not support SSE (for OpenGL gaming, I believe), so I tried to swap it with a newer CPU. Something worth noting; The heat-transfer gel on my CPU has solidified and when I pulled the heatsink out, the processor came out with it before I could release the CPU pins. It was at this point that I discovered that AMD and Intel are NOT interchangeable.
So I put the old CPU back in and flipped it on. GRUB loaded up and I tried to boot under Ubuntu. All I can remember seeing is the phrases "cannot load kernel" and "oops". I flipped it off and back on.
This time, GRUB did not load. I received "GRUB error 15." This tells me that I need to reinstall GRUB. Only now my live CD won't boot. I get the message, "Cannot boot from this disk. Try a BIOS update." Joy.

Thing is, it only said this once. It has stopped telling me to flash my BIOS and has started behaving very strangely. I don't like using the word "erratic," but I have to. It starts up with a wide variety of effects and flavors, none of them pleasing.

Quote:
> When the Live CD is in, it:
-Loads up the boot menu and shows me my choices. (memory test is the only one that works)
-Loads up the boot menu and immediately freezes
-Loads the logo of the boot menu and nothing else
-Tries to load the boot menu, but ends up hard resetting the machine.

> When the Live CD is NOT in:
-GRUB loads up and when I select my kernel, it sends me a kernel panic.
-GRUB loads up and I proceed to log in normally. Halfway through the startup sound effect, the machine freezes/resets.
-GRUB sends me "Error 15"
-occasionally, GRUB doesn't load at all. Instead, it skips GRUB entirely and shows me a screen with a circular blue gradient. Weird.
On one of the occasions where I could log in, I tried to start a failsafe GNOME session. It proceeded to load my desktop picture and immediately freeze. Not sure if it's worth mentioning, but at this point, my CAPS and SCROLL lock lights were flashing.

I've got to say, this machine is doing things I didn't know were possible. It's freaking me out. Got any ideas out there?

---

### Post by Jazzy_Jeff on 2009-07-27
It sounds like you might have damaged your cpu or other part of your mother board. 

It also sounds like you don't know what you are doing in replacing a cpu. You might want to find someone who can check out your system before doing anything else.

---

### Post by Ravernomina on 2009-07-27
+1 on checking hardware it sounds like ur BIOS is toast :/ or ur north bridge is screwed

---

### Post by anthony62490 on 2009-07-27
> **Jazzy_Jeff said:**
> It sounds like you might have damaged your cpu or other part of your mother board. 

It also sounds like you don't know what you are doing in replacing a cpu. You might want to find someone who can check out your system before doing anything else.

Gee, thanks. :/
I've got a friend who knows a thing or two about hardware. He might be able to tell me what's wrong.

---

