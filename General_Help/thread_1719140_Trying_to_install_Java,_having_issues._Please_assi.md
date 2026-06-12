---
title: "Trying to install Java, having issues. Please assist. :)"
date: 2011-04-01
forum: General Help
---

### Post by DMHarms on 2011-04-01
Howdy, everyone.

I'm *a little* new to Ubuntu, and definitely new to the 11.04 beta (what I'm running currently).

What I'm having trouble with, is installing Java.

I'd just like to know if there is a simple way to install java, so I can run my Java apps/clients/web start stuff in Ubuntu (which would make my defection from Windows 7 complete).

Thank you in advance, I greatly appreciate it. :)

---

### Post by Enigmapond on 2011-04-01
```
sudo apt-get install ubuntu-restricted-extras
```

This will install java...

Cheers!

---

### Post by Azdour on 2011-04-01
Hi,

Installing 'ubuntu-restricted-extras' will install other packages as well as the openjdk. 

My advice would be to use the synaptic package manager to install either openjdk-6-jdk or sun-java6-jdk.

In Ubuntu 10.04 (maybe the same in 11.04), if either of these are not showing then:

[LIST=1]
[*] Go to System | Administration | Software Sources.
[*] Click on the Other Software tab.
[*] Tick both the archive.canonical.com partner
[*] Open the Synaptic Package Manager and you should now be able to find them
[/LIST]

Personally I have installed the Sun JDK because I have had several JVM crashes using openjdk.

---

### Post by Spyderkid on 2011-04-01
don't install from site if you download the wrong package it can cause a re-install situation which I experienced a while ago, (I got the binary self-extracting file instead of the deb one, so it seriously messed up the computer)

---

### Post by stinkeye on 2011-04-01
See here for installing Sun java.
[**_[COLOR="DarkRed"]http://sites.google.com/site/easylinuxtipsproject/java[/COLOR]_**]("http://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by DMHarms on 2011-04-01
> **Enigmapond said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```This will install java...

Cheers!

Alright, I got Open JDK Java 6 runtime installed...but I still can't start up my .jnlp files. If it would help, this *is* a game launcher client, but the launcher (as far as I know) doesn't use any renderers, it's just a launcher.

Thanks for that simple solution, but yes, I still can't launch my java application.

---

### Post by N33k on 2011-04-08
Uninstall OpenJDK completely. Go to the Synaptics Package Manager, type "sun-java6" in the search box, and mark "sun-java6-bin", "sun-java6-jre", and "sun-java6-plugin" for installation. Click "Apply" and let them install. You shouldn't have any more problems after that.

---

### Post by DMHarms on 2011-04-09
> **N33k said:**
> Uninstall OpenJDK completely. Go to the Synaptics Package Manager, type "sun-java6" in the search box, and mark "sun-java6-bin", "sun-java6-jre", and "sun-java6-plugin" for installation. Click "Apply" and let them install. You shouldn't have any more problems after that.

Thank you, N33k. That worked PERFECTLY, and was very simple.

Thanks to everyone else, too...but this last tip was the one that worked. =)

---

### Post by N33k on 2011-04-11
Glad to help.  I'm a new user of the forums here, but I hope to contribute a lot more.

---

