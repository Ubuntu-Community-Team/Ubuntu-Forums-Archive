---
title: "Java.."
date: 2010-09-07
forum: General Help
---

### Post by Jaike on 2010-09-07
Ok so I have recently purchased my VPS and I have installed the wonderful "Ubuntu 10.04 32bit". I have installed VNC fine and I can connect to the Remote Desktop with a GUI.

Im looking to run "RsBot" but im unsure on how to run Java. I am really stuck and I was wondering how I can install java as when I try and run the setup it just open the folder up..

Thanks x
__

Im currently installing OpenJDK Java 6 Runtime, ill update you when its done.

---

### Post by mendhak on 2010-09-07
Not sure what you mean by the setup opening as a folder, but you can install JRE/JDK via Synaptic or terminal.

*sudo apt-get install sun-java6-jdk 			 		*

You could also have a look at [this page](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html).

So it should do the download *and* do the symbolic links for you.


Also, I don't know what rsbot is but I was able to find this post talking about [setting up rsbot on Ubuntu, including getting Java](http://www.sythe.org/showthread.php?t=574222).

---

### Post by krishnandu.sarkar on 2010-09-07
^^+1

sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin

---

### Post by Jaike on 2010-09-07
Thanks but none of the remidies work, the guide above on Sythe does not work.

Basically I just want to install Java on my VPS.

---

