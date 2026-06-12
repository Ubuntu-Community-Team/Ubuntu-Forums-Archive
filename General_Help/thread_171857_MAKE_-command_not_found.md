---
title: "MAKE -command not found"
date: 2006-05-07
forum: General Help
---

### Post by ofer_shm on 2006-05-07
hi... i just install  the abubtu and i try to run the command "MAKE" and i got a msg the the command not found
 anybody can help me to install this command

thanks

---

### Post by JoeMetal on 2006-05-07
Go to the Synaptics package manager and search for it.  Then install it. :)

---

### Post by Ptero-4 on 2006-05-07
Install build-essential.

---

### Post by tonyweb on 2006-05-07
apt-get install make

---

### Post by AndyCooll on 2006-05-07
You can just install the "make" package using Synaptic, better though is to install the build-essential package as this will install make plus a host of other packages that the make function will use. Copy and paste the following into a terminal

```
sudo apt-get install build-essential
```

:cool:

---

