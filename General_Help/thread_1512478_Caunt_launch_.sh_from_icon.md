---
title: "Caunt launch .sh from icon"
date: 2010-06-18
forum: General Help
---

### Post by raafe on 2010-06-18
Hi all,

Was wondering if anyone could help me out here, i am running Kubuntu 10.04 and i want to make some icons on the desktop to launch various telnet sessions. So i make a .sh using vi test.sh and then put in telnet 180.9.x.xx and save and quit. Then i chmod 777 it to make it executable and then moved it to my Desktop folder. But when i double click or right click and open with konsole nothing happens. I know it is probably something stupid which i have overlooked but when i have done this in Ubuntu in the past it has worked.

Thanks all 

Raafe

---

### Post by raafe on 2010-06-18
Guess i will just stick to launching from konsole then O:)

---

### Post by Chame_Wizard on 2010-06-18
.sh is a shell script,so you have to make a workaround for it.

---

### Post by raafe on 2010-06-18
Thanks for the reply - i know .sh is a script. I was just curious as to know why i can double click an executable .sh and it will launch in Ubuntu but nothing happens if i do the same in Kubuntu. It's no biggy it's just i have about 20 different machines to telnet into and it's easier having an icon for each and just clicking it and being away instead of opening the konsole and then typing the name of the script..

---

### Post by phildini on 2010-06-18
If you have the correct header, something like 

```
#! /bin/bash
```

and save it as a .sh, you can right-click the icon on the desktop, go to Properties > Open With > Add and add "/bin/bash" under the command. 

Also, you should think about using SSH instead of telnet.

---

### Post by raafe on 2010-06-21
> **phildini said:**
> If you have the correct header, something like 

```
#! /bin/bash
```and save it as a .sh, you can right-click the icon on the desktop, go to Properties > Open With > Add and add "/bin/bash" under the command. 

Also, you should think about using SSH instead of telnet.

Thanks for the reply, still no luck - I can see bash trying to open but it closes itself before anything shows up. Perhaps it is a problem with the Maverick Alpha. Anyway i will stick to launching them from konsole. And unfortunatley ssh is not an option - logging in to very old telephone systems.

---

### Post by Smart Viking on 2010-06-21
> **raafe said:**
> Thanks for the reply, still no luck - I can see bash trying to open but it closes itself before anything shows up. Perhaps it is a problem with the Maverick Alpha. Anyway i will stick to launching them from konsole. And unfortunatley ssh is not an option - logging in to very old telephone systems.

Hi, i had the same thingy goin' on, just have this in the top of your script:

```
#!/bin/bash
tty -s; if [ $? -ne 0 ]; then "xfce4-terminal" -e "$0"; exit; fi
```But you must change "xfce4-terminal" with whatever terminal you are using, per example "konsole". (if that is the command to launch konsole). I hope this helped. :)

---

### Post by raafe on 2010-06-21
> **Smart Viking said:**
> Hi, i had the same thingy goin' on, just have this in the top of your script:

```
#!/bin/bash
tty -s; if [ $? -ne 0 ]; then "xfce4-terminal" -e "$0"; exit; fi
```But you must change "xfce4-terminal" with whatever terminal you are using, per example "konsole". (if that is the command to launch konsole). I hope this helped. :)


You Sir are a life saver! Replacing xfce4-terminal with konsole worked a treat. Thanks very much :p

---

