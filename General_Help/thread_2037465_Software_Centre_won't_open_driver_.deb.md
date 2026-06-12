---
title: "Software Centre won't open driver .deb"
date: 2012-08-04
forum: General Help
---

### Post by Bucky Ball on 2012-08-04
Hi all,

As per the title.

Downloaded the drivers for my Brother printer. They are .deb files and exactly the same as the ones I already have. Click on them, opens Software Centre, then I get the error message:

> There isn&#8217;t a software package called &#8220;file:&#8221; in your current software sources.So I try with versions I downloaded awhile ago (which are identical) and, not surprisingly, same result.

I have installed these drivers probably half a dozen times on four different machines and on three different installs on this machine and never had any problem at all, so thinking 12.04. I'm also having other problems which I'm posting separate threads for. What gives with this anomoly?

Xubuntu 12.04 LTS (installed yesterday). If I search for a file in Software Centre it installs fine (tried with Filezilla). 

Tnx in advance. ;)

---

### Post by MG&amp;TL on 2012-08-04
Don't know what the software centre's up to, but the old-fashioned way to do things is:

```
sudo dpkg -i <deb>
```

where <deb> is the path to your file. Repeat if there is more than one.

---

### Post by gifford on 2012-08-04
You might try checking in synaptic to see if the driver you are wanting to install is part of the Brother printer package of drivers. If so, just install from synaptic. The other option is to following the instructions on the Brother support site to install via the terminal.

Good luck, I have always installed my Brother drivers via the command line.

---

### Post by Bucky Ball on 2012-08-04
> **gifford said:**
> You might try checking in synaptic to see if the driver you are wanting to install is part of the Brother printer package of drivers. If so, just install from synaptic. 

Not. There is one but not specific. The other is.

> **gifford said:**
> Good luck, I have always installed my Brother drivers via the command line.

Me too and I might end up doing that. Cheers.

* Update: Yea, I did install them via the terminal and when I did a search in 'Printing' they were found this time. Will try for a test page tomorrow but looks like it's solved. Thanks for the input ... ;)

PS: The printing GUI is really dodgy though. It was doing some strange things but a story for another day.

---

