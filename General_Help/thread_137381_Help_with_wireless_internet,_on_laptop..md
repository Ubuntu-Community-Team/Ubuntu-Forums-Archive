---
title: "Help with wireless internet, on laptop."
date: 2006-02-27
forum: General Help
---

### Post by gtkourounis on 2006-02-27
I just bought a Acer Aspire 5002WLMi, and i installed ubuntu in it. Everything runs smoothly except for one thing. I cant get ubuntu to find my wireless card (integrated) and i therefore i cant communicate with my wireless without a E-net wire. I read somthing about ndiswrapper or something similar but i didnt really undertand what to do. I searched for which wireless card i have and i think i have a Acer InviLink 802.11b/g wireless LAN. But i am not sure about that so if you have any ways of double checking that please do.(i got that info from ebay so i wouldnt put my money on that). If you could help me out pls do. and by the way ubuntu rox. 10000 better then windows or mac.

thanx in advance.


EDIT - the name of the card is..... Broadcom Corporation BCM4318 802.11 b/g

---

### Post by aosmith on 2006-02-27
well first of ndiswrapper is a program that allows you to use *most* windows drivers.  it comes pre-loaded, but not installed.  In order to install you need to use the synaptic package manager (system -> admin).  Once you have ndiswrapper installed go to the folder where you are storing the .inf .sys and (sometimes) .bin files.  run the command <ndiswrapper -i {name of driver}>.  This will install the driver.  Now you have to append the modprobe file, so run the command <ndiswrapper -m>, also run <ndiswrapper -hotplug> just to be safe.  You may have to sudo with some of these commands.  Good Luck!

---

### Post by gtkourounis on 2006-02-27
i am kind of a noob in all this stuff so i was wondering if you could explain in more of like a "the dummies guide to.." please. I got the driver. I also found ndiswrapper but i dont know how to do anything else after that. If you could pls help tell me. Thanx in advance again.

---

### Post by romdos on 2006-02-28
a good howto for ndiswrapper can be found [ here]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto")

---

### Post by binarybro on 2006-02-28
I took the lazy mans way out.  I replaced the original wifi card with one that was built using the intel chipset.  It's an intel pro/wireless 2200BG.  I purchased it from ebay for $20.00

The drivers are already included in Ubuntu.  It was recognized and installed without user intervention.

---

### Post by gtkourounis on 2006-02-28
what does make a deb mean?  pls check the 5th step and if you could pls explain i would be more then thankfull.

[https://wiki.ubuntu.com/HowtoUseNdiswrapperOnAmd64Ubuntu?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowtoUseNdiswrapperOnAmd64Ubuntu?highlight=%28ndiswrapper%29)

---

### Post by romdos on 2006-03-02
I think that the author of that portion of the wiki means that you should use the tools in the ndiswrapper source to create a debain package that can be installed and uninstalled with dpkg

to do this

1) download the source

2) untar the source

```

tar xzvf ndiswrapper-1.10.tar.gz

```

3) cd into the newly untarred ndiswrapper directory

4) "make a deb"
```

romdos@freekbox:~/ndiswrapper-1.10$ make deb

```

the file ndiswrapper-modules-2.6.12-10-386_1.10-1_i386.deb and  ndiswrapper-utils_1.7-1_i386.deb
 will be created (the numbering may be a little different depending on your kernel and your selected architecture) one directory below the directory that you are in

5) install the debs
```

romdos@freekbox:~$ sudo dpkg -i ndiswrapper-*.deb 

```

now you should have ndiswrapper installed the proper Debian way!

---

