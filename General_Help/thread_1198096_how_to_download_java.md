---
title: "how to download java?"
date: 2009-06-27
forum: General Help
---

### Post by JakeHinojosa on 2009-06-27
I just put ubuntu on one of my computers, but i forgot how to download it and install java on it. And i am using ubuntu 8.10 if that helps with answering.

---

### Post by synapsys on 2009-06-27
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10)

---

### Post by QIII on 2009-06-27
Unless you want the very most recent JRE (I think it is Update 14), you can install the JRE from the Ubuntu Multiverse repository.

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-bin sun-java6-fonts

---

### Post by JakeHinojosa on 2009-07-01
> **QIII said:**
> Unless you want the very most recent JRE (I think it is Update 14), you can install the JRE from the Ubuntu Multiverse repository.

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-bin sun-java6-fonts

I tried that but it didnt work at all. So if i could get another way of installing java, it would be good because id like to get java installed soon.

---

### Post by EclipseAgent on 2009-07-01
> **JakeHinojosa said:**
> I tried that but it didnt work at all.

Do you have the repository enabled?

---

### Post by JakeHinojosa on 2009-07-01
> **EclipseAgent said:**
> Do you have the repository enabled?

i have no idea what you mean by that.

---

### Post by buzzmandt on 2009-07-01
follow this guide [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
it will give you java and most codecs you'll ever need

---

### Post by CatKiller on 2009-07-01
> **JakeHinojosa said:**
> i have no idea what you mean by that.

System -> Administration -> Software Sources. Put a tick in the multiverse box.

---

### Post by JakeHinojosa on 2009-07-02
so now i have java installed and its working, but how do i update it to the latest version, because i dont think i downloaded the most recent one.

---

### Post by abhi_69 on 2009-07-02
ubuntu repo. will not update java to latest one (latest one is java-6u14). because, according to policy multiverse packages will not receive update. so, u hav to use distro independent build (.bin) from sun's website & install it to get latest one. u will get both jdk & jre.
hope this will help.

---

### Post by JakeHinojosa on 2009-07-02
> **abhi_69 said:**
> ubuntu repo. will not update java to latest one (latest one is java-6u14). because, according to policy multiverse packages will not receive update. so, u hav to use distro independent build (.bin) from sun's website & install it to get latest one. u will get both jdk & jre.
hope this will help.

I dont exactly understand what you are saying

---

### Post by JakeHinojosa on 2009-07-02
Well i just checked and it turns out i have the latest version installed, but i have no idea why it doesnt work right. I use java to play [Runescape]("http://www.runescape.com"), i can play it in normal detail, but when i try high detail firefox just closes. Is it a java problem or is it something else?

---

### Post by abhi_69 on 2009-07-02
well...i check this game & it runs ok in both normal & high details using opera & flock.
may be it can be a bug or other problem in firefox, becoz, i can't even load this game using firefox 3.0.11 (& seamonkey also)!!!!!
u can try this out via opera/flock....

---

### Post by JakeHinojosa on 2009-07-02
> **abhi_69 said:**
> well...i check this game & it runs ok in both normal & high details using opera & flock.
may be it can be a bug or other problem in firefox, becoz, i can't even load this game using firefox 3.0.11 (& seamonkey also)!!!!!
u can try this out via opera/flock....

i tried it on opera, but then when i went to full screen, opera too just closed and also everything became magnified on my computer. Should i re install ubuntu on my computer and try to install java again and see if it works?

---

### Post by JakeHinojosa on 2009-07-02
or is it possible to replace ubuntu with linux mint without having to put it on a disk? because i know that linux mint already has java installed.

---

