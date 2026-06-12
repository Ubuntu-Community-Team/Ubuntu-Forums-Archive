---
title: "virtualbox / vmware screenlet!"
date: 2009-09-27
forum: General Help
---

### Post by sale666 on 2009-09-27
Hello i saw a vid on youtube that i cant find now again, but the thing is its a screenlet (i think so) that is placed on the desktop with the windows sign and you click it and it starts vmware/virtualbox! 
Does any 1 know what is the name of it and where i could get it? 
Sasha

---

### Post by Jose Catre-Vandis on 2009-09-27
Are you sure it wasn't just an icon?

You can set up a launcher to run your virtual machine without opening up the vbox console. The command you need is something like this:
```
VBoxManage startvm XP
``` if you called your XP vm "XP"
Then find your favourite windows logo from somewhere and use as the icon.

---

### Post by sale666 on 2009-09-27
Actualy im not really sure it wasent an icon but hey thanks! i can set it up that way! i need it cause that way i can launch it faster! i need it so i can play cod 4 XD... lol thats all why i need windows to be installed and by having that icon will make it a lot less mess to launch!
Im still kind-a new at linux but iv been using it long enough to know some stuff however could you explain the way of creating a launcher for that?
The problem is i need the launcher set up to directly boot to xp (at least i want it to) and if possible full screen! like an application... im not really sure how to set that up!

---

### Post by Jose Catre-Vandis on 2009-09-27
I can tell you how for Xubuntu (xfce) - right click on desktop and select "Create Launcher" from drop down menu. There must be something similar in Ubuntu (gnome)

---

### Post by sale666 on 2009-09-27
yes its the same thing but i cant tell how to set up the command! how will it know to launch what i want! i want it to auto start windows xp on click!
Need the command :/

---

### Post by Jose Catre-Vandis on 2009-09-27
Not working as above?
```
VBoxManage startvm XP
```

---

### Post by sale666 on 2009-09-29
I have now switched to vmware because i cannot setup my graphic card 9800gtx in virtual box! the best thing is that i cant even do it now in vmware jesus... could you tell me what would be the command for vmware to start it like that?

Thanks and sorry for wasting ur time!

---

### Post by Jose Catre-Vandis on 2009-09-30
Last time I used Vmware was a couple of years ago, but then it was something like this:
```
vmrun start "/full/path/to/your//VirtualMachine/Windows XP Professional.vmx"
```

---

### Post by sale666 on 2009-10-01
WORKED LIKE A CHARM!
Thanks man! I was sooo pissed off cause i lost 20&#8364; on sport bets now and the same second you fixed me :D haha! 

One more thing iv been trying to do is the icon... since i downloaded the icon in PNG still the white square appears i want it to be seetrough if you know what i mean?... like a normal icon not an icon and white square around it like adding a normal picture! what kind of icon do i need for it? .ico?

Edit:
DOne it! seems that the first .png wasent a good icon it was like a photo, downloaded a new one and it works perfectly! =)

Thanks for all man! Ur a genius!

---

### Post by Jose Catre-Vandis on 2009-10-02
:)

Please mark as solved

---

