---
title: "Icedtea / OpenJRE oddity. (Lucid Lynx)"
date: 2010-05-11
forum: General Help
---

### Post by AmbyR00 on 2010-05-11
I play a game called Go, and I often practice it by solving problems at [Goproblems.com]("http://www.goproblems.org/"). Recently, after upgrading to Lucid Lynx I bumped into a [weird error message]("http://www.goproblems.com/forum/viewtopic.php?f=4&t=735&start=0") using their java applets. It seems that somewhere along the line the "?" in a URL gets changed into a "_", and the time trial mode breaks.

So, anyone know what might be causing this? Should I go straight to the OpenJRE or Icedtea devs and ask what's going on?

I was told to also relay the following things:
- showDocument() method of java.applet.AppletContext has the problem.
-  The URL class instance seems created correctly, as seen in the test  applet.
And here's the source for a test applet we used to collect these bits of info: [http://www.goproblems.com/test/javaurl/GoTestApplet.java](http://www.goproblems.com/test/javaurl/GoTestApplet.java)

Thanks in advance.

---

