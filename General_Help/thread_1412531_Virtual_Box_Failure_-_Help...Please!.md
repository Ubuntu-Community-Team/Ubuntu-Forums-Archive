---
title: "Virtual Box Failure - Help...Please!"
date: 2010-02-21
forum: General Help
---

### Post by jimcameron on 2010-02-21
Hi guys, 

Last night i closed down the VB as 'save current state' but i think i might have been hasty with shutting down the Ubuntu machine at the same time. This morning when i loaded up VB it came up with the following message

Start tag expected, '<' not found.

Location: '/home/jim/.VirtualBox/Machines/XP/XP.xml', line 1 (0), column 1.

/home/vbox/vbox-3.1.2/src/VBox/Main/MachineImpl.cpp[5821] (nsresult Machine::loadSettings(bool)).
Result Code: NS_ERROR_FAILURE (0x80004005)
Component: VirtualBox
Interface: IVirtualBox {2158464a-f706-414b-a8c4-fb589dfc6b62}


Does anybody know what this means? Can anybody help?

Cheers Jim

---

### Post by s.fox on 2010-02-21
Hello.

Try running this command in terminal:

```
sudo /etc/init.d/vboxdrv setup
```

Then try and launch virtual box again :)

-Silver Fox

---

### Post by jimcameron on 2010-02-21
Hi Silver Fox,

Cheers for that, that didn't sort it out. Still has the same error message. Any other solutions?

Cheers
JIm

---

### Post by endeavormac on 2010-02-21
what are the contents of:
/home/jim/.VirtualBox/Machines/XP/XP.xml

---

### Post by jimcameron on 2010-02-21
A folder for called Logs and another called Snapshots.

---

### Post by s.fox on 2010-02-22
Hello,

In that same directory you should see XP.xml

Does it not exist? 

-Silver Fox

---

