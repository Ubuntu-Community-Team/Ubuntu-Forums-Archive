---
title: "cannot add programs"
date: 2009-12-13
forum: General Help
---

### Post by R3bellation on 2009-12-13
when i use the Add/Remove programs, and click on any field, it says there are 0 programs available. 

also, when i try using the terminal to download something (using the sudo command) this appears:

E: Type 'sudo' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.


any idea what's wrong?

---

### Post by staf0048 on 2009-12-13
Go into the terminal and type:

```
sudo gedit /etc/apt/sources.list
```

When your text document comes up, go down to the line the error is talking about (56) and remove any reference to sudo.  This should not be in your sources.list file.  

Save, close, and type:

```
sudo apt-get update
```

See if you are still getting the errors.  If you are, please go back to your sources.list and copy and paste into a reply so we can see exactly what's there.

---

### Post by R3bellation on 2009-12-13
that worked. thank you very much.

---

