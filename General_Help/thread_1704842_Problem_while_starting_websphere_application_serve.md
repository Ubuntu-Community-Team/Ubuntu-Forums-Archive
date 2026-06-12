---
title: "Problem while starting websphere application server"
date: 2011-03-11
forum: General Help
---

### Post by vat with tux on 2011-03-11
Hello friends.

I have installed websphere application server community edition from ubuntu software center.
Now whenever i tries to execute the file "startup.sh" (which is the file to start websphere server) i receive following error.

> Neither the JAVA_HOME nor the JRE_HOME environment variable is defined.
At least one of these environment variable is needed to run this program.


Now i searched web & find out the way to set JAVA_HOME environment variable which is according to my knowledge done by following command.

> export JAVA_HOME=/usr/lib/jvm/java-6-sun


Now after executing this command also the same error is coming.:(

Please someone help me that what to do.

---

### Post by Rubi1200 on 2011-03-12
Unfortunately, I have never used this software so I am unable to advise you on this problem.

However, here is a link to their documentation; perhaps there is something there that can help?
[http://publib.boulder.ibm.com/wasce/Front_en.html](http://publib.boulder.ibm.com/wasce/Front_en.html)

---

### Post by vat with tux on 2011-03-12
After setting JAVA_HOME using "export JAVA_HOME=/usr/lib/jvm/java-6-sun" , i fired following command to check whether variable is set properly or not:"echo JAVA_HOME" & the o/p is:> /usr/lib/jvm/java-6-sun
But after closing the terminal & starting again when i fired same command:"echo JAVA_HOME" I found o/p as blank line.:(

Now can anyone tell that how to set environment variables properly?

---

