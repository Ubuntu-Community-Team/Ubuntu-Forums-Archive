---
title: "I want to creat a custom application launcher for matlab"
date: 2011-05-30
forum: General Help
---

### Post by northfly on 2011-05-30
I installed matlab and setup the environmental variable in /etc/environment,

when I need run the matlab, I just open a terminal and type matlab.

but I now i want to simplify further and create a launcher on the desktop bar.

here is what I got:

1:I choose the type as "application" and command as "matlab",
the matlab looks been started and I can see the splash image of matlab, but it disappear quickly and then nothing happen anymore.

2: I choose the type as "application in terminal" and command as "matlab"
the matlab open with an x terminal, and I can use the matlab.


how can I open the matlab without open a terminal? Thanks.

---

### Post by northfly on 2011-05-30
help me!

---

### Post by tobsco on 2011-05-30
Have you tried finding the executable file and dragging it onto the panel?

---

### Post by JCM_Pico on 2011-05-30
Hi mate,
You can always do:

1. Get an icon for your launcher: 
```
sudo wget http://upload.wikimedia.org/wikipedia/commons/2/21/Matlab_Logo.png -O /usr/share/icons/matlab.png
```

2. Get pre-configured launcher file: 

```
 
sudo wget 'https://help.ubuntu.com/community/MATLAB?action=AttachFile&do=get&target=matlab-r2011a.desktop' -O /usr/share/applications/matlab.desktop 
```

It worked pretty well for me...

I've followed this document --> [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

farewell

---

### Post by wildmanne39 on 2011-05-30
> **northfly said:**
> I installed matlab and setup the environmental variable in /etc/environment,

when I need run the matlab, I just open a terminal and type matlab.

but I now i want to simplify further and create a launcher on the desktop bar.

here is what I got:

1:I choose the type as "application" and command as "matlab",
the matlab looks been started and I can see the splash image of matlab, but it disappear quickly and then nothing happen anymore.

2: I choose the type as "application in terminal" and command as "matlab"
the matlab open with an x terminal, and I can use the matlab.


how can I open the matlab without open a terminal? Thanks.Hi, click on the power users guide under this text in my signature then scroll down the page of to Launcher and Quick Lists and it will tell you how to make a icon launcher for a terminal app.

---

