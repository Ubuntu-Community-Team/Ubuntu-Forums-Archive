---
title: "installing java to ubuntu 9.10"
date: 2010-02-02
forum: General Help
---

### Post by raffi_1970 on 2010-02-02
Hi, I'm very new to Ubuntu and am having difficulties installing Java for it.

I think what I did wrong was when I got the Sun authentication screen, I didn't know to press TAB and then enter to hit ok. 

Is there any way to start all over?

What I originally tried was:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

What I got as a consequence was:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-15-1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
  sun-java6-plugin: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


any suggestions???

Thanks!

---

### Post by Atzu on 2010-02-02
You could try installing it via synaptic package manager... open it (System >> Administration >> Synaptic Package Manager) then search for jdk (java development kit) or jre (java runtime environment) dunno which you want and click then install 

P.D: terminal is suggesting you to use sudo apt-get -f install to try correct the problem...

good luck!

---

### Post by rogue_0111 on 2010-02-02
I agree with Atzu. Package Manager. Here is a how to link:

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

--

---

