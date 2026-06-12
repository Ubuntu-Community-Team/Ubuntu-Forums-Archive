---
title: "Java apps no longer working"
date: 2010-07-30
forum: General Help
---

### Post by rowbird on 2010-07-30
Hi all, I am running Karmic, and all of my Java apps no longer work. What can I do to get them going again? I have Java version 1.5.0.  Thanks in advance.

---

### Post by chopinhauer on 2010-07-30
Are you using OpenJDK or the Sun JVM? The latter is available in Canonical's [Partner Repository](https://help.ubuntu.com/community/Repositories/Ubuntu#line-101).

---

### Post by rowbird on 2010-07-30
I am using sun-java6-jre, sun-java6-bin, and java-common, according to synaptic. Version 6.20-dljOubuntu-1.9.10 of jre according to synaptic properties to be exact.

---

### Post by chopinhauer on 2010-07-30
> **rowbird said:**
> I am using sun-java6-jre, sun-java6-bin, and java-common, according to synaptic. Version 6.20-dljOubuntu-1.9.10 of jre according to synaptic properties to be exact.

If both Sun Java and OpenJDK are installed on your system, Ubuntu links the 'java' binary to the version with highest priority. And OpenJDK has a bigger priority, but it breaks some applications. To test which JVM is 'java' symlinked to you can run:
```
sudo update-alternatives --config java
```

If more than one JVM is present on your system 'update-alternatives' offers you a menu to choose the default one.

If Sun's Java is already the one that is used, maybe you are missing some libraries to run your applications?

---

### Post by rowbird on 2010-07-31
Update. Java is not working with firefox. Outside of that my other apps are working fine. I would still like to find a solution.

---

### Post by stinkeye on 2010-07-31
> **rowbird said:**
> Update. Java is not working with firefox. Outside of that my other apps are working fine. I would still like to find a solution.
Have a look at this to get java working with firefox.
[**_[COLOR="DarkRed"]http://www.ghacks.net/2010/05/21/install-java-on-ubuntu-10-04/[/COLOR]_**]("http://www.ghacks.net/2010/05/21/install-java-on-ubuntu-10-04/")

---

### Post by rowbird on 2010-07-31
Hi, thanks for the tip, but no avail.I just ran the last command, cause it seemed that java was installed. I am not sure if it was in the about:plugins section. Is it supposed to be headered in bold? I am getting this in the applet window. "Your browser is completely ignoring the <APPLET> tag!"

---

### Post by dino99 on 2010-07-31
remove/purge everything about java then reinstall sun-java (canonical partner repo enabled)

---

### Post by rowbird on 2010-07-31
[Solved]You guys are awesome! Thanks a million. It worked like a charm.

---

