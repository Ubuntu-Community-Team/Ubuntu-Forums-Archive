---
title: "Last Mount Time is in the Future"
date: 2010-06-22
forum: General Help
---

### Post by mmett on 2010-06-22
All,

I screwed up and set the date/time wrong on a unbuntu server (10.2) and rebooted.  now that I have fixed the date/time the system won't boot.  The error message is:
[FONT=Courier New][SIZE=2]
[/SIZE][/FONT][INDENT][FONT=Courier New][SIZE=2]/dev/mapper/engtest-root: UNEXPECTED INCONSISTENCY;  run fsck manually/

/dev/sda1: Supterblock last mount time (6/22/2035...) is in the the future.[/SIZE][/FONT]

[/INDENT]But the system isn't up and I can't do anything to get to a prompt to manually run fsck.

Any ideas and/or suggestions or just reinstall the server again?

-MM

---

### Post by SoFl W on 2010-06-22
Trying running  fsck, (from a Live CD or USB boot) making sure the date/time is correct before you run it.

---

### Post by babdel on 2011-01-10
I had the same problem .... the solution (after changing the coin cell battery) was to press the letter F from the keyboard in responding to the "unhelpfull" error message....   this run the FSCK .... you have to press F one time for each mount point on your system ...  you don't have to use live CD or booting usb or even booting in recovery mode...

---

