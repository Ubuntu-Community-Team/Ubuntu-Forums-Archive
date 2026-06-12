---
title: "Putting laptop to sleep from command line"
date: 2006-06-08
forum: General Help
---

### Post by Hanj on 2006-06-08
After doing a fresh Dapper install on my laptop, suspend-to-ram *finally* seems to work! :D However, I would like to be able to suspend my comp from the command line (since I'm currently playing around with OpenBox), but I can't find out how to do this. I tried "sudo /etc/acpi/sleep.sh", but that had no effect. I also tried "acpitool -s" but that caused the screen to go blank and I couldn't restore the computer. So, what command is being run when I select "Suspend" from the Gnome logout menu.
Also, how can I make the computer suspend to ram when I close the lid?

---

### Post by Raoul Duke on 2006-06-08
Make sure ACPI_SLEEP is set to true in /etc/default/acpi-support
Also use the command /etc/acpi/sleep sleep
 to override gnome-power-manager policy

---

### Post by Hanj on 2006-06-08
Thanks for the reply. I enabled ACPI_SLEEP in /etc/default/acpi-support and tried "sudo /etc/acpi/sleep.sh sleep", but that just froze my terminal window, nothing else happened.

Since sleeping works from within Gnome, I would think that sleeping from the command line would be a simple matter of running some command? But then, I don't know much about how these things work...

---

### Post by Raoul Duke on 2006-06-08
I can't think of why your terminal window would hang. All I can say is that it works for me...sorry no more ideas.

Anyone else?

---

### Post by Hanj on 2006-06-08
I found out that running gnome-power-preferences will give me a battery icon in pypanel which I can click and select suspend, and that's good enough for me. Would still be cool to know how to do it from the command-line though.

---

