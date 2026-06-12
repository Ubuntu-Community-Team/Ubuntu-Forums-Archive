---
title: "Startup Manager Issue"
date: 2011-06-01
forum: General Help
---

### Post by nikRbokR on 2011-06-01
I upgraded to 11.04, and as a result it looks like the GRUB files were modified (even though I thought there was an option to leave those files be, but oh well).

Now, using Start-up Manager, I'd like to put Windows 7 as my default OS (with the normal 10 second timer). In the manager, I've actually set it to timeout in 10 seconds and default boot into Windows 7... but upon booting up it actually just sits in the boot menu (with no timer) and rests on the 1st entry (Ubuntu).

After upgrading, my default actually changed to mem-check. In this case, the timer was working. Only after I made the change myself did it stop working.

Any help would be appreciated. It's just a little bit annoying that this doesn't seem to work.

---

### Post by garvinrick4 on 2011-06-01
Did you sudo update-grub:
I believe when you change grub default have to do so.

---

### Post by drs305 on 2011-06-01
There were some major changes with Grub 1.99 (Natty). A better GUI tool is probably Grub Customizer. The creator has been on top of Grub 2. There are a couple of G2 changes in Natty he hasn't completed yet but it's a much better app for G2 than StartUp-Manager.

Check out the 'Customizer' link in my signature line. If it doesn't work for you we can work on your issues here.

---

### Post by nikRbokR on 2011-06-01
> **garvinrick4 said:**
> Did you sudo update-grub:
I believe when you change grub default have to do so.

I tried this first. The timer works now, but it's also now defaulted to Ubuntu, regardless of what Startup Manager says.

Also, now my Restart doesn't work. It just hangs up. D#@!~ Ubuntu.

I'll try the other utility next.

---

### Post by nikRbokR on 2011-06-01
I had a question about Grub Customizer actually.

There are a couple of check boxes at the bottom that say "custom -> new Entries". These obviously don't show up if they're empty, but nothing should go wrong if I uncheck them right?

---

### Post by drs305 on 2011-06-01
> **nikRbokR said:**
> I had a question about Grub Customizer actually.

There are a couple of check boxes at the bottom that say "custom -> new Entries". These obviously don't show up if they're empty, but nothing should go wrong if I uncheck them right?

I believe the "New entries" block you are referring to is to prevent additional entries from being automatically added in the future. If it's in the Custom (i.e.40_custom or 41_custom), it probably removes the executable bit from those files. So no, it won't hurt anything.

---

### Post by grahammechanical on 2011-06-01
Please do not be offensive. It puts me off from offering help. I appreciate the OS I am using and all the effort that has gone into producing it and the programs I use on it. We all have a choice of whether to use it or not so there is no need to be insulting.

Regards.

---

