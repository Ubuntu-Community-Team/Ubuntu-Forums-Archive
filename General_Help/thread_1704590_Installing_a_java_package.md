---
title: "Installing a java package"
date: 2011-03-10
forum: General Help
---

### Post by Blastronomy on 2011-03-10
Hello,

I recently (today) starting using unbuntu as my OS because I was having major problems using Windows Vista and I don't have the resources to purchase any new OS. But anyways...I am  beginning java developer and I am using Eclipse. I need to somehow import the BreezyGUI into my java files before i am able to use the Import function within eclipse.

Can anyone help me out?

---

### Post by doas777 on 2011-03-10
its been a while since I've done it, but you can add additional jar files to java's build path in the eclipse settings when your workspace is open. after that you should be able to import classes in your libraries. sorry I can't give you click-by-click.

you may also want to install the sun jdk instead of openjdk. 
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
[http://www.clickonf5.org/linux/how-install-sun-java-ubuntu-1004-lts/7777](http://www.clickonf5.org/linux/how-install-sun-java-ubuntu-1004-lts/7777) 
(note, for maverick, change the articles add-app-repository line to say maverick not lucid).

here are some resources for eclipse in ubuntu
[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)
[https://help.ubuntu.com/community/EclipseWebTools](https://help.ubuntu.com/community/EclipseWebTools)

---

### Post by Blastronomy on 2011-03-10
Thank you! I am also a little new to Eclipse since my class has learned on BlueJ. I'll see what I can do. I do have the java.sun files. All the stuff I grabbed were all straight from the source. I was just used to adding the java package to the java source file on a mac and I cant seem to locate the java source file on unbuntu

---

### Post by doas777 on 2011-03-10
> **Blastronomy said:**
> Thank you! I am also a little new to Eclipse since my class has learned on BlueJ. I'll see what I can do. I do have the java.sun files. All the stuff I grabbed were all straight from the source. I was just used to adding the java package to the java source file on a mac and I cant seem to locate the java source file on unbuntu
what version do you have? 

this might help. not sure. do you need to add it for all apps, or just your current project?:
[http://www.wikihow.com/Add-JARs-to-Project-Build-Paths-in-Eclipse-%28Java%29]("http://www.wikihow.com/Add-JARs-to-Project-Build-Paths-in-Eclipse-%28Java%29")

---

### Post by Blastronomy on 2011-03-10
hmmm...for ecplipse? I have helios i believe.

---

### Post by Blastronomy on 2011-03-10
ok...so i was able to add Breezy as Reference library in eclipse using those instructions...but for some reason it still wont let me import BreezyGUI.*;

---

### Post by doas777 on 2011-03-10
have you build once? that might make a difference. 
you can try cracking open the jar (its just an archive file), and making sure that there is a BreazyUI.class file.

---

### Post by Blastronomy on 2011-03-10
there is a console.class file.

Maybe it is because i have Breezy as a zip file?

---

### Post by doas777 on 2011-03-10
> **Blastronomy said:**
> there is a console.class file.

Maybe it is because i have Breezy as a zip file?
well, zips should work as well as I understand it, but you could try extracting it and jar-ing it with archive manager. what are the permissions on the zip file?

---

