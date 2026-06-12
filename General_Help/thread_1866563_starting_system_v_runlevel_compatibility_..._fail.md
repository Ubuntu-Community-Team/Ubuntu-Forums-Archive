---
title: "starting system v runlevel compatibility ... fail"
date: 2011-10-21
forum: General Help
---

### Post by wakajawaqa on 2011-10-21
Hi all. I recently installed Kubuntu on several public school computers (they were in a junk heap!) as well as my sister's laptop (she's a teacher at the school) and I'm running into a weird problem.

The school computers appear to be operating fine, thank goodness, but my sister's is not shutting down properly. When I shut it down, via the K menu, or ```
#shutdown -h now
#halt

```the system goes through the shutdown sequence and displays the message "The system has halted." I can hear everything stop, the fan stops running, etc., but the screen will not turn off, everything remains on the screen.

The message, of course, is only shown when I disable "quiet splash" in GRUB, otherwise it just hangs on the kubuntu splash screen (the one with the four dots).

Reboot works as expected.

The only odd thing I noticed in the boot / shutdown messages was the message ```
 Starting System V runlevel compatibility  ........ [fail]
```Sounds pretty serious and I'm not sure what to do about it. Any suggestions?

I was happy I could save those old computers from being thrown away, but now I feel like a schmuck because the most important one isn't functioning properly and I can't fix it! :redface:

---

### Post by wakajawaqa on 2011-10-21
forgot to mention, disabling acpi in /etc/default/grub does not work either...

---

### Post by wakajawaqa on 2011-10-22
Sorry to bump so soon, are the two problems even related? What other information can I provide?

Thanks

---

