---
title: "dual boot message"
date: 2010-07-11
forum: General Help
---

### Post by mrdusty on 2010-07-11
[SIZE=3]I pulled a swift one! I used wubi to install ubuntu inside windows 7. All worked well. Then, days later in a moment of ignorance, looking at c:// I noticed ubuntu . Dumb me, I deleted the folder.
Still get the dual boot at start up, but errors when click on ubuntu (naturally!).
How can I get rid of that boot start up?
I reinstalled ubuntu with wubi, hoping that I'd get the file then I could delete it that way.
Got two ubuntu's to boot from.
Can't find wubi1dr.mbr on drive any where.
Thanks,
Rich[/SIZE]

---

### Post by garvinrick4 on 2010-07-11
In windows go to command line and 
```
bcdedit
```

You can find the wubilder in the boot manager and delete:
Use your own {number}

```
bcdedit delete {8kefuss87gg0ssll}
```

---

### Post by mrdusty on 2010-07-12
Thanks.  In trying to follow your instructions, I did a search for bcdedit.exe (didn't know about before)
I found a program called easybcd downloaded it and edited the file easily.  All is back to 
normal now. 
No more messing around until I'm off my pain meds for broken shoulder and can type with both hands!!!

---

