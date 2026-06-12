---
title: "Left over programs in startup applications list"
date: 2011-01-09
forum: General Help
---

### Post by oldskool on 2011-01-09
Hello, 

I noticed that some applications are still in the startup applications list even after i have removed these applications. 

Would there be any app files left over anywhere / is there a command i can run to clean up the filesystem. 

Or is it just a case of removing them from the startup app list? 


Thanks,

---

### Post by TeoBigusGeekus on 2011-01-09
> **oldskool said:**
> ...Or is it just a case of removing them from the startup app list?Thanks,
^ This.
The entries in startup applications are just scripts that run whenever you log in.
You're right that gnome should try and clean them up after you run apt, but I think it's safer this way.

---

### Post by Krytarik on 2011-01-09
There may be some entries left in the Startup Applications if respective *.desktop-files are stored in your home folder, check in "~/.config/autostart".

---

### Post by oldskool on 2011-01-09
Thanks v.much guys

---

