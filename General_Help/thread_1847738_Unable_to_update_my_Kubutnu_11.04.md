---
title: "Unable to update my Kubutnu 11.04"
date: 2011-09-21
forum: General Help
---

### Post by tehno 2 on 2011-09-21
I am using Kubuntu 11.04 
Since few days I started having problem when I want to check for update. When I enter my password, an error window pop us saying:


Sorry- KpackageKit

E: Error cdrom://Kubuntu 11.04 _Natty Narwhal_ 
Release amd64 (20110427) natty/main amd64 Packages
Please use apt-cdrom to make this CD-ROM recognized
by APT. apt-get update cannot be used to add new CD-ROMs

What is that supposed to mean and how can it be fixed

Thanks in advance

---

### Post by zvacet on 2011-09-22
See if you can uncheck CD as repository in KpackageKit.If not 

```
sudo kate /etc/apt/sources.list
```

and put # sign in front of CD rom line.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by tehno 2 on 2011-09-22
zvacet	
Re: Unable to update my Kubutnu 11.04
See if you can uncheck CD as repository in KpackageKit.If not 

Code:
sudo kate /etc/apt/sources.list
and put # sign in front of CD rom line.

Code:
sudo apt-get update && sudo apt-get upgrade



Thank you very much, I just unchecked CD and it worked

---

### Post by raja.genupula on 2011-09-22
we are glad that your issue got solved , please mark the thread as solved .

---

