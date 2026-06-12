---
title: "newbie q - what to do with broken packages?"
date: 2009-07-15
forum: General Help
---

### Post by mantorpcity on 2009-07-15
Running the updates in synaptic today I received this message.

You have 2 broken packages on your system!
Use the "Broken" filter to locate them.

So I do that and I see

sun-java6-bin and
sun-java6-jre

I choose mark for upgrade in synaptic because I don't think I want to get rid of these.

Synaptic then says:

E: /var/cache/apt/archives/sun-java6-bin_6-14-0ubuntu1.9.04_i386.deb: trying to overwrite `/usr/lib/jvm/java-6-sun', which is also in package tersus


How do I fix this?

Thanks

---

### Post by carml on 2009-07-15
Mantain your cable and connection on,reboot your system and:
1. if you have only Ubuntu press ESC and select the recovery mode (the second you see from top),there's one for every kernel you got installed,
2. if you have got a dual boot just choose the recovery mode for the latest kernel you see (the kernel is that sequence of numbers like 2.6.XX.XX ).
Once you selected the recovery mode choose the entry named Try to repair broken packages and it will check your packages and repair the broken ones.

---

### Post by prem1er on 2009-07-15
> **carml said:**
> Mantain your cable and connection on,reboot your system and:
1. if you have only Ubuntu press ESC and select the recovery mode (the second you see from top),there's one for every kernel you got installed,
2. if you have got a dual boot just choose the recovery mode for the latest kernel you see (the kernel is that sequence of numbers like 2.6.XX.XX ).
Once you selected the recovery mode choose the entry named Try to repair broken packages and it will check your packages and repair the broken ones.

How do packages become broken in the first place?  Also, would removing and reinstalling fix this problem?

---

### Post by carml on 2009-07-15
Packages became broken with a wrong download or if a evil genius (the one of Renee Descartres) touch them :lolflag:
Apart from jokes a wrong download or a forced upgrade (issue with the dependences) as far as I know can broke packages. :)

---

### Post by mcduck on 2009-07-15
> **prem1er said:**
> How do packages become broken in the first place?  Also, would removing and reinstalling fix this problem?

In case of these packages, my bet is that when you installed them you didn't accept the EULA that the Java installer pops up. And without accepting it the package installation couldn't continue, thus the packages broke.


You could try running something like "sudo dpkg-reconfigure sun-java6-bin sun-java6-jre", or just removing and then installing the packages again. And in case I was right and you missed the EULA, accept it this time (it opens in a terminal window, and you need to press TAB key to select the "accept"-button and then press enter.)

---

### Post by mantorpcity on 2009-07-15
Thanks everyone, I chose to remove and reinstall in synaptic and it worked, I first tried the reconfig thing but I got the same error about the package being broken. 

It also removed tersus but I guess I can just reinstall that. I had accepted the license before because when I reinstalled it said I already had accepted it and it didn't ask again so I am not sure what broke it.

Moving on...

---

### Post by johnaaronrose on 2009-07-15
Just had same problem. Mantor's method worked good for me.

---

### Post by blair nilsson on 2009-07-15
This mornings update broke the JRE here. I think this thread is going become more active over the next couple of days.

---

