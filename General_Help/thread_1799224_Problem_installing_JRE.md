---
title: "Problem installing JRE"
date: 2011-07-07
forum: General Help
---

### Post by lakshmen on 2011-07-07
I needed to download JRE for to download youtube video. I used Q4Wine to download the JRE and it says it was downloaded. But when i went back to the website, it says Java not detected.
 
The website is [www.voobys.com](www.voobys.com)

what should i do?

---

### Post by oldos2er on 2011-07-07
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by lakshmen on 2011-07-07
my java is installed properly but it is still not detecting... in the preferences it says enable javascript. how do i enable java also?

---

### Post by oldos2er on 2011-07-07
Are you talking about Firefox? If you have java installed, Firefox should find it automatically, but you may need to restart Firefox or reboot your computer first. 

Can you run **java -version** in a terminal, and post the output?

---

### Post by lakshmen on 2011-07-07
when i type java-version in the terminal,

it says java-version: command not found

am i supposed to type java-version or something else?

---

### Post by Gyokuro on 2011-07-07
the command is: 

java -version

however you should install java via:


sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin

or by your system GUI package manager (synaptic,...)

---

### Post by lakshmen on 2011-07-07
THe output is

java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.7) (6b20-1.9.7-0ubuntu1)
OpenJDK Server VM (build 19.0-b09, mixed mode)

---

### Post by gakon77 on 2011-07-07
It may sound a silly question, but is possible that java only runs in gnome?

---

### Post by oldos2er on 2011-07-07
Some apps seem to respond better to Sun java rather than the OpenJDK package. To install sun-java6-jre, you need to enable the partner repository first.

---

### Post by gakon77 on 2011-07-07
> **gakon77 said:**
> It may sound a silly question, but is possible that java only runs in gnome?

Forget about it, I'm just running the application in xfce.

---

### Post by gakon77 on 2011-07-07
> **oldos2er said:**
> Some apps seem to respond better to Sun java rather than the OpenJDK package. To install sun-java6-jre, you need to enable the partner repository first.

Which are those repositories, where do I find them?

---

### Post by oldos2er on 2011-07-07
In Synaptic, Settings, Repositories, Other Software, tick the boxes next to 'Canonical Partners'. Are you really using 9.10?

---

### Post by lakshmen on 2011-07-07
So guys is my version correct? is there anything i should do? should i download the sun java?

---

### Post by lakshmen on 2011-07-07
will following this link [http://www.mkyong.com/java/how-to-install-java-jdk-on-ubuntu-linux/](http://www.mkyong.com/java/how-to-install-java-jdk-on-ubuntu-linux/) be good?

---

### Post by Gyokuro on 2011-07-08
The guide is good but everyone posted you already how to install java via the system package managers. Therefore please let us know with which application are you trying to download the videos?

---

### Post by lakshmen on 2011-07-08
I downloading youtube videos from voobys,com and playing it using Flv.

---

### Post by lakshmen on 2011-07-08
i get this 

Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source 

when
sudo apt-get install sun-java6-jre sun-java6-plugin

---

### Post by Gyokuro on 2011-07-08
Ok,

can you please post your:

/etc/apt/sources.list

---

### Post by oldos2er on 2011-07-08
> **lakshmen said:**
> i get this 

Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source 

when
sudo apt-get install sun-java6-jre sun-java6-plugin

If you added the partner repository already, you need to run **sudo apt-get update**

---

### Post by lakshmen on 2011-07-08
it says 
bash: /etc/apt/sources.list: Permission denied

---

### Post by fernandoc1 on 2011-07-08
I have done this documentation:
[https://docs.google.com/document/pub?id=1JzkQTZJaCBiqYws37gGs1hT8TP43SzrvYM6YGxqchYc](https://docs.google.com/document/pub?id=1JzkQTZJaCBiqYws37gGs1hT8TP43SzrvYM6YGxqchYc)

If you are using Ubuntu 10.10 or earlier, follow the steps at the beginning of the document. Otherwise follow the information at the bottom of the document.
These steps worked for me.

---

### Post by TBABill on 2011-07-08
I had a similar instance of it not working after installing Sun Java plugin back in either 9.10 or 10.04 and I had to go into synaptic and remove the package icedtea-plugin because it's the open source java and would not even allow Chromium to start up. 
 
As stated previously, change sources to add the partner repos (not sure if that's what it's called from my 9.10 time), then ```
sudo apt-get update
``` and then do the install of the Sun Java plugin (or find it in synaptic, mark for installation and click apply)

---

### Post by oldos2er on 2011-07-08
> **lakshmen said:**
> it says 
bash: /etc/apt/sources.list: Permission denied

Should be **cat /etc/apt/sources.list**

---

### Post by gakon77 on 2011-07-08
It's strange, because since I use Karmic Koala, can't remember having to install anything related to java. 
Now when running squeeze in a virtual machine, I have an application in particular that doesn't seem to work fine because is missing java.

Here, [http://openjdk.java.net/faq/](http://openjdk.java.net/faq/) I found the answer to the question above, but whatever I tried to do to install it -java web page, [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) or forums-, couldn't succeed. 

Still to check harder with squeeze anyway because the Karmic Koala comes with java, it may be something else.

---

### Post by gakon77 on 2011-07-08
> **gakon77 said:**
> Still to check harder with squeeze anyway because the Karmic Koala comes with java, it may be something else.

This is what eventually helped me to have [http://www.brettspielwelt.de/](http://www.brettspielwelt.de/) working. Check this out [http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)

Now I wonder how to make it work with OpenJDK?

Isn't it nice GNU/Linux!
:D

---

