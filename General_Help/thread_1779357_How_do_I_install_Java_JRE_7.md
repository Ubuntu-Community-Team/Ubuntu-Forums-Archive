---
title: "How do I install Java JRE 7?"
date: 2011-06-10
forum: General Help
---

### Post by GnarHoff on 2011-06-10
Hi, I'm running Ubuntu 11.04 and am wondering how do I install this x64 version of Java? here is the website: [http://jdk7.java.net/download.html](http://jdk7.java.net/download.html) I chose the Linux x64 JRE tar.gz.

---

### Post by tredegar on 2011-06-10
[http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux](http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux)

---

### Post by ruffEdgz on 2011-06-10
> **tredegar said:**
> [http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux](http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux)

So, I would take this link here, scroll down the step 12 and keep it there because we will need it later.

So, once you download the JRE 7 tarball, I usually untar it in the /opt/ directory. 
```

sudo tar -xzvf ./Downloads/jre-7-ea-bin-b145-linux-x64-07_jun_2011.tar.gz -C /opt/

```
Once untar process is complete, you should see a new directory called 'jre1.7.0' under /opt

Now that you have your java installed under /opt/, it would be wise to change some environment variables under /etc/profile.d/. Go back to that 'step 12' page of the link provided above and we will be setting our JAVA_HOME variable to the new 1.7.0 location and placed a new PATH location as well:
```

sudo touch /etc/profile.d/java_home.sh
sudo vim /etc/profile.d/java_home.sh (you can use whatever text editor you want here)
---ADD THESE LINES---
JAVA_HOME=/opt/jre1.7.0
PATH=$PATH:$JAVA_HOME/bin

export JAVA_HOME PATH
---ADD THESE LINES---

```
Once the file is saved and everything looks well, you can reboot or just run this command to get those environment variables working:
```

source /etc/profile

```
If anything else is needed variable wise for java, you will want to go back to /etc/profile.d/java_home.sh, edit it with what you need, then reboot or source the profile again, etc... etc...

Cheers!

---

### Post by ratcheer on 2011-06-10
removed by poster

---

