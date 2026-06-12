---
title: "laptop won't boot after update"
date: 2010-09-05
forum: General Help
---

### Post by tapenick on 2010-09-05
I installed an update on my Dell D800 last night and now it won't boot.  Attaching a pic of the screen... I'm sure I have not included enough info so please let me know if you have questions / suggestions.

Tom

---

### Post by tapenick on 2010-09-07
Update - I wonder if something happened in the middle of the update.  I updated another computer yesterday... was prompted many times on whether to keep or replace files.  Nothing like that on the laptop.  I have two teenage girls.. one of them may have switched users or who knows what during the update.  Any suggestions?

---

### Post by utnubuuser on 2010-09-07
Press Shift at post/boot, to access a grub menu, then try to select an older kernel (second or third down the list).

It's tough getting at the grub boot menu sometimes if you don't normally get a grub menu, and you have to hit the shift key at the right moment. sometimes I just keep pressing it quickly while the computer boots. In older version of grub it's the esc key.
Might wanna try another screenshot too, - can't really see the one you've posted

---

### Post by tapenick on 2010-09-11
I tried booting into the recovery mode kernel for the current version (2.6.24-28) then the normal and recovery mode for the previous two (27 and 26).  No luck.  Attaching a pic of the screen with the error I receive when I try 27 and 26.. any suggestions?

---

### Post by tapenick on 2010-09-13
Sorry for replying to my own post.. stuck and need suggestions.  

I have an IDE - USB adaptor... should I yank the drive, recover the data, and reload?  
If so, can I access the Linux file system from a Windows machine?

---

### Post by wilee-nilee on 2010-09-13
Hard to really tell whats going on, I think you mean upgrade not update right. Try this command from a command line if you can get to one on the computer.
```
sudo apt-get install -f
```

I have used this, in this way to finish upgrades that were borked in various forms.

So it sounds like you have access to recovery make sure your plugged into the net when you run that command there is a network command choice in recovery.

Generally Windows doesn't read linux files, there are exceptions, but in this case a recovery of whats inside would be best done with a Live Ubuntu or Linux cd.

---

### Post by tapenick on 2010-09-14
It drops out to a (initramfs) prompt which doesn't recognize sudo, etc.  

Sorry guys, I'm lost.. suggestions appreciated!

---

### Post by tapenick on 2010-09-28
Thanks for the suggestions - I just hooked the drive up to another system, retrieved the data I wanted, and started over.

---

