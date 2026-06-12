---
title: "Everything is slow!"
date: 2010-06-09
forum: General Help
---

### Post by quequotion on 2010-06-09
:confused:
My whole computer seems to have slowed down to half it's usual speed. In either Metacity or Compiz everything takes longer to open than usual; video plaback is choppy at best but often unwatchable; games are running like molasses. Login takes over a minute between pushing the button and seeing a desktop. Shut down is also very slow.

I've run hardware diagnostics and everything checks out.

Oddly, if I have compiz running with the cube_atlantis plugin, I can see the fish start to move normally (quickly) for a few seconds just before shut down.

I'm using a not-so-old nVidia card and the latest proprietary driver.

I'll be back with the list of kernel modules and such later.... it's very late and I am sleepy.

---

### Post by dtfinch on 2010-06-09
If you run 'top' from the terminal, is anything using a lot of cpu?

---

### Post by quequotion on 2010-06-10
> **dtfinch said:**
> If you run 'top' from the terminal, is anything using a lot of cpu?


Good idea, didn't get a chance to try. Did have a look at gnome-system-monitor and saw some funny things, like gnome-system-moitor *itself* was using 70% of the CPU! I also didn't get a chance to gather all my system data, but it wasn't necessary.

I found the source of the problem, although I'm not certain about the cause.

I have and HP Proliant ML115 G1 server that I'm using as a desktop. There are two APM features in the BIOS, a "throttle" and "APM Event", both of which have short descriptions in the BIOS that don't make much sense (bad english + technical jargon = incomprehensible mess).

Each feature has a ratio setting, which I believe to be either the amount of overheat before the setting is triggered or the amount of total heat capacity before the setting is triggered or the amount to enforce the setting when triggered (the documentation makes **no** distinction between these).

Enabling either feature causes severe system-wide slowdown, limiting the server to nearly half of it's CPU power. I noticed that it wasn't just a GPU problem when I tried booting with an older kernel; it took two seconds to scroll between each GRUB menu item (press down key, wait 1.. 2.. next option). The throttling feature is intended to do this kind of thing, but I am definitely not experiencing overheating. Neither feature should be triggered at all.

I don't know if this is a bug in the BIOS or hardware or if this is an intended feature of the server. It is not an Ubuntu problem.

---

### Post by dcstar on 2010-06-10
> **quequotion said:**
> Good idea, didn't get a chance to try. Did have a look at gnome-system-monitor and saw some funny things, like gnome-system-moitor *itself* was using 70% of the CPU! I also didn't get a chance to gather all my system data, but it wasn't necessary.

I found the source of the problem, although I'm not certain about the cause.

I have and **HP Proliant ML115 G1** server that I'm using as a desktop.
........
I don't know if this is a bug in the BIOS or hardware or if this is an intended feature of the server. It is not an Ubuntu problem.

That is old hardware now, you should make sure that the heatsinks/fans are not clogged with dust causing overheating and therefore slow running.

---

### Post by quequotion on 2010-06-11
> **dcstar said:**
> That is old hardware now, you should make sure that the heatsinks/fans are not clogged with dust causing overheating and therefore slow running.

the waterblocks/pump are working just fine :)

---

