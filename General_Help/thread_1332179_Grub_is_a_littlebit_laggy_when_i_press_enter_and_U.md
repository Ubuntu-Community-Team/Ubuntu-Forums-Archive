---
title: "Grub is a littlebit laggy when i press enter and Usplash changes resolution"
date: 2009-11-20
forum: General Help
---

### Post by AlexZaim on 2009-11-20
Hello.

My problem is that when i press enter on the selected os i want to boot, it doesn't switch right away like it used to in 9.04's GRUB. I am using the grub from 9.10 now,clean install. That 1-2 second lag bothers me a little bit. Is there a way to change that?

And after a while, before switching to usplash, it says that usplash couldn't configure a certain resolution so it switches to another(1024x768). Can i make that one as a default, so it won't change it all the time?

---

### Post by atropa on 2009-11-20
After I put a # in front of the option
GRUB_CMDLINE_LINUX=" splash vga=769" in /etc/default/grub,
because grub complained while bootup about "...deprecated option vga=769...",
I now have the same problem.

Though I could get rid of that vga complaint.

---

