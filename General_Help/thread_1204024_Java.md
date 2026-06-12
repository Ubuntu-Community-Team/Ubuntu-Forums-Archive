---
title: "Java"
date: 2009-07-04
forum: General Help
---

### Post by theozzlives on 2009-07-04
I'm setting up a [StoresOnline]("http://www.storesonlineexpress.com") website on my server using Ubuntu 9.04. The directions say:> Before continuing to Instal StoresOnline Pro the enviornment variable JAVA_HOME needs to be set. JAVA_HOME is used to run administrative scripts for starting/stopping StoresOnline Pro and running the Java tools for installing a SSL Certificate.   It don't say what to set the variable to. I was hoping someone has run into this and can help me out. I don't know anything about JAVA.

---

### Post by ~sHyLoCk~ on 2009-07-04
> **theozzlives said:**
> I'm setting up a [StoresOnline]("http://www.storesonlineexpress.com") website on my server using Ubuntu 9.04. The directions say: It don't say what to set the variable to. I was hoping someone has run into this and can help me out. I don't know anything about JAVA.

See if [this]("http://www.cyberciti.biz/faq/linux-unix-set-java_home-path-variable/") helps. Change the Java version accordingly.

---

### Post by theozzlives on 2009-07-04
> **~sHyLoCk~ said:**
> See if [this]("http://www.cyberciti.biz/faq/linux-unix-set-java_home-path-variable/") helps. Change the Java version accordingly.

looks good next time I'm upstairs at my server, I'll try it.

---

### Post by txcrackers on 2009-07-04
**DON'T BLINDLY COPY THE SETTINGS!** If you've installed the latest Java, it's *not* 1.5. Check your directory paths before you make the changes to your .bashrc -- use whatever is showing in */usr/lib/jvm*

---

### Post by theozzlives on 2009-07-05
> **txcrackers said:**
> **DON'T BLINDLY COPY THE SETTINGS!** If you've installed the latest Java, it's *not* 1.5. Check your directory paths before you make the changes to your .bashrc -- use whatever is showing in */usr/lib/jvm*

Don't worry, mines 1.6.0_14. Still haven't tried it yet, but I will... sounds like it'll work.

---

