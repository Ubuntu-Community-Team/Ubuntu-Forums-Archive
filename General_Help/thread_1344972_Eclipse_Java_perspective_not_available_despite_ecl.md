---
title: "Eclipse Java perspective not available despite eclipse-jdt is installed"
date: 2009-12-03
forum: General Help
---

### Post by sarcangeli on 2009-12-03
Hi all,
running Ubuntu 9.10 on amd64.
I installed eclipse-platform and eclipse-jdt, and then i installed also the "eclipse" package (which includes both, and also eclipse-pde). 
The java alternative is configured to point to java-6-sun (the JDK bin, not the JRE).
Eclipse starts up fine, it has subclipse and the SVN perspective working fine (I have subversion installed and i was pleased to know that subclipse was automatically added to my eclipse), but the Java perspective is still not available, despite i can see JDT included in the list of core plugins installed.

Any clue?

thanks,
silvio

---

### Post by NTHQ on 2009-12-08
I was having the same problem but after I installed the Ubuntu Restricted Extras packcage everything worked fine.

---

### Post by sarcangeli on 2009-12-10
I tried installing ubuntu-restricted-extras, but it had no effect in my case... the java perspective still doesn't appear. 
Should we log a bug somewhere? looks like there's an issue with the distribution anyway.

---

### Post by NTHQ on 2009-12-11
Have you tried asking on the Eclipse forum? I'm sure there's a fix for it since it works for me.
9.10 works like a charm for me. The problems I had in 9.04 are fixed in 9.10.
I just installed CDT also and it works perfectly fine too.

---

### Post by nasp on 2010-01-02
I'm having the same issue with amd64 and the extrat packaged installed.

Did you solve your issue somehow?

---

