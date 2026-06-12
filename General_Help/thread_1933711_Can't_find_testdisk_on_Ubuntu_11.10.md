---
title: "Can't find testdisk on Ubuntu 11.10"
date: 2012-02-29
forum: General Help
---

### Post by DMMR87 on 2012-02-29
i'm using ubuntu 11.10 from a flash drive. i can't find testdisk, photorec, etc from the software center or terminal

---

### Post by imachavel on 2012-02-29
Can you just try downloading it????? Then install throu the terminal. Sudo apt-get install (application name)

Great thing about Linux, the repository has like a thousand free apps, and you download another thousand free apps if you want. Also thunderbird and evolution local mail client. Make sure you know your outgoing and incoming, I mean Smtp and pop or smtp and imap. Skype is great and works great in Linux. Sorry don't mean to get so off topic. I love this OS. It's friggin free what more could you want. Is it a pain to configure??? Sure, but so is windows, at least you don't have to pay for activation keys:popcorn:

---

### Post by jerome1232 on 2012-02-29
> **DMMR87 said:**
> i'm using ubuntu 11.10 from a flash drive. i can't find testdisk, photorec, etc from the software center or terminal

First make sure universe is enabled.

Click on the icon in the top right of your screen, click system settings, click software sources, make sure "Community-maintained Open Source Software(universe)" is checked.

Now open your dash, search for synaptic, open synaptic and type your password, click reload, search for testdisk, check the check box and click apply.

Once testdisk is installed it is ran from a terminal, it does use a ncurses gui so it's not all commandline.

---

### Post by DMMR87 on 2012-03-01
> **jerome1232 said:**
> First make sure universe is enabled.
 
Click on the icon in the top right of your screen, click system settings, click software sources, make sure "Community-maintained Open Source Software(universe)" is checked.
 
Now open your dash, search for synaptic, open synaptic and type your password, click reload, search for testdisk, check the check box and click apply.
 
Once testdisk is installed it is ran from a terminal, it does use a ncurses gui so it's not all commandline.
 
 
Thanks! Got it to work!

---

