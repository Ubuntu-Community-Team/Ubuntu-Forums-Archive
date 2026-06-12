---
title: "Opening A Port"
date: 2006-04-15
forum: General Help
---

### Post by Harold P on 2006-04-15
Okay, I need some help, and it's a pretty straight-forward question:

How do I open a port?

I've searched the forums and have found nothing:
[http://ubuntuforums.org/search.php?searchid=4873548](http://ubuntuforums.org/search.php?searchid=4873548)

Thanks in advance,
Harold

---

### Post by gibson on 2006-04-15
Easiest way.... 

> sudo apt-get install firestarter

then

> gksudo firestarter

and then you will get an intuitive interface for firewall configs in your system tray area thingy...

hope this helps :)

---

### Post by Harold P on 2006-04-15
[QUOTE=gibson]Easiest way.... 



then



and then you will get an intuitive interface for firewall configs in your system tray area thingy...

hope this helps :)[/QUOTE]

Oh gosh! I just installed the new kernel. It doesn't support iptables. Guess I'll boot into the old kernel then...

Thanks,
Harold

---

### Post by gibson on 2006-04-15
Which kernel is that?

im on 2.6.12-10-686-smp and all seems to be fine.

If the kernel does not suppport iptables then arent all the port open by definition?

Sorry, i dont mean to sound dumb, but i know very very little about networking

thanks

---

