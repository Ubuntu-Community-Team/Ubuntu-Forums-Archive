---
title: "Unable to login into my user account."
date: 2011-05-06
forum: General Help
---

### Post by karthick87 on 2011-05-06
I am unable to login into my user account. A pop up appears in top right corner stating "[COLOR=Red]Install problem! The configuration defaults for Gnome Power Manager have not been installed correctly. Please contact your computer administrator.[/COLOR]" Pls find the attached screenshot.

---

### Post by zvacet on 2011-05-06
Boot in recovery mode and try to fix it with those commands

```
sudo dpkg --configure -a
sudo apt-get --fix-missing
sudo apt-get -f install
```

---

### Post by karthick87 on 2011-05-06
Can you pls say me, how to get into recovery mode ? Do i need internet connection to execute those commands ?

---

### Post by pakidevil on 2011-05-06
If you have a single-boot (Ubuntu is the only operating system on  your computer), to get the boot menu to show, you have to hold down the *Shift* key during boot up. ....  Good Luck ..:)

---

### Post by karthick87 on 2011-05-06
I have both windows and ubuntu.

---

### Post by pakidevil on 2011-05-06
If you have a dual-boot (Ubuntu is installed next to Windows, another  Linux operating system, or Mac OS X; and you choose at boot time which  operating system to boot into), the boot menu should appear without the  need to hold down the *Shift* key. From the boot menu, select *recovery mode*, which is usually the  second boot option. After you select recovery mode and wait for all the boot-up processes  to finish.:)

---

### Post by karthick87 on 2011-05-06
Oke but do i need internet access to execute those commands ? Also i dont get recovery menu, long back i have hidden it i guess. But now i dont find the way to revert it back. Can anyone help ?

---

### Post by karthick87 on 2011-05-08
I get the following options in the recovery menu. Which option i have to choose ?

---

### Post by zvacet on 2011-05-08
One you selected on picture is the one in witch you want to boot.Yes,you will need internet connection to execute commands.

---

### Post by yetiman64 on 2011-05-08
> **zvacet said:**
> One you selected on picture is the one in witch you want to boot.Yes,you will need internet connection to execute commands.

The one selected in the picture is a normal root prompt, the OP will need to use netroot (the one above it) for use with the internet.

---

### Post by karthick87 on 2011-05-09
> **zvacet said:**
> Boot in recovery mode and try to fix it with those commands

```
sudo dpkg --configure -a
sudo apt-get --fix-missing
sudo apt-get -f install
```


I have executed the above commands in recovery mode but still the same problem continues.

---

### Post by karthick87 on 2011-05-11
Do any one have solution to this problem ?

---

### Post by wilee-nilee on 2011-05-11
> **karthick87 said:**
> Do any one have solution to this problem ?

Were you plugged into the net when you ran the commands, and did you notice post; that the default you showed was off one line?

You want netroot and be plugged in.

---

### Post by karthick87 on 2011-05-12
I am sure i am plugged into internet and i executed those commands but still i am facing the same problem. Any other solution ?

---

