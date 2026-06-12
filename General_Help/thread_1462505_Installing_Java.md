---
title: "Installing Java"
date: 2010-04-25
forum: General Help
---

### Post by Tacozmeister on 2010-04-25
Okay, I wanted to install Java so that I could play the popular game "RuneScape" on my Ubuntu system, but I followed the steps posted on the website and it said something like "Extract using the console" and gave me the name of the object to extract, but it did not say anything about what folder or anything, so the system did not know where to extract from.

I am very new to Ubuntu, so it'd be great if someone could speak noob to me about how to do it so I understand not only how to install Java, but some other things as well. Thank you ahead of time!

---

### Post by ratcheer on 2010-04-25
Are you trying to install the .bin file from Sun's website? If so, I can help with that. If you are doing something else, somebody else will have to help you.

Tim

---

### Post by Nickynak on 2010-04-25
I'm new to Ubuntu linux myself and am having really big problems installing Java, so would appreciate any help? I think my problem is that I need it broken down into very simple stages that I can follow, but the bin file for Java has defeated me so far, managed to get wine going OK and the adobe flash installed pretty well. Don't want to go back to Windows after getting a horrid virus that killed my netbook last week.

---

### Post by Tacozmeister on 2010-04-25
I don't know, really. I got the bar at the top of my browser (I'm not on Linux right now, so I can't link you) telling me I need Java, and it directed me to the website with several links and installation steps. I believe it's a .bin, though. Sorry I'm not much help.

---

### Post by ratcheer on 2010-04-25
Ok, it is not really very hard to install using the .bin file. First, you have to decide where you want it installed (since you are doing it, manually). I suggest either /usr/java or /opt/java. Create that directory:

```
sudo mkdir /usr/java
```Next, copy your .bin file to that directory. cd to the location of your saved .bin file and:

```
sudo cp <the .bin filename> /usr/java
```Now, you have to make the copied file executable:

```
cd /usr/java
sudo chmod 755 <the .bin filename>
```Now, execute it:

```
./<the .bin filename>
```Now, you should find a subdirectory in /usr/java named jre1.6.0_20. That is your JAVA_HOME directory. Add it to your environment by adding the following to the end of your .bashrc file:

```
JAVA_HOME=/usr/java/jre1.6.0_20
PATH=$JAVA_HOME/bin:$PATH
CLASSPATH=$JAVA_HOME/lib

```Finally, you have to link the java plugin to your web browser's plugins folder. That depends on what web browser you are using.

Tim

---

### Post by Tacozmeister on 2010-04-25
I only 25% understood that.. I've only had Ubuntu for a short while, so I'll just try that without understanding what's going on (: But I guess I'll catch on. Thank you!

---

### Post by QIII on 2010-04-25
By far the easiest method (unless you are running Lucid and simply activate the partner repo) can be found here:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

This will get you the most current version of Java.

In Lucid, just activate the partner repository and install it from Synaptic.

---

### Post by scouser73 on 2010-04-25
> **QIII said:**
> By far the easiest method (unless you are running Lucid and simply activate the partner repo) can be found here:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

This will get you the most current version of Java.

In Lucid, just activate the partner repository and install it from Synaptic.

+1 for installing via the [[COLOR="Red"]**Easy Linux Tips Project: Java**[/COLOR]]("http://sites.google.com/site/easylinuxtipsproject/java") It will show you step by step how to install the latest version of Java.

---

### Post by Nickynak on 2010-04-26
Thanks for the reply, I will be trying out your advice.

---

### Post by 98cwitr on 2010-04-26
yeah the Software Center would work "best" Just type in "jre" into the search field and then do the same with the java plugin and fonts :)

---

### Post by 3rdalbum on 2010-04-26
> **QIII said:**
> By far the easiest method (unless you are running Lucid and simply activate the partner repo) can be found here:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

This will get you the most current version of Java.

In Lucid, just activate the partner repository and install it from Synaptic.

+1

Obi-Wan Kenobi says: "Use the repositories, Luke!".

---

