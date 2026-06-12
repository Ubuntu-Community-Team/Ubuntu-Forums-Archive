---
title: "Changing Hostname Not Working"
date: 2012-07-29
forum: General Help
---

### Post by omiazad on 2012-07-29
Hi,
I changed my computer's name with the following methods-
```
gksu gedit /etc/hostname
```
and
```
sudo hostname new_host_name
```

Now the terminal shows the new hostname, but when I sudo something, it says-
```
sudo: unable to resolve host new_host_name
```

Also when I paired my phone with the computer, it's showing the old name.

Can you please suggest a way to change the name universally?

---

### Post by ajgreeny on 2012-07-29
You need to edit both the /etc/hosts and /etc/hostname files for the change to be successful, I think, unless your hostname command, which I was unaware of does that in another way.

---

### Post by Cheesemill on 2012-07-29
+1

You need to edit /etc/hosts as well.

---

### Post by omiazad on 2012-07-29
Thanks. This fixed the _unable to resolve host_ problem but how to fix the Bluetooth hostname?

---

### Post by ajgreeny on 2012-07-30
> **omiazad said:**
> Thanks. This fixed the _unable to resolve host_ problem but how to fix the Bluetooth hostname?
Not a clue!  Sorry, but I have never had or used a bluetooth item of any sort, so do not know how to use it in Ubuntu.

---

### Post by omiazad on 2012-07-30
> **ajgreeny said:**
> Not a clue!  Sorry, but I have never had or used a bluetooth item of any sort, so do not know how to use it in Ubuntu.

No worries brother, you already helped a lot.

---

