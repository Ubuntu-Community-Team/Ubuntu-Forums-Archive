---
title: "software center source not authenticated"
date: 2010-12-31
forum: General Help
---

### Post by chuzzle44 on 2010-12-31
I am using Ubuntu Netbook Edition installed inside Windows xp.  When I try to install programs from Ubuntu Software Center, I get a message telling me that the source is not authenticated. The installation ends when I click okay. I am not sure what the problem is.
Does anyone know how this can be fixed?  I am new to Linux and I appreciate any help.
Also, I was able to install several programs before this started happening.

---

### Post by Verbeck on 2010-12-31
open a terminal (listed under accessories) and enter[I] 
```
sudo apt-get update
```[/I]then try again

edit: do you have any other repositories added other than the default ones?

---

### Post by gdiloren on 2010-12-31
> **Verbeck said:**
> open a terminal (listed under accessories) and enter[I] 
```
sudo apt-get update
```[/I]then try again
I think that you should also enter:
sudo apt-get upgrade
to get it installed (you'll be asked to accept or want the changes y/n- type "y")

---

### Post by chuzzle44 on 2011-01-01
Thank you both! Software Center is working perfectly!
Verbeck: Sorry, I'm not sure what a repository is.
Thanks for taking the time to help a newb like me.  :-P

---

