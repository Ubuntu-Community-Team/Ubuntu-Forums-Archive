---
title: "Sun Java Plugin in Ubuntu LL 64 bit"
date: 2011-12-21
forum: General Help
---

### Post by Blasphemous on 2011-12-21
I have some problems with **Sun-Java plug in**, **Firefox 8** and **Ubuntu LL 64 Bit**.

Java is installed;* java -version* gives me
> tommaso@Portatile:~$ java -version
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) 64-Bit Server VM (build 20.1-b02, mixed mode)
tommaso@Portatile:~$ it is selected, *sudo update-alternatives --config* *java* gives me
> È presente una sola alternativa nel gruppo java: /usr/lib/jvm/java-6-sun/jre/bin/java
Nulla da configurare.which is the italian for "There's only Sun Java and no other possibilities so there's nothing to configure"

BUT

I still **can't get to make my plug in to work**: everytime I try to run a java applet I get messages like "Please install java", even with the ufficial Sun test page, [http://java.com/it/download/installed.jsp](http://java.com/it/download/installed.jsp).

The **sun-java-plugin packege is installed**, according to synaptic, but there's nothing named java in the /home/.mozilla/plugins folder or in the Mozilla lib folder...

I **don't** want to install OpenJDK and IcedTea, I just need Sun Java...

---

### Post by Lampi on 2011-12-21
try this:
```
sudo ln -vs /usr/lib/mozilla/plugins/libnpjp2.so /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so
```

And please read [this]("http://www.omgubuntu.co.uk/2011/12/java-to-be-removed-from-ubuntu-uninstalled-from-user-machines/") to understand why you'll have to upgrade java on your own in the near future.

---

### Post by QIII on 2011-12-21
You get the Java plugin by creating a symbolic link to the .so.

If you don't want to do that manually, I highly recommend the following website.  It gives explicit instructions, and commands you can C&P into the terminal to get Java set up.

This may be the best way to go, since it allows you do just trash your current Java setup and install a new one when an update comes out.

I would probably go to the jvm directory first and use the uninstall script that should be there to uninstall what you have now so you don't run into problems.  If you installed via Synaptic, uninstall it there.

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

(Egad!  Almost forgot.  I think the instructions say to uninstall OpenJDK.  DON'T.  You can bork other things.  But when you get to the part of the instructions where he says to remove the IcedTea plugin, you can do that.)

---

### Post by Lampi on 2011-12-21
I noticed you use 64bit ubuntu - so it's possibly not /i386/, but something like 64bit

Sorry I missed that, but I'm sure you'll find out the correct path to your 64bit libnpjp2.so :)

---

### Post by Blasphemous on 2011-12-21
> **Lampi said:**
> I noticed you use 64bit ubuntu - so it's possibly not /i386/, but something like 64bit

Sorry I missed that, but I'm sure you'll find out the correct path to your 64bit libnpjp2.so :)

*sudo ln -vs /usr/lib/mozilla/plugins/libnpjp2.so /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/amd64/libnpjp2.so* gives me this:

```
ln: creazione del collegamento simbolico "/usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/amd64/libnpjp2.so": Il file esiste
```which means

```
The file already exists
```

EDIT: Well, now Firefox crash everytime I tray to load a java applet...

---

### Post by Lampi on 2011-12-21
damn ... also my mistake, it's the other way around!
```
sudo ln -vs /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/amd64/libnpjp2.so /usr/lib/mozilla/plugins/libnpjp2.so
```

---

### Post by Blasphemous on 2011-12-21
Solved by removing, cleaning up (bleachbit - deborphan) and reinstalling Java!
Easier than we thought!

Thanks!

---

### Post by Lampi on 2011-12-21
I don't know about that, but the reason you had "Il file esiste" is: I gave you the path the wrong way around, sorry!

---

### Post by Pjotr123 on 2011-12-21
> **QIII said:**
> (Egad!  Almost forgot.  I think the instructions say to uninstall OpenJDK.

They don't say that anymore: I've corrected that some time ago in the how-to.... It says now that only the Icedtea browser plugin should be removed, which is quite safe. :) 

By the way: currently, there's even an automated option (mentioned in my how-to as well, since yesterday): the duinsoft repo. That repo contains a script that pulls in the newest Oracle Java (6u30) from the Oracle website and installs it. Which is still allowed by the Oracle license.
[http://sites.google.com/site/easylinuxtipsproject/java#TOC-The-repository-of-duinsoft.nl](http://sites.google.com/site/easylinuxtipsproject/java#TOC-The-repository-of-duinsoft.nl)

So there are two easy options now.

---

### Post by QIII on 2011-12-21
Thanks for the update, Pjotr.  I've been recommending that tutorial for a long time.  I guess I hadn't looked at it for a while because I have a "tips and tricks" file I've put together for myself over the years.

---

