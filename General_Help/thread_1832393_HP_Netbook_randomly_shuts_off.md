---
title: "HP Netbook randomly shuts off"
date: 2011-08-24
forum: General Help
---

### Post by Bioret on 2011-08-24
Hello.
It's been about a month with ubuntu 11.04 and I love it. However, I'm having some issues on my HP mini 110 netbook.

It will randomly shut off sometimes with no warning whatsoever.  It doesn't happen often, and in fact it has only happened 5 times.

Perhaps it might have something to do with overheating because I think it runs hotter than it did on windows.

If there's any logs or something I can post to help you help me let me know.

Thank you for reading.

---

### Post by win0922 on 2011-08-24
have you tried the BIOS; cause computers are usually programmed to shut off at a csertain tempreture so you could try by looking a phehaps changing a setting. :popcorn:

---

### Post by Bioret on 2011-08-24
The BIOS on this netbook is very limiting...apart from being able to view a 'diagnostic log' (which shows nothing) and the usual boot options and memory testing theres not much.  The only thing I don't know about that I could potentially change is something labeled as "Processor C4 state".

---

### Post by win0922 on 2011-08-24
It's a power setting in ACPI I think, and it's one of the higher power settings. Some people turn it off to get rid of the loud sound of fans running. Since that's an HP, I imagine you may be familiar with the "airplane noise" that some HP's make at full fan?

---

### Post by Bioret on 2011-08-26
Is the acpi power settings somethings I can change then?

No, actually i never hear the fans now; thats the problem.

---

### Post by win0922 on 2011-08-26
Go into the BIOS settings and look for ACPI settings and see if you can change anything. If it says that your fans are working on full powere I would advise you to have your laptop looked at to see if your fan has broken and if so have it replaced. this may be why your computer shuts off randomly.

---

### Post by win0922 on 2011-08-26
> **Bioret said:**
> The BIOS on this netbook is very limiting...apart from being able to view a 'diagnostic log' (which shows nothing) and the usual boot options and memory testing theres not much. The only thing I don't know about that I could potentially change is something labeled as "Processor C4 state".
 
 
Enter this and try.

---

### Post by Bioret on 2011-08-27
> **win0922 said:**
> Enter this and try.

Changing the "Processor C4 state" to disabled fixed it.

I can feel and hear the fan on now.
Thank you.

---

