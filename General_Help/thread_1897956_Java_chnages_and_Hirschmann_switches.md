---
title: "Java chnages and Hirschmann switches"
date: 2011-12-20
forum: General Help
---

### Post by stanbrown on 2011-12-20
I have several Ubuntu LTS machines that we use to support, among other things, a number of network switches by a vendor called Hirschmann. These switches can be configuresd by using a web interface. Yhis web interface, as I understand it consists of a JAVA ( applet ?) that is downloaded to the browser and executed there. Then the commands are actually sent to the switch using SNMP.
 
I read the post on slashdot this weekend about Ubuntu's changes regarding Sun's JAVA, and whne I went to do my rotuine "apt-get dist-upgrade" yesterday morning, I thought I looked very carefully to see if any packages were going to be dleted by this, as I wnated to avoid breaking access to these switces.
 
Yesterfday aftrenoon, I got an alarm from one of the switchesand wanted to log in to it to see what was in the log. Ubfurtantely, when I pointed Firefox ar this switch, I got a message about needing to downlaod and install JAVA. I want to emphasize that I had used this machine as recently as last friday to access a number of these switches, and I have not change anything on the switches.
 
I am not all that familar with JAVA, and how it works, and how it interacts with the browser (Firefox) to preform this functionality, so could some kind person please advise me what I need to do to start troubleshooting/resolving this issue?

---

### Post by Palmstroem on 2011-12-20
Hi stanbrown,

in order to communicate with your switches you need a java plugin for your browser (firefox or something). This plugin can no longer be installed from firefox directly.

Solution 1: install OpenJDK and the IcedTea plugin from the Ubuntu repository. May work.

Solution 2: if you really need the "original" Oracle (Sun) Java then follow this guide: [http://sites.google.com/site/easylinuxtipsproject/java#TOC-Removal1]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-Removal1")

Hope this helps.

---

### Post by stanbrown on 2011-12-20
> **Palmstroem said:**
> Hi stanbrown,

in order to communicate with your switches you need a java plugin for your browser (firefox or something). This plugin can no longer be installed from firefox directly.

Solution 1: install OpenJDK and the IcedTea plugin from the Ubuntu repository. May work.

Solution 2: if you really need the "original" Oracle (Sun) Java then follow this guide: [http://sites.google.com/site/easylinuxtipsproject/java#TOC-Removal1](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Removal1)

Hope this helps.

Thanks for the reply.

I have a couple of folowup questions, if I might.

1) Which specific packages should I install to see if this solution works for us?

2) Any idea why the apt-get dist-upgrade broke this, as I am almost 100% certain it's summary did not show deleting any packages. Is this a "stealth delete" that is hidden from the user, and is it even actually in force yet?

Thanks, again.

---

### Post by stanbrown on 2011-12-20
Sorry for the 2nd followup, I should have followed your link before I replied the first time. 

It appears that that link refers to how to manually install the Sun/Oracle version on Ubuntu 32 bit systems. I neglected to mention that ours are AMD 64bit systems. Does that change what I need to do to re-install the original Sub?Oracle version (assuming Opne-JDK does not work for us)?

---

### Post by Pjotr123 on 2011-12-20
License issues prevent Ubuntu from packaging newer versions of Oracle Java. 6u26 was still allowed, but has become insecure. That's why it has been removed from the repo's, and disabled by updates on machines that had 6u26 installed.

When you still want Oracle Java, you have two options:

Install by hand (moderately easy):
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)
(as already suggested by Palmstroem)

Left column for 32 bit, right column for 64 bit.

Install by means of a script (very easy):
This script automatically pulls the newest Oracle Java from the Oracle website and installs it (still allowed by the license, comparable with the procedure for Adobe Flash Player).
[http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)

Works both for 64 bit and for 32 bit.

This script has been made by a respected member of the Dutch Ubuntu community, a programmer. I have tested it myself, and it works fine.

---

### Post by stanbrown on 2011-12-20
OK, I have installed the following packages on one of the affected machines:

openjdk-6-jre
 openjdk-6-jre-headless
openjdk-6-jre-lib
icedtea-6-jre-cacao
icedtea6-plugin

Now when I try to connect to the switches using Firefox, I get the expected login prompt, but when I enter the correct credentials,, I get an error message about a missing class.

If I run the jar file provided by Hirschmann like this:

java -jar marL2P07002_00.jar

Then I can connect top the switch and manage it.

Can anyone explain why this works, and invoking from the browser does not?

---

### Post by stanbrown on 2012-01-11
> **Pjotr123 said:**
> License issues prevent Ubuntu from packaging newer versions of Oracle Java. 6u26 was still allowed, but has become insecure. That's why it has been removed from the repo's, and disabled by updates on machines that had 6u26 installed.

When you still want Oracle Java, you have two options:

Install by hand (moderately easy):
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)
(as already suggested by Palmstroem)

Left column for 32 bit, right column for 64 bit.

Install by means of a script (very easy):
This script automatically pulls the newest Oracle Java from the Oracle website and installs it (still allowed by the license, comparable with the procedure for Adobe Flash Player).
[http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)

Works both for 64 bit and for 32 bit.

This script has been made by a respected member of the Dutch Ubuntu community, a programmer. I have tested it myself, and it works fine.

Thanks for the advice. I was able to install the Sun Java package on one of my machines using the duinsoft link mentioned above. I can configure my switches from this machine fine now.

Unfortuntely this does not completly solve my proble. The machine that I was able to do this on has direct access to the outside world. Most of my machines do not, and I update them using apt-cacher-ng. On the clinets I configure /etc/apt/apt.conf.d/01proxy  to have the address and port of the machine that has access to the outside workd, and they then are able to use it's access to obtain the .debs, etc.

I was able to install the key on these "inside" machines by using apt-key export on the main machine and app-key add on the "inside" machine. Then I can install this package. But, when the package tries to download the Java binary from Oracle, it fails of course.

Is there a way I can tell the "inside" machines to use a proxy to download the file from Oracle?

---

### Post by stanbrown on 2012-01-11
I worked on this a bit more this morning, Acorddig to the apt-get documentation, I should be able to set up a temporary proxy using this syntax:

 export http_proxy=http://machine:3128

When I do this, I am able to use lynx to access, for instance Google from the "inside" machine, yet when I try to add the package, at the download stage I get this:
Creating /var/cache/update-sun-jre (if necessary) . . .
Reset switch given - removing info page . . .
Options for wget: -nd -v --progress=dot:binary -t 3 -T 15
Downloading info page from [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp) . . .
--2012-01-11 07:38:56--  [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)
Resolving [www.java.com](www.java.com)... 137.254.16.66
Connecting to [www.java.com|137.254.16.66|:80](www.java.com|137.254.16.66|:80)... failed: Connection refused.
update-sun-jre: failed to download info page


It appears as if the proxy environment variable is not being honored during the package installation.

Any suggestions?

---

