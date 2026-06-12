---
title: "How do I install Java?"
date: 2012-05-10
forum: General Help
---

### Post by QIII on 2012-05-10
"[B]The author of this post has edited and moved this material to the Java Community Help Wiki at [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

This post will no longer be monitored by the author, who asks that you refer to the Wiki and create new posts in the appropriate forum if you need further assistance.[/B]"

Since so many people ask and I answer so many times, I figured maybe I could make a single post I can direct people to so I don't have to repeat this so often.

Maybe it will be useful for others to direct posters to.

How do I install Java?

Well, if possible, your first choice should be OpenJDK 7 because it is open source.  That can be installed easily from the repo using apt, aptitude, the Software Center of Synaptic as you choose.  

Unfortunately, that may not be good for you. Although ***OpenJDK 7 is the reference implementation for Java 7***, much of the world does not recognize OpenJDK as Java.  It's an odd state of affairs, but it is what it is.  (Fortunately, both Oracle Java and OpenJDK can exist on the same machine without problems and you can switch easily between the JREs as you care to.  Swapping the browser plugins may be a bit of a challenge.)

Java used to be available in the repos of most major distros when Sun was Sun and Java was Sun Java.  But The Ravenous Monstoracle ate Sun and now it's Oracle Java.  Now Oracle has decided to nullify any license allowing distros to maintain Java in their repos.  We can't install from our friendly neighborhood repo any more.

All of the Java 6 installation tutorials all over the web are about to be useless, since Java 6 is reaching end of life.

But happy days are here again thanks to the folks at webupd8.org.  They created a package that installs Java 7 for you, installs the browser plug-in and even updates Java as Oracle releases them. They don't have Java in a repo, but rather a script that downloads the package from Oracle and does all that magic for you.

Please, for reference, have a look here since these guys deserve the credit for this:

[webupd8]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html")

and here, while you're at it:
[U]
[webupd8]("https://launchpad.net/%7Ewebupd8team/+archive/java")

[/U] Just because I know most of us are simply too lazy/busy/in-a-hurry to go to something silly like a website by the people who provide something, I'm going to lay it out here in all of its difficult detail.

In the terminal:

**1.  Add webupd8's PPA to your sources.list**
```
sudo add-apt-repository ppa:webupd8team/java
```**- or, if you don't mind adding several other packages  -**

```
sudo apt-get install ubuntu-restricted-extras
```  (you may substitute xubuntu-restricted-extras, kubuntu-restricted-extras, etc).  This won't *install *anything.  It will just make some interesting things available -- one of which is webupd8's Java installer.

**2.  Update**
```
sudo apt-get update
```**3.  Install**
```
sudo apt-get install oracle-java7-installer
```**4.  To update your Java alternatives:**

```
sudo update-alternatives --config java
```and choose from a list that will look something like this (the details may differ for you):

```
There are 2 choices for the alternative java (providing /usr/bin/java).  
Selection Path Priority Status 
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212; 
* 0 /usr/lib/jvm/java-6-openjdk/jre/bin/java 1061 auto mode 
1 /usr/lib/jvm/jre1.7.0/jre/bin/java 3 manual mode  

Press enter to keep the current choice
[*], or type selection number: 1
```I know that was a lot to do, but I think we can all struggle through it.

If you ever want to get rid of Oracle Java, it's even harder:

```
sudo apt-get remove oracle-java7-installer
```If you find this useful, please contact webupd8.org and let them know you appreciate their work.


**Please also note** that the following well-written tutorial has been updated for Oracle Java 7, if you ONLY want the JRE and not the JDK as well, here:  [Easy Linux Tips]("http://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by codemaniac on 2012-05-10
Thanks QIII it will really be very helpful .

---

### Post by itagomo on 2012-05-10
thanks .. very helpful post ..

---

### Post by TheYetiWakes on 2012-05-10
Excellent, many thanks for this.

---

### Post by bzik06 on 2012-05-17
Tank you!
works like a charm :)

---

### Post by oldrocker99 on 2012-05-18
WebUp8's installer did the trick for me. Thanks so much for solving a knotty problem.

---

### Post by Shiryu on 2012-05-27
Is it true that OpenJDK 7 is the reference implementation for Java 7?
If Java belongs to Oracle, why is not Oracle Java the reference implementation?

I have had many problems with OpenJDK 6 and I do not rely on OpenJDK.

I want to install Java 7.
I do not care what version to install if it works and can run any old or newer Java application.
Which version should I install?

---

### Post by halfhearted on 2012-06-06
Shiryu, this is exactly the kind of reasonable straightforward question that you will NEVER get an answer to. This thread makes clear the utter mess that Ubuntu/Linux has with Java at the moment. Do not expect a resolution any time soon.

---

### Post by halfhearted on 2012-06-06
Paddy Landau, please read Post #1 in the thread that QIII has kindly supplied in his sig link.

[http://ubuntuforums.org/showthread.php?p=12002898#post12002898](http://ubuntuforums.org/showthread.php?p=12002898#post12002898)

This will disabuse you of the fantasy that "Java works out of the box!" in Ubuntu linux and start to explain the complete confusion that currently exists. Thank you for your help QIII - I think on balanace I will do it my way - if I can find an answer to my OP.

---

### Post by QIII on 2012-06-13
> **halfhearted said:**
> Shiryu, this is exactly the kind of reasonable straightforward question that you will NEVER get an answer to. This thread makes clear the utter mess that Ubuntu/Linux has with Java at the moment. Do not expect a resolution any time soon.

The straight forward answer is given in my original post:

Use OpenJDK if it works.  It doesn't always -- not because there is anything wrong with it, but because it is often not recognized by the world as Java.  Oracle recognizes it as Java, since it is the reference implementation.  Install OpenJDK and set it as your alternative.  Go to the Oracle site that tests for Java on your machine.  If you have the most recent update of OpenJDK 7, you will be greeted with a "Congratulations.  You have the most recent version of Java!" just like you would if you had Oracle Java installed.

If OpenJDK does not work for whatever your intended use, use Oracle Java -- which is universally recognized.

The "mess" is not with Linux.  It is due to two things:

1.  Developers who do not recognize OpenJDK, particularly web developers who do not recognize the OpenJDK browser plugin.

2.  Oracle has withdrawn licenses from *everyone* and *nobody *can legally maintain Java in their repositories or software stores.   This includes Microsoft's Windows platform.  If you do a fresh install of Windows, you *still  *have to install Java separately.

Neither is any indictment of Linux or Windows.  

There is no "resolution" to be found because there is no "resolution" needed.  Windows or Linux, OpenJDK is not universally recognized.  Windows or Linux, you must still install Oracle Java independently.

---

