---
title: "SD Card port on Dell unfunctional"
date: 2012-07-19
forum: General Help
---

### Post by KaisaUbun2 on 2012-07-19
is there anything I can install which will enable Ubuntu to find my SD card reader.

---

### Post by spjackson on 2012-07-19
You haven't given us much to go on here.

What model Dell is this?

Which version of Ubuntu are you running?

If you have Windows, is the SD slot functional from Windows?

If you boot with an SD card in the slot, can it then be seen in Ubuntu?

Any information you can get about the device, either from Windows or from Ubuntu if the above method works, would also help.

---

### Post by edjski on 2012-07-19
> **spjackson said:**
> You haven't given us much to go on here.

What model Dell is this?

Which version of Ubuntu are you running?

If you have Windows, is the SD slot functional from Windows?

If you boot with an SD card in the slot, can it then be seen in Ubuntu?

Any information you can get about the device, either from Windows or from Ubuntu if the above method works, would also help.
I have the same problem. 
I have a samsung qx410 (with a built-in sd card reader) 
dual booting Win 7 and Ubuntu 11.10.
The card reader detects and reads cards in windows. However, in Ubuntu the card is not detected. Booting with the card in the card slot does not cause the card to be detected.
The card reader worked before upgrading to 11.10

Thanks for any thoughts/assistance.

ed

---

### Post by KaisaUbun2 on 2012-07-20
> **spjackson said:**
> You haven't given us much to go on here.

What model Dell is this?

Which version of Ubuntu are you running?

If you have Windows, is the SD slot functional from Windows?

If you boot with an SD card in the slot, can it then be seen in Ubuntu?

Any information you can get about the device, either from Windows or from Ubuntu if the above method works, would also help.

I have a Dell XPS L702x i5 core processor, i'm running Ubuntu 12.04

yes I'm also running windows & professional and the port is functional. 

I have not attempted to boot it with the SD card in but i have my suspicion that it would not work.

---

### Post by Whovian on 2012-07-20
Booting with the sd card in the slot probably won't fix the problem. 

An try ```
lspci
```

---

### Post by KaisaUbun2 on 2012-07-20
> **Whovian said:**
> Booting with the sd card in the slot probably won't fix the problem. 

An try ```
lspci
```

I'm quite the beginner, what does this do?

---

### Post by efflandt on 2012-07-20
"ls" (small L) as in list, and pci as in PCI devices.  **lspci** in a terminal will list PCI devices.

Or you can get more complete details, including modules in use for each device with: **sudo lspci -v**

For posting any output that has multiple spaces or columns it helps to preserve formatting by highlighting that pasted output and click **#** in the message window to wrap it with code tags.

Something else to look at after inserting a memory card would be to look at the tail end of the output when typing: **dmesg**

Many memory card slots in laptops are not made to boot from, since they are a different type of block device than USB mass storage.  Many card slots in desktops (and my tablet PC) can be booted from if internally USB connected.

---

