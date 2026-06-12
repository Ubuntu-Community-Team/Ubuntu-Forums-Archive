---
title: "update manager problem"
date: 2009-08-14
forum: General Help
---

### Post by Inspector Gadget on 2009-08-14
unable to run update manager and get this

E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

any help?

---

### Post by ubudog on 2009-08-14
I am not sure if this will work, but we can try.  Open a terminal(Applications>Accessories>Terminal) and type ```
sudo apt-get update
```   Then try.  Hope that helps. :P

---

### Post by Soul-Sing on 2009-08-14
```
sudo rm /var/lib/apt/lists/* -vf
```
```
sudo apt-get update
```

---

### Post by Inspector Gadget on 2009-08-14
Thank you very much guys

now sorted...:)

until we meet again

stay lucky...

---

### Post by ubudog on 2009-08-14
> **Inspector Gadget said:**
> Thank you very much guys

now sorted...:)

until we meet again

stay lucky...

You are welcome.  :P

---

