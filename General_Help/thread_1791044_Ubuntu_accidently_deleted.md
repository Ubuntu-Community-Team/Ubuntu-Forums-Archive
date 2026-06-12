---
title: "Ubuntu accidently deleted"
date: 2011-06-26
forum: General Help
---

### Post by Megacack on 2011-06-26
Well, I was on Windows and I accidentally deleted my Ubuntu install. Now when I boot I have Windows 7 and Ubuntu, and it's corrupt. So I went to add remove programs in Windows 7 and it just deleted the Ubuntu uninstaller (cause i deleted it) and now i'm stuck with a corrupt boot, can someone tell me how to remove it because I want to re install Ubuntu and it's annoying having 2 Ubuntu systems (one corrupt) and Windows 7 on my boot screen.

---

### Post by nzjethro on 2011-06-26
Hi Megacack. Just to clarify, do you now have two OSes installed - Windows 7 and a corrupted Ubuntu install? And trying to delete that Ubuntu install and reinstall it?

Try booting to a Live CD, then opening GParted by typing into a terminal:

```
sudo gparted
```

(You may have to install it first).

Then, in GParted, find your corrupt Ubuntu install and delete it.

Then, reinstall Ubuntu into the now empty partition you just created. Choose your main HDD to install the bootloader to.

---

### Post by doas777 on 2011-06-26
I assume based on your description, that you are referring to a WUBI installation (ubuntu installed inside windows). 
if you just want to restore your windows MBR, removing the linux boot loader and just using windows, try this:
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

otherwise you could reinstall windows, though I would recommend a real dual boot rather than a wubi install. just my preference.

---

### Post by bcbc on 2011-06-26
You need to use BCDEDIT to edit your BCD entries. That's the built in windows command line tool for editing your boot manager entries. There is also a program called easyBCD that you can download.

To use BCDEDIT, click START, enter "cmd", then look above and right click "cmd.exe" and select "Run as administrator".

Then enter:
BCDEDIT

That will list your current boot entries.

Here's something that looks like a decent guide: [http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)
You'll want to identify the old Ubuntu entry and delete it.

---

