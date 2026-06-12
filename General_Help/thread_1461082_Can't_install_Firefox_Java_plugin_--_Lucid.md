---
title: "Can't install Firefox Java plugin -- Lucid"
date: 2010-04-23
forum: General Help
---

### Post by donsy on 2010-04-23
Ubuntu 10.04 32-bit, Firefox 3.6.3.

I can't install the Java plugin:

1. Firefox can't find a suitable plugin.
2. It doesn't appear at all in Synaptic.
3. Apt-get sun-java6-jre sun-java6-plugin doesn't work.
4. Ubuntu Software Center shows an entry for Sun Java 6.0 Plugin but with no install option button. I can get more info, but can't install.

---

### Post by mkvnmtr on 2010-04-23
On 10.04 I believe I used the open source java that is in Synaptic. It seems to work fine . If you have to have the other maybe you should search Synaptic for the plugin. It is probably there just not called what it was n older releases.

---

### Post by donsy on 2010-04-23
Installed OpenJDK -- didn't work.
Installed IcedTea  -- worked.

---

### Post by geirha on 2010-04-23
For Ubuntu 10.04, the sun java packages have been moved to the partner repositories, which are disabled by default. See [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding Canonical Partner Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding Canonical Partner Repositories) on how to enable them.

Though if the icedtea plugin works for you, I recommend you stick with that. (The only reason I use sun's java plugin is because my bank's online banking system doesn't work with the icedtea plugin yet.)

---

### Post by donsy on 2010-04-23
> **geirha said:**
> For Ubuntu 10.04, the sun java packages have been moved to the partner repositories, which are disabled by default. See [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding Canonical Partner Repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories") on how to enable them.

Though if the icedtea plugin works for you, I recommend you stick with that. (The only reason I use sun's java plugin is because my bank's online banking system doesn't work with the icedtea plugin yet.)
Yes you know I'm really surprised that OpenJDK didn't work in Firefox because it's the real deal. I'm able to run Java .class files compiled months ago with Javac. And according to the Java test Web page it's running fine.
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

---

### Post by vintermann on 2010-05-25
> **geirha said:**
> 
Though if the icedtea plugin works for you, I recommend you stick with that. (The only reason I use sun's java plugin is because my bank's online banking system doesn't work with the icedtea plugin yet.)

I suspect you use the same bank as me!

My problem is that I can't install the plugin. I add the partner repositories, but it still doesn't show up - In synaptic, the other two sun java packages (the sdk and the jre) show up, but not the plugin. In "Ubuntu Software Center" the plugin shows up, but doesn't have an install button.

---

### Post by geirha on 2010-05-25
> **vintermann said:**
> I suspect you use the same bank as me!

My problem is that I can't install the plugin. I add the partner repositories, but it still doesn't show up - In synaptic, the other two sun java packages (the sdk and the jre) show up, but not the plugin. In "Ubuntu Software Center" the plugin shows up, but doesn't have an install button.

Odd. What does this terminal command say?
```
aptitude search sun-java6
```

---

### Post by tman_ubuntu on 2010-05-25
This thread is marked solved. May I ask what was the solution?:confused:

---

### Post by donsy on 2010-05-26
> **tman_ubuntu said:**
> This thread is marked solved. May I ask what was the solution?:confused:
Well did you read post #3 above? That's when I marked this thread as solved. However, I have an update. Since that time I uninstalled OpenJDK and IcedTea and did the following:

```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
```And the Java plugin works as expected. So I would still mark this thread as solved.

---

### Post by dox_drum on 2010-06-01
In order for this to work, I should removed icetea6,
```
sudo apt-get autoremove openjdk-6-jre
```
Then it worked!!!

Thx!

---

### Post by NoBugs! on 2010-07-12
I noticed a similar problem, although the Java browser plugin was installed, it didn't work and didn't show up in tools-addons-plugins. The [solution]("https://help.ubuntu.com/community/Java") is to run
```
sudo update-java-alternatives -s java-6-sun 
```

---

### Post by Elmer Fudd on 2010-07-12
If other solutions don't work.
Verbose, very complete step by step at:

[http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU)

---

