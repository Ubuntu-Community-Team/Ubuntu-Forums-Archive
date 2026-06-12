---
title: "The package system is broken"
date: 2010-04-08
forum: General Help
---

### Post by Hastings101 on 2010-04-08
I was installing Ubuntu Restricted Extras in the Software Center and Ubuntu froze.  After waiting a while I just shut the computer off and restarted.  Now I get a warning saying that The package system is broken and that I should fix the packages in Synaptic.  Everytime I use Synaptic to fix them it comes up with an error like this:

E: /var/cache/apt/archives/java-common_0.30ubuntu5_all.deb: subprocess dpkg-deb --control returned error exit status 2
E: /var/cache/apt/archives/sun-java6-jre_6-15-1_all.deb: subprocess dpkg-deb --control returned error exit status 2
E: /var/cache/apt/archives/odbcinst1debian1_2.2.11-16ubuntu1_amd64.deb: subprocess dpkg-deb --control returned error exit status 2
E: /var/cache/apt/archives/unixodbc_2.2.11-16ubuntu1_amd64.deb: subprocess dpkg-deb --control returned error exit status 2


So what do I do?  I've tried rebooting and trying again but that didn't make any difference.

---

### Post by cogier on 2010-04-08
Try this in Terminal ```
sudo apt-get install -f
```. Type ```
man apt-get
``` for more help with this command.

---

### Post by Hastings101 on 2010-04-08
Using "sudo apt-get install -f" shows a lot of errors too.  Aftering saying yes to the install it shows up with a bunch of text (sorry for length):

E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/java-common_0.30ubuntu5_all.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/sun-java6-jre_6-15-1_all.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/odbcinst1debian1_2.2.11-16ubuntu1_amd64.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/unixodbc_2.2.11-16ubuntu1_amd64.deb
debconf: apt-extracttemplates failed: Bad file descriptor
dpkg-deb: `/var/cache/apt/archives/java-common_0.30ubuntu5_all.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/java-common_0.30ubuntu5_all.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: `/var/cache/apt/archives/sun-java6-jre_6-15-1_all.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/sun-java6-jre_6-15-1_all.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: `/var/cache/apt/archives/odbcinst1debian1_2.2.11-16ubuntu1_amd64.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/odbcinst1debian1_2.2.11-16ubuntu1_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: `/var/cache/apt/archives/unixodbc_2.2.11-16ubuntu1_amd64.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/unixodbc_2.2.11-16ubuntu1_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/java-common_0.30ubuntu5_all.deb
 /var/cache/apt/archives/sun-java6-jre_6-15-1_all.deb
 /var/cache/apt/archives/odbcinst1debian1_2.2.11-16ubuntu1_amd64.deb
 /var/cache/apt/archives/unixodbc_2.2.11-16ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Soul-Sing on 2010-04-08
Did you "forget" to sign the license that comes with sun java?
If so remove sun java with: ```
sudo dpkg --remove --force-remove-reinstreq <exact name of the package>
```

---

### Post by cogier on 2010-04-08
You could try the same command with **remove** instead of install and see if that helps. If not it will take a more knowledgeable person than I to assist you. Sorry:(

---

### Post by Hastings101 on 2010-04-08
> **leoquant said:**
> Did you "forget" to sign the license that comes with sun java?
If so remove sun java with: ```
sudo dpkg --remove --force-remove-reinstreq <exact name of the package>
```

Yep this was the problem. I must have missed the box when I went to agree with the license and this fixed the problem.  Feel kinda stupid now but glad the problem's fixed.  Thanks! :)

---

### Post by L4nce0 on 2010-05-27
Okay so I'm having the exact problem, but I don't know where to find the package name..........

---

### Post by L4nce0 on 2010-05-28
bump

---

