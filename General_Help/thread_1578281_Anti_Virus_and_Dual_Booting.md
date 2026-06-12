---
title: "Anti Virus and Dual Booting"
date: 2010-09-20
forum: General Help
---

### Post by samstreet101 on 2010-09-20
Hi all, would like to get some opinions on the matter. I've been dual booting Lucid with Windows XP for some time now and noticed i got the odd virus here and there when using XP, it's been fine lately though and was nothing too bad in either case. My question is: If when using my Ubuntu partition (which is the vast majority of the time) and i am not running any anti virus programs, am I likely to pick up a virus which although most likely harmless to linux, could manifest itself when I boot into XP? If so would you recommend some linux AV programs? I here clam is good.

---

### Post by kaldor on 2010-09-20
Really, you won't need to worry about malware when dual-booting. However, if you share files between Linux and Windows often, there's a chance you could affect the Windows partition. 

If you really do want to run and AV application, go for Clam.

---

### Post by samstreet101 on 2010-09-20
Thanks for the suggestion, does running Clam significantly affect performance in the same way that many AV programs affect Windows' performance?

---

### Post by gandaran on 2010-09-20
> **samstreet101 said:**
> Hi all, would like to get some opinions on the matter. I've been dual booting Lucid with Windows XP for some time now and noticed i got the odd virus here and there when using XP, it's been fine lately though and was nothing too bad in either case. My question is: If when using my Ubuntu partition (which is the vast majority of the time) and i am not running any anti virus programs, am I likely to pick up a virus which although most likely harmless to linux, could manifest itself when I boot into XP? If so would you recommend some linux AV programs? I here clam is good.
if you download an infected file or program using linux/ubuntu and store it in the windows partition then yes, when you open the file using windows it will infect the windows pc but if it is stored in the ubuntu home directory it wont affect windows unless windows can read the linux partitions!
I would not recommend clam antivirus, see this [http://www.tuxradar.com/content/get-best-virus-scanner-linux](http://www.tuxradar.com/content/get-best-virus-scanner-linux)
bitdefender is the best and easiest linux antivirus.

---

### Post by gandaran on 2010-09-20
> **samstreet101 said:**
> Thanks for the suggestion, does running Clam significantly affect performance in the same way that many AV programs affect Windows' performance?
no, most linux antivirus only run on demand so it wont affect performance.

---

### Post by searchfgold6789 on 2010-09-20
There is no chance that you can install a virus on linux ( which you knid of have to do on purpose ) and it will spread to XP, and vice-versa. However if you get an infected *file* onto Ubuntu that is meant to infect Windows and you open said file from Windows, chances are you will see the Windows partition get infected with a virus.

---

### Post by fintos on 2010-09-20
There is no need to worry about viruses use samba server to manage windows ans linux. it can resolve most of the issues.

---

