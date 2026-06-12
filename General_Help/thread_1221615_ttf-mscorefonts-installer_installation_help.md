---
title: "ttf-mscorefonts-installer installation help"
date: 2009-07-24
forum: General Help
---

### Post by t43m4n on 2009-07-24
I'm having a hard time installing ttf-mscorefonts-installer via apt-get command in terminal. Im getting a ISA server error since I can't configure it properly due to my password having special characters (its a requirement). I only install programs through Add/remove or via Synaptic Package Manager. 

Is there another way of installing ttf-mscorefonts-installer than using apt-get? I need to install it for the latest ver of wine.

I'm a unix newbie so I'd prefer to work with the gui.

---

### Post by lemuriaX on 2009-07-24
Maybe try a search from within Synaptic for msttcorefonts and installing from there.

---

### Post by t43m4n on 2009-07-24
im getting an error

E: ttf-mscorefonts-installer: subprocess post-installation script returned error exit status 1
E: msttcorefonts: dependency problems - leaving unconfigured

---

### Post by lemuriaX on 2009-07-30
Hmmm...I'm not sure on that, hopefully someone else here more knowledgeable can help out.

---

### Post by boehr on 2009-10-12
> **t43m4n said:**
> im getting an error

E: ttf-mscorefonts-installer: subprocess post-installation script returned error exit status 1
E: msttcorefonts: dependency problems - leaving unconfigured

I found only one solution to this problem. I had to download the fonts manually and then reinstall the ttf-mscorefonts-installer package. See the full solution here:
[http://ubuntuforums.org/showpost.php?p=8095621&postcount=15]("http://ubuntuforums.org/showpost.php?p=8095621&postcount=15")

---

