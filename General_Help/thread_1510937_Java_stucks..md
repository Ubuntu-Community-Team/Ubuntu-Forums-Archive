---
title: "Java stucks."
date: 2010-06-16
forum: General Help
---

### Post by ewuldoxx on 2010-06-16
I got two problems. Both with Java and here they are:
1) Sometimes when i do play some games that are based on java applet, my java simply stucks and i need to restart it every time. I could live with it, but it becomes annoying, i wouldn't care if it would happen once a week or so, but sometimes it happens in few minutes..
2) And my java applet doesn't show lithuanian letters like &#260; &#268; &#280; &#278; &#302; Š &#370; &#362; Ž and so on... it doesnt show some symbols also. instead of them i get so called "black diamond" which looks so:
[IMG]http://www.part.lt/img/89a2f49c148d886b27d352224a2bf64f829.png[/IMG]

My system is 
Ubuntu 10.04 32bit
Intel Celeron 2.26GHz(yes, i know old one)
1.25GB ram
Nvidia FX5500
I use 173v drivers and all effects are turned off.
2.6.32-22 kernel  version
java version is 1.6_20

I think i placed enough information.. Thanks for your further help : )

---

### Post by ewuldoxx on 2010-06-17
bump this thread.

---

### Post by jesseafrantz on 2010-06-17
> **ewuldoxx said:**
> bump this thread.
The problem is all the java games are based upon using windows, which windows users are most of the time using a much more advanced version of java well past version six. Six is just a very bad out-dated version, and you are pretty much stuck with it. I hate to say there really isn't anything you can do.

---

### Post by QIII on 2010-06-17
> **jesseafrantz said:**
> The problem is all the java games are based  upon using windows, which windows users are most of the time using a  much more advanced version of java well past version six. Six is just a  very bad out-dated version, and you are pretty much stuck with it. I  hate to say there really isn't anything you can do.
 
 Not quite.  Version 6 Update 20 is the latest update for all OSs.   

Please refer to this:  [http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)

Windows users have no advantage over Linux users in that regard. Java is, by design, cross-platform.  Please refrain from dispensing FUD.

The OP  may simply have an outdated version of the plugin if the game is web-based, even though he apparently has the latest version of the JRE.

For the OP:

Set aside the character set rendering for the moment.  That might be a completely different issue to solve later.

The freezing problem with Java may be the plugin if this behavior is happening when you are trying to play games in your browser.  A less likely, but still possible, cause is your nVidia card and driver.

If you are using Firefox, please type

```
about:plugins
```in the navigation bar.  Inspect the plugins displayed and make sure you are using the Update 20 plugin.  If not, you need to replace it.  If you are using the OpenJDK plugin, your website may not recognize it.  Although I would like OpenJDK to be perfect, it is not.

Are you using Lucid Lynx (10.4)?  The latest version of Java JRE, JDK and the plugin are available in the Partner Repository for Lucid.  If you are using Lucid, activate the Partner Repository and install the Java plugin via apt or Synaptic, the version will be updated when Oracle/Sun makes the new update available and you do your normal periodic updates.

If you are using Lucid and you did not install Java via the repositories, I would suggest uninstalling all of the components and then reinstalling them via the repositories.

If you are using a version prior to Lucid, please refer to this:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Using repositories prior to Lucid will give you Version 6 Update 15 (or perhaps Update 16), which has been replaced due to security flaws.

---

### Post by ewuldoxx on 2010-06-17
As i mentioned in my first post, i use Lucid 32bit system and my java is 1.6_20 
it works good, except that stucking and not recognizing some symbols is annoying.

---

### Post by QIII on 2010-06-17
The problem with the hanging may be that the plugin is not current, despite the fact that you have the current JRE.

They are separate things.

Could you check for the plugin version as I explained?

---

### Post by ewuldoxx on 2010-06-19
Here you go : )
[IMG]http://www.part.lt/img/61336a7ebfcb61c5c81bb4106f2d46c9661.png[/IMG]

and i installed java using this script that i found in internet.
```
cd
mkdir java_install
mkdir -p ~/.mozilla/plugins >& /dev/null
sudo mkdir -p /opt/java/32
cd java_install
javalink=`curl "http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com" 2> /dev/null | grep "Linux (self-extracting file)" | head -n1 |cut -d "\"" -f4`
wget $javalink -O java.bin
sudo mv java.bin /opt/java/32/
sudo chmod 755 /opt/java/32/java.bin
cd /opt/java/32
sudo ./java.bin
sudo rm java.bin
javakonyvtar=`ls -d -t jre* | head -n1`
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/$javakonyvtar/bin/java" 1
sudo update-alternatives --set java /opt/java/32/$javakonyvtar/bin/java
sudo apt-get remove --yes icedtea6-plugin
cd ~/.mozilla/plugins/
rm libjavaplugin_oji.so libnpjp2.so >& /dev/null
ln -s /opt/java/32/$javakonyvtar/lib/i386/libnpjp2.so ~/.mozilla/plugins/ >& /dev/null
cd
rmdir java_install

```


And could someone help with those "black diamonds" ? Maybe it's font fault?

---

### Post by ewuldoxx on 2010-06-20
**B**ring **U**p **M**y **P**ost

---

