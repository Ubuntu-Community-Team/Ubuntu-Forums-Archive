---
title: "Java version 6 update 27 is available"
date: 2011-09-08
forum: General Help
---

### Post by Cavsfan on 2011-09-08
If any one is interested in obtaining the latest version of java, one of the links in my sig. will tell you if you need to update.
Another will tell you how to do it. Just keep in mind that page hasn't been updated yet and you will need to change the 26 to 27.
On the left side is instructions for 32 bit systems and instructions for 64 bit systems are on the right.

It says to first remove the older version before installing the new one. 
I did the 64 bit version and the file name is **jre-6u27-linux-x64.bin**.

It's CLI but, I have used this method for about 2 years and no problems yet.

---

### Post by Raven17 on 2011-09-09
Super smooth!

Thanks for the instructions.:KS

---

### Post by Cavsfan on 2011-09-10
> **Raven17 said:**
> Super smooth!

Thanks for the instructions.:KS

You are welcome! :)

---

### Post by Cavsfan on 2011-09-15
BTW the link in my sig. has now been updated with the new version. So, copy and paste will do. :-D

---

### Post by Governa on 2011-09-15
Great tutorial, well done!

I have a question though. Having followed your first set of instructions (uninstall openjdk and installing sun-java6-jre from the partner repository) I ended up with Java 6 update 26 (previously I had update 22). Although there's an update 27 I will stick to the one I have otherwise I would have to manually check and update every new version as oposed to wait until a new update is pushed by the partner repository automatically.

Now, questions:

1- I have rebooted the machine but when I open terminal and do a java -version query I still get the following info:

Java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.2) (6b22-1.10.2-0ubuntu1~11.04.1)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)

How can this be? When I check at [http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp) it gives me a totally different information:

Your Java version: Version 6 Update 26

Is this normal?

2- I am running 11.04 64bit, how can I check if I'm running Sun's 64bit or 32bit JVM?

---

### Post by Governa on 2011-09-16
*shameless bump*

---

### Post by Cavsfan on 2011-09-16
> **Governa said:**
> Great tutorial, well done!

I have a question though. Having followed your first set of instructions (uninstall openjdk and installing sun-java6-jre from the partner repository) I ended up with Java 6 update 26 (previously I had update 22). Although there's an update 27 I will stick to the one I have otherwise I would have to manually check and update every new version as oposed to wait until a new update is pushed by the partner repository automatically.

Now, questions:

1- I have rebooted the machine but when I open terminal and do a java -version query I still get the following info:

Java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.2) (6b22-1.10.2-0ubuntu1~11.04.1)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)

How can this be? When I check at [http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp) it gives me a totally different information:

Your Java version: Version 6 Update 26

Is this normal?

2- I am running 11.04 64bit, how can I check if I'm running Sun's 64bit or 32bit JVM?

Sorry for not getting back with you but, I don't get on here more than a couple times a day. One day is no cause for a *shameless bump*. 
You should be a little more patient as most people in this forum have lives too.

Thanks but, I did not create a tutorial, just put 2 links in my signature.

You can look in **/opt/java/32/** and if that folder exists and you have a 64 bit system, I would suggest going by the instructions on the left side just to remove the 32 bit java.

Then the only thing I can think of is to just try it again. You can do the same steps over and over and you are not going to hurt anything.
And no need to restart computer, just restart the browser and then look at ```
about:plugins
```You should see **Java(TM) Plug-in 1.6.0_27**
The right side pertains to 64 bit and you need to first remove the java you have installed which is detailed towards the bottom and then install the version you downloaded.

It looks to me that you are using the 64bit java. But, step 12 in the 64 bit installation says to remove the IcedTea plugin:
```
12. Now remove the IcedTea plugin, if it has been installed.

Type (copy/paste):
 sudo apt-get remove icedtea6-plugin
```[SIZE=3][COLOR=#000000][COLOR=#0000FF]
[/COLOR][/COLOR][/SIZE]

Here is my output of **java -version**:
```
cavsfan@cavsfan-desktop:~$ java -version
java version "1.6.0_27"
Java(TM) SE Runtime Environment (build 1.6.0_27-b07)
Java HotSpot(TM) 64-Bit Server VM (build 20.2-b06, mixed mode)

```So, I would say just try it again and if you have the output as I have above you are good.
And using this method will require you to manually update each version. You could just bookmark the 2 links in my sig. or go with the one in the repository.
But, if have followed these steps from my signature I cannot help you get back to the repository version.
I was simply providing a way to manually update java.

---

### Post by Governa on 2011-09-16
> **Cavsfan said:**
> One day is no cause for a *shameless bump*. You should be a little more patient as most people in this forum have lives too.

I was under the impression it's ok to bump a thread after 24 hours.

> **Cavsfan said:**
> You can look in **/opt/java/32/** and if that folder exists and you have a 64 bit system, I would suggest going by the instructions on the left side just to remove the 32 bit java.

I don't.

> **Cavsfan said:**
> It looks to me that you are using the 64bit java. But, step 12 in the 64 bit installation says to remove the IcedTea plugin.

I had done that already.

The problem was it didn't remove ALL traces of openjdk/icedtea like I thought it would. I solved the problem by removing the remaining stuff via Synaptic.

> **Cavsfan said:**
> Here is my output of **java -version**:
```
cavsfan@cavsfan-desktop:~$ java -version
java version "1.6.0_27"
Java(TM) SE Runtime Environment (build 1.6.0_27-b07)
Java HotSpot(TM) 64-Bit Server VM (build 20.2-b06, mixed mode)

```

Here's mine now:
```
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) 64-Bit Server VM (build 20.1-b02, mixed mode)
```

> **Cavsfan said:**
> And using this method will require you to manually update each version. You could just bookmark the 2 links in my sig. or go with the one in the repository.

I decided to go with the one in the repository. It's update 26 but still better than my previously installed update 22.

Thank you

---

### Post by Cavsfan on 2011-09-17
The *shameless bump* is A-OK if you want to waste your time but, it did *not* get me to look at this any sooner than I did anyway.
I think a day is a little bit shy of enough time. I have posted questions and a week later I posted additional info and then maybe someone replied maybe not.

If you wanted the one in the repository, I don't understand why you even bothered to use this thread.

This thread is to manually install the newest version of java and yes you will need to do it again when another version comes out.
Which is why I open up a new thread when I notice a new version of java has been released.

You are welcome.

---

### Post by Governa on 2011-09-17
> **Cavsfan said:**
> If you wanted the one in the repository, I don't understand why you even bothered to use this thread.

Well simply because I didn't know we had two JVM options under linux: OpenJDK and Sun's. Oracle's website stated I was using Java 6 update 22 and I wanted to update but I had no idea the default in Ubuntu was OpenJDK so this thread was useful as in the end I learned I needed to uninstall OpenJDK and tick Sun's in the repository. Now I run update 26 so problem solved.

---

### Post by Cavsfan on 2011-09-19
> **Governa said:**
> Well simply because I didn't know we had two JVM options under linux: OpenJDK and Sun's. Oracle's website stated I was using Java 6 update 22 and I wanted to update but I had no idea the default in Ubuntu was OpenJDK so this thread was useful as in the end I learned I needed to uninstall OpenJDK and tick Sun's in the repository. Now I run update 26 so problem solved.

Glad you got it all sorted out. I am sure the repositories aren't very far behind Oracle but, 
I like to occasionally check what the latest version is and update manually if necessary.

---

