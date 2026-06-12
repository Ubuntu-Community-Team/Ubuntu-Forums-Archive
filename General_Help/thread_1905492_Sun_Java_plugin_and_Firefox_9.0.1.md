---
title: "Sun Java plugin and Firefox 9.0.1"
date: 2012-01-07
forum: General Help
---

### Post by stchman on 2012-01-07
Hello all.  I have the package sun-java6-plugin installed and Firefox 9.0.1 installed on my Ubuntu 10.04 64 bit.  Now Java used to work, but doesn't anymore.  Has anyone else had the same problems?

Thanks.

---

### Post by stchman on 2012-01-07
I figured it out.

Apparently Firefox 9.0.1 does a few weird things.  I had to re-create the symbolic link using the following command:

```

sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so /usr/lib/firefox-addons/plugins/

```

I have 64 bit Ubuntu hence the amd64.

---

### Post by thekat on 2012-01-11
> **stchman said:**
> I figured it out.

Apparently Firefox 9.0.1 does a few weird things.  I had to re-create the symbolic link using the following command:

```

sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so /usr/lib/firefox-addons/plugins/

```

I have 64 bit Ubuntu hence the amd64.

Thank you for this..
Running Lucid 32-bit using PPA
```

sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/**i386**/libnpjp2.so /usr/lib/firefox-addons/plugins/


```

---

### Post by lahtis on 2012-02-03
> **stchman said:**
> Hello all.  I have the package sun-java6-plugin installed and Firefox 9.0.1 installed on my Ubuntu 10.04 64 bit.  Now Java used to work, but doesn't anymore.  Has anyone else had the same problems?

Thanks.

The Canonical partner archive currently contains Oracle's Sun Java JDK packages (sun-java6, sun-java6-plugin) for Ubuntu 10.04 LTS, Ubuntu 10.10 and Ubuntu 11.04.  As of August 24th 2011, we no longer have permission to redistribute new Java packages as Oracle has retired the “Operating System Distributor License for Java” [1][2].  Oracle has published an advisory about security issues in the version of Java we currently have in the partner archive [3]. Some of these issues are currently being exploited in the wild.  Due to the severity of the security risk, Canonical is immediately releasing a security update for the Sun JDK browser plugin which will disable the plugin on all machines. This will mitigate users' risk from malicious websites exploiting the vulnerable version of the Sun JDK.  In the near future (exact date TBD), Canonical will remove all Sun JDK packages from the Partner archive. This will be accomplished by pushing empty packages to the archive, so that the Sun JDK will be removed from all users machines when they do a software update. Users of these packages who have not migrated to an alternative solution will experience failures after the package updates have removed Oracle Java from the system.  If you are currently using the Oracle Java packages from the partner archive, you have two options:  1- Install the OpenJDK packages that are provided in the main Ubuntu    archive. (icedtea6-plugin for the browser plugin, openjdk-6-jdk or    openjdk-6-jre for the virtual machine) 2- Manually install Oracle's Java software from their web site [4].  For more information, please consult the wiki page on the subject [5].  We apologize for any inconvenience this may cause, and thank you for your understanding.

for fixit go to

[http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)

---

### Post by zerofloat on 2012-02-04
> **lahtis said:**
> The Canonical partner archive currently contains Oracle's Sun Java JDK packages (sun-java6, sun-java6-plugin) for Ubuntu 10.04 LTS, Ubuntu 10.10 and Ubuntu 11.04.  As of August 24th 2011, we no longer have permission to redistribute new Java packages as Oracle has retired the “Operating System Distributor License for Java” [1][2].  Oracle has published an advisory about security issues in the version of Java we currently have in the partner archive [3]. Some of these issues are currently being exploited in the wild.  Due to the severity of the security risk, Canonical is immediately releasing a security update for the Sun JDK browser plugin which will disable the plugin on all machines. This will mitigate users' risk from malicious websites exploiting the vulnerable version of the Sun JDK.  In the near future (exact date TBD), Canonical will remove all Sun JDK packages from the Partner archive. This will be accomplished by pushing empty packages to the archive, so that the Sun JDK will be removed from all users machines when they do a software update. Users of these packages who have not migrated to an alternative solution will experience failures after the package updates have removed Oracle Java from the system.  If you are currently using the Oracle Java packages from the partner archive, you have two options:  1- Install the OpenJDK packages that are provided in the main Ubuntu    archive. (icedtea6-plugin for the browser plugin, openjdk-6-jdk or    openjdk-6-jre for the virtual machine) 2- Manually install Oracle's Java software from their web site [4].  For more information, please consult the wiki page on the subject [5].  We apologize for any inconvenience this may cause, and thank you for your understanding.

for fixit go to

[http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)

Thanks! Got me going.

---

