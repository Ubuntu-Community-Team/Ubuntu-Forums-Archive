---
title: "Need help installing a pluging for Firefox"
date: 2012-04-10
forum: General Help
---

### Post by ubuntu27 on 2012-04-10
Hello all. A new term started for me in College and it requires the students to install a plugin in the browser.

The company [does not support Linux]("http://www.aleks.com/support/system_requirements"), but gives instruction anyway for those who are "experts"


The instructions that they provide are from Sun Java, I don't know what to change for OpenJDK or IceTea. (Which directory?)



[Here is the instruction for Linux]("http://www.aleks.com/downloads/linux_jvm")


Thank you :popcorn:

---

### Post by mikewhatever on 2012-04-11
Try '/usr/lib/jvm/java-1.6.0-openjdk/jre/lib/ext/'. That seems to be the path on Lucid, and it should be the same or similar on other releases.

---

### Post by fiatveritas on 2012-04-11
Did you try opening the file with Ubuntu Software Center? Usually, that works if not you have to brute force it by typing commands at the terminal.

---

### Post by ubuntu27 on 2012-04-28
I tried mikewhatever solution and it works.

Thanks guys.


PS: For Ubuntu [Linux] **64-bit**, it is:

/usr/lib/jvm/java-1.6.0-openjdk-amd64/jre/lib/ext

---

