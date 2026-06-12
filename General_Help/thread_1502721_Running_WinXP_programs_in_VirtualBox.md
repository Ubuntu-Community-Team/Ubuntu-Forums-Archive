---
title: "Running WinXP programs in VirtualBox"
date: 2010-06-05
forum: General Help
---

### Post by misterfixit on 2010-06-05
I am running VirtualBox on my Ubuntu box.  Everything works fine; No problems running WinXP from an ISO, etc.  I have several Windows only applications which I want to run on the WinXP VM.  I cannot see the programs I have downloaded when using Explorer for Windows.  Ordinarily, in a WinXP only system, I just find the program to be installed and double click on it to start the automatic installation routine.  In this case, I cannot see any of the .exe files used for the install.  I have placed those downloaded Windows application in the same directory on my Ubuntu Box as where VirtualBox, the Sun Guest Editions and the CD Image of the Garmin Trip and Map system.  I installed the Garmin system directly from and ISO of the CD I made using Brasero.  It works without a hitch.  Should I take the Windows e.e programs and burn them to a CD and then transfer them as ISO tback to the VM drive???  Surely there must be an easier, click and run capability.

---

### Post by mikewhatever on 2010-06-05
Why don't you download and the programs in Windows, to the Windows desktop, and then install from there?
Can you also clarify the following sentence:
```
Ordinarily, in a WinXP only system, I just find the program to be installed 
and double click on it to start the automatic installation routine
```

---

### Post by misterfixit on 2010-06-05
> **mikewhatever said:**
> Why don't you download and the programs in Windows, to the Windows desktop, and then install from there?
Can you also clarify the following sentence:

```
Ordinarily, in a WinXP only system, I just find the program to be installed 
and double click on it to start the automatic installation routine
```

I suppose I could re-download the programs.  Seems like a duplicate effort when i already have them on the HD, but point taken -- I have to remember that I no longer have a 300 baud dial-up with my Heathkit H89 attached to it.

Expanding upon running windows programs from the double click, If i d/l one and choose to not go through the run business but save it for another day I can double click on the program icon sitting in my downloads folder and it will run.  That is what I mean.

---

### Post by eriqjaffe on 2010-06-05
You can share a folder (or multiple folders) between your Ubuntu install and the virtual machine:

[http://www.virtuatopia.com/index.php/VirtualBox_Shared_Folders](http://www.virtuatopia.com/index.php/VirtualBox_Shared_Folders)

I do this for my scanner, since sane doesn't support it - I just scan in VirtualBox directly to a shared folder, and then I can edit the pictures in Ubuntu.  Works like a charm.

---

