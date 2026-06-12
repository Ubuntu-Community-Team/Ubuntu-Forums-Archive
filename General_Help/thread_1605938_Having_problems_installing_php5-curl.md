---
title: "Having problems installing php5-curl"
date: 2010-10-25
forum: General Help
---

### Post by alishawkat on 2010-10-25
Hi guys, I already have php5 installed but when I try to install php5-curl to use magento I get this message,

The following packages have unmet dependencies:
 php5-curl : Depends: php5-common (= 5.3.3-1ubuntu9) but 5.3.3-1ubuntu9.1 is to be installed
E: Broken packages


Is there anyway around this? I'm using Ubuntu 10.10 desktop.

thanks

---

### Post by alishawkat on 2010-10-26
"bump" any solutions guys?

Thanks

---

### Post by firstlunchthenwar on 2010-10-27
I had a similar issue when trying to install php5-dev. To get around it I used synaptic to force the php5-common package version to 5.3.3-1ubuntu9.1.

In synaptic, select php5-common. Package -> Force Version... and select the maverick-updates.

Doing this did remove php-pear, php5-mysql, php5-tidy but they all installed again without issue.

---

