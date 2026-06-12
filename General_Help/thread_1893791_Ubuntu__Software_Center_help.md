---
title: "Ubuntu  Software Center help?"
date: 2011-12-11
forum: General Help
---

### Post by MyUbuntoo on 2011-12-11
My Ubuntu Software Center is being really weird. Same with my Synaptic PackageManager. What happens is I open the programs, and after 5 seconds or so, They close down with no warning...Anybody know whats happening here? I could really use the help.:(

---

### Post by BC59 on 2011-12-11
Do you remember what tricks you tried ultimately? I had a similar problem when I tried to install the Mate desktop of LinuxMint.

---

### Post by MyUbuntoo on 2011-12-11
All i know is one day I got on my computer, opened USC, Only to find out its "Broken". It was working fine before.

---

### Post by BC59 on 2011-12-11
Ok then, open a terminal with CTRL+ALT+T and run the commands:

first 

```
sudo dpkg --configure -a
```

and then

```
sudo apt-get -f install
```

If you notice a problem, post it here.

---

