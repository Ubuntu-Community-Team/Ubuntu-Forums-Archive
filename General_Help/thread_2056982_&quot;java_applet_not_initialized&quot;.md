---
title: "&quot;java applet not initialized&quot;"
date: 2012-09-12
forum: General Help
---

### Post by kurja on 2012-09-12
Running latest Ubuntu LTS version and firefox 15 / chromium browser, I'm running into java issues at chess.com,  java applications such as finishing a game against computer won't work - it just says applet not initialized and suggests I down load java 7 from java.com.

Searching for java in software center, I have open JDK java runtime 6 and 7 (?!), icedtea java plugin and icedtea web starter installed.

....help?

---

### Post by QIII on 2012-09-12
Although I think we should all use OpenJDK when we can because it is open source, the fact is that OpenJDK is not universally recognized as Java by all developers and xml embedded in the website that is attempting to launch the applet may be looking specifically for Oracle Java 7 (or, more precisely, the Oracle Java 7 browser plugin).

In such cases, use of Oracle Java 7 may be required.

In the wiki in my signature, in the "Oracle Java 7" section, under "Command line methods" is a link "Using webupd8.org's strikingly simple method."

I recommend using that over lengthy manual install tutorials you can find on the web because webupd8 keeps its PPA up to date when Oracle puts out updates.  That means you get the updates to Oracle Java 7 as they come out when you do your normal Ubuntu updates, rather than having to watch for them and reinstall.  The PPA does not actually contain the Java packages because Oracle has withdrawn licenses for anyone to do that.  Rather, it scripts the download and installation process for you.

Although different versions of Java can coexist on a machine, Oracle Java 6 and OpenJDK 6 are due to reach end of life and are also vulnerable to attack.  It would be safest to uninstall OpenJDK 6 completely.  But leave OpenJDK 7.  Some web tutorials incorrectly say that you have to uninstall OpenJDK.  You don't.

---

### Post by Ubunterrific on 2012-09-12
> **kurja said:**
> Running latest Ubuntu LTS version and firefox 15 / chromium browser, I'm running into java issues at chess.com,  java applications such as finishing a game against computer won't work - it just says applet not initialized and suggests I down load java 7 from java.com.

Searching for java in software center, I have open JDK java runtime 6 and 7 (?!), icedtea java plugin and icedtea web starter installed.

....help?

```
 java -version 
```  just so we're clear?

Personally, i have no problems with java 7 from the webupd8 ppa.

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer 
```

---

### Post by kurja on 2012-09-12
```
java -version
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.4) (6b24-1.11.4-1ubuntu0.12.04.1)
OpenJDK Client VM (build 20.0-b12, mixed mode, sharing)

```

removed openjdk6 and did that again, no change.

ran ```
sudo add-apt_**-**_repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

now ```
java -version
java version "1.7.0_07"
Java(TM) SE Runtime Environment (build 1.7.0_07-b10)
Java HotSpot(TM) Client VM (build 23.3-b01, mixed mode)
```

And now it works. Thanks guys =)

---

### Post by Ubunterrific on 2012-09-12
> **kurja said:**
> ```
java -version
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.4) (6b24-1.11.4-1ubuntu0.12.04.1)
OpenJDK Client VM (build 20.0-b12, mixed mode, sharing)

```removed openjdk6 and did that again, no change.

ran ```
sudo add-apt_**-**_repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```now ```
java -version
java version "1.7.0_07"
Java(TM) SE Runtime Environment (build 1.7.0_07-b10)
Java HotSpot(TM) Client VM (build 23.3-b01, mixed mode)
```And now it works. Thanks guys =)

I love it when it all works harmoniously :popcorn:

---

