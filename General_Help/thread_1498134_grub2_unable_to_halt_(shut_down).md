---
title: "grub2 unable to halt (shut down)"
date: 2010-05-31
forum: General Help
---

### Post by quigybo on 2010-05-31
I am trying to add an entry to grub2 to turn the computer off using the 'halt' command, but grub2 freezes and I have to manually reboot. 

I have tried both 'halt' and 'halt --no-apm', both with and without 'insmod halt' first. The 'reboot' command however works fine (even without 'insmod reboot') so it doesnt seem to be an acpi/apm issue. This was all tested at grub2's command line, so there isnt any problems with syntax in the config file. 

The laptop I am trying this on is an Acer Aspire One, I am using Ubuntu Netbook Edition 10.04 (Lucid), and a more or less default config for grub2 (GNU GRUB 1.98-1ubuntu6) as far as modules are concerned.

Is anybody having similar issues, or has an Acer Aspire One to test this on? Any suggestions? Thanks.

---

### Post by quigybo on 2010-06-06
<bump> any suggestions? </bump>

---

### Post by KhurramM on 2012-01-03
This might help someone:

**edit:**
/etc/grub.d/40_custom

**Add following entries (only change if you know what you are doing):**

menuentry 'System shutdown' {
	halt
	echo	'System shut down initiated ...'
}

menuentry 'System restart' {
	reboot
	echo	'System rebooting initiated ...'
}


**run:**
update-grub

---

