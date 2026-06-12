---
title: "Prevent the computer from hibernate"
date: 2006-03-23
forum: General Help
---

### Post by tronsmo on 2006-03-23
I run Ubuntu Breezy Badger on my laptop.

Problem is that theres has been trouble waking up my computer after going to sleep. So what I want is to shut this function off. Is this possible?

:confused:

---

### Post by nanotube on 2006-03-23
edit this file:
/etc/default/acpi-support
and put "false" instead of "true" in the first two non-comment lines:
# Uncomment the next line to enable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true
that should disable sleep and hibernate.

---

### Post by tronsmo on 2006-03-23
Thanks a lot. I`ve done what you said. No I`ll just have to see if it worked.

---

### Post by rayburn on 2006-03-23
Thanks for that tip, I didn't know such a file existed!

---

### Post by cab1024 on 2006-03-23
How about the opposite? I have an old energy hungry box. I can't find anyway to put it to sleep. If I select Log Out --> Hibernate, it seems like it goes through the process of shutting down. And even so, I can't find a way to have it Hibernate on its own, just turn off the display. But does that really save power if the monitor is plugged into the wall rather than the back of the computer?

My experience has been that to wake it from Hibernation takes just as long (if it is not actually the same process) as booting up. So why not just use Shut Down with Save State checked?

---