### Post by schwabdale on 2010-04-26
> **QIII said:**
> By far the easiest method (unless you are running Lucid and simply activate the partner repo) can be found here:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

This will get you the most current version of Java.

In Lucid, just activate the partner repository and install it from Synaptic.


How do I activate the parter repo?

---

### Post by schwabdale on 2010-04-26
So, if there is a Partner Repository... Does that make it legal to sell software?

---

### Post by QIII on 2010-04-26
To activate the partner repository, go to System | Administration | Software Sources (I think.  I'm not at my Ubuntu machine and a lot of this is just "muscle memory" for me).

Click to select "Partner ...".  I don't know for sure if there is a partner repository earlier than Lucid.

As for what you can sell:  

Sun Java - no.

Anything you build to run in the JRE - Yes.

Somewhat like .NET.  There is a freely distributable .NET Framework.  Same with Java JRE.  Java's JRE is freely distributable by virtue of the fact that anyone can  install it.  But you can't alter Sun Java or the .NET Framework.  They are both proprietary, which is why Sun Java is not available in the standard Ubuntu repos.

You can, however, modify OpenJDK if you wish and if you follow all licensing agreements.  OpenJDK is the open source version of Java.  It's not quite perfect, but Oracle/Sun and independent developers in the Linux community are getting there.

If you are speaking in a broader, more general sense -- Yes.  It is OK to sell software you develop.  "Free" doesn't mean "free" as in "free beer".  Free means you have freedom to take what you have and modify it to fit your needs and, if the licensing agreement so states, distribute your version -- providing that you make your source code available and give credit where it is due.

There is commercial Linux software.  There are people who refuse to install anything they have to pay for.  There is a market for justly priced task-specific software, but I don't know that most personal users would be interested.  I wouldn't expect anyone to support it if the source code is not open.  And you wouldn't get rich.  Many developers depend on donations.

---

### Post by schwabdale on 2010-04-26
Thanks for the info. To clarify, I can install JRE through the repositories, just not Sun Java?
I can redistrube JRE and not Sun Java? And JRE runs pretty good?

---

### Post by QIII on 2010-04-26
Not quite.
  
  A bit of clarification.  The JRE is the Java Runtime Environment and is  part of Sun Java when you install it.  (I'll talk about OpenJDK in a  moment.)
  
   The current Update of Sun Java (20) is in the partner repositories for  Lucid.  It is there because it is proprietary and closed source, so Canonical does not put it in the standard repos.
   
   An older Update (15 or 16) is available in the standard repos prior to  Lucid.  However, these Updates have some serious security issues.
 
 Without knowing which version of Ubuntu you have, I said either do it  with the detailed instructions or, if using Lucid, activate the partner  repository and install it through package management.

Anything you design in Java (except notes about OpenJDK below) will have to run in the JRE, so Sun Java (at least the JRE) will  have to be installed on the machine running it.  Rather than you  distributing it, it should be installed by the user.  Installations of various Linux distros may vary, so it would be hard to say for sure how it should be installed. It can also be installed for a single user or for anyone on the machine and you don't know how the end-user plans to set that up.  Other operating systems, such as OpenSolaris (an open source Unix system), will have a slightly different installation process.

OpenJDK is an open source alternative to Sun Java, but it is still  Oracle/Sun's baby with help from open source developers.  It is just open source.  It is something the user  would have to install before your software would work.

OpenJDK is the standard repositories.  It is in the standard repositories  because it is not closed source and proprietary.

---

### Post by schwabdale on 2010-04-26
Thank you very much for the time you put into clarifying it. Just one more question please...
If I sold a System Modified with Ubuntu 10.04.. I could add the partner repository... and stop there. 
The user would have to do the rest based on instructions I provide? 

This should be legal right?

---

### Post by QIII on 2010-04-26
No matter what you do I am pretty certain that you could not, under any  circumstances, charge the customer for Ubuntu itself.

I can't answer for Canonical beyond that.  You will need to consult with Canonical for any details about selling a system with Ubuntu pre-installed.  

As far as the repo activation, it would be better to teach someone how to do it rather than doing it for them.  Teach a man to fish, you know.

---

