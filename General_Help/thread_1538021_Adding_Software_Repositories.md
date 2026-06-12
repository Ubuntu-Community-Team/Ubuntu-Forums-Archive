---
title: "Adding Software Repositories"
date: 2010-07-24
forum: General Help
---

### Post by jereece on 2010-07-24
I have been trying to convert from Windows to Ubuntu and one of my frustrations is the lack of software.  I was reading [this article]("http://www.howtogeek.com/howto/ubuntu/adding-extra-repositories-on-ubuntu/") about adding more repositories and wanted to try this to see if adding the repositories would help me find more software that I want.  However in following the instructions, the file "sources.list" is read only.  How can I open this file where I can uncomment the other repositories and save the changes?

On a similar note, are there other software repositories I should add or are these the only ones?

Thanks,
Jim

---

### Post by BigCityCat on 2010-07-24
You don't add ppa's unless you have a specific piece of software you wish to add and then you want to be sure what your adding is safe. You could add the mediubuntu repositories if you like.

Try these.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by howefield on 2010-07-24
> **jereece said:**
> How can I open this file where I can uncomment the other repositories and save the changes?

Open a terminal, (Applications > Accessories > Terminal) and type

```
gksudo gedit /etc/apt/sources.list
```

Enter your password if prompted.

Watch what you are doing, it could be easy to mess up your sources.list. You can also use the graphical System > Administration > Software Sources to do the same thing a little more safely. ;-)

---

### Post by BigCityCat on 2010-07-24
Here are some more you can try.

[http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html](http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html)

---

