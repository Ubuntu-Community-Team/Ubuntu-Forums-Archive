---
title: "Ubuntu 9.10 to 10.04 upgrade issue"
date: 2010-05-25
forum: General Help
---

### Post by gmclark8 on 2010-05-25
Ubuntu 9.10 to 10.04 upgrade failed. This machine is purely linux (i.e. no windows partition). I know I should have saved my data first. I can no longer boot from hard drive.  I can boot from  9.1 install disk and upon interigating the file system, can see my folders are still there but need to know how to access/save them before re-installing 9.10.  Fairly new to linux so any help will be greatly appreciated.

---

### Post by hansdown on 2010-05-25
Hi gmclark8.

You should be able to drag and drop your files to a USB thumb drive, or external hard drive.

---

### Post by gmclark8 on 2010-05-25
Hansdown, thanks for your reply, however when I try to copy the folders I get a "you do not have permissions to read it" message.  Figure I need to somehow sign on using my original login but I am unable to use switch user as I get an "Authentication Error".

---

### Post by hansdown on 2010-05-25
O.K.

Click applications> accessories> terminal.

Copy and paste this and hit enter.

```
 gksudo nautilus
```

Hopefully this will help.

If not, right click the file, then click properties> permissions.

See if you can get read and write permissions.

---

### Post by radite on 2010-05-25
My old computer love Jaunty Jackalope :biggrin: i don't want to upgrading yet....

---

### Post by gmclark8 on 2010-05-26
Hansdown, you are a champion.  I think you have saved my life. This worked perfectly for me.  The machine was my wifes and it had all her work docs on it, needless to say I have been expecting bits of my body to be removed if I could not recover.  Thanks again.

---

### Post by hansdown on 2010-05-26
Glad you fixed it gmclark8.

---

