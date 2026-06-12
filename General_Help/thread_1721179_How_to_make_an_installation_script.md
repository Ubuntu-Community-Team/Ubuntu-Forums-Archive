---
title: "How to make an installation script?"
date: 2011-04-04
forum: General Help
---

### Post by pras on 2011-04-04
Hi all!

I want to make an installation script to make a(some) software(s) installation easily. 
In the same script I want to have also user rights configurations and installation of all relative software that needs my software to run.

How can I do that?

Thank you

Christos

---

### Post by domu on 2011-04-04
use:

```
apt-get -qq install [your_chosen_package]
```

apt-get will ensure that any dependencies are satisfied too.

---

### Post by pras on 2011-04-04
> **domu said:**
> use:

```
apt-get -qq install [your_chosen_package]
```

apt-get will ensure that any dependencies are satisfied too.

Hi domu and thank you for the prompt post,

What I meant was to make an installation script to install the following software:
1. Mysql
2. Manual installation of Tomcat 6 and configuration (thats why I want script)
3. Apache Ant
4. Sun Java JDK
5. Copy two files to specific folder
6. Give user/owner rights in specific folders/files.

And all these must be done with one installation script file....

Is it possible to do that?

Thank you

---

