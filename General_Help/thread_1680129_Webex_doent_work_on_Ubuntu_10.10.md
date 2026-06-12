---
title: "Webex doent work on Ubuntu 10.10"
date: 2011-02-02
forum: General Help
---

### Post by sgooty on 2011-02-02
Hi,

Am new to Ubuntu, My env details

OS: Ubuntu 10.10 - 64 bit 
HP laptop 

For my some reason Webex doesnt work on FF and chrome. 

I have installed ubuntu-restricted-extras and sun-java6-plugin.

And i have tested that java jvm plugin is install on browser.

[http://www.javatester.org/version.html](http://www.javatester.org/version.html)

Thanks in advance

---

### Post by Don Barzini on 2011-02-02
Here is the Webex system requirements....

[http://support.webex.com/support/system-requirements.html](http://support.webex.com/support/system-requirements.html)

Have you tried it on 32 bit Ubuntu?

---

### Post by indothai on 2011-04-02
I contacted WebEx Support regarding this, Ubuntu 10.10 it does not support video conferencing afaik.

WebEx Support did say that if there is a demand for it, they will enable this feature.

I'm pretty disappointed about it :(

---

### Post by nossifer on 2011-05-03
It does indeed work, but you need to switch versions of Java.  I don't remember the version numbers offhand, but maybe that will get you started.  I was googling for a Natty / Unity solution and came across this thread.  Sorry for the lack of details, but I will post back when I find them.

EDIT:  it was working for me on 32bit 10.10

EDIT:  Try this, it sounds right from my memory.
sudo apt-get install sun-java6-jre sun-java6-plugin

---

### Post by nossifer on 2011-05-04
Hmm... this is more accurate I think.  (more memory + more google) :)

[http://www.zdnet.co.uk/blogs/jamies-mostly-linux-stuff-10006480/ubuntu-1004-lucid-lynx-and-java-10015534/](http://www.zdnet.co.uk/blogs/jamies-mostly-linux-stuff-10006480/ubuntu-1004-lucid-lynx-and-java-10015534/)

sun-java6 is no longer in the standard repositories. Installing ubuntu-restricted-extras will get you openjdk6 and icedtea, NOT Sun java6. There are still some significant applications, especially at the corporate security level, which do not work with openjdk and/or icedtea. To get around this problem, you have to remove openjdk and icedtea, and install sun-java6 from the "partner" repository.

---

