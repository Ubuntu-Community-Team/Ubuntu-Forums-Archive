---
title: "Problems with connecting to the internet"
date: 2006-03-25
forum: General Help
---

### Post by pango on 2006-03-25
Hi,
I quite recently moved from Fedora 4 to Ubuntu, and I am having some problems connecting to the internet.
Because of the modem that I have, I am unable to find any Linux drivers for it and so I need to use [EciADSL](http://eciadsl.flashtux.org).
EciADSL requires a C compiler to be installed, but I can't seem to be able to install one without connecting to the internet. Does anyone have any ideas on how I can connect to the internet?

Thanks.

---

### Post by pango on 2006-03-25
Sorry for the major bump, but I would really like to be able to use Ubuntu. Can anyone help me?

---

### Post by pango on 2006-03-25
I guess no one is going to reply to this.

---

### Post by Lifman on 2006-03-26
well, i am a newbie as you are, but i think you should look into welsh_spud's guide. it almost helped me...
search the forums for "eciadsl install" or something like that.

---

### Post by cjazz on 2006-03-26
You should be able to install gcc, which is the GNU C Compiler, by installing the package build-essential from your install CD, either through Synaptic or by entering the line "apt-get install build-essential" at a terminal.

---

