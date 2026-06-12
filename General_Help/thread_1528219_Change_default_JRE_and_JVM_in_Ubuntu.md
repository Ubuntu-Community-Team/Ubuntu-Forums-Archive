---
title: "Change default JRE and JVM in Ubuntu"
date: 2010-07-10
forum: General Help
---

### Post by Odaym on 2010-07-10
> One of the greatest things about Linux, ( I'm currently using Ubuntu 10.04 LTS) is your ability to install more than one version of java. Ubuntu, and by default, comes loaded with OpenJdk, which is an open source version of Java. As I stated in a previous discussion, I had some issues to run glassfish with the OpenJdk, so I decided to install the "closed" version of Java directly from Sun microsystem's website ( Hosted by oracle nowadays).

After downloading the latest Java development kit(JDK) which also includes the Java Runtime Envirnonment (JRE), I installed it from the terminal. The java file I downloaded was a ".bin" file. I have explained in the previous discussion, how to install a .bin file.

The installer will extract all the contents of the ".bin" file to a folder in the same directory as of the ".bin" file.
Assuming that you have extracted the contents of the ".bin" file to a folder on your Desktop called JAVA6, then the path to this folder would be:
/Desktop/JAVA6

after that go to your terminal window and do the following:
sudo update-alternatives --install "/usr/bin/java" "java" "/Desktop/JAVA6/bin/java" 1

Then issue the following command:

sudo update-alternatives --set Desktop/JAVA6/bin/java

This should set your newly installed java as your default JVM and JRE.

This was a thread started somewhere by someone, is this information accurate? appreciate a brief explanation if it isn't, thank you!

---

### Post by dino99 on 2010-07-10
use this now:

sudo update-alternatives --config java

---

### Post by ajgreeny on 2010-07-10
You can use the normal installation methods for this, eg synaptic.

Just make sure you have the partner repos enabled, (archive.canonical) then search for sun-java and you will find all the sun java applications available to you

---

