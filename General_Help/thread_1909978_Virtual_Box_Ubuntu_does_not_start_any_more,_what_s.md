---
title: "Virtual Box Ubuntu does not start any more, what should I do?"
date: 2012-01-16
forum: General Help
---

### Post by unfortunately_no_idea on 2012-01-16
Dear all,

I use Ubuntu from the Virtual Machine. After a system break down, when I had not been able to close Ubuntu and the Virtual Machine properly, I get the following message if I try to start Ubuntu:

Runtime error opening 'C:\Users\Poi\VirtualBox VMs\Ubuntu_11x14\Ubuntu_11x14.vbox' for reading: -102 (File not found.).
D:\tinderbox\win-4.1\src\VBox\Main\src-server\MachineImpl.cpp[707] (Machine::registeredInit).
Fehlercode:
E_FAIL (0x80004005)
Komponente:
VirtualBox
Interface:
IVirtualBox {c28be65f-1a8f-43b4-81f1-eb60cb516e66}

As far as I can see, the Virtual Machine works well, only Ubuntu does not. What can I do? Is it a) possible to download from somewhere this missing file? b) should I install a new version of Ubuntu or c) do something else?

Thank you so much for you help! I have
unfortunately_no_idea.

---

### Post by dino99 on 2012-01-16
the good news is that vdi a virtual installation, so no drama. As it seems to be corrupt, the easiest/fastest choice is to do a new install.

---

### Post by unfortunately_no_idea on 2012-01-18
Thank you! :) Do you think there is any possibility to get the documents I had on the Ubuntu? I know it sounds stupid, but I cannot find the personal documents i had stored there (I clicked through everything of the Virtual Machine, and there is no Ubuntu-Folder). Or Do you think if I reinstall it, the old documents will still be there?

---

### Post by 3rdalbum on 2012-01-18
> **unfortunately_no_idea said:**
> 
Runtime error opening 'C:\Users\Poi\VirtualBox VMs\Ubuntu_11x14\Ubuntu_11x14.vbox' for reading: -102 (File not found.).

Somehow (either a human error accident, or filesystem corruption) the instance of Ubuntu has been erased from the hard disk - that's why you're getting the "File not found" error message. It's gone.

The ".vbox" file that it mentions is a small file that defines settings for that virtual machine. If you still have the ".vdi" file, that's the one that contains your virtual Ubuntu hard disk, and you can simply create a new virtual machine with that existing ".vdi" file as its virtual hard disk. It will be like nothing happened.

The bad news: If you're missing the ".vbox" file, you're probably also missing the ".vdi" file. In which case, your Ubuntu and all its documents are gone.

Have a look anyway in the directory mentioned in the error message, and see if you can find a .vdi file that was associated with the virtual machine, and try my suggestion.

Good luck.

---

### Post by unfortunately_no_idea on 2012-01-20
Thank you for your suggestion! I appreciate it very much. I seem to be lucky: the .vdi still exists (it is, in fact, quite a large file). So I just install Ubuntu again and than change the new created .vdi-file with my old one?

---

### Post by cryptotheslow on 2012-01-20
No need to install Ubuntu again. Just create a new machine in VirtualBox and in its settings attach that .vdi file as its harddrive. Then just power on the virtual machine.

Make a copy of that vdi file to somewhere safe before doing any of the above just in case something goes wrong.

---

