---
title: "Dell Inspirion Mini"
date: 2009-12-12
forum: General Help
---

### Post by blur xc on 2009-12-12
Well, I did it.  I got my wife a Dell Mini for Chirstmas, and wiped the HDD (win 7 starter) and did a full clean install of karmic nbr.

I really should have done my homework on this one.  I assumed (yeah ***-u-me) that since Dell offered them w/ Ubuntu preinstalled that it would be a piece of cake, and it would go smoothly.  So far, I've got real slow, laggy, choppy 800x600 video and no wireless.  sudo apt-get doesn't work w/o a network connection.  So, my option is to wait until the house is empty and plug it into the router w/ a cat 5 cable, or what?

Should I be calling Dell for a restore cd or should I tough this out?  Will flash ever work properly?  This *is* a netbook, and primarily will be used to browse the web, flash based websites...

Thanks,
BM

---

### Post by gordintoronto on 2009-12-12
I hope you will get a response from someone who owns a similar netbook.  I *think* the computer is a little light on processing power for displaying flash well.

"Dell Inspiron Mini" could be one of several computers.  It might help to give the complete identification.  Then you could search the forums to see how other people have dealt with the wireless.

---

### Post by fooman on 2009-12-12
plug the ethernet in, run the following in a terminal and post the output back here:

```
lspci
```

---

### Post by blur xc on 2009-12-12
> **fooman said:**
> plug the ethernet in, run the following in a terminal and post the output back here:

```
lspci
```

I found a site that says that there's some bug w/ the way karmic identifies the broadcom wireless chip in that computer.  There instructions said the same, connect the ethernet, and do some apt-gets to install the driver properly.  

Since it is a surprise, I'll have to wait and take care of it when no one is around.

Thanks,
BM

---

