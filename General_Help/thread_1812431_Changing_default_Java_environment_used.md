---
title: "Changing default Java environment used"
date: 2011-07-26
forum: General Help
---

### Post by ki4jgt on 2011-07-26
How do you switch the default Java environment used from openjdk to sun-java6?

---

### Post by Gremlinzzz on 2011-07-26
go to software center uninstall icetea java openjdk 
in repositories make sure canonical is checked
sudo apt-get install sun-java6-jre sun-java6-plugin
when prompted to click on OK hit tab then enter.:)

for those who don't know how to get to repositories 
click on synaptic package manager then click on settings then repositories 
then check boxes if not already checked for canonical

---

### Post by ki4jgt on 2011-07-26
> **Gremlinzzz said:**
> go to software center uninstall icetea java openjdk 
in repositories make sure canonical is checked
sudo apt-get install sun-java6-jre sun-java6-plugin
when prompted to click on OK hit tab then enter.:)

for those who don't know how to get to repositories 
click on synaptic package manager then click on settings then repositories 
then check boxes if not already checked for canonical

My only problem is, when ever I uninstall open-jre the next time I have updates, the computer removes sun java and installs open-jre. :-(

---

### Post by Gremlinzzz on 2011-07-26
> **ki4jgt said:**
> My only problem is, when ever I uninstall open-jre the next time I have updates, the computer removes sun java and installs open-jre. :-(

thats strange never happened to me did you add to the repository
that might be doing that.:confused:
when it shows the updates cant you just uncheck open Java?

---

### Post by TBABill on 2011-07-26
That's definitely strange behavior. You can go into Synaptic and mark Jave to not change, but that'll keep it from getting updates when available and potentially leaving the machine exposed if you miss security updates.
 
When you remove open jdk are you ONLY removing icedtea-plugin? That's the only piece you need to remove, not the entire open jdk. Remove that, then install the sun java6 plugin.

---

### Post by tredegar on 2011-07-26
Try:```
sudo update-alternatives  --config   java
```
Choose the java you want to be the default (ie be linked to **/usr/bin/java** )
Here's mine as an example. You can see that I am using sun's java as the default:
```
update-alternatives --config java
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                      Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
* 2            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode

Press enter to keep the current choice[*], or type selection number: 

```

---

### Post by ki4jgt on 2011-07-26
Just found out what was going on. Have two apps which specifically state that they depend on open-jre. That's why it happens. Don't know why sun is removed, but that's why I stopped dealing with Java and just kept it the way it was, I was tired of removing it over and over. anyway, I'll try it again. Leaving everything installed except for icedtea plugin and install java plugin.

---

