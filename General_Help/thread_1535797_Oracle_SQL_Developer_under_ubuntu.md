---
title: "Oracle SQL Developer under ubuntu?"
date: 2010-07-21
forum: General Help
---

### Post by poltak on 2010-07-21
Hi guys, just got a quick question:

I need to install Oracle's SQL Developer since I need to use the program for a database unit at Uni.
Anyway, if you've tried to use it before you'd realise that there is only a .rpm installer available for it (no .deb). So I tried to convert it to .deb using alien. When I "sudo alien --scripts" the .rpm I get:
error: incorrect format: unknown tag
mkdir: cannot create directory `sqldeveloper-2.1.1.64.45': File exists
unable to mkdir sqldeveloper-2.1.1.64.45:  at /usr/share/perl5/Alien/Package.pm line 257.

Basically, I'm asking, does anyone know what I'm doing wrong here? I've never used alien before since I've never had a need to convert a .rpm before. I also tried installing and running Java JDK and SQL Developer under Wine, but was unsuccessful with that as well :(

Anyway, thanks for taking your time to read and (hopefully) help with this ;) Oh and I'm using Ubuntu 10.04 32bit, if that helps?

---

### Post by poltak on 2010-07-22
Ah, crud. Managed to solve this problem with the help of another more-advanced-than-me linux user. Anyway, I'll write up how we got it sorted without needing to convert an rpm package to deb just so if anyone else has this same problem in the future and googles this or something...

First make sure you have Java JDK installed. I used openjdk (open-source alternative to the official Sun Java jdk thingie).
Download the "Oracle SQL Developer for other platforms" from the Oracle site ([http://www.oracle.com/technology/software/products/sql/index.html)and](http://www.oracle.com/technology/software/products/sql/index.html)and) then extract it into its own folder. Then in terminal, cd to the extracted directory and:
sudo sh sqldeveloper.sh
It'll ask you to type the pathname of your J2SE installation.
Mine turned out to be "/usr/lib/jvm/java-6-openjdk". Then press enter and you should be right and it will boot up and work the exact same as it does under Windows or OS X.

Hopefully this helps another linux newbie out one day down the track :)

---

### Post by nilsnh on 2010-10-15
> **poltak said:**
> 
Hopefully this helps another linux newbie out one day down the track :)

Thanks man. Totally helped me out. :)

---

### Post by jmgold on 2010-11-11
Thanks poltak, after spending all day trying to get 'linux' versions to work, the 'other systems' version you suggested did the trick!

ubuntu 10.10

---

### Post by BryanFRitt on 2011-01-29
To get [FONT="Courier New"]sqldeveloper.sh[/FONT] to stop asking for "[FONT="Courier New"]the full pathname of a J2SE installation[/FONT]" create the folder [FONT="Courier New"]~/.sqldeveloper[/FONT]
```
mkdir ~/.sqldeveloper/
```

---

### Post by adam s on 2011-02-21
Another vote of thanks.

Adam.

---

### Post by willo24 on 2011-06-01
Thanks guys for sorting this out and putting together a nice little tute. It doesn't seem to be necessary to run the sqldeveloper.sh as root so I dropped the 'sudo'.  I also added a desktop launcher with the help of this instruction:

[http://ubuntuforums.org/showthread.php?t=680302](http://ubuntuforums.org/showthread.php?t=680302)

Cheers again,

Willo

---

### Post by deboh on 2012-02-21
pls can yu explain what yu mean by cd to the extracted directory... I downloaded to the Downloads and extracted there aswell, so what exactly do i type?
2- the sh stuff yu gave here does not work for me?

I need urgent help from anybody who understand what the dude is trying to explain in complex shortforms

---

### Post by TheKojuEffect on 2012-06-07
You must have sqldeveloper folder in ~/Downloads where you extracted the downloaded zip file.

```
cd ~/Downloads/sqldeveloper
```
```
sh sqldeveloper.sh
```


Try this.

---

### Post by oldos2er on 2012-06-07
Old thread closed, please don't bump old threads.

---

