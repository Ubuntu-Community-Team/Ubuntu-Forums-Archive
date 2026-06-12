---
title: "Please help installing Java"
date: 2010-01-05
forum: General Help
---

### Post by salman4u on 2010-01-05
Hello,

This is my 1st post so please bear with me if something i have done wrong. My problem is that i installed Ubuntu 9.10 inside Windows 7 then i downloaded Java SDK and Java JRE, both were .bin files. Then using sudo command i ran those .bin files in terminal ( i dont know how to run GUI way .bin files. If you know that then tell me that too) , whose location were Windows OS disk, so it created folder there. Ok then after few minutes it gave installed message on command line, but in ubuntu software center i don't get Java in the list. Am i doing something wrong? Even when i type java -version in terminal it asks me to install packages and says command not found. When i already installed both the things then why is it prompting me for again installing through packages?? I have spent now almost 3 hours but still not able to figure it out. I am absolute new to Ubuntu and i like this OS very much but i am not aware of some basic things. Do i need to set some environment variables for it? in Windows  i used to set CLASSPATH(path to class files) and PATH(path to jre). Please guide me step by step.

Thanks in advance,
[LEFT]Salman4u
[/LEFT]

---

### Post by Avidanis on 2010-01-05
What type of Ubuntu install do you have ? Wubi ? Did you partition your harddrive and install it or run Wubi ? 

One way to install Java is to open up Synaptic Package Manager. Like so 

System/Administration/Synaptic Package Manager

It will ask for root password.

type java into the the search box and you will get something like the following

[ATTACH]142566[/ATTACH]l

check off Sun Java(TM) Runtime Environment (JRE) 6 (32-bit) or whatever is appropiate for your system . Click "mark for installation"

Then click apply . Thats it .

---

### Post by bjk03 on 2010-01-05
You can install them with the Synaptic Package Manager.

---

### Post by salman4u on 2010-01-05
Thanks,
for your replies. Yes i know it can be installed using Synaptic Package Manager but actually i downloaded the .bin files from Sun. I installed using WUBI (means didnt allocate separate partition). I think i need to set some JAVA_HOME variable or something like that but now i have faced so much trouble installing it from .bin that now i am thinking of installing using Synaptic Package Manager only. Thanks again for your replies.

---

