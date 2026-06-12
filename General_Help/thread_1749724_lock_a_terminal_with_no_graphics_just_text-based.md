---
title: "lock a terminal with no graphics just text-based"
date: 2011-05-04
forum: General Help
---

### Post by leegold on 2011-05-04
Hi,

I have a ubuntu server PC with no xwindows just text command-line. Usually I use xlock but this PC has no graphics. How do I lock/unlock the PC while I'm away from it? I don't necessarily need a screen saver just a way to secure the terminal while I'm away without logging off.

Thanks,

Lee G.

---

### Post by lmarmisa on 2011-05-04
I recommend to use the command **away**.

Type this command to install it:

```

sudo apt-get install away

```

This is an example of use:

```

luis@UB1010ENG:~$ away -C lock

       You went away at 02:34:47

 -- Press [Enter] to come back online --

Password: 


```

---

