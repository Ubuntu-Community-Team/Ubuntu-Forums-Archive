---
title: "Problems installing the JavaDK - Netbeans."
date: 2010-09-14
forum: General Help
---

### Post by lsteamer on 2010-09-14
Hello. How's it going?

I'm a Newbie and I just got Ubuntu up and running today. So far I'm loving it! well, since i got it today I'm already installing programs.

& Normally use Netbeans to Develop the lines of code I write, So I downloaded JDK(jdk-6u21-linux-i586.bin) & Netbeans (Full Suite netbeans-6.9.1-ml-linux.sh)

And so I'm following the tutorial [found here.]("http://wiki.netbeans.org/InstallingNetbeansUbuntu7.04")

But when It comes to Update the Java Alternatives, I type this Command on the Terminal:

*sudo update-java-alternatives -s java-1.5.0-sun "/usr/lib/jvm/java-1.5.0-sun*" 

It gives me an error. This error:
[I]
sudo: update-java-alternatives: command not found.[/I]

I've tried Changing the *java-1.5.0-sun* to *java-1.6-sun* but with no avail.

Am I overlooking something? Is it a bug? What can I do to get it Installed.
And Since we're on it. How do I remove the installations from the system? From the Terminal and an "Unistall"? or something alike?

Thanks in advance.

---

### Post by howefield on 2010-09-15
> **lsteamer said:**
> It gives me an error. This error:
sudo: update-java-alternatives: command not found.

Try this instead...

```
sudo update-alternatives --config java
```

To uninstall software you can either use the terminal eg

```
sudo apt-get remove packagename
```

type

```
man apt-get
```

for an explanation of each of the options that can be used.

Or, load up Synaptic Package Manager and do it from the GUI if preferred.

---

