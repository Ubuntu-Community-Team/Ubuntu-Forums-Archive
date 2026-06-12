---
title: "trouble getting Java to install"
date: 2011-04-22
forum: General Help
---

### Post by shalamabobbi on 2011-04-22
I have a new install of ubuntu 10.04 LTS
I came across the following instructions:

sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
sudo update-alternatives --config java

After the third instruction I get something like an acceptance license agreement show up in the terminal window. 
But it doesn't respond to any input. It just hangs waiting for me to accept the license agreement.

So I eventually closed the terminal and had to redo a fresh install.

I just want java to work in my firefox browser to play chess against the computer online..

Any other way to install it?

---

### Post by dino99 on 2011-04-22
Open a Terminal window

Run sudo update-java-alternatives -l to see the current configuration and possibilities.

Run sudo update-java-alternatives -s XXXX to set the XXX java version as default. For Sun Java 6 this would be sudo update-java-alternatives -s java-6-sun

Run java -version to ensure that the correct version is being called. 

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by shalamabobbi on 2011-04-22
Reading through the references you provided I got the feeling I should be using the synaptic package manager to install openjdk-6-jre and icedtea6-plugin.

I did that.

sudo update-java-alternatives -l
resulted in:
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk

sudo update-java-alternatives -s java-6-openjdk
resulted in a lot of error messages..

java version
resulted in:
1.6.0_20
IcedTea6 1.9.7
6b20-1.9.7-Oubuntul -10.04.1
build 19.0-b09, mixed mode

Following the last link to the Java site where it tested my PC resulted in a message that I needed to get a more current update. I downloaded it.

I followed the instructions to create the link to the plugin but ran into trouble. I can navigate through the gui windows to the firefox folder 
but trying to duplicate it with the terminal window I have the following problem. The firefox directory doesn't show up even though I traced the same path. 

I am stumped..

---

### Post by shalamabobbi on 2011-04-22
ok - found another web page with instructions.

I opened a terminal window and typed:

cd /usr/lib/mozilla/plugins
 and it worked..

I followed with:
sudo ln -s /home/jerry/jre1.6.0_24/plugin/i386/ns7-gcc29/libjavaplugin_oji.so

and that worked too.

But still no java functionality in firefox..

Do I need to reboot the PC or just close and restart the browser?

---

### Post by shalamabobbi on 2011-04-22
OK, I got it sorted out..

hxxp://ubuntuforums.org/showthread.php?t=1517979 (change xx to tt)

I uninstalled iced tea and openjdk using synaptic and marking for COMPLETE removal. Then used the software center to add repository as directed in the referenced thread above. I could not get the software center to function though for adding the sun plugin so I used the synaptic package manager for that. Afterwards everything worked.

Oh I also had to toss the folder I created earlier by downloading and installing the java update from the java site.

---

