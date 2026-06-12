---
title: "java"
date: 2009-11-11
forum: General Help
---

### Post by genkiz on 2009-11-11
I installed firefox 3.5.5 (ubuntuzilla) and need java for online banking
tried to install openjdk-6-jre without success (dependecies, broken packages)
than could installed sun java6 from ubuntu sw center but [test site]("http://www.java.com/en/download/help/testvm.xml") fails
How could I install a working version?

---

### Post by Crafty Kisses on 2009-11-11
You can try running:
```
apt-get install ubuntu-restricted-extras
```

---

### Post by marshmallow1304 on 2009-11-11
Did you install sun-java6-plugin ?

---

### Post by wojox on 2009-11-11
```
sudo apt-get install sun-java6-jre sun-java6-plugin equivs
```

---

### Post by genkiz on 2009-11-11
I tried, extras installed, but still get "Something is wrong. Java is not working."
> **Crafty Kisses said:**
> You can try running:
```
apt-get install ubuntu-restricted-extras
```

---

### Post by genkiz on 2009-11-12
this installed more than 100mb and i can not believe but i still get "Something is wrong. Java is not working."


> **wojox said:**
> ```
sudo apt-get install sun-java6-jre sun-java6-plugin equivs
```

---

### Post by nanotube on 2009-11-14
> **genkiz said:**
> I installed firefox 3.5.5 (ubuntuzilla) and need java for online banking
tried to install openjdk-6-jre without success (dependecies, broken packages)
than could installed sun java6 from ubuntu sw center but [test site]("http://www.java.com/en/download/help/testvm.xml") fails
How could I install a working version?

question 1: did java work before you upgraded with ubuntuzilla?
question 2: are you running 64bit or 32bit ubuntu?
question 3: which version of ubuntu are you running?

---

