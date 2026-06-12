---
title: "Easy way to always start with noapic?"
date: 2010-01-04
forum: General Help
---

### Post by Final Version on 2010-01-04
To boot into Ubuntu 8.10, I have to boot with noapic. Is there an easy way to always boot with this command. And don't worry, I have fair bit of computer know how, just moving from windows to ubuntu.

---

### Post by prshah on 2010-01-04
> **Final Version said:**
> To boot into Ubuntu 8.10, I have to boot with noapic. Is there an easy way to always boot with this command. And don't worry, I have fair bit of computer know how, just moving from windows to ubuntu.

Boot into your ubuntu as usual, then edit the /boot/grub/menu.lst file. Look for the options "kopt" or "defoptions". 

Add either ONE of the below lines to the file```
**#**kopt=noapic
# OR #
**#**defoptions=noapic
``` Make sure you do not override any existing kopt or defoptions, and that you [s]remove[/s] **don't remove** any leading "#" to your line.

Then open a terminal (Applications-Accessories-Terminal) and update grub with the command```
sudo update-grub
``` Now, every time you reboot, noapic should be active in the kernel options. To check, reboot, open a terminal and give the command```
dmesg|grep Kernel\ command
``` and you should find noapic listed in the command line.

Please post back here if you have any questions or comments.

---

### Post by Final Version on 2010-01-04
I add
```
kopt=noapic
```to /boot/grub/menu.lst, save it and close gedit. Then I open terminal and enter
```
sudo update-grub
```but it removes the line from menu.lst. Also to open menu.lst I used the following in terminal.
```
sudo gedit /boot/grub/menu.lst
```

Why does it remove the line from menu.lst?
How do I get around this?
And do I need to put a # in front of
```
kopt=noapic
```

Thanks.

---

### Post by prshah on 2010-01-04
> **Final Version said:**
> Why does it remove the line from menu.lst?
And do I need to put a # in front of
```
kopt=noapic
```

Are you using the server edition, by any chance? When using the server edition, update-grub restores a default menu.lst (I think, I'm not sure).

I prefer you use defoptions. 

Given that it's removing the line, simply don't use the update-grub command. Save the menu.lst file, and just reboot normally to check.

Yes, please put a "#" in front of kopt / defoptions; my earlier advice to remove the "#" was wrong. If either already have parameters, just add a space " " and the noapic keyword.

---

### Post by Final Version on 2010-01-04
Ok I added it and updated it, just need to reboot.

---

### Post by Final Version on 2010-01-04
Ok all working now thanks.

---

