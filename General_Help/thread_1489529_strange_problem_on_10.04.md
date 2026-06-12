---
title: "strange problem on 10.04"
date: 2010-05-21
forum: General Help
---

### Post by D3jan on 2010-05-21
when i install some programs from software center , alfter istalation  in Aplication menu , no program in their categoru (7zip, rar , sms sender ......and many others) Any posibility that this new Ubuntu not suport some programs in their list :\

---

### Post by nothingspecial on 2010-05-21
Command line tools don`t appear in application menus.

---

### Post by D3jan on 2010-05-21
That happens after I began installing  upadates , before that everything work fine , also i have problem with splash scren resolution but i solved that
perhaps  i not well described the problem, when i install something from the Software Center program does not exsist anywhere in the  system and appears to be installed, and when I go through the terminal then everything works 100%

---

### Post by 3rdalbum on 2010-05-21
> **D3jan said:**
> 
perhaps  i not well described the problem, when i install something from the Software Center program does not exsist anywhere in the  system and appears to be installed, and when I go through the terminal then everything works 100%

A vanishingly-small number of GUI programs don't have the necessary .desktop files to add themselves to your menu. You can add these manually, since you know how to access them through the terminal.

The programs you mention like 7z, rar etc are command-line programs. They don't appear in your applications menu, because you have to run them on the command-line. In fact, 7z and rar are automatically used by Ubuntu's default archive manager (File Roller) when they are available. This isn't Windows, where you need to learn seven different archive managers just to deal with different file types; this is Linux where you only need to learn one program which will automatically use other programs.

---

### Post by D3jan on 2010-05-21
thanks for advice :)

---

