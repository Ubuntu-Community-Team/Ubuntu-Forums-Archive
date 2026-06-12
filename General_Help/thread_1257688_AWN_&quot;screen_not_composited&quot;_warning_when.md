---
title: "AWN &quot;screen not composited&quot; warning when shutting down"
date: 2009-09-04
forum: General Help
---

### Post by Thanh-BKK on 2009-09-04
(SOLVED)

Hello.

Ever since i installed Jaunty 9.04 on my machine last week i have a small but annoying issue. Every time when i shut down the machine i get a warning popup that say something about the screen not being composited and i should please run a compositing manager or some such. This only stays for about a second but comes along with one or several beeps from the system speaker.

Now i KNOW it is caused by AWN and i guess it happens because Compiz is shut down before AWN itself. So is there a way to tell Ubuntu to shut down AWN first and then the rest..?

Appreciate any advice..... thanks in advance :)

Thanh

---

### Post by CatKiller on 2009-09-04
Alt-F2 &#8594; gconf-editor &#8594; /apps/avant-window-navigator/show_dialog_if_non_composited

Uncheck it.

---

### Post by Thanh-BKK on 2009-09-04
Hi.

Thank you very much - will try that as soon as i am back at home and report if it worked :)

Kind regards.....

Thanh

---

### Post by Thanh-BKK on 2009-09-04
Hi.

Yup that did the trick - once again many many thanks for finding the solution for me :)

Kind regards.....

Thanh

---

