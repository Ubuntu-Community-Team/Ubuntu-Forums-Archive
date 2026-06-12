---
title: "downloaded jre-6u20-linux-x64.bin and ran it but no java"
date: 2010-06-25
forum: General Help
---

### Post by tckotb on 2010-06-25
i downloaded java from their website, and chmoded it with the command "chmod 777 ./*.bin" and ran it, but it just extracted a bunch of crap to my download folder, and i cant run java applets. help, please?!

and yes i do have a 64 bit processor

---

### Post by hangfire on 2010-06-25
There are post-install instructions on the Sun/Oracle web site. You'll need to put the shared library in your browser's plugins folders, and change the soft links to put java in the executable path.

---

### Post by tckotb on 2010-06-25
i cant find these instructions, on the site they stop at the running of the .bin file

---

### Post by tckotb on 2010-06-25
okay, i put a link to the .so file in my plugins directory, but it stil doesn't work! how do i install the rest of java.

this has never been hard before, why did they remove sun-java6-* from the repositories?

---

### Post by emyr42 on 2010-06-25
> **tckotb said:**
> this has never been hard before, why did they remove sun-java6-* from the repositories?

They didn't remove it, they just moved it to the "partner" repository.

See [http://www.ubuntugeek.com/sun-java-moved-to-the-partner-repository-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/sun-java-moved-to-the-partner-repository-in-ubuntu-10-04-lucid.html)

---

### Post by hangfire on 2010-06-25
> **tckotb said:**
> okay, i put a link to the .so file in my plugins directory, but it stil doesn't work! how do i install the rest of java.

this has never been hard before, why did they remove sun-java6-* from the repositories?

You are right, Oracle has broken the instructions.

There are multiple firefox/mozilla plugins directories in Unbuntu. 

You also need to link java into /etc/alternatives/java.

There are also issues launching 64 bit Java from 32 bit Firefox and vice-versa.

Here are some instructions:

[http://www.greatwhiteit.com/web/guest/technology-blog/-/blogs/how-to-install-oracle-sun-java-jdk-and-jre-in-ubuntu-10-04-lucid-lynx](http://www.greatwhiteit.com/web/guest/technology-blog/-/blogs/how-to-install-oracle-sun-java-jdk-and-jre-in-ubuntu-10-04-lucid-lynx)

Here are some more:

[http://www.tikalk.com/java/blog/ubuntu-and-suns-java-silent-divorce](http://www.tikalk.com/java/blog/ubuntu-and-suns-java-silent-divorce)

The short version of why is, Oracle Java is not "free software". It is still available in the "partner repositories".

---

