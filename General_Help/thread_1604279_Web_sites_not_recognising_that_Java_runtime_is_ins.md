---
title: "Web sites not recognising that Java runtime is installed"
date: 2010-10-23
forum: General Help
---

### Post by xtheunknown0 on 2010-10-23
The output of dpkg --get-selections | grep java on Karmic Koala is

ca-certificates-java				install
java-common					install
libaccess-bridge-java				install
libaccess-bridge-java-jni			install
sun-java6-bin					install
sun-java6-jre					install
tzdata-java					install

yet when I go to a site like keepvid.com and enter a valid URL I get

Error: Please click here to download Java. If you already have Java, please restart your browser and try again.
It appears you do not have Java installed or it is disabled on your system.
You can get Java here.

If you are still having difficulty with Java, check here for installing Java, or here for detailed instructions on enabling Java in your browser.

What do I need to do?

---

### Post by oldos2er on 2010-10-23
Are you using Firefox? Do you have a script blocker such as Noscript running?

---

