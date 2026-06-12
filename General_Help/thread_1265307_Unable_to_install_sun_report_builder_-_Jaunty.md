---
title: "Unable to install sun report builder - Jaunty"
date: 2009-09-13
forum: General Help
---

### Post by lithops on 2009-09-13
I have installed OOo base using synaptic and downloaded the sun report builder extension from the Sun site. When I attempt to install using extension manager I receive the message "OOo 3.1 system dependencies not fulfilled".

Synaptic does not list RB.

I checked OOo and found the version installed is 3.0.1 and my version of Ubuntu is Jaunty. Did a bit of looking around and it appears I cannot use RB 1.1.0 with OOo 3.01 and must use OOo 3.1 or higher.

More looking around and I think I will need to wait until OOo 3.1 is available to be installed in Jaunty. Is that correct?

Have just started with Linux OS so am a bit unfamiliar with this idea of different packages needed for different distros.

Will the Update Manager advise when OOo 3.1 is available?

---

### Post by jmszr on 2009-09-13
lithops,

You can find the OpenOffice.org 3.1.1 Jaunty ppa here: [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa) .

Also you will need to install:```
sudo apt-get install openoffice.org-java-common
``` if you haven't already.

Hope that helps.

---

### Post by lithops on 2009-09-13
To: jmszr

Yes, that works. Thank you very much.

---

