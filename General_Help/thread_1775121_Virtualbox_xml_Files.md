---
title: "Virtualbox xml Files?"
date: 2011-06-04
forum: General Help
---

### Post by Quarkrad on 2011-06-04
Running 10.10  and Virtualbox 4.0.8.  I have winXP and Ubuntu 11.04 running in VirtualBox.  I keep reading that certain changes are made to the xml file for each machine located, e.g, at **/home/username/.VirtualBox/Machines/Windows XP/Windows XP.xml**.  However, when I look in my **/home/username/.VirtualBox/Machines**/ folder it is empty.  Both virtual machines work so I'm assuming everything is setup OK.  As the specified folder is empty the xml files must be located elsewhere - but where?

---

### Post by howefield on 2011-06-04
Do you have 

> /home/user/VirtualBox VMs

You should have a .vbox file in there for your VM, I believe this is what used to be (pre virtualbox version 4.0) the .xml file.

---

### Post by Quarkrad on 2011-06-04
Thank you - yes I have and I can see my winXPand Ubuntu 11.04 folders.  However, there are files but no xml files.  Do you know if the 'google posts' that refer to editing these xml files are not relevant to 4.0.8?

---

### Post by howefield on 2011-06-04
But you should have .vbox files in there.

It will contain your VM settings and is editable.

---

### Post by coffeecat on 2011-06-04
I've just done a fresh install of 4.08 and it's interesting that there is no Machines folder in ~/.VirtualBox. As howefield says the virtuals discs are now in ~/"VirtualBox VMs". Did you do an upgrade of VB from an earlier version? Perhaps that's why the Machines folder is still there. Anyway, I can see a VirtualBox.xml file in ~/.VirtualBox. There are just four files there - no folders. **EDIT**: but no *xml files in ~/"VirtualBox VMs" that I can find.

---

### Post by Quarkrad on 2011-06-05
Thank you for your replies.  I did install 4.0.8 from scratch - however, I'm happy now I know about the Virtualbox VMs folder in Home.

---

