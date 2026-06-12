---
title: "Could not applt the stored configuration for monitor"
date: 2012-07-17
forum: General Help
---

### Post by yellowho on 2012-07-17
Hi 

i'm newbie with ubuntu, i was running ubuntu 12.04 on my machine. Recently faced an error "Could not apply the stored configuration for monitor" when i power on my machine.

Tried find some info on net, saying that remove .config/monitors.xml will solve my problem, but i did'nt found this file at all.

Please help, thanks.

---

### Post by dino99 on 2012-07-17
every file starting with a dot in its name is a hidden files under linux; to see it you need to unhide it: ctrl+h (ctrl key   +  h)

---

### Post by yellowho on 2012-07-17
> **dino99 said:**
> every file starting with a dot in its name is a hidden files under linux; to see it you need to unhide it: ctrl+h (ctrl key   +  h)

yes, i already unhide it
[[IMG]http://img600.imageshack.us/img600/294/screenshotfrom201207171.png[/IMG]](http://imageshack.us/photo/my-images/600/screenshotfrom201207171.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by yellowho on 2012-07-17
please help.....thanks

---

### Post by yellowho on 2012-07-18
anybody can help this, it really annoying me. thanks

---

### Post by yellowho on 2012-07-18
please help me....

---

### Post by maan81 on 2012-07-28
> **yellowho said:**
> Hi 

i'm newbie with ubuntu, i was running ubuntu 12.04 on my machine. Recently faced an error "Could not apply the stored configuration for monitor" when i power on my machine.

Tried find some info on net, saying that remove .config/monitors.xml will solve my problem, but i did'nt found this file at all.

Please help, thanks.

What dos the error say ? Perhaps more detail would be helpful.

---

### Post by aselvan on 2012-07-29
> **yellowho said:**
> please help me....

Open up a shell (i.e. run gnome-terminal) and type the following commands and hit enter. 

mv ~/.config/monitors.xml ~/.config/monitors.xml.broken

---

### Post by yellowho on 2012-08-07
> **aselvan said:**
> Open up a shell (i.e. run gnome-terminal) and type the following commands and hit enter. 

mv ~/.config/monitors.xml ~/.config/monitors.xml.broken

thanks for your reply, i had follow your command but it's show "no such directory" after hit "Enter"

---

### Post by yellowho on 2012-08-17
pls help....thanks

---

### Post by mitchd123 on 2012-09-30
Aselvan's  command eliminated the problem on my system. 

Essentially you want to rename or delete the file .config/monitor.xlm

---

