---
title: "Setting proper classpath"
date: 2010-07-23
forum: General Help
---

### Post by RFrenette on 2010-07-23
I am able to "javac Main.java", where Main.java is in: /src/HelloWorld/src/helloworld

When I don't use a package, the following works fine: java Main

However, when I add "package helloworld;" I cannot run Main because of the classpath. So, in the console, I set: CLASSPATH = /src/HelloWorld/src/helloworld

Then I compiled fine but I cannot run: java helloworld.Main

Could someone please advise as to why this isn't working, even with the CLASSPATH set to the directory Main.class is in?

Thanks!

---

### Post by RFrenette on 2010-07-23
I figured it out. I was too deep in the dir structure. :o

/src/HelloWorld/src/ java helloworld.Main works fine.

---

