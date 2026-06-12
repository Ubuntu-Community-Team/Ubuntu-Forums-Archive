---
title: "How do I download a git repository?"
date: 2010-07-18
forum: General Help
---

### Post by Mr_VeRiTy on 2010-07-18
Hi, I'm trying to install the Atlantis compiz plugin, but it says that I need to download it from git, I was just wondering how I might do that. I managed to navigate myself to [http://gitweb.compiz.org/?p=compiz/plugins/atlantis;a=summary]("http://gitweb.compiz.org/?p=compiz/plugins/atlantis;a=summary") but thats about it.

---

### Post by Vaphell on 2010-07-18
1. install git - **sudo apt-get install git-core**
2. create a dir for git stuff
3. go to that dir in terminal and run **git clone git://anongit.compiz.org/compiz/plugins/atlantis** or whatever repository you want to get from that list -> [http://cgit.compiz.org/](http://cgit.compiz.org/) (git address is at the bottom of a page with details)
4. go to freshly created sub-directory and follow the instructions in README file

---

### Post by Mr_VeRiTy on 2010-07-19
> **Vaphell said:**
> 1. install git - **sudo apt-get install git-core**
2. create a dir for git stuff
3. go to that dir in terminal and run **git clone git://anongit.compiz.org/compiz/plugins/atlantis** or whatever repository you want to get from that list -> [http://cgit.compiz.org/](http://cgit.compiz.org/) (git address is at the bottom of a page with details)
4. go to freshly created sub-directory and follow the instructions in README file
Thanks, I tried using the http:// url instead of git://.

---

