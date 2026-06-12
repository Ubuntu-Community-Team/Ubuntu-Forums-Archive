---
title: "Can't install .run file according to instructions"
date: 2010-06-27
forum: General Help
---

### Post by TheAnomalyCoder on 2010-06-27
Well I downloaded an ATI driver, and there are some installation instructions:
Launch the Terminal Application/Window and navigate to the ATI CatalystTM
Proprietary Linux driver download.
Enter the command sh ./ati-driver-installer-10-6-x86.x86_64.run to launch the ATI
CatalystTM Proprietary Linux driver installer.
The ATI CatalystTM Proprietary Linux Driver Setup dialog box is displayed.

My result:
marek@marek-desktop:~$ sh ./ati-driver-installer-10-6-x86.x86_64.run
sh: Can't open ./ati-driver-installer-10-6-x86.x86_64.run

Help? I'm new to Ubuntu so I could use a pointer or two. :popcorn:

---

### Post by Rubi1200 on 2010-06-27
> **TheAnomalyCoder said:**
> Well I downloaded an ATI driver, and there are some installation instructions:
Launch the Terminal Application/Window and navigate to the ATI CatalystTM
Proprietary Linux driver download.
Enter the command sh ./ati-driver-installer-10-6-x86.x86_64.run to launch the ATI
CatalystTM Proprietary Linux driver installer.
The ATI CatalystTM Proprietary Linux Driver Setup dialog box is displayed.

My result:
marek@marek-desktop:~$ sh ./ati-driver-installer-10-6-x86.x86_64.run
sh: Can't open ./ati-driver-installer-10-6-x86.x86_64.run

Help? I'm new to Ubuntu so I could use a pointer or two. :popcorn:
Try prefacing the command with sudo

```
sudo sh ./ati-driver-installer-10-6-x86.x86_64.run
```

See if that helps.

---

### Post by ronnielsen1 on 2010-06-27
If you're in terminal you would have to chmod +x ati-driver-installer-10-6-x86.x86_64.run
and then sudo  ./ati-driver-installer-10-6-x86.x86_64.run or sudo sh ati-driver-installer-10-6-x86.x86_64.run but if it's anything like nvidia drivers, you would have to exit X. (I've never had an ATI card)
You don't list your card you're trying to get running

---

### Post by TheAnomalyCoder on 2010-06-27
> **Rubi1200 said:**
> Try prefacing the command with sudo

```
sudo sh ./ati-driver-installer-10-6-x86.x86_64.run
```See if that helps.

marek@marek-desktop:~$ sudo sh ./ati-driver-installer-10-6-x86.x86_64.run
[sudo] password for marek: 
sh: Can't open ./ati-driver-installer-10-6-x86.x86_64.run
marek@marek-desktop:~$ 

Didn't help :\

> **ronnielsen1 said:**
> If you're in terminal you would have to chmod  +x ati-driver-installer-10-6-x86.x86_64.run
and then sudo  ./ati-driver-installer-10-6-x86.x86_64.run or sudo sh  ati-driver-installer-10-6-x86.x86_64.run but if it's anything like  nvidia drivers, you would have to exit X. (I've never had an ATI card)
You don't list your card you're trying to get running

I'm not listing the name of the card, that's actually the name of the file :o. 
I tested out what you said to do, and my output for the first part (chmod) is:

marek@marek-desktop:~$ chmod +x ati-driver-installer-10-6-x86.x86_64.run
chmod: cannot access `ati-driver-installer-10-6-x86.x86_64.run': No such file or directory

Do I have to set my Directory before I run this command ? (The file is on my desktop).




EDIT:

FOUND SOLUTION:
sudo sh ./ati-driver-installer-10-6-x86.x86_64.run
Thanks for the clues though guys.

---

### Post by coldraven on 2010-06-27
The ./  (dot-slash) means that the file you are trying to run is in the current directory.
Use "pwd" to find out which directory you are in then "cd" to Desktop.
For example:
```
pwd
/home/yourname
```then:
```
cd Desktop
```Note that commands are case sensitive, Desktop starts with a capital D.
After typing the D you can use the Tab button to autocomplete the command

---

