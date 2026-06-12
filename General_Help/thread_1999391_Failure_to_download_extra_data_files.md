---
title: "Failure to download extra data files"
date: 2012-06-08
forum: General Help
---

### Post by hiranyaroma on 2012-06-08
Hi,

Everytime i update my Lubuntu 12.04, I get the followong error. 

> Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

ttf-mscorefonts-installer, flashplugin-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.


While all the other update packages are downloaded these two are always  left out.  I dont have ms core fonts in word and my flash videos do not play most of the time. I have already installed flash aid add on. Help me.

---

### Post by hiranyaroma on 2012-06-08
this new reply wasnt intended. where is the delete post icon? The edit/delete icon only lets me edit.

---

### Post by rubo77 on 2012-08-15
I had the same Problem and the solution was this:

```

sudo apt-get remove --purge ttf-mscorefonts-installer
sudo apt-get install ubuntu-restricted-extras

```

see
[http://askubuntu.com/questions/153928/annoying-message-is-showing-after-installing-ttf-mscorefonts-installer-package](http://askubuntu.com/questions/153928/annoying-message-is-showing-after-installing-ttf-mscorefonts-installer-package)

---

### Post by hiranyaroma on 2012-08-16
This discussion has moved to
[http://ubuntuforums.org/showthread.php?p=12175262#post12175262](http://ubuntuforums.org/showthread.php?p=12175262#post12175262)

---

