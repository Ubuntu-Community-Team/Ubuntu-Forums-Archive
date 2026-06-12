---
title: "Run Java Applets on Ubuntu 9.04 x64"
date: 2009-10-02
forum: General Help
---

### Post by TarasIv on 2009-10-02
I love the site NinjaVideo.net, but I can't get the Java Applet on it to run on Ubuntu. Is there a way to get Java Applets working? I am running 9.04, 64-bit. Any help is appreciated.

---

### Post by Giblet5 on 2009-10-02
I'm assuming that you've installed the java runtime, right?

Bring up synaptic, edit the repositories to add the Ubuntu restricted repository. Then click the Reload button.

Search for "restricted" by clicking the Search button. Select ubuntu-restricted-extras. That will install a lot of audio codecs, movie player codecs, and the JRE.

You'll wanna restart Firefox when that's done...

---

### Post by sedawk on 2009-10-02
I have a 64-bit linux (non-Ubuntu) box here where a java plugin
(openjdk) seem to work at least partly.
E.g. it works on this page:
[http://www.javatester.org/enabled.html](http://www.javatester.org/enabled.html)

But not really on this page:
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)
(a grey box in the middle that stays empty ...).

Sometimes problems are also related to flash which
is (was?) 32-bit only (many video sites use flash).
When I had to find a workaround for this 64-bit
problem (more than a year ago) the only workaround
was to install firefox 32-bit including all dependencies.
I later switched that computer back to 32-bit because
of this and other reasons ...

---

### Post by Giblet5 on 2009-10-02
> **sedawk said:**
> I have a 64-bit linux (non-Ubuntu) box here where a java plugin
(openjdk) seem to work at least partly.
E.g. it works on this page:
[http://www.javatester.org/enabled.html](http://www.javatester.org/enabled.html)

But not really on this page:
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)
(a grey box in the middle that stays empty ...).

Sometimes problems are also related to flash which
is (was?) 32-bit only (many video sites use flash).
When I had to find a workaround for this 64-bit
problem (more than a year ago) the only workaround
was to install firefox 32-bit including all dependencies.
I later switched that computer back to 32-bit because
of this and other reasons ...

JRE (and Adobe Flash 10) are available for x64 now...

---

### Post by TarasIv on 2009-10-02
Will try and update with results. Thanks for the help guys.

---

### Post by TarasIv on 2009-10-02
Got it working. Thanks for the help guys!

---

