---
title: "problems with sun virtural box and ubuntu"
date: 2010-10-11
forum: General Help
---

### Post by mprodman on 2010-10-11
windows xp ruuning on a hp laptop (Elite Book 6930p)
sun now oracle virtual box version 3.2.8
installed ubuntu 10.10 
 
Problem I am unable to view system in full screen mode it even after I have tried installing VBOXADDItTIONS 3.2.8_64453. 
 
So I am stuck with a screen resolution of 800x600 and montior is unknown under the montior prefernces. 
 
Any suggestions.

---

### Post by JustinR on 2010-10-11
> **mprodman said:**
> windows xp ruuning on a hp laptop (Elite Book 6930p)
sun now oracle virtual box version 3.2.8
installed ubuntu 10.10 
 
Problem I am unable to view system in full screen mode it even after I have tried installing VBOXADDItTIONS 3.2.8_64453. 
 
So I am stuck with a screen resolution of 800x600 and montior is unknown under the montior prefernces. 
 
Any suggestions.

Hi,

When you get into Ubuntu, go to **Applications > Acessories > Terminal:**

```

sudo apt-get install virtualbox-ose-guest-x11

```

Restart Ubuntu and it should work.

---

### Post by mprodman on 2010-10-11
Thanks Justin that did the trick -- everythings working great now.

---

