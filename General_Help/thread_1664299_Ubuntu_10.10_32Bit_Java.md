---
title: "Ubuntu 10.10 32Bit Java"
date: 2011-01-10
forum: General Help
---

### Post by TonyFordz on 2011-01-10
Hello,

I have looked all over the Internet for this one & the line I used before is not working this time...

```

sudo aptitude install sun-java5-jre sun-java5-plugin
&
sudo aptitude install sun-java6-jre sun-java6-plugin

```

The above command lines returns the following,

*sudo: aptitude: command not found*

Any ideas?

---

### Post by pricetech on 2011-01-10
Synaptic Package Manager ???

---

### Post by wojox on 2011-01-10
Open a terminal and run this:

```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner";apt-get update -y;apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

```

---

### Post by oldos2er on 2011-01-10
> **TonyFordz said:**
> 
```

sudo aptitude install sun-java5-jre sun-java5-plugin
&
sudo aptitude install sun-java6-jre sun-java6-plugin

```

The above command lines returns the following,

*sudo: aptitude: command not found*

Any ideas?

Yes, aptitude is not installed by default in 10.10. ```
sudo apt-get update && sudo apt-get install aptitude
``` Now try the code Wojox gave you.

---

### Post by Bucky Ball on 2011-01-10
This will get java and other goodies. You don't need to tweak about to do this stuff nowadays:

Open Synaptic Package Manager;
Search for 'ubuntu-restricted-extras'
Install

You're good. Java should be installed.

---

