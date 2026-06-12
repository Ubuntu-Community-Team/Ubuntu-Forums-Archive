---
title: "Latest Java Update"
date: 2010-11-17
forum: General Help
---

### Post by dmurphy787 on 2010-11-17
[B]Hello,
Java 6.18 came installed on Ubuntu 10.04 and I have followed the instructions from [http://www.java.com/](http://www.java.com/) to install the latest Java version "Linux RPM (self-extracting file)" = "jre-6u22-linux-i586.rpm" and I have installed the file "jre-6u22-linux-i586.bin" to the /usr/java directory as shown at [http://www.java.com/](http://www.java.com/).
When I run the check your Java version at Java.com it still says I have version 6.18.
Can anyone please help me to see what I have done wrong, as I would like to remove 6.18 and replace with 6.22.
Ps I have shut my browser down and restarted after install but it still doesnt seem to make a difference.
I am very grateful for anyones help.[/B]

---

### Post by lykeion on 2010-11-17
The latest version of Java in Lucid it's 6.22. You shouldn't have to use any guides on some web page even though it's java.com (and it's often a bad idea to do that anyway).

So do this to update to 6.22 the official way.
1) Remove the previous manually installed 6.22
2) Enable the partner repository
```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```
3) Update
```
sudo apt-get update
```
4) Install
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```
5) Remove the OpenJDK Java browser plugin
```
sudo apt-get remove icedtea6-plugin
```

---

