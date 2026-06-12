---
title: "Jaunty Freezes when Image Loaded in Gimp"
date: 2009-07-24
forum: General Help
---

### Post by moldy on 2009-07-24
Hi all - as the title suggests, I have just installed Jaunty on my Samsung NC20 netbook, and everything works pretty well (or as well as I expected it to).

I don't have the random Jaunty freezes that others have been reporting.  But when I open any image in Gimp, the whole system halts.  I cannot even use ctrl-alt-f1 to get to the text screen.

I have not managed to make Gimp freeze without an image, and I have not had any other freeze outside of Gimp.

Any ideas what the issue is?  I would really like to be using Gimp to avoid Windows (although I rarely have an issue in Windows).

Moldy

---

### Post by pbotros1234 on 2009-07-25
Maybe it's not updated, and the bug has been corrected? Open up a terminal and type:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

See if updating helps.

---

### Post by moldy on 2009-07-26
> **pbotros1234 said:**
> Maybe it's not updated, and the bug has been corrected? Open up a terminal and type:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

See if updating helps.

Hey mate - thanks for the reply - unfortunately I'm fully updated. And this keeps happening.  I simply can't use Gimp.  Perhaps it is incompatible with my computer?

---

### Post by DeMus on 2009-07-26
> **moldy said:**
> Hi all - as the title suggests, I have just installed Jaunty on my Samsung NC20 netbook, and everything works pretty well (or as well as I expected it to).

I don't have the random Jaunty freezes that others have been reporting.  But when I open any image in Gimp, the whole system halts.  I cannot even use ctrl-alt-f1 to get to the text screen.

I have not managed to make Gimp freeze without an image, and I have not had any other freeze outside of Gimp.

Any ideas what the issue is?  I would really like to be using Gimp to avoid Windows (although I rarely have an issue in Windows).

Moldy

It should not happen like this but you could consider to un-install The Gimp and after a reboot install it again. See how it goes.

---

### Post by moldy on 2009-07-26
> **DeMus said:**
> It should not happen like this but you could consider to un-install The Gimp and after a reboot install it again. See how it goes.

Thanks DeMus - I will try your idea and see how I go.  

I was also wondering whether it might be my hardware.  The Samsung NC20 is a fairly new netbook - and was wondering whether there might be some issue with my graphics card or something?  But I don't have the techno-smarts to know!

---

### Post by moldy on 2009-08-03
Same result unfortunately.  I can't manage to open even a blank document without the whole system freezing solid.  I can reproduce this every time.

It surely must have something to do with my computer?

---

