---
title: "Synaptic Package Manager Issue"
date: 2011-02-11
forum: General Help
---

### Post by kolahalb on 2011-02-11
Hi, I have just installed U10.10 (dual partition Ubuntu and Windows) and was installing some softwares (k3b, emacs latex editor etc by 'sudo apt-get install') to my / directory. There was some problem with emacs installation and it stopped. I wanted to reinstall the package using synaptic package manager when I got the following error messages:

======================
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
======================
Running "sudo dpkg --configure -a", only initiates a newline with ">"

I am not sure how to get around the problem...Can anyone please suggest a solution?

-Kolahal

---

### Post by kolahalb on 2011-02-11
Hi everyone, I have resolved the issue...I had put a ' after "... -a" accidentally...

---

