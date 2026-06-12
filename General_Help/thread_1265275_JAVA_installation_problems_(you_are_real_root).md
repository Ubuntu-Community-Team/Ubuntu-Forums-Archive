---
title: "JAVA installation problems (you are real root)"
date: 2009-09-13
forum: General Help
---

### Post by antdgar on 2009-09-13
I'm trying to install JAVA

```
sudo fakeroot make-jpkg jre-6u16-linux-i586.bin
You are real root -- unfortunately, some Java distributions have
install scripts that directly manipulate /etc, and may cause some
inconsistencies on your system. Instead, you should become a
non-root user and run:

fakeroot make-jpkg jre-6u16-linux-i586.bin

which will allow no damage to be done to your system files and
still permit the Java distribution to successfully extract.

Aborting.
```So I thought not to use 'sudo':

```
fakeroot make-jpkg jre-6u16-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.EsJmRHSiDc
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

Detected build architecture: i386
Detected GNU type: i486-linux-gnu

No matching plugin was found.
Removing temporary directory: done
```any ideas for this one?

---

### Post by chriskin on 2009-09-13
are you by any chance logged in as root?

---

### Post by newsoft on 2009-09-13
> are you by any chance logged in as root?


wondering the same

---

### Post by DougieFresh4U on 2009-09-13
Why don't you just go to 'add/Remove' and select 'Sun Java'?
Make sure that 'All applications' is selected on the top of Add/Remove.

---

### Post by antdgar on 2009-09-13
I don't know if I'm root. I'm a user called 'antdgar'. There's a user called 'root' too but I'm not logged in as that. Also, I add my user to sudoers list.

I've already done ```
apt-get install java-package
```
I don't have this 'add/remove' thing which you are talking about. I'm using KDE.

---

