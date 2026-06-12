---
title: "Java not working anymore."
date: 2009-09-13
forum: General Help
---

### Post by Kamrua on 2009-09-13
> [FONT=Arial]I had Java installed.. I have no clue what I did. It's not working anymore.

I checked about: [/FONT][FONT=Arial][COLOR=Black]p[/COLOR][/FONT][FONT=Arial]lugins, it says I have Ic[/FONT][FONT=Arial]edTea Java Web browser plugin and Java(TM) Plug-in 1.6.0_16 installed.[/FONT][B][FONT=Courier New]
[/FONT][/B][FONT=Courier New][FONT=Verdana]
**Solved!**[/FONT]
[/FONT]

---

### Post by peetbull on 2009-09-13
If it doesn't work, that means that some package is uninstalled (less likely) or some settings are misconfigured (more likely).

Try this guide for a setup and configuration from scratch:

[http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/)

Make sure you follow all the steps, even they seem odd to follow.

Good luck!

---

### Post by geirha on 2009-09-13
It should be enough with just one of those steps, namely the command
```
sudo update-java-alternatives -s java-6-sun
```

You can run «update-java-alternatives --list» to get a list of all currently installed java versions, and you should see java-6-sun listed there. The command symlinks all commands, libraries and plugins for that specific version, into the proper places under /usr so that it becomes the default java version on your system.

---

### Post by newsoft on 2009-09-13
Probably a certain package is missing

---

### Post by Kamrua on 2009-09-13
Thanks guys! Got it working again :)

---

