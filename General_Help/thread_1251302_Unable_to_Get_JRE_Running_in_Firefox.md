---
title: "Unable to Get JRE Running in Firefox"
date: 2009-08-27
forum: General Help
---

### Post by CarlosinFL on 2009-08-27
Every time I try to connect via Webex which requires JRE on my Firefox browser, it fails and tells me the following:

"Meeting Center cannot be installed because Java is disabled in your Web browser. Please enable Java in your browser, and then click Set Up again. For instructions on enabling Java, refer to your browser's online help.

If Java cannot be enabled for any reason, you can download the manual installer and install it from your desktop by double-clicking the installer icon.
"

Can someone please tell me what I am doing wrong in 9.04? I installed "sun-java6-jre "sun-java6-plugin" "sun-java6-bin" "sun-java6-fonts" on my Ubuntu system and I can't get this to connect.

When I try to test my Java at the following URL:

[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

I seem to load the Java fine so I don't know what the problem is...

---

### Post by scouser73 on 2009-08-27
To install Java, go to Syanptic Package Manager, in the search box type **Sun Java** & select **Mark For Installation**, now do the same for **sun-java6-bin**, **sun-java6-jre** & **sun-java6-plugin**.  Now click **Apply**, a small dialogue box will appear, then click **Apply** again.

---

### Post by CarlosinFL on 2009-08-27
I don't use Synaptic but I did install all the following:

```
cwilliams@tunafish:~$ sudo apt-cache policy sun-java6-jre sun-java6-plugin sun-java6-bin
sun-java6-jre:
  Installed: 6-14-0ubuntu1.9.04
  Candidate: 6-14-0ubuntu1.9.04
  Version table:
 *** 6-14-0ubuntu1.9.04 0
        500 http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
        100 /var/lib/dpkg/status
     6-13-1 0
        500 http://us.archive.ubuntu.com jaunty/multiverse Packages
sun-java6-plugin:
  Installed: 6-14-0ubuntu1.9.04
  Candidate: 6-14-0ubuntu1.9.04
  Version table:
 *** 6-14-0ubuntu1.9.04 0
        500 http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
        100 /var/lib/dpkg/status
     6-13-1 0
        500 http://us.archive.ubuntu.com jaunty/multiverse Packages
sun-java6-bin:
  Installed: 6-14-0ubuntu1.9.04
  Candidate: 6-14-0ubuntu1.9.04
  Version table:
 *** 6-14-0ubuntu1.9.04 0
        500 http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
        100 /var/lib/dpkg/status
     6-13-1 0
        500 http://us.archive.ubuntu.com jaunty/multiverse Packages

```

How can I test to make sure my browser plugin works and why am I getting the error then when I try and connect to Webex sessions...???

---

### Post by scouser73 on 2009-08-27
To test your Java is installed and working correctly, go to the [[COLOR="Red"]**Java Test Website**[/COLOR]]("http://www.java.com/en/download/help/testvm.xml").

---

### Post by CarlosinFL on 2009-08-27
Did you see my attached screen shot? The Java site said I have it working properly and I attached the screen shot but I can't do any Java Webex sessions...they all fail.

---

