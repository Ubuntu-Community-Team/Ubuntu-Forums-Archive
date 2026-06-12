---
title: "Installing software from getdeb (apturl) in 9.10"
date: 2010-04-30
forum: General Help
---

### Post by beastrace91 on 2010-04-30
I am trying to install "MyPaint" from getdeb.net but instead of just providing .deb downloads like they used to they now are using this goofy apturl that my firefox seems to have no idea what to do with. At first it told me "no protocol associated with apt" but a bit of googling told me to install the apturl package - now instead of telling me it can't do anything when I click install it runs what appears to be apt-get update through synaptic before telling me it cannot find the "mypaint" package... Anyone know how I install this package through getdeb?

Regards,
~Jeff

---

### Post by nzso on 2010-04-30
> **beastrace91 said:**
> I am trying to install "MyPaint" from getdeb.net but instead of just providing .deb downloads like they used to they now are using this goofy apturl that my firefox seems to have no idea what to do with. At first it told me "no protocol associated with apt" but a bit of googling told me to install the apturl package - now instead of telling me it can't do anything when I click install it runs what appears to be apt-get update through synaptic before telling me it cannot find the "mypaint" package... Anyone know how I install this package through getdeb?

Regards,
~Jeff

[http://www.getdeb.net/updates/Ubuntu/all#how_to_install](http://www.getdeb.net/updates/Ubuntu/all#how_to_install)

Sounds to me like you missed the below step...


Add the repository GPG key, open a terminal window and type:
 								wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -

---

### Post by beastrace91 on 2010-04-30
> **nzso said:**
> [http://www.getdeb.net/updates/Ubuntu/all#how_to_install](http://www.getdeb.net/updates/Ubuntu/all#how_to_install)

Sounds to me like you missed the below step...


Add the repository GPG key, open a terminal window and type:
 								wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -

Ahh yep! I found it about two seconds after posting this - I found the link through google so I never saw that page.

~Jeff

---

