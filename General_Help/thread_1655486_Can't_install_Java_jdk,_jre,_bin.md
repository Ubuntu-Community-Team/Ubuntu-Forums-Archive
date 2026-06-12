---
title: "Can't install Java jdk, jre, bin"
date: 2010-12-29
forum: General Help
---

### Post by Konsigliare on 2010-12-29
Hi all
I've been trying the best part of the day trying to install Java on a server remotely through terminal.
I've read many guides and they are all straightforward - use "sudo apt-get update" and then the following:
```
sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-bin
```

However, I keep getting an error - 

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate
```

Someone had the same problem (although on a different version of ubuntu) and someone suggested adding a line to their sources.list, however I didn't know what file to edit :(

After I install this, I will need to set the system/envirnoment variables - if anyone knows how to do that, please do share!

Help concerning this is greatly appreciated.
Thanks

---

### Post by wojox on 2010-12-29
Go into Software Sources > Other Software and enable the archive's.

---

### Post by Konsigliare on 2010-12-29
> **wojox said:**
> Go into Software Sources > Other Software and enable the archive's.
Hi, thanks for the reply
I'd love to do that, only I can only use terminal!

---

### Post by Gremlinzzz on 2010-12-29
go to synaptic package manager click settings choose repositories and  choose other software tab and check canonical partners.
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin

[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Add_Extra_Repositories](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Add_Extra_Repositories)
adding repos through terminal

---

### Post by 3rdalbum on 2010-12-29
sudo nano /etc/apt/sources.list

Uncomment the Partner repository line by removing the # character at the start of the line.

Control-X, press Y and then Enter to save.

sudo apt-get update.

Now you can install Java.

---

### Post by wojox on 2010-12-29
> **3rdalbum said:**
> sudo nano /etc/apt/sources.list

Uncomment the Partner repository line by removing the # character at the start of the line.

Control-X, press Y and then Enter to save.

sudo apt-get update.

Now you can install Java.

+1 I missed the whole Server part. :confused:

---

