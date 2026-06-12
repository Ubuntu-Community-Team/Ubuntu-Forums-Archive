---
title: "aptitude or apt-get?"
date: 2006-06-19
forum: General Help
---

### Post by lex1 on 2006-06-19
what is the general difference between installing and removing packages with apt-get or aptitude?


lex1

---

### Post by barbarian on 2006-06-19
Hi, I think aptitude is smarter with dependencies..

[here]("http://en.wikipedia.org/wiki/Aptitude_%28program%29")

:)

---

### Post by aysiu on 2006-06-19
Just paste these commands into the terminal, and you'll soon find out: ```
sudo aptitude update
sudo aptitude install kword
sudo aptitude remove kword
sudo apt-get update
sudo apt-get install kword
sudo apt-get remove kword
```

---

### Post by msak007 on 2006-06-19
Like barbarian said, aptitude remembers dependencies that are installed, and removes those along with the package when you uninstall it if they are no longer needed. If you run through the commands aysiu gave, you'll see that kword's dependencies are not uninstalled when you uninstall kword using apt-get instead of aptitude. I'm really surprised that Syanptic / Adept don't use aptitude by default, but I think I saw somewhere that this was a suggestion for Edgy. It really should be and I'd welcome that change.

---

### Post by lex1 on 2006-06-19
thanks for your posts

aysiu

yep i now use your sources list to, many thanks

lex1

---

### Post by Najand on 2006-06-19
If you want to compare package managers, better not to forget traditional dpkg and GUI Synaptic, too.

---

