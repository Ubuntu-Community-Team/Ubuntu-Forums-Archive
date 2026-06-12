---
title: "How to setup a bukkit server?"
date: 2012-06-15
forum: General Help
---

### Post by ugotboxed on 2012-06-15
I'm trying to set up a bukkit server on my desktop. The only problem is that what is on the help forums on bukkit aren't very descriptive. so I'm wondering if anyone could help me. I downloaded the recommended build of craftbukkit and made a minecraft.sh text document. Then I pasted the stuff that they told me to. But it doesn't seem to be working. Thanks for the help in advance.

---

### Post by SDX0 on 2012-06-15
You need to have some sort of Java installed on your computer to run a Bukkit server.  If you're already able to play Minecraft then you have that prerequisite filled out for sure.  If not, install OpenJDK or Sun Java 6 before continuing.

After that you should probably put the Bukkit jar file into its own folder.  I would suggest a folder named "Bukkit" in your home folder.

From there just open a terminal and type "java -jar ~/Bukkit/*[name of your bukkit file]*.jar" and Bukkit will create the other files and folders it needs automatically.

---

