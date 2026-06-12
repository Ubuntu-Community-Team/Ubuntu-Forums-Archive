---
title: "mod_lisp with Apache"
date: 2010-04-23
forum: General Help
---

### Post by hickhack on 2010-04-23
Hello,

I want to install mod_lisp with Apache. I searched for some tutorials or examples but all didn't work.

Has anybody some experiences with that and can help me?

Thanks in advance

---

### Post by Ryan Dwyer on 2010-04-23
sudo apt-get install libapache2-mod-lisp

---

### Post by hickhack on 2010-04-26
Hi,

thanks for this first answer. Do you know a website where I can find an example that explains the installation of an initial website with Lisp?
I searched for examples or a detailed explanation but could not find anything.

---

### Post by hessiess on 2010-04-26
From my understanding, mod_lisp does nothing more than redirect the web traffic to a lisp application via a TCP socket, everything else has to be implemented in Lisp. I did look into Common Lisp Webdev some time ago, and found some examples, but unfortunately I cannot find them any more.

For developing web applications in common lisp you are better off using a Lisp web server like hunchentoot behind mod_proxy. There's more tutorials available for it, for example [http://www.newartisans.com/2007/11/a-quick-hunchentoot-primer.html](http://www.newartisans.com/2007/11/a-quick-hunchentoot-primer.html).

[http://www.weitz.de/hunchentoot/](http://www.weitz.de/hunchentoot/)

The results of my own Lisp webdev experiments were that, although Lisp is a good language for webdev, its currently more trouble than its worth. You may have better luck with newer lisps like Clojure, which doesn't have the problem of few 3rd party libs, as it can use anything which runs on the JVM.

---

