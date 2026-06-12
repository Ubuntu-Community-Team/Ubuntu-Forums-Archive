---
title: "Wine Apps starting up really slow"
date: 2010-05-22
forum: General Help
---

### Post by stukpixel on 2010-05-22
I did a fresh install of wine (beta from ubuntu software center) on ubuntu (10.04)

However the apps take 5 minutes or so to start up.

Can anyone help?

---

### Post by ssj6akshat on 2010-05-22
run wine from Terminal and post the output here.

---

### Post by stukpixel on 2010-05-22
user@user-laptop:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
user@user-laptop:~$ wine notepad
err:process:__wine_kernel_init boot event wait timed out
user@user-laptop:~$ wine notepad
err:process:__wine_kernel_init boot event wait timed out

did it twice to confirm, all apps take 5 minutes to boot up, one doesn't start at all.

---

### Post by stukpixel on 2010-05-22
I am running a core 2 duo process at 2.00 ghz btw

---

### Post by ca0ca0 on 2010-05-24
I also had this problem. I'll recomend you to delete ~/.wine. Than try to start applications. In my situation it solved problem.

---

### Post by stukpixel on 2010-05-25
thanks ca0ca0 that worked :)

---

### Post by ssj6akshat on 2010-05-27
> **stukpixel said:**
> thanks ca0ca0 that worked :)

Then mark this thread as solved.

---

