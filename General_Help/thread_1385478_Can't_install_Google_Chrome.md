---
title: "Can't install Google Chrome"
date: 2010-01-19
forum: General Help
---

### Post by rob22941 on 2010-01-19
I'd like to install Google Chrome, not Chromium OS, just the web browser and I'm getting an error in the Package Installer saying, "Error: Wrong architecture 'amd 64'". I'm not sure what other information to provide but I get the same error each time I try so I can run it again and tell you any specific information. Now I have this computer dual booting with Windows 7 and I have Chrome on there so I don't see how it's a hardware problem. Thanks much.

---

### Post by patchwork on 2010-01-19
Are you running 64 bit ubuntu?  Google Chrome is only available for linux for 64 bit architecture right now (though they do have a 32 bit version and a 64 bit version for windows).  If you have 64 bit ubuntu, you shouldn't have any trouble downloading and installing from [http://www.google.com/chrome/index.html?brand=CHMO&utm_campaign=en&utm_source=en-et-hclinux&utm_medium=et](http://www.google.com/chrome/index.html?brand=CHMO&utm_campaign=en&utm_source=en-et-hclinux&utm_medium=et)    EDIT:  I seem to be mistaken, as I have found several places with a 32 bit .deb for chrome.  All the ones I've seen so far, however, are listing it as unstable.  Perhaps someone else can chime in...

---

### Post by Leppie on 2010-01-19
if you installed 64bit Ubuntu, you will have to download and install the 64 bit chrome browser: [http://www.google.com/chrome/eula.html?platform=linux_ubuntu_x86_64](http://www.google.com/chrome/eula.html?platform=linux_ubuntu_x86_64)

---

### Post by Leppie on 2010-01-19
> **patchwork said:**
> Are you running 64 bit ubuntu?  Google Chrome is only available for linux for 64 bit architecture right now (though they do have a 32 bit version and a 64 bit version for windows).  If you have 64 bit ubuntu, you shouldn't have any trouble downloading and installing from [http://www.google.com/chrome/index.html?brand=CHMO&utm_campaign=en&utm_source=en-et-hclinux&utm_medium=et](http://www.google.com/chrome/index.html?brand=CHMO&utm_campaign=en&utm_source=en-et-hclinux&utm_medium=et)
they also have a 32bit version for linux: [http://www.google.com/chrome/eula.html?platform=linux_ubuntu_i386](http://www.google.com/chrome/eula.html?platform=linux_ubuntu_i386)

---

### Post by code-jockey on 2010-04-17
just switch to super user and run dpkg

sudo su
dpkg -i google-chrome-beta_current_i386.deb

---

