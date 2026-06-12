---
title: "Do I have to cmplile to enable battery ?"
date: 2006-04-08
forum: General Help
---

### Post by junglemike on 2006-04-08
Hi all.
I'm new linux user, and only starting to learn things. 
(but not afraid to read manuals and docs :-))
I have Kubuntu 5.04 installed on my work laptop, which specs are at the bottom. Kubuntu doesn't have any control over battery usage, screen brightness, and so on, When i   browse to "Power control" in "Control Center" - in all the tabs it says the following:
> Your computer seems to have a partial ACPI installation. ACPI was probably enabled, but some of the sub-options were not - you need to enable at least 'AC Adaptor' and 'Control Method Battery' and then rebuild your kernel.
Is it really as  bad as it sounds? Or maybe i'm just missing something simple. In case it really requires understanding of compiling and such (which i don't have) - could you redirect me to some document or howto where to start?

---

### Post by That Other Guy on 2006-04-08
It's probably not as bad as it sounds - that's just a generic KDE developer message, who doesn't know how your system is configured.  Assuming you're using the Ubuntu kernel that the installation gave you (which would be the case unless you've already re-compiled a kernel), that part is already taken care of.  When I got the same message on my laptop, it was because I had removed the ACPI packages and tried to use the APM packages instead.

I'm not sure what your level of familiarity with computers is, but ACPI and APM are both power management "systems", with unique software, hardware and BIOS requirements.  In the past, with other flavors of Linux, I couldn't get the features of ACPI to work reliably, even though Dell said my laptop was ACPI-compliant (it's a 5-year old Latitude, PIII 750MHz).  The APM system did work, though with not quite all the extra features ACPI offered.  When I recently installed Kubuntu, I tried to use APM but ran into the same error message as you.  I used Adept (the package management tool) to search for and reinstall the ACPI packages, and all was well again.  I ended up with acpi, acpi-support and acpid installed.  It seems that the Linux implementation of ACPI has improved in the last few years.

This is a long-winded suggestion, but hopefully gave a little more insight than just "install acpi."

Later, 

mike

---

### Post by junglemike on 2006-04-08
so you are saying that i can simply install it as another package? . Ok thanks, I will search for anything in Synaptic that has "acpi" in them.

---

### Post by That Other Guy on 2006-04-08
Yeah, just more packages.

---

