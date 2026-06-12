---
title: "Auto install script, no need for confirmation..."
date: 2010-04-13
forum: General Help
---

### Post by Lord DEA on 2010-04-13
Hello everybody,
I just reinstalled Ubuntu, but before that I made a list of all the programs that needed to reinstall too..
so I ended up with a script that looks like:
```

#!/bin/bash
sudo apt-get install app1
sudo apt-get install app2
sudo apt-get install app3
.
.
.

```

the thing is that it keeps asking me for confirmation before installing every app, and I want it not to... so I can get some sleep while it sets up everything...
How do I do this?
maybe using the "yes" command, but how?

---

### Post by Lord DEA on 2010-04-13
Fool of me, forgot that man pages existed...
FTR, only needed to add "-y" option:
```

#!/bin/bash

sudo apt-get -y install app1
sudo apt-get -y install app2
sudo apt-get -y install app3
sudo apt-get -y install app3
.
.
.

```

---

### Post by Mr Nemo on 2010-04-13
Thats a good idea for when I upgrade. Thanks for posting this.

---

### Post by prodigy_ on 2010-04-13
You can simplify the code by removing leading **sudo**-es (because you can run the whole script with sudo). Also, no need to call apt-get for every single app. Instead you can use something like: ```
apt-get -y install <app_1> <app_2> <app_3> \
        <app_4> <app_5> <app_6> \
        <app_7> <app_8> <app_9> \
...
```

---

### Post by Lord DEA on 2010-04-14
whoa, much simpler now...
thx a lot

---

### Post by DeMus on 2010-04-14
What is also possible is to export a list from Synaptic of installed programs. Then after the re-install just import that list and apply the changes made. Works fine.

---

### Post by prodigy_ on 2010-04-14
> **DeMus said:**
> What is also possible is to export a list from Synaptic of installed programs. Then after the re-install just import that list and apply the changes made. Works fine.

Indeed. First, you need to save the names of all installed packages to a file. For example:
```
dpkg -l|awk '{ print $2 }'|grep -v '^[A-Z]' > ./pkgs.list 
```

Then you can move **pkgs.list** to another installation and use a very simple script to parse it: ```
#!/bin/sh
apt-get update
while read line; do apt-get install -y $line; done < ./pkgs.list
```

---

### Post by DeMus on 2010-04-15
> **prodigy_ said:**
> Indeed. First, you need to save the names of all installed packages to a file. For example:
```
dpkg -l|awk '{ print $2 }'|grep -v '^[A-Z]' > ./pkgs.list 
```

Then you can move **pkgs.list** to another installation and use a very simple script to parse it: ```
#!/bin/sh
apt-get update
while read line; do apt-get install -y $line; done < ./pkgs.list
```

Why so complicated when Synaptic can export it with a simple click of the mouse?

---

