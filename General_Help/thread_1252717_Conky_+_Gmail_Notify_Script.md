---
title: "Conky + Gmail Notify Script"
date: 2009-08-29
forum: General Help
---

### Post by N_Nick on 2009-08-29
I'm looking for a way to call Conky and Gmail Notify X seconds after system startup so i don't get Conky RSS errors until my Internet connection is up and running.

What's the best way to do that?

Thanks

---

### Post by N_Nick on 2009-08-29
Anyone?

Can i do it with cron? Or is cron just for specific day/time?

---

### Post by sagara on 2011-06-04
You can achieve this in two steps:
[LIST=1]
[*]Create a script that launches conky and gmail notify for you.  The script will wait 10 seconds before launching the two programs. 
[*]Set the script to run on startup once you boot/log into ubuntu
[/LIST]

If you need more detailed instructions let me know and I will be glad to help.

---

