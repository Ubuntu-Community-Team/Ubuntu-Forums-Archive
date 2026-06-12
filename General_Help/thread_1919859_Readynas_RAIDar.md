---
title: "Readynas RAIDar"
date: 2012-02-03
forum: General Help
---

### Post by Holtan66 on 2012-02-03
Hello good people.
I hope you can help med with a challenge I have been stuck with some days.
I have downloaded the newest RAIDar installer to my download folder, Nedlastinger.
I do this and I got this error message:
xxx@Anthrax:~/Nedlastinger$ sudo bash RAIDar_Linux.sh -c
[sudo] password for xxx: 
Unpacking JRE ...
Preparing JRE ...
RAIDar_Linux.sh: line 209: bin/unpack200: Ingen slik fil eller filkatalog
Error unpacking jar files. The architecture or bitness (32/64)
of the bundled JVM might not match your machine.

Probably no need to point out, but I am a beginner with Ubuntu.
But can anyone tell me what the problem is and how I can change it?

---

### Post by Khayyam on 2012-02-04
holtan66 ...

Is your install 64bit? It looks like this is the case (you can check with 'uname -m') 

As I remember from an old ReadyNAS forum post, installing the ia32-lib package will fix this:

See if its installed ..

```
dpkg -l ia32-libs
```

If not, install it ..

```
sudo apt-get install ia32-libs
```

BTW, this is with [Version 4.3.4](http://www.readynas.com/?cat=41)?

HTH ...

---

### Post by Holtan66 on 2012-02-04
That did the trick!
Thanks a lot!

Yes, Version 4.3.4 it is.

---

### Post by Khayyam on 2012-02-04
OK .. good. You should now [mark this thread as [SOLVED]](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6).

---

