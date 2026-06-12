---
title: "Java Web Start issues :("
date: 2010-04-03
forum: General Help
---

### Post by karimruan on 2010-04-03
When try to run java web start (which I know nothing about,and all I find online is people writing java programs for it), I get the following error. i am hopefully supplying a screenshot.

when I chose it from the menu, nothing happens. When I run it in terminal with the command 

```

/usr/lib/jvm/java-6-sun-1.6.0.15/bin/javaws %u

```

with or without sudo, I get the error.

If it helps I am trying  to use the freecast web app...

Thanks!

---

### Post by lykeion on 2010-04-05
Well, read the error: Could not load file: ... %u

when starting java web start you should provide the jnlp-file as argument (and %u is not a jnlp-file)

Read the wikipedia antry about java web start: [http://en.wikipedia.org/wiki/Java_Web_Start]("http://en.wikipedia.org/wiki/Java_Web_Start")

In short: Java web start is a way to deploy Java applications. It uses a jnlp-file (a type of xml-file) with the path to the java application (jar-file) to launch.

Hope that it helps...

[edit]

Ok, I may have misread your question. 
From what I gather you have installed freecast via java web start, but you cannot launch it. 
Is that correct?

if so, try
/usr/lib/jvm/java-6-sun-1.6.0.15/bin/javaws -viewer

from there you can launch applications from your cache

---

### Post by karimruan on 2010-04-05
thanks! that worked! I'll probably just write a shell script to shorten the length of the command... 

thanks again!

---

