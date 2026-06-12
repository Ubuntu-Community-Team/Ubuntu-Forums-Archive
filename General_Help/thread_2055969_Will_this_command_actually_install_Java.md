---
title: "Will this command actually install Java?"
date: 2012-09-10
forum: General Help
---

### Post by linuxvstheworld on 2012-09-10
Seems like a stupid question, I know but I need some confirmation before I actually run the following command.
```
sudo apt-get install openjdk-7-jdk openjdk-7-jre icedtea-7-plugin
```
The plugin meaning java will work in browser right?
And will the code I posted work on Ubuntu 12.04?
EDIT: A fellow member Chessemill came up with this method.
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```
Will either of them work? Cheesemill's way will actually keep java up to date.
Which way is actually preferred?

---

### Post by Cheesemill on 2012-09-10
That will install the Open Source version of Java which is fine for most websites. Some sites, however, refuse to recognise it.

If this is the case then you can install Oracle Java instead by running the following commands:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer

```
All of this is information can be found in the Ubuntu Wiki.
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by linuxvstheworld on 2012-09-10
Surprised that you actually replied, Cheesemill! Will the way you posted actually run .jar files? That's the main reason for me to actually have java.

---

### Post by Cheesemill on 2012-09-10
Yes it will.

I know that some applications (Minecraft) run better using Oracle Java than they do using OpenJDK.

---

### Post by linuxvstheworld on 2012-09-10
> **Cheesemill said:**
> Yes it will.

I know that some applications (Minecraft) run better using Oracle Java than they do using OpenJDK.
Will it run at least okay though? Like about 20 or so FPS? (Helping my friend get Linux, and he has Minecraft, and using 1.5GB of RAM :))
EDIT: Actually, just noticed the commands you listed which I saved actually get Oracle Java, better read closer next time ;).
Thanks for the help!

---

### Post by Zvlwab on 2012-09-10
Minecraft runs just fine in openjdk-7.

---

