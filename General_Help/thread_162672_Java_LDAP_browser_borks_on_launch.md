---
title: "Java LDAP browser borks on launch"
date: 2006-04-19
forum: General Help
---

### Post by enigma_0Z on 2006-04-19
Hi all,

I'm *trying* to get a good ldap browser up and running, but nothing is working *good* so far...

Anyway, I found this one LDAP Browser (found at www-unix.mcs.anl.gov/~gawor/ldap/ ). It uses java, but whenever I run it, I get the followign error:

```
Exception in thread "main" java.lang.NullPointerException
   at lbe.ui.DnDDirTree.<init> (DnDDirTree.java:35)
   at lbe.ui.Browser.<init> (Browser.java:163)
   at lbe.ui.BrowserApp.main (BrowserApp.java:224)

```

Looking on the 'net,  I couldn't find anything regarding this error, so maybe someone here can help? ](*,) 

Thanks.

PS: If someone knows of a better LDAP browser, please let me know.

---

### Post by nagilum on 2006-04-19
Can't help you with your error since I'm not familiar with Java but I though I'd let you know about another LDAP browser (GTK based) which I discovered recently: [LAT](http://dev.mmgsecurity.com/projects/lat)
Looks pretty good and compiles fine on Dapper.

---

### Post by quax on 2006-09-16
-> Simply install the Java virtual machine!

Happened to me to. Could not understand, why it breaks and checked the JVM. Coul not believe, that there was none....


-Quax

---

