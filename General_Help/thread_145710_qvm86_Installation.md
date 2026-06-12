---
title: "qvm86 Installation"
date: 2006-03-16
forum: General Help
---

### Post by AlexEagar on 2006-03-16
Does anyone have a link to a good qvm86 installation HOWTO for Ubuntu?

Is the installation the same as for kqemu?

[This is the best HOWTO]("http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/QemuCompilation") I have been able to find on compiling kqemu for Ubuntu.

It would be really nice if Ubuntu included this in the official repository for people who have to have access to Windows. It would be super nice if such a package also included host level networking available on the guest OS.

Alex Eagar

---

### Post by lha on 2006-03-17
[Here's]("http://oui.com.br/n/content.php?article.23") a script that installs qemu&kqemu. Kqemu cannot be put in the repos because the license of kqemu is a bit restrictive.

Installing qemu&qvm86 is almost like installing qemu&kqemu. You have to use cvs to get the source, though. You'll get a directory with files in it. Check the README file. It instructs you to apply a patch to qemu sources and then compile it.

---

