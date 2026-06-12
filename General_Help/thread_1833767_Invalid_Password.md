---
title: "Invalid Password?"
date: 2011-08-26
forum: General Help
---

### Post by iambrandon on 2011-08-26
After fixing my previous issue I've now run in to another. If I install something through the Ubuntu Software Center and enter my password for access to do so it will work, however if I try and run Synaptic or something else and enter the password it considers it invalid. Is there something I'm missing? A different password?

---

### Post by allwimb on 2011-08-26
try doing sudo apt-get update and put your password if it doesn't that mean you've changed the sudoers file and you need to allow once again your user to run sudo.

[spring login]("http://www.java-forums.org/blogs/spring-framework/531-login-forms-spring-security.html")

---

### Post by iambrandon on 2011-08-26
> **allwimb said:**
> try doing sudo apt-get update and put your password if it doesn't that mean you've changed the sudoers file and you need to allow once again your user to run sudo.

Just tried that and it took the password and worked fine, synaptic is still yelling at me telling me my administrative password is wrong though.

---

### Post by raja.genupula on 2011-08-26
> **iambrandon said:**
> After fixing my previous issue I've now run in to another. If I install something through the Ubuntu Software Center and enter my password for access to do so it will work, however if I try and run Synaptic or something else and enter the password it considers it invalid. Is there something I'm missing? A different password?


in ubuntu we have only one password for normal and root operations . recently have you changed your password . ? if so give a try by giving old one

---

### Post by iambrandon on 2011-08-26
> **raja.genupula said:**
> in ubuntu we have only one password for normal and root operations . recently have you changed your password . ? if so give a try by giving old one

My password hasn't changed, everything else seems to work fine other than synaptic.

---

### Post by raja.genupula on 2011-08-26
try this and run synaptic again 
```
gksudo passwd -l root
```

---

### Post by iambrandon on 2011-08-26
> **raja.genupula said:**
> try this and run synaptic again 
```
gksudo passwd -l root
```

Still nothing. Possibly just broken?

---

### Post by raja.genupula on 2011-08-26
[http://ubuntuforums.org/showthread.php?t=1592766](http://ubuntuforums.org/showthread.php?t=1592766)

he also have the same problem and got solved by desktop-base .

[https://launchpad.net/ubuntu/+source/desktop-base](https://launchpad.net/ubuntu/+source/desktop-base)

---

### Post by iambrandon on 2011-08-26
> **raja.genupula said:**
> [http://ubuntuforums.org/showthread.php?t=1592766](http://ubuntuforums.org/showthread.php?t=1592766)

he also have the same problem and got solved by desktop-base .

[https://launchpad.net/ubuntu/+source/desktop-base](https://launchpad.net/ubuntu/+source/desktop-base)


That fixed it. Thank you :D

---

### Post by raja.genupula on 2011-08-26
i am happy to hear this . but please mark this thread as solved by clicking at thread tools and every time your problem got solved

---

