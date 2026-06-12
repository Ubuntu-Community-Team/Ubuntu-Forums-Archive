---
title: "How to download &amp; install g++ in Ubuntu 9.04?"
date: 2009-07-16
forum: General Help
---

### Post by sreejithbabu on 2009-07-16
I have downloaded  *g++-3.4_3.4.6-1ubuntu2_i386.deb*  &  *g++_4.3.3-1ubuntu1_i386.deb* from the net.
When I doubled clicked this in Ubuntu, and selected install package they are showing errors like 
   [B]Error: Dependency is not satisfiable: gcc-3.4-base (= 3.4.6-1ubuntu2)
   Error: Dependency is not satisfiable: g++-4.3 (>= 4.3.3-1)[/B]
for each of them respectively.
Are these downloaded packages correct or did I use the wrong way to install them?
I want to know how install g++ in Ubuntu.

---

### Post by michy99 on 2009-07-16
The easiest way to install g++ is through the repositories. In fact, you can install g++ and everything else needed for compiling by installing the build-essential package.```
sudo apt-get install build-essential
```

---

### Post by sreejithbabu on 2009-07-16
Should I need to download the build-essential package separately or is it already present in Ubuntu?
If not present where to download the build-essential package?

---

### Post by michy99 on 2009-07-16
You do not usually need to download packages from a website. Click on System->Administration->Synaptic Package Manager. Search for whatever software you want. Mark to install and click 'Apply'. You can also install from the terminal using apt-get like in the reply above. Please read this page about installing software:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

