---
title: "How to access 'Users and Groups' ?"
date: 2012-03-25
forum: General Help
---

### Post by susja on 2012-03-25
Hello,
I just installed Virtualbox on my Ubuntu 11.10 in order to use Windows and access it using USB. I hit a known issue i.e. I can't access USB inside Virtualbox.
Ubuntu documentation states that to fix it I have to do the following: "Add yourself to the user group vboxusers,...."
First of I can't find Users and Groups. I could see only 'User Accounts' in System settings. I also don't see vmboxusers group when I run %groups from command line.
Anyway I have to add myself to vmboxusers group in order to use USB on Virtualbox.
Could someone pls help me with that?
Thanks

---

### Post by lechien73 on 2012-03-25
Hi,

I had the same problem with a fresh install recently. The answer was to open a terminal window and type:

```
sudo usermod -a -G vboxusers USERNAME
```

Replace USERNAME with your username. I had to log out and back in again for the changes to take effect.

---

### Post by matt_symes on 2012-03-25
Hi

> **susja said:**
> Hello,
I just installed Virtualbox on my Ubuntu 11.10 in order to use Windows and access it using USB. I hit a known issue i.e. I can't access USB inside Virtualbox.
Ubuntu documentation states that to fix it I have to do the following: "Add yourself to the user group vboxusers,...."

From the terminal

```
sudo usermod -aG vboxusers <your_user_name>
```

Change your user name as required. Enter your password. It will not be echoed to the screen. This will add you as a member of vboxusers.

```
newgrp
```

The above will allow you to use the group without rebooting.

> First of I can't find Users and Groups. I could see only 'User Accounts' in System settings. 

That's the one you want. You can add and remove users to groups from there (but not in precise as far as i am aware)

> 
I also don't see vmboxusers group when I run %groups from command line.

The *groups* command will just show you the groups you are currently a member of.

```
cut -d : -f1 /etc/group
```

That will give you a list of all the groups.

Kind regards

---

### Post by susja on 2012-03-25
> **lechien73 said:**
> Hi,

I had the same problem with a fresh install recently. The answer was to open a terminal window and type:

```
sudo usermod -a -G vboxusers USERNAME
```Replace USERNAME with your username. I had to log out and back in again for the changes to take effect.

Thanks ... that worked for me as well ...
Just curious why I can't access groups using GUI while I'm member of administrators but that's apparently another question.
But regarding adding myself to group using usermod it worked for me.
thanks

---

### Post by lechien73 on 2012-03-25
I think the old "Users & Groups" applet was part of GNOME. I know it can be installed by typing:

```
sudo apt-get install gnome-system-tools
```

In a terminal window.

I've always been of the opinion that Linux provides a powerful CLI, with less powerful GUI so that you don't make changes accidentally. Windows, on the other hand, seems to have moved towards a crippled CLI while letting any old user do whatever they want in the GUI. Just my opinion, and it could well be wrong :D

Anyway, if it's worked for you, could you use the **Thread Tools** menu above the first post and mark the issue as [SOLVED], please?

Thanks

---

