---
title: "How to set JAVA_HOME"
date: 2010-05-24
forum: General Help
---

### Post by sureshatt on 2010-05-24
You can install Java either using "Synaptic Package Manager" or using "apt-get install java-6-openjdk" command.
Java will be installed to the location "/usr/lib/jvm/java-6-openjdk"
Now open a terminal and type "sudo gedit /etc/bash.bashrc ".
Append the following lines to the opened "bash.bashrc" file
"export JAVA_HOME=/usr/lib/jvm/java-6-openjdk/"
"export PATH=$PATH:$JAVA_HOME/bin"
Save & close the "bash.bashrc" file
Go to the terminal and type the following command
"source /etc/bash.bashrc "
Now your done with setting up JAVA_HOME. to test, type the following command.
"echo $JAVA_HOME" (or type "env")
It should print "/usr/lib/jvm/java-6-openjdk"
Now, everything is done. thnx

---

### Post by ishan_sangai on 2011-09-21
Hi,

Actually I am not getting where to add 

"export JAVA_HOME=/usr/lib/jvm/java-6-openjdk/"
"export PATH=$PATH:$JAVA_HOME/bin"

these lines in bash.bashrc file.

in the last or in between ?

 please help me 

Thanks,
Ishan

---

### Post by vinayg18 on 2011-10-06
Anywhere's fine, just as long as it's not within any of the if blocks

---

