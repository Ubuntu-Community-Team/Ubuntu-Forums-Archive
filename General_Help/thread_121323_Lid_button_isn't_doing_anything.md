---
title: "Lid button isn't doing anything"
date: 2006-01-24
forum: General Help
---

### Post by gamma on 2006-01-24
I just came from using Gentoo for the last 4 years, and everything works great except for the lid button not working. It is recognized by the kernel, here's the dmesg snippet..

```
[4294714.669000] ACPI: AC Adapter [AC] (on-line)
[4294714.971000] ACPI: Battery Slot [BAT0] (battery present)
[4294714.988000] ACPI: Lid Switch [LID]
[4294714.988000] ACPI: Power Button (CM) [PBTN]
[4294714.988000] ACPI: Sleep Button (CM) [SBTN]
[4294715.084000] ibm_acpi: ec object not found
[4294715.187000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)

```

Here's the code for my /etc/acpid/events/lidbtn

```
# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/hibernate.sh
#action=/etc/acpi/lid.sh


```

I had this issue with Gentoo, and I think I fixed it by adding a line to the grub boot line. It was tied into the battery applet not updating when unplugged after being on ac power. Any idea how to fix this? Help would be appreciated..

UPDATE: I thought it might have been pci=noacpi, but that doesn't seem to be doing anything. acpid isn't showing any events in the log...

/proc/acpi/button/lid/LID/state displays the correct status also, so I'm guessing it's got something to do with acpid not reading the scripts.

---

### Post by gamma on 2006-01-27
If I manually call the script it works, acpid isn't picking up on the event. Isn't there supposed to be a default event script?

---

