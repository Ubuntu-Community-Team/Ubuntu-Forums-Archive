---
title: "Sun Java dont work after updates"
date: 2011-12-16
forum: General Help
---

### Post by Hannu Mikael on 2011-12-16
Ubuntu 10.04.3.
There is the same problem in Lubuntu, but I dont understand, how I can fix it.
My browsers are Chromium 15.0.874.106, and Firefox 3.6.24.
I really need Sun Java, and OpenJDK is not solution.
This done already few times:

[http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html)

Edit: 
Reason for waiting:
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/905026](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/905026)

---

### Post by 2F4U on 2011-12-16
And what exactly is the problem?

---

### Post by HannuMR on 2011-12-22
> **2F4U said:**
> And what exactly is the problem?

My bank use in internet only Sun Java, and I can not pay my bills.

This is serious for me:

[http://lwn.net/Articles/472466/](http://lwn.net/Articles/472466/)

(I am Hannu Mikael)

---

### Post by TBABill on 2011-12-22
You can go and download Oracle's Java from their website and install per their instructions.

---

### Post by Karlchen on 2011-12-22
Based on my own experience, I tend to suggest: Follow this step by step instruction on how to download and install the genuine Oracle Java runtime software on Ubuntu: [**Oracle (Sun) Java JRE for Ubuntu, Linux Mint and Debian**]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-INSTALL-MANUALLY")

---

### Post by sammiev on 2011-12-22
> **Karlchen said:**
> Based on my own experience, I tend to suggest: Follow this step by step instruction on how to download and install the genuine Oracle Java runtime software on Ubuntu: [**Oracle (Sun) Java JRE for Ubuntu, Linux Mint and Debian**]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-INSTALL-MANUALLY")

+1 used this method for a few years now.

---

### Post by 73ckn797 on 2011-12-22
This link will also give the solution: [https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by QIII on 2011-12-22
Yes.  That is the solution.

I had contact with one of the maintainers of that tutorial a couple of days ago.  Some issues I didn't like with it were resolved recently, much to my relief.  I had directed people to the tutorial with a warning not to do something as directed there, but they took that part out.

I'm going to suggest a similar (or additional) set of instructions for those who want to develop Java software on Debian-based platforms for installing the JDK after the JRE has been installed.  Very simple after following the tutorial referenced above.

(BTW:  I tested the tutorial on Bodhi Linux, and it works fine.  For anyone interested in installing Sun's JRE and JDK on Fedora, I can direct you to the step-by-step for that, too.)

---

