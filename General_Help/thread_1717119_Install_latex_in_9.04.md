---
title: "Install latex in 9.04"
date: 2011-03-29
forum: General Help
---

### Post by arun ganesh on 2011-03-29
Hi all,
I've ubuntu 9.04..I want to insall the latex package how should i do??
i tried sudo apt-get install latex-beamer
"E: Couldn't find package latex-beamer"
please help me out!!!

---

### Post by Chronon on 2011-03-29
You want the Texlive packages:
> apt-cache search texlive

---

### Post by arun ganesh on 2011-03-30
> **Chronon said:**
> You want the Texlive packages:
Thanks and how to install Vim editor....well i have worked in ubuntu 10.10,10.04 there when i need any packages i type
sudo apt-get install vim
but due to some reasons i had to switch back to Ubuntu 9.04 and i find it difficult to install any packages.....

---

### Post by Chronon on 2011-03-30
If you do 
```
apt-cache search vim
```
it should tell you all packages with name (or description) containing that string.  Alternatively, you can use a graphical package manager like Synaptic or the Software Center.

---

### Post by oldos2er on 2011-03-30
9.04 is no longer supported. You can try the old release repositories: [http://atlanticlinux.ie/blog/?p=143](http://atlanticlinux.ie/blog/?p=143)

---

### Post by 3Miro on 2011-03-30
> **oldos2er said:**
> 9.04 is no longer supported. You can try the old release repositories: [http://atlanticlinux.ie/blog/?p=143](http://atlanticlinux.ie/blog/?p=143)

+1. Upgrade to a newer version.

---

