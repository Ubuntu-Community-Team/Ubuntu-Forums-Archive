---
title: "java help"
date: 2006-03-02
forum: General Help
---

### Post by njzillest on 2006-03-02
how do i activate my JDK (java compiler for programming) i downloaded it from synaptic. Also how do i put my plug ins to mozilla. i allready have done it through apt-get but now it has proven to be useless. I cant view flash programs and i cant play java games.

---

### Post by steve.horsley on 2006-03-02
To use the compiler, you need to put the JDK bin directory in your path. I don't know where yours is installed, but use a command something like this:
> export PATH=$PATH:/opt/jdk1.5.0_05/bin
Then you can use javac etc. from the command line.

To get the plugin working in firefox (I guess mozilla is similar), I had to make a symlink in the fifrefox plugins directory thusly:
> 
cd /opt/firefox-1.5/plugins/
sudo ln -s /opt/jdk1.5.0_05/jre/plugin/i386/ns7/libjavaplugin_oji.so  libjavaplugin_oji.so


---

