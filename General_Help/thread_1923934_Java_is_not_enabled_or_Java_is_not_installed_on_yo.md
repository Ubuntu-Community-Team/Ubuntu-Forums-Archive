---
title: "Java is not enabled or Java is not installed on your machine. Please, enable Java"
date: 2012-02-11
forum: General Help
---

### Post by SuperFreak on 2012-02-11
I have signed up for a practice brokerage account with Questrade [http://www.questrade.com](http://www.questrade.com) , When I log on I get the following message > 	
Java is not enabled or Java is not installed on your machine. Please, enable Java in your browser or install Java.

I have looked in my Firefox (10.0.1) settings in preference and it appears as though Java is enabled (Under Content Javascript is checked).

Before I decide whether I want to use this brokerage I need to know how to correct the error message. Any help would be appreciated.

I believe I have Java 6 installed on my machine but I am not sure how to verify this

---

### Post by josephmills on 2012-02-11
Do you have JRE installed ? here is a [LINK](http://www.oracle.com/technetwork/java/javase/downloads/index.html) could be many other things also. but try that first if no workie please post all error's 
thanks

---

### Post by bluexrider on 2012-02-11
I use this PPA
```
deb [http://ppa.launchpad.net/ferramroberto/java/ubuntu](http://ppa.launchpad.net/ferramroberto/java/ubuntu) maverick main  

deb-src [http://ppa.launchpad.net/ferramroberto/java/ubuntu](http://ppa.launchpad.net/ferramroberto/java/ubuntu) maverick main 
```Then ```
sudo apt-get install sun-java6

```

---

### Post by savanna on 2012-02-11
Some Java apps will only run with Sun Java, not an open Java. Also, it's handy to install the JDK, so I usually install "sun-java6-jdk" (this will include the java-jre).

You may also have to setup various env vars in your ~/.bashrc:

export JAVA_HOME="/usr/lib/jvm/java-6-sun/jre"
export PATH="$PATH:$JAVA_HOME/bin"

---

### Post by Paqman on 2012-02-11
> **SuperFreak said:**
> 
I have looked in my Firefox (10.0.1) settings in preference and it appears as though Java is enabled (Under Content Javascript is checked).


Java and Javascript are two completely different things (I know, it's confusing). You need to install Java seperately if you haven't already. It's included in [ubuntu-restricted-extras]("apt:ubuntu-restricted-extras"), which is a handy package to install, or you can install it seperately by installing [icedtea6-plugin]("apt:icedtea6-plugin").

---

### Post by SuperFreak on 2012-02-11
Thanks everyone for your replies. I went to [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins) for directions on installing sun-java6-plugin and it seems to work fine now.

---

