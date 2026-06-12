---
title: "Is Java installed? Interpreting the terminal response."
date: 2012-03-04
forum: General Help
---

### Post by LightSnack on 2012-03-04
I typed java -version in terminal and this is what I got:

The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: sudo apt-get install <selected package>

I interpret this to mean that Java packages are available on my computer, but Java is not installed on my computer. Is this correct?

For the record, I do not want Java installed on my computer.

---

### Post by raja.genupula on 2012-03-04
No thats means Java is available to install in your computer but its not in your computer .
Actually in Ubuntu if you wanna install anything that particular application's PPA should added to Ubuntu repo's then only we can install that application .

actually Java here a default one , already it will be in the list no need to add repo of it . 

so if you type that command as mentioned , then from Ubuntu server first java installation file will be downloaded  and then only its going to installed . 

  for every application process will be like that  .

---

### Post by LightSnack on 2012-03-04
> No thats means Java is available to install in your computer but its not in your computer.

Oh, I see. Thanks. 

What would the terminal output look like if a version of Java was installed on my computer?

---

### Post by drdos2006 on 2012-03-04
From the terminal:  java -version

Result is :

java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.13) (6b20-1.9.13-0ubuntu1~10.04.1)
OpenJDK 64-Bit Server VM (build 19.0-b09, mixed mode)


regards

---

