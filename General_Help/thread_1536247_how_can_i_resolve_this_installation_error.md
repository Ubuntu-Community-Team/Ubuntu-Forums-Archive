---
title: "how can i resolve this installation error?"
date: 2010-07-21
forum: General Help
---

### Post by itsjoshgrant on 2010-07-21
ok i just installed codeblocks ide (trying to reach my self programing) so i went 
to the software center and went to get the gnu c++ complier and i got the following message...

what can i do to resolve this?
thanks

---

### Post by Rubi1200 on 2010-07-21
Try this first and see what happens, in other words if there are error messages and the like:

```
sudo dpkg --configure -a
```

If all goes well, you should then be able to install/reinstall the programs/packages you need.

---

### Post by itsjoshgrant on 2010-07-21
> **Rubi1200 said:**
> Try this first and see what happens, in other words if there are error messages and the like:

```
sudo dpkg --configure -a
```

If all goes well, you should then be able to install/reinstall the programs/packages you need.

i put above code in the terminal then went to software center to get it again and got the following message...

"E:I wasn't able to locate a file for the libstdc++6-4.4-dev package. This might mean you need to manually fix this package. (due to missing arch): "

---

### Post by Rubi1200 on 2010-07-21
Did you try reinstalling codeblocks?

---

### Post by itsjoshgrant on 2010-07-21
> **Rubi1200 said:**
> Did you try reinstalling codeblocks?

no but its solved now
it appeared in update manager randomly and it ended up saying "g++ complier package is broken" and it removed the package and i was able to install it again! :D

thanks for the help!

---

### Post by Rubi1200 on 2010-07-22
Glad to hear things worked out for you.

:)

---

