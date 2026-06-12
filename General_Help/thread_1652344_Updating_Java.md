---
title: "Updating Java"
date: 2010-12-24
forum: General Help
---

### Post by MarkVLK on 2010-12-24
Hi everyone.

I have a fairly simple sounding task that I am thus far unable to accomplish. All I want to do is upgrade from Java 1.6.0_22 to 1.6.0_23. I downloaded the .bin file and made it executable and ran/installed it as directed on the Java website but when I run java -version in the terminal it still says java version "1.6.0_22"

How do I uninstall all previous versions of Java and install the newest version? I'm running Ubuntu 10.10 32-bit and using Chrome as my default browser.

Thanks in advance (and happy holidays)!

---

### Post by MarkVLK on 2011-01-04
bump...

Any help would be greatly appreciated. I'm going to try again I'm just afraid I'm going to remove some necessary system files.

---

### Post by gerowen on 2011-01-04
Try manually removing the ones from synaptic with:

```

sudo apt-get remove --purge sun-java6-bin sun-java6-jre sun-java6-plugin

```

Check and make sure that it's not trying to remove anything dependent on it that you don't want to lose, sometimes Ubuntu will form some weird dependencies.

Then re-run the installer from java.com.  You may have to put your own symbolic link to the plugin file in /usr/lib/mozilla/plugins

---

### Post by MarkVLK on 2011-01-04
> **gerowen said:**
> Try manually removing the ones from synaptic with:

```

sudo apt-get remove --purge sun-java6-bin sun-java6-jre sun-java6-plugin

```

Check and make sure that it's not trying to remove anything dependent on it that you don't want to lose, sometimes Ubuntu will form some weird dependencies.

Then re-run the installer from java.com.  You may have to put your own symbolic link to the plugin file in /usr/lib/mozilla/plugins

After doing that the repository ended up re-installing all the Java files I removed using the commands you gave me. "java -version" is still giving me java version "1.6.0_22"

I guess if it's that much of a hassle I can just leave it at that but I can't help but feel like there's a ton of Java clutter that doesn't need to be there. I installed the JRE in /usr/java as the website mentioned but it seems like the repositories are automatically installing Java in /usr/lib/jvm so I'm not sure what to do to replace the Java version(s) there with the newest 1.6.0_23.

I've attached a screenshot of my terminal so you can see what the repositories automatically installed into /usr/lib/jvm and what the Java .bin file installed into /usr/java

It seems like my browsers (Chrome and Firefox) aren't recognizing Java as being installed in the browsers even though I followed the instructions on Java.com's installation page to create a symbolic link from the newest version of Java to Mozilla's plugins folder. They were previous to this removal/re-installation of Java but I don't remember what I did before so any help would be greatly appreciated. Sorry I'm such a noob to Ubuntu but I really am trying to figure it out.

UPDATE: I just realized all I had to do was run sudo apt-get install sun-java6-plugin and that got Java working in Firefox and Chrome but Java's website is complaining that I hava version 6 update 22 instead of the newest update 23... back to the OP.

---

### Post by MarkVLK on 2011-01-04
I'm happy to say I finally figured it out thanks to the great instructions on the following page:

[http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java")

I hope this helps anyone else wanting to update to Java 6 Update 23 on Ubuntu 10.10!

I guess all I need to do now is try to remove the remaining older, unused versions of Java although I may just leave it as is since I'm afraid I'll end up removing a symbolic link or something. Given the updated screenshot of my /usr/lib/jvm folder can anyone tell me if there's folders in there I can remove for sure without breaking the newest update of Java? I'm assuming I can probably remove the java-6-openjdk, java-1.6.0-openjdk, java-1.5.0-gcj-4.4, and java-6-sun-1.6.0.22 folders and all their contents but I wanted to check with someone that knows a little more about Ubuntu than I do before doing that.

---

### Post by MarkVLK on 2011-01-08
So, does anyone know how to do what the aforementioned website does for the Java 1.6.0_23 JRE for the JDK? I imagine it's nearly identical, I'm just afraid that if I try to wing it I'll mess something up.

---

