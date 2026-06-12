---
title: "foxit reader no such file or directory error"
date: 2009-12-20
forum: General Help
---

### Post by manuleka on 2009-12-20
just downloaded foxitreader 1.1 and installed on my Ubuntu 9.10

when i click on the menu icon i get the following error message:

```

**Could not launch 'FoxitReader'**
Failed to execute child process
"FoxitReader" (No such file or directory)

```

anyone come across this before?

---

### Post by howefield on 2009-12-20
[https://help.ubuntu.com/community/Foxit](https://help.ubuntu.com/community/Foxit)

*```
Warning: this program is not known to work
```*

---

### Post by jrusso2 on 2009-12-20
Not sure why it does't work on Ubuntu it works fine on Mandriva.

---

### Post by kaibob on 2009-12-20
> **manuleka said:**
> just downloaded foxitreader 1.1 and installed on my Ubuntu 9.10

when i click on the menu icon i get the following error message:

```

**Could not launch 'FoxitReader'**
Failed to execute child process
"FoxitReader" (No such file or directory)

```

anyone come across this before?

I encountered the same problem in August when version 1.1 was released. I just extracted the executable and copied it to the /usr/bin directory.

[http://ubuntuforums.org/showthread.php?t=1176859&highlight=foxit&page=2](http://ubuntuforums.org/showthread.php?t=1176859&highlight=foxit&page=2)

---

### Post by manuleka on 2009-12-20
thanks guys... am going to try kaibob's copy and paste :) cheers

---

### Post by ersatzorama on 2010-03-18
As I faced the same problem and had a hard time finding a solution, here's what made Foxit work on my 64-bit installation. Make sure you've got **ia32-libs** installed from the repositories! 

Hope this tip can help others out!

---

