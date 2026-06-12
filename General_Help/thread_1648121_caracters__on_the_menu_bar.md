---
title: "caracters ??? on the menu bar"
date: 2010-12-18
forum: General Help
---

### Post by redsprite on 2010-12-18
hi..
i did not understand what happening for my vlc and many other programs such as vmwork station and open office..
ubuntu 10.04 english..
please help me ..


[CENTER][IMG]http://www7.0zz0.com/2010/12/18/16/508957999.png[/IMG]
[/CENTER]

---

### Post by sikander3786 on 2010-12-18
Welcome to the forums :-)

Appears like language is changed there.

System > Administration > Language Support

Bring English to the top of that list and Apply System Wide.

---

### Post by redsprite on 2010-12-18
thx i did that yet but no changes ....

---

### Post by sikander3786 on 2010-12-18
> **redsprite said:**
> thx i did that yet but no changes ....
Logout and then log back in.

---

### Post by redsprite on 2010-12-18
still same problem !!!!!
..

---

### Post by sikander3786 on 2010-12-18
Ok. Go to Applications > Accessories > Terminal and post the output of these commands.

```
sudo dpkg-reconfigure locales
```

```
locale -a
```

---

### Post by redsprite on 2010-12-18
i got this 

******************
Generating locales...
  ar_AE.UTF-8... done
  ar_BH.UTF-8... done
  ar_DZ.UTF-8... done
  ar_EG.UTF-8... done
  ar_IN.UTF-8... done
  ar_IQ.UTF-8... done
  ar_JO.UTF-8... done
  ar_KW.UTF-8... done
  ar_LB.UTF-8... done
  ar_LY.UTF-8... done
  ar_MA.UTF-8... done
  ar_OM.UTF-8... done
  ar_QA.UTF-8... done
  ar_SA.UTF-8... done
  ar_SD.UTF-8... done
  ar_SY.UTF-8... done
  ar_TN.UTF-8... done
  ar_YE.UTF-8... done
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
  fr_FR.UTF-8... done
Generation complete.

adn this one for " locale -a "
ar_AE.utf8
ar_BH.utf8
ar_DZ.utf8
ar_EG.utf8
ar_IN
ar_IQ.utf8
ar_JO.utf8
ar_KW.utf8
ar_LB.utf8
ar_LY.utf8
ar_MA.utf8
ar_OM.utf8
ar_QA.utf8
ar_SA.utf8
ar_SD.utf8
ar_SY.utf8
ar_TN.utf8
ar_YE.utf8
C
en_AG
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NG
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
fr_FR.utf8
POSIX

---

### Post by sikander3786 on 2010-12-18
As you see, Arabic and French seem installed on your system. Go to System > Administration > Synaptic Package Manager and apply the Installed filter from left column. Search for French and Arabic (if you don't need them) and un-installed both. Reboot and see if that solves the problem.

---

### Post by redsprite on 2010-12-18
certainly i got french , so i un-installed it lask week ..
for the arbic can i keep it if does not coz  any problem ..

---

### Post by sikander3786 on 2010-12-18
Keep English on the top of that list and Arabic shouldn't cause a problem. Select English under the Text tab as well.

---

### Post by redsprite on 2010-12-18
i have now only english on my computer ,
but the problem not resolved..

---

### Post by sikander3786 on 2010-12-19
> **redsprite said:**
> i have now only english on my ***puter ,
but the problem not resolved..
Please post the output of locale -a once more.

---

### Post by redsprite on 2011-01-06
azerty@illusion:~$ locale -a
C
en_US.utf8
fr_BE.utf8
fr_CA.utf8
fr_CH.utf8
fr_FR.utf8
fr_LU.utf8
POSIX
azerty@illusion:~$

---

