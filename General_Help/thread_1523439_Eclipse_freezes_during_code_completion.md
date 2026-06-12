---
title: "Eclipse freezes during code completion"
date: 2010-07-03
forum: General Help
---

### Post by freon2 on 2010-07-03
Hi,
my version of Java is "1.6.0_20", it is the Java from package sun-java6-jdk from the repository.
Version of Eclipse is 3.5.2 Galileo (but the new Helios has the same problem)

The problem is that code  completion (ctrl + space) freezes the Eclipse everytime I want to use it. There is nothing in the log (${WORKSPACE}./metadata/.log) and it seems to me like deadlock or something. When I run the Eclipse as root the problem don't occur.
I tried to create new workspace, reinstall the eclipse, this advice ([http://www.eclipse.org/forums/index.php?t=msg&goto=530816&](http://www.eclipse.org/forums/index.php?t=msg&goto=530816&)) but nothing worked.

Help me please.

---

### Post by Cholsen on 2010-07-07
I have the same issue on Lucid x64, running Eclipse Helios (not from the repository) on OpenJDK 6b18-1.8-0ubuntu1. Starting Eclipse as root does not solve the problem for me. :(

---

### Post by yevgenys on 2011-05-15
Hi,

If your eclipse is stuck, I would suggest opening a bug in eclipse bugzilla ([https://bugs.eclipse.org/bugs/enter_bug.cgi](https://bugs.eclipse.org/bugs/enter_bug.cgi)).

Please refer to: [http://wiki.eclipse.org/How_to_report_a_deadlock](http://wiki.eclipse.org/How_to_report_a_deadlock)

On linux you can run a script that every second run jstack on eclipse pid, it should look like this:
while [ true ] ; do  jstack pid > `date "+%Y%m%d.%H%M.%S"` ; sleep 1; done

Thanks,
Yevgeny

---

