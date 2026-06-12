---
title: "Java Help Please"
date: 2006-03-08
forum: General Help
---

### Post by Phixion on 2006-03-08
Hi there, I'm trying to install java, I'm following the guide @ [http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-java](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-java) but It doesn't seem to be working.

I downloaded the latest JRE from the website (jre-1_5_0_06-linux-i586.bin) and typed the command in the guide and got this:

```
mark@blaaat:~/Desktop$ fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.XXXXVlu97I
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
```

Please help! 

Thankyou.

---

### Post by CallsignBaron on 2006-03-08
The easiest way to get JRE is Applications>Add Applications>Internet>More Programs and select Java. It is ver 1.4 but works flawlessly for me. Got Limewire up and running with it.

---

### Post by Phixion on 2006-03-08
Great thanks very much man... I have no problem running older versions as long as it all works ;)

---

### Post by CallsignBaron on 2006-03-08
No problem, glad I could help. Have fun! :)

---

### Post by towsonu2003 on 2006-03-08
according to [https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)

use this:
DEB_BUILD_GNU_TYPE=i386-linux fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin

---

