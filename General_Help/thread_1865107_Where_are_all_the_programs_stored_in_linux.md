---
title: "Where are all the programs stored in linux?"
date: 2011-10-19
forum: General Help
---

### Post by olain on 2011-10-19
Where are all the programs stored in linux?

---

### Post by d.atanasov on 2011-10-19
> **olain said:**
> Where are all the programs stored in linux?

If you mean by this where are the software folders there are here:

/etc/

If you need all the executable scripts they are located in this folder 

/usr/bin/

regards

---

### Post by gsmanners on 2011-10-19
I'd take a look in /usr/share/applications <-- that gives you another idea what you have installed. As for where they put their files, you can discover that for yourself using:

```
dpkg -L whatever
``` (where whatever is the name of the package)

---

### Post by olain on 2011-10-19
No I mean the packages.

---

### Post by d.atanasov on 2011-10-19
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

this may be useful to you. 

"
Locating software on your system Synaptic  can tell you about every file that belongs to a software package it  knows about and show you where it is located on your system. Search the  database for the software package you are interested in and select it in  Synaptic's main window. Next, click on the *Installed Files* tab to see a list of all files and where they are."

---

### Post by oldos2er on 2011-10-19
Packages are stored in /var/cache/apt/archives

---

