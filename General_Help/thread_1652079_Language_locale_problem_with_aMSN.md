---
title: "Language locale problem with aMSN"
date: 2010-12-24
forum: General Help
---

### Post by TheDestroyer on 2010-12-24
Hello guys,

aMSN is doing something strange with Arabic language, where it writes the sentences from left to right and the letters are separated. Arabic must be from right to left with connected letters. I pursued the problem and found that I must install the Arabic locale in my system, and so I did.

I went to System -> Administration -> Languages and added the Arabic language in every sense, and went to the console and used the commands:

sudo locale-gen ar_SA.UTF-8
sudo locale-gen ar_SY.UTF-8

but when I do the reconfigure for the locales with the command:

sudo dpkg-reconfigure locales

I get the following error at some point:

ar_SA.UTF-8... hash collision (1734041931) ar_SA.utf8, es_SV.utf8
failed

So what does this error mean? and is it the cause of the problem? 
the output of the reconfigure command is the following

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
  ar_SA.UTF-8... hash collision (1734041931) ar_SA.utf8, es_SV.utf8
failed
  ar_SD.UTF-8... done
  ar_SY.UTF-8... up-to-date
  ar_TN.UTF-8... done
  ar_YE.UTF-8... done
  de_AT.UTF-8... done
  de_BE.UTF-8... done
  de_CH.UTF-8... done
  de_DE.UTF-8... done
  de_LI.UTF-8... done
  de_LU.UTF-8... done
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
Generation complete.

Thank you for any efforts.

---

### Post by TheDestroyer on 2010-12-24
The problem is still there, but I solved the locales' collision problem by doing the following:

1. execute: sudo apt-get install localepurge
2. Select the language of conflict and remove them (es_sv and es_sv.utf8 in this case).
3. execute again: sudo dpkg-reconfigure locales

But the problem still persists with aMSN... could anyone help me with that??? I'm tired of searching and looking... is it a problem with the kernel of that program???

Thank you for any efforts!

---

### Post by ahmed abd elkader on 2011-01-24
bump , i have the same problem too

---

