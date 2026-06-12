---
title: "Cannot Install/Update"
date: 2012-05-05
forum: General Help
---

### Post by anakluhur on 2012-05-05
I cannot install anything from Ubuntu Software Center. It always says 
"**Failed to download package files**
Check your internet connection.
Details
Failed to fetch httpU://au.archive.ubuntu.com/ubuntu/pool/main/i/icedtea-web/icedtea-plugin_1.2-2ubuntu1_all.deb Connection failed"

On Update Manager following message shows up everytime I want to click "Install Updates"
"**Failed to download package files**
Check your internet connection.
Details
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/u/upstart/upstart_1.5-0ubuntu7_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/u/upstart/upstart_1.5-0ubuntu7_amd64.deb) Connection failed"

I tried ubuntugeek method [here]("http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html").
I tried method 1 but nothing happened.
For method 2
adhi@adhi-RF511-RF411-RF711:~$ sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
[sudo] password for adhi: 
sudo: aptitude: command not found"

I am using Ubuntu 12.04 64 bit. Since installation update manager and ubuntu software center were smooth. But now suddenly this problem shows up.

Any help is appreciated.

[]("http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html")

---

### Post by anakluhur on 2012-05-05
Is this in any way is caused by Java?
There is this educational site called "Blackboard" in which you have to have Java plug-in to view its content.
So I installed OPENJDK Java 7 Runtime. But nothing happened.
I clicked more info, and ticked 
[http://i46.tinypic.com/2dhd311.png](http://i46.tinypic.com/2dhd311.png)

I verified the java [HERE]("http://java.com/en/download/testjava.jsp") but the version is not uptodate.
Is this some kind of virus? Baecause I still can't see the content of Blackboard eventhough I can use Keepvid.com (a site that requires Java). Maybe Blackboard need more updated version of Java?

I tried to remove the jave but the following message showed up
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/j/java-common/default-jre-headless_1.6-43ubuntu2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/j/java-common/default-jre-headless_1.6-43ubuntu2_amd64.deb) Connection failed
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre_6b24-1.11.1-4ubuntu2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre_6b24-1.11.1-4ubuntu2_amd64.deb) Connection failed
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/j/java-common/default-jre_1.6-43ubuntu2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/j/java-common/default-jre_1.6-43ubuntu2_amd64.deb) Connection failed
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/i/icedtea-web/icedtea-netx-common_1.2-2ubuntu1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/i/icedtea-web/icedtea-netx-common_1.2-2ubuntu1_all.deb) Connection failed
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/i/icedtea-web/icedtea-netx_1.2-2ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/i/icedtea-web/icedtea-netx_1.2-2ubuntu1_amd64.deb) Connection failed


And the weirdest thing is, there is only 25 rating of this software. **25** mind you!
Such important application only have 25 reviews.

---

### Post by anakluhur on 2012-05-05
Solved.
I use google chrome to view pdf content.
The server was down for maintenance.

---

