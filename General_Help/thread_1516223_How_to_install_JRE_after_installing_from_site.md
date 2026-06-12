---
title: "How to install JRE after installing from site"
date: 2010-06-23
forum: General Help
---

### Post by Tombgeek on 2010-06-23
Hey there

I downloaded Java from the site itself, and I got a 20mb file named jre-6u20-linux-i586.bin
How do I install it?

Sorry, I am a new to linux

---

### Post by howefield on 2010-06-23
Enable the partner repository and installing it with Synaptic Package Manager would be the easiest way.

System > Administration > Software Sources > Other Software tab and check the box beside the partner repository.

Reload and install, this way, you stay updated as new versions are released.

---

### Post by Tombgeek on 2010-06-23
> **howefield said:**
> Enable the partner repository and installing it with Synaptic Package Manager would be the easiest way.

System > Administration > Software Sources > Other Software tab and check the box beside the partner repository.

Reload and install, this way, you stay updated as new versions are released.

Alright, but how can I install the file I already have?
I hear I have to make it into a deb file, how to I do that?
And how do I install from there?

By the way, sorry for the thread name. Just a small error I made.

---

### Post by tango_ninja on 2010-06-23
> **Tombgeek said:**
> Alright, but how can I install the file I already have?
I hear I have to make it into a deb file, how to I do that?
And how do I install from there?

By the way, sorry for the thread name. Just a small error I made.

If you're new, I suggest deleting that downloaded file and installing it from the repositories instead.  Take a look at this article [How To Install JRE in Ubuntu Linux]("http://justplainobvious.blogspot.com/2010/06/how-to-install-java-jre-in-ubuntu-linux.html").

Also, I assume you only want the JRE (for viewing websites, etc.) and not the JDK (for java programming)?  If you also want JDK, [see this thread]("http://ubuntuforums.org/showthread.php?t=1506642").

---

### Post by howefield on 2010-06-23
> **Tombgeek said:**
> Alright, but how can I install the file I already have?

[http://www.java.com/en/download/help/linux_install.xml#selfextracting](http://www.java.com/en/download/help/linux_install.xml#selfextracting)

I still say it's better to install from the repository. :)

---

### Post by Tombgeek on 2010-06-23
> **tango_ninja said:**
> If you're new, I suggest deleting that downloaded file and installing it from the repositories instead.  Take a look at this article [How To Install JRE in Ubuntu Linux]("http://justplainobvious.blogspot.com/2010/06/how-to-install-java-jre-in-ubuntu-linux.html").

Also, I assume you only want the JRE (for viewing websites, etc.) and not the JDK (for java programming)?  If you also want JDK, [see this thread]("http://ubuntuforums.org/showthread.php?t=1506642").

> **howefield said:**
> [http://www.java.com/en/download/help/linux_install.xml#selfextracting](http://www.java.com/en/download/help/linux_install.xml#selfextracting)

I still say it's better to install from the repository. :)

Okay, well thanks anyway.

The reason is because I don't want to download the file again. I have almost reached my cap limit and I don't want to download again. I will wait until the beginning of the new month.

Thanks.

---

### Post by eltonw on 2010-06-23
> **Tombgeek said:**
> Hey there

I downloaded Java from the site itself, and I got a 20mb file named jre-6u20-linux-i586.bin
How do I install it?

Sorry, I am a new to linux

The easiest way is to right click on the file, choose Properties, and change it to executable. You can then run it as an installation program. 
_The following should also be of help to you_:
[http://ubuntuforums.org/showthread.php?t=1483371&highlight=eltonw]("http://ubuntuforums.org/showthread.php?t=1483371&highlight=eltonw")
Linux for newbies / beginners

cheers, ):P

---

