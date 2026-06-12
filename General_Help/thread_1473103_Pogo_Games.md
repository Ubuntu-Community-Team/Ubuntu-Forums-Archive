---
title: "Pogo Games"
date: 2010-05-04
forum: General Help
---

### Post by accodata on 2010-05-04
Hi

I have had a great experience with upgrading to ubuntu 10.4, just 1 problem, I can't get pogo games to play!
Has anyone got an idea on how I can fix this please?

with thanks


Accodata
):P

---

### Post by WorMzy on 2010-05-04
No idea what Pogo games are, but if they're flash games, then you need to install ubuntu-restricted-extras.

---

### Post by accodata on 2010-05-04
Hi WorMzy thanks for your prompt reply.

Yes they are flash games, I checked to ensure that I had ubuntu-restricted-extras, and it was already installed, so I reinstalled.

Didn't work.
thank you for your help though

---

### Post by WorMzy on 2010-05-04
Hmmm.. try also installing flashplugin-installer.

EDIT: Sorry, I meant *reinstalling*.

---

### Post by hunterkasy on 2010-05-04
> **accodata said:**
> Hi

I have had a great experience with upgrading to ubuntu 10.4, just 1 problem, I can't get pogo games to play!
Has anyone got an idea on how I can fix this please?

with thanks


Accodata
):P


pogo.com uses java, make sure java is installed and is the latest, also make sure pop up blocker isn't blocking anything on pogo

---

### Post by FootySr on 2010-05-04
I installed the restricted extras and it installed the OpenJDK Java which didn't work with animated weather sites I frequent. I un-installed the OpenJDK Java and Icedtea Java Plugin and installed the regular Sun Java and all is working again. Try that. ;)

---

### Post by WorMzy on 2010-05-04
If it's Java, try reinstalling icedtea6-plugin.

---

### Post by accodata on 2010-05-04
> **FootySr said:**
> I installed the restricted extras and it installed the OpenJDK Java which didn't work with animated weather sites I frequent. I un-installed the OpenJDK Java and Icedtea Java Plugin and installed the regular Sun Java and all is working again. Try that. ;)

Thank you for your help, reinstalling the restricted extras, OpenJDK Java,now

many thanks

---

### Post by accodata on 2010-05-04
Thank you so much for you help however it didn't work.  GRRR!!

but your thoughts and help were appreciated.

Accodata

---

### Post by FootySr on 2010-05-04
> **accodata said:**
> Thank you for your help, reinstalling the restricted extras, OpenJDK Java,now

many thanks

Actually I said I un-installed OpenJDK. :) At least some of the games at Pogo are Flash, Bejeweled is at least. Now I can't get pogo.com to open at all. :)

Follow the "INSTALL FROM THE PARTNER REPOSITORY" topic on this site. It will tell you how to remove OpenJDK, then you'll have to enable the Sun Java repository (instructions on that same page) and install sun-java6-jre.

[http://sites.google.com/site/easylinuxtipsproject/java#TOC-INSTALL-FROM-THE-PARTNER-REPOSITORY](http://sites.google.com/site/easylinuxtipsproject/java#TOC-INSTALL-FROM-THE-PARTNER-REPOSITORY)

---

### Post by FootySr on 2010-05-05
accodata, maybe you read this but someone in another thread said they just removed the Icedtea JAVA Plugin and pogo works for them again.

---

