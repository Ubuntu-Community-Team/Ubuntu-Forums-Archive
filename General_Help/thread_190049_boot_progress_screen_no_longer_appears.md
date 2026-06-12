---
title: "boot progress screen no longer appears"
date: 2006-06-05
forum: General Help
---

### Post by coldrick on 2006-06-05
After yesterday's  updates, my boot progress screen has disappeared. I get a blank screen on boot, and eventually it provides a text view.

Nothing obvious in dmesg, altho the first time it happened I saw some message referring to a failure wrt a "boot font" I think.

Any suggestions, either for tracking it down, or for re-installing whatever package might be involved?

Thanks and regards,
David

---

### Post by xXx 0wn3d xXx on 2006-06-05
[QUOTE=coldrick]After yesterday's  updates, my boot progress screen has disappeared. I get a blank screen on boot, and eventually it provides a text view.

Nothing obvious in dmesg, altho the first time it happened I saw some message referring to a failure wrt a "boot font" I think.

Any suggestions, either for tracking it down, or for re-installing whatever package might be involved?

Thanks and regards,
David[/QUOTE]
Try reinstalling usplash and see what happens.

---

### Post by coldrick on 2006-06-05
Nope, tried that: didn't change anything

---

### Post by coldrick on 2006-06-06
OK, found the error message from the boot: it's

```

set_kernel_font 
Invalid Argument

```

The grub menu.lst doesn't mention font anywhere.

Any ideas?

Regards,
David

---

