---
title: "is there anything that can be used instead of network manager?"
date: 2009-09-04
forum: General Help
---

### Post by chriskin on 2009-09-04
Network manager, or at least mine, is WAY too buggy for my taste. it gets me offline every now and then, stops wireless when it likes, it doesn't show all wireless routers around me until minutes have passed etc etc. Now, for example, it is sure that i am not online :) --(perhaps i have spent too much time close to the router and i can connect myself wirelessly, no PC required? or is it just buggy?)

is there anything else i can use instead of it?

---

### Post by hessiess on 2009-09-04
wicd

---

### Post by chriskin on 2009-09-04
> **hessiess said:**
> wicd

this one seems to understand the art of being online

thank you :) 

does it keep the passwords of other networks i have been connected to, though? if so, how can i see them?

---

### Post by speedwell68 on 2009-09-04
> **hessiess said:**
> wicd


^^^QFT.  It knocks the socks off of network-manager.  WiCD is in the Jaunty repositories.  IIRC it also has it's own repository.

If you do the following in the Terminal it will remove the existing network-manager and replace it with WiCD.

```
sudo apt-get install wicd
```

:D

---

### Post by chriskin on 2009-09-04
> **speedwell68 said:**
> ^^^QFT.  It knocks the socks off of network-manager.  WiCD is in the Jaunty repositories.  IIRC it also has it's own repository.

If you do the following in the Terminal it will remove the existing network-manager and replace it with WiCD.

```
sudo apt-get install wicd
```

:D

already did, that's why i said that it can find my network

what i need to know now is if it has the choice network-manager has to autoconnect to different connections depending on where you are

---

### Post by &#32 Greg on 2009-09-04
Yes, it does. When you click on the line with the name, you get more options for the network (at least I think the line with the name).

---

### Post by chriskin on 2009-09-04
> **  Greg said:**
> Yes, it does. When you click on the line with the name, you get more options for the network (at least I think the line with the name).

i haven't seen the arrow next to the name
thank you :)

would you know where it keeps it's history as well? in case i have forgotten any password and want to connect from another laptop?

---

### Post by dawnlove on 2009-09-04
I also could not get WiCD to work with 9.04. The WiCD forms are full of problems with 9.04 and no real fixes. If there is a fix I would like to know about it.
> **speedwell68 said:**
> ^^^QFT.  It knocks the socks off of network-manager.  WiCD is in the Jaunty repositories.  IIRC it also has it's own repository.

If you do the following in the Terminal it will remove the existing network-manager and replace it with WiCD.

```
sudo apt-get install wicd
```

:D

---

### Post by The Cog on 2009-09-04
> **chriskin said:**
> would you know where it keeps it's history as well? in case i have forgotten any password and want to connect from another laptop?

/etc/wicd

---

