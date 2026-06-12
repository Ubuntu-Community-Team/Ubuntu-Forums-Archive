---
title: "plugin is bugged"
date: 2011-06-17
forum: General Help
---

### Post by 28s on 2011-06-17
Hello,
I have been trying to play runescape the last couple of days, and I still get get it to work; every time I try to play it says I need the JRE 6 u26 plugin but when I click next, it doesn't work as it says not available. I have installed all of the latest java updates, and it still never works. Any help would be appreciated, thank-you

---

### Post by gandaran on 2011-06-17
which java have you installed? sun-java or openjdk-java? both are available from the software center to install and runescape only works with sun-java, better to remove openjdk and keep only sun-java.

---

### Post by 28s on 2011-06-17
Thank-you for replying.
I have sun java 6 installed; whenever I press 'play' it says additional plugin required, and says JRE 6 u26.
I click next to install it, and it instantly says not available.
I read that you had to install firefox, sun java 6 etc. and I did without success.
Any help is appreciated, thank-you

---

### Post by gandaran on 2011-06-17
> **28s said:**
> Thank-you for replying.
I have sun java 6 installed; whenever I press 'play' it says additional plugin required, and says JRE 6 u26.
I click next to install it, and it instantly says not available.
I read that you had to install firefox, sun java 6 etc. and I did without success.
Any help is appreciated, thank-you
you have the plugin installed too?
```
sudo apt-get install sun-java6-plugin
```
also check java version
```
java -version
```

---

### Post by 28s on 2011-06-17
Thanks again.
I installed all of the java etc. through synaptic; I tried the java -version command you said and got: 
$ java -version
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

---

### Post by clhsharky on 2011-06-17
28s

Are you using Ubuntu 8.04?


Sharky

---

### Post by 28s on 2011-06-18
Yeh sharky I am using ubuntu 8.04 hardy heron.
Is this why I cannot install JRE 1.6 u26?

---

### Post by gandaran on 2011-06-18
> **28s said:**
> Yeh sharky I am using ubuntu 8.04 hardy heron.
Is this why I cannot install JRE 1.6 u26?
8.04 isn't supported anymore, upgrade to 10.04 or 11.04
or you can still install java u26 downloading the bin file from oracle java website.

---

### Post by 28s on 2011-06-18
Thank-you for replying, how do I actually upgrade because it says that I should set it to show new distribution releases, but I cannot see this anywhere?

p.s. I have also checked the update manager check button, and my system is up to date, though when I click check again, it doesn't say that a new OS is available?

Any help is appreciated, thanks

---

### Post by 28s on 2011-06-18
Hello,
I also just tried to upgrade through the terminal and got the result of, 'no new release'
what is going on?
Any help?

---

