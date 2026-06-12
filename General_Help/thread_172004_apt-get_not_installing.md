---
title: "apt-get not installing?"
date: 2006-05-07
forum: General Help
---

### Post by MST3Kakalina on 2006-05-07
My problem is basically what the title says.  running **apt-get update** for me will fetch the updated packages and read them...but not *install* them. **apt-get dist-upgrade** will fetch, read, and install just fine.  Here's what I mean:

[img]http://ubuntuforums.org/attachment.php?attachmentid=9195&stc=1&d=1147046473[/img]

I AM right in that apt-get update should be INSTALLING, yes?

---

### Post by hermesrules on 2006-05-08
[QUOTE=MST3Kakalina]My problem is basically what the title says.  running **apt-get update** for me will fetch the updated packages and read them...but not *install* them. **apt-get dist-upgrade** will fetch, read, and install just fine.  Here's what I mean:

I AM right in that apt-get update should be INSTALLING, yes?[/QUOTE]

Everything seems fine on your computer. Apt-get update only makes sure that if you want to install any packages you will have the latest versions. Apt-get dist-upgrade will ONLY install new packages, if they are required by others in the process of upgrading. It will just make your system up-to-date.

To install a package, you need to do this:

```
sudo apt-get install *packagename*
```

Every once in a while, you can do

```
sudo apt-get update
sudo apt-get dist-upgrade
```

in order to bring your system up-to-date.

---

