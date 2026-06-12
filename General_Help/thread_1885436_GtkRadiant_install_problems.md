---
title: "GtkRadiant install problems"
date: 2011-11-23
forum: General Help
---

### Post by cazazo on 2011-11-23
I'm trying to install the **GtkRadiant** by referring to this link: [http://openarena.wikia.com/wiki/Configure_GTK_Radiant_under_Linux]("http://openarena.wikia.com/wiki/Configure_GTK_Radiant_under_Linux")
I managed to go up to the "**build**" step. But when I execute the **install** command (python ./GtkRadiant/install.py) the message I get at the terminal is: *usage: install [target directory] [source directory]*

I don't quite know what to do here... Any help?:confused:
Ps. I'm using the Ubuntu 10.10 32bits

Thank you!

---

### Post by gordintoronto on 2011-11-23
You don't understand what target directory and source directory mean?

This might work: just once, issue this command: mkdir rad

Then:
python ./GtkRadiant/install.py ./rad ./GtkRadiant

The package will be installed in the directory rad.

---

### Post by cazazo on 2011-11-24
> **gordintoronto said:**
> You don't understand what target directory and source directory mean? 

Well in fact I do understand, my apologies for the misunderstood... I did provided the names for the folders, but still did not work. Thank you for your reply!

I've found a solution by searching Google! Thank you for the help.

---

### Post by gordintoronto on 2011-11-25
What was the solution?

---

### Post by cazazo on 2011-11-26
> **gordintoronto said:**
> What was the solution?

Sorry guys just to give you a following up... I did end up using the [Net Radiant]("http://dev.alientrap.org/wiki/7") a fork of the Gtkradiant, which is heaps easier to install and configure and still under development/improvement which is not the case with the GtkRadiand. It's base still is the version 1.5 of the GTKRadiant, and at their web site you can find all the downloads you need for it! Enjoy it!! Thanks for the Help!

---

