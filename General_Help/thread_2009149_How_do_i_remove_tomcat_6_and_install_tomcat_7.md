---
title: "How do i remove tomcat 6 and install tomcat 7"
date: 2012-06-24
forum: General Help
---

### Post by sorabh.v6 on 2012-06-24
I have installed tomcat 7 but there is still tomcat 6 in ubuntu and when running localhost:8080 it opens tomcat 6 files.Please somebody help me...

---

### Post by Zvlwab on 2012-06-24
```
sudo apt-get purge tomcat6 && sudo apt-get autoremove && sudo apt-get install tomcat7
```

---

### Post by irving129 on 2012-06-24
thank you very much the truth, surely others were also looking.

[lanzadores de xploits](http://www.lanzador-de-xploits.iives.com)
[como hackear twitter](http://www.como-hackear-twitter.iives.com/como-hackear-twitter.html)

---

### Post by elliotn on 2012-06-24
I always use synaptic than having to use command lines

---

### Post by sethmerriman on 2013-06-04
Thanks, Zvlwab.  How easy is that!

---

### Post by oldos2er on 2013-06-04
Old thread closed.

---

