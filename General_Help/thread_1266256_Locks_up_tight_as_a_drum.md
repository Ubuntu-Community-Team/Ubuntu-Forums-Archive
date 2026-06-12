---
title: "Locks up tight as a drum"
date: 2009-09-14
forum: General Help
---

### Post by celem on 2009-09-14
Darn, I decided to switch to 100% Linux but - foiled again. I had a sideline Ubuntu 9.04 box to I had configured to do everything that I wanted, i.e., all the codecs loaded, etc. Yesterday I retired the XP box and connected the Ubuntu full-time. However, twice today, while printing to my HP 6940 the Ubuntu box froze dead. No response to Ctl+Alt+F1 or F7, nothing! I had to RESET the PC. Many print jobs worked fine - just two at random froze the machine.

Logic would indicate that this is some sort of hardware issue, but what I don't know. It never failed me during testing as a secondary machine and printing to the same printer through the XP box as a networked printer.

With regret, the XP box is back as my primary machine.

---

### Post by cariboo on 2009-09-14
Usually when you get a crash like that you can ssh into the computer and stop the process that is causing the problem.

---

### Post by P4man on 2009-09-14
Not really helpful, but use the XP box as print server ? :)
What printer is it?

---

### Post by celem on 2009-09-14
Hmmm, I could have tried to SSh in via a laptop - didn't think of it. The Ubuntu 9.04 was a simple desktop - no server. The HP 6940 was direct connected via USB. Never encountered this problem previously when the XP box was primary and the Ubuntu printed to the same printer via the shared windows printer. I wonder if it is a USB hardware.driver issue?

I'll have to reconnect it as primary and try the SSH as suggested.

---

### Post by philinux on 2009-09-14
When it hard locks up use this.

[http://lifehacker.com/298891/gently-restart-a-frozen-system](http://lifehacker.com/298891/gently-restart-a-frozen-system)

Then when back in look at the log file to see what happened.

System>admin>log file viewer> messages

---

