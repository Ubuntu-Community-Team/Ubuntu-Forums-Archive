---
title: "How do I Install Java on Ubuntu 10.4?"
date: 2010-04-30
forum: General Help
---

### Post by BinaryMadman on 2010-04-30
I'm trying to install Limewire and FrostWire but they are having trouble with java dependecies.  This is the error that shows up:

"Error: Dependency is not satisfiable: sun-java6-jre|icedtea-java7-jre|sun-java6-jdk|icedtea-java7-jdk"

What do I have to do to get them to work?

---

### Post by ratcheer on 2010-04-30
Add the Partner repository to get Sun Java.

Tim

---

### Post by BinaryMadman on 2010-04-30
What are the steps to add the partner repository?

---

### Post by doas777 on 2010-04-30
go to System -> Administration -> Software Sources -> Other Software and check the pair of "partner repositories" listed there. 

then jsut follow the steps here:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by BinaryMadman on 2010-04-30
Thank you, they work now.  Spent most of yesterday night trying to figure it out.:)

---

### Post by Elchin on 2010-05-05
You need to add partner repositories and then update package list. Doing it from GUI administration did not work for me, so I did it from command line. I described everything in my [blog entry]("http://www.asgarli.net/2010/05/installing-sun-java-runtime-environment.html")

---

### Post by _0R10N on 2010-05-05
What I always do is downloading the installer from the Java page and installing it manually wherever I want just running the installer. By doing that I can be sure that everything is set as I want it to be.

---

### Post by vis.15 on 2010-05-09
Thank You Elchin! That worked for me.

---

### Post by solwic on 2010-05-09
> **BinaryMadman said:**
> I'm trying to install Limewire and FrostWire but they are having trouble with java dependecies.  This is the error that shows up:

"Error: Dependency is not satisfiable: sun-java6-jre|icedtea-java7-jre|sun-java6-jdk|icedtea-java7-jdk"

What do I have to do to get them to work?

I always just loaded up Firefox and went to a site that used Java (i.e. uploading a picture on Facebook, or a speedtest at dslreports.com).  The browser prompts me to install Java, and voila.  :)

EDIT:  Alternatively, doesn't 

```
sudo apt-get install ubuntu-restricted-extras
``` 

install Java?

---

### Post by Elchin on 2010-05-11
> **vis.15 said:**
> Thank You Elchin! That worked for me.

You're welcome :)

---

### Post by Cavsfan on 2010-05-11
Don't mean to butt in, but I found this site with very good instructions on updating java.
The 32 bit instructions are on the left and the 64 bit instructions are on the right of the page.
(The 32/64 bit is your machine not the java)

I have used it with great results several times.

[COLOR=Blue][U][Easy Java Update Instructions]("http://sites.google.com/site/easylinuxtipsproject/java")

[/U][COLOR=Black]The instructions say to modify them for the next version of java, but every time I have used them they were up to date.

Hope this helps!
[/COLOR][/COLOR]

---

### Post by Paul Lynch on 2011-10-14
> **Cavsfan said:**
> Don't mean to butt in, but I found this site with very good instructions on updating java.
The 32 bit instructions are on the left and the 64 bit instructions are on the right of the page.
(The 32/64 bit is your machine not the java)

I have used it with great results several times.

[COLOR=Blue][U][Easy Java Update Instructions]("http://sites.google.com/site/easylinuxtipsproject/java")

[/U][COLOR=Black]The instructions say to modify them for the next version of java, but every time I have used them they were up to date.

Hope this helps!
[/COLOR][/COLOR]


Worked a charm fro me. Thanks Cavsfan

---

### Post by Cavsfan on 2011-10-14
> **Paul Lynch said:**
> Worked a charm fro me. Thanks Cavsfan

You are welcome! Glad I could help. :)

---

### Post by zeiz on 2011-12-28
Elchin! Timeless! Works as a charm!
Many thanks.

---

