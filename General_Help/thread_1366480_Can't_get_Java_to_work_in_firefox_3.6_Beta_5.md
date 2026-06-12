---
title: "Can't get Java to work in firefox 3.6 Beta 5"
date: 2009-12-28
forum: General Help
---

### Post by Ben2r25 on 2009-12-28
I downloaded the new beta of firefox and extracted it to my home directory. Java was already installed on my system via synaptic (I used the sun-java6-jre and the sun-java6-plugin packages) and it worked fine in firefox 3.5.6. When I ran 3.6 flash worked out of the box but java didn't. I downloaded the JDK update 17 self extracting binary (I am interested in doing some java programming as well) from the sun website. I extracted it to /usr/java. I navigated to /home/my-username/firefox/plugins (firefox 3.6 was extracted to my home folder) and make a symbolic link with this command ```
ln -s /usr/java/jdk1.6.0_17/jre/plugin/i386/ns7/libjavaplugin_oji.so
``` I tried restarting firefox and the computer but java still isn't working. What am I doing wrong?

---

### Post by mattman on 2009-12-28
Check out the following link.  [http://forums.mozillazine.org/viewtopic.php?f=23&t=1576825](http://forums.mozillazine.org/viewtopic.php?f=23&t=1576825) Firefox 3.6 uses a different plugin file that is only available with the lastest Java off of Suns website.  Hope this helps.

---

### Post by Ben2r25 on 2009-12-28
> **mattman said:**
> Check out the following link.  [http://forums.mozillazine.org/viewtopic.php?f=23&t=1576825](http://forums.mozillazine.org/viewtopic.php?f=23&t=1576825) Firefox 3.6 uses a different plugin file that is only available with the lastest Java off of Suns website.  Hope this helps.
Thanks that worked perfectly.

---

### Post by jamesstansell on 2009-12-29
> **mattman said:**
> Firefox 3.6 uses a different plugin file that is only available with the lastest Java off of Suns website.  Hope this helps.

Just to clarify, the new java plugin from sun was introduced in java 6 update 10 (6.0_10 aka 6u10).  Most ubuntu versions from 8.04 LTS and later have a sun-java6-bin version that includes the new plugin.

(Not sure that the associated sun-java6-plugin package always chooses the new plugin instead of the old, but simply having the plugin present is the first step to being able to use it.)

Regards,

-james.

---

### Post by mattman on 2009-12-30
I had Java installed from the repositories but could not find the new plugin anywhere on my system.

---

### Post by jamesstansell on 2010-01-02
> **mattman said:**
> I had Java installed from the repositories but could not find the new plugin anywhere on my system.

With java 6 update 10 or later you should have results similar to this:

```
$ dpkg -L sun-java6-bin |grep libnpjp2
/usr/lib/jvm/java-6-sun-1.6.0.17/jre/lib/i386/libnpjp2.so

```

Regards,

-james.

---

