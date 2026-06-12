---
title: "Can't turn on Personal file sharing"
date: 2010-04-25
forum: General Help
---

### Post by joelw135 on 2010-04-25
I am running Ubuntu 10.4 and I am unable to turn on Personal file sharing. The error I get is that required files are not installed. I need to know how to correct this as I am stuck. Thanks.

---

### Post by Ozpilot on 2010-04-25
Installing the apache2 package worked for me.

---

### Post by AlanR8 on 2010-04-25
Found this elsewhere in these forums and it just worked:

> sudo apt-get install apache2.2-bin libapache2-mod-dnssd

---

### Post by joelw135 on 2010-04-25
> **AlanR8 said:**
> Found this elsewhere in these forums and it just worked:
Thanks that worked for one problem, now I have another.
When I click on network I get the following error.
Nautilus could not handle network locations. Any ideas on this?

---

### Post by mcoleman44 on 2010-04-25
Did you try 
```
shares-admin
```

---

### Post by joelw135 on 2010-04-25
> **mcoleman44 said:**
> Did you try 
```
shares-admin
```

Tried that it said it was installing but nothing happened. Do I need to do something else?

---

### Post by Morbius1 on 2010-04-25
sudo apt-get install gvfs-backends

---

### Post by joelw135 on 2010-04-25
> **Morbius1 said:**
> sudo apt-get install gvfs-backends

Thank you that did the trick, have no idea why the upgrade to 10.4 screwed everything up.

---

### Post by non-prophet on 2010-05-01
I have same problem but that solution did not work for me as Synaptic says that gvfs-backends is already Active. 
Any other clues anyone?
Thanks.

Arrghh. I didn't see the Apache suggestion. I tried that and BINGO it works. 

Thanks for the postings. Very helpful.

---

