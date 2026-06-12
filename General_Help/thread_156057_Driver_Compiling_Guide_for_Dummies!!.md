---
title: "Driver Compiling Guide for Dummies!!"
date: 2006-04-06
forum: General Help
---

### Post by doc_kamolly on 2006-04-06
Hi people,

i need help compiling my dial-up modem driver from scratch, please help me in a single-tracked way, like baking a cake.

Last time I tried, I got lost and didn't know what to do.

Help!!

Thanks.

---

### Post by taurus on 2006-04-06
You need step by step but you don't tell us what kind of modem do you have!!!  However, before you plan to build or compile something, you need to install all the neccessary files on your system first and you can do that with this command.
```

sudo apt-get install build-essential

```

---

### Post by towsonu2003 on 2006-04-06
check out the second link in my signature

---

### Post by doc_kamolly on 2006-04-07
in the wiki guide, the command is different than the one posted above, what does the linux-headers-`uname -r` signify?

Sorry, I'm still a NEWBIE, and a hugy one.

---

### Post by curtis on 2006-04-07
> 
in the wiki guide, the command is different than the one posted above, what does the linux-headers-`uname -r` signify?

Sorry, I'm still a NEWBIE, and a hugy one.

They are for compiling kernel modules, the headers are used the same as the -dev packages.
Things that build kernel modules, E.g. the nVidia driver and other drivers.
Need the kernel headers as well.

---

### Post by shahrc on 2006-04-07
[QUOTE=curtis]They are for compiling kernel modules, the headers are used the same as the -dev packages.
Things that build kernel modules, E.g. the nVidia driver and other drivers.
Need the kernel headers as well.[/QUOTE]
do we have to change the **'uname -r'** to our kernel name(version)?

---

### Post by towsonu2003 on 2006-04-07
[QUOTE=doc_kamolly]in the wiki guide, the command is different than the one posted above, what does the linux-headers-`uname -r` signify?

Sorry, I'm still a NEWBIE, and a hugy one.[/QUOTE]
let me rephrase curtis' response :)

open up a terminal and type ```
uname -r
``` The output is the version of our kernel. when you compile kernel, you need either the source of your version of kernel or its headers. when you input ```
sudo apt-get install linux-headers-`uname -r`
``` and hit enter, the uname -r will automagically be replaced by the version that was shown in the output and the appropriate kernel headers are downloaded. you could as well write linux-headers-outputofunameminusr there, but it's harder to explain what's going on in there in a wiki (which should be concise) :)

---

