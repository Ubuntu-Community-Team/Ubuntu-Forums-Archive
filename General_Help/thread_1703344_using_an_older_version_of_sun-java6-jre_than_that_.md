---
title: "using an older version of sun-java6-jre than that in repositoy"
date: 2011-03-09
forum: General Help
---

### Post by austinium on 2011-03-09
Hi,

I am using Lucid Lynx. sun-java6-jre in the repository is 1.6.0_22, i am trying to run an application that needs sun-java6-jre 1.6.0_2.

Is there anyway i can get this version via synaptic?

Thanks

---

### Post by howefield on 2011-03-09
Try reloading your software packages, 6_24 should be in the repository by now ?

---

### Post by gandaran on 2011-03-09
> **austinium said:**
> Hi,

I am using Lucid Lynx. sun-java6-jre in the repository is 1.6.0_22, i am trying to run an application that needs sun-java6-jre 1.6.0_2.

Is there anyway i can get this version via synaptic?

Thanks
no, or only if you can find a ppa/repository that contains the update_2 version.
the best way would be to download the old update versions from oracle/sun website, search the sun website, they have all the linux versions available in .bin file format.

---

### Post by austinium on 2011-03-09
@gandaran:
how can i run the bin file and make sure its installed just as synapctic would do it?
by running the .bin file from /usr/lib/jvm ???

---

### Post by kc1di on 2011-03-09
Here is a PPA repository that has the latest Java 

[http://www.multimediaboom.com/how-to-install-java-in-ubuntu-11-04-natty-narwhal-ppa/]("http://www.multimediaboom.com/how-to-install-java-in-ubuntu-11-04-natty-narwhal-ppa/")

worked for me.

---

### Post by austinium on 2011-03-09
I am looking for a way to install and older version through Synaptic.
Would adding and old-release's apt line help?

---

