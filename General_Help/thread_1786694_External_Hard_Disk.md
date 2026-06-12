---
title: "External Hard Disk"
date: 2011-06-20
forum: General Help
---

### Post by shamz_71 on 2011-06-20
Earlier i used my hard disk with windows 7 and i had set a password to unlock and access the data i have in my drive.
Now in ubuntu , when i connect my hard drive it shows me the UNLOCK.exe file but when i click on it ,instead of asking password , it opens up with ARCHIVE MANAGER and shows some files.

How do i access my data ?

---

### Post by shamz_71 on 2011-06-20
Its a Western Digital portable hard disk , i hope there are no compatibility issues

---

### Post by idoitprone on 2011-06-20
You hardrive uses a windows program to protect your data. Use wine to open your data

```
sudo apt-get install wine

wine UNLOCK.exe
```

or 

```
right-click open with wine
```

---

### Post by shamz_71 on 2011-06-20
No alternative other than wine ?

---

### Post by idoitprone on 2011-06-20
hey, ur the one who use a windows program to encrypt your work. Wine is a program that forges a windows environment in linux, or use virtual box

---

### Post by shamz_71 on 2011-06-20
> **idoitprone said:**
> hey, ur the one who use a windows program to encrypt your work. Wine is a program that forges a windows environment in linux, or use virtual box

im installing wine , but i dont like it . Is there any Linux program to encrypt my data, so that i dont need wine to open it?

---

### Post by idoitprone on 2011-06-20
I am do not know alot of encryption software.

Truecrypt ?

---

### Post by shamz_71 on 2011-06-20
"The application has encountered an unexpected error and is now exiting"
this is the error message i get after opening with WINE.

when i right click open with , 
i get 2 options
WINE windows program loader
and
WIne core exe

---

### Post by shamz_71 on 2011-06-20
anyone ?? 
need to access the data in HDD , its important

---

### Post by samthemule on 2011-06-20
I have a very similar problem, i have a western digital passport ext hd and i have transfered m data to another drie and i want to be able to use this harddrive with mylinux system but i amvery new to linux and not sure how this is possible can so,eone help me with the format or another solution. thank you

---

### Post by shamz_71 on 2011-06-20
you transferred your data , i cant even open my data. I'm running only Ubuntu

---

### Post by idoitprone on 2011-06-20
> **samthemule said:**
> I have a very similar problem, i have a western digital passport ext hd and i have transfered m data to another drie and i want to be able to use this harddrive with mylinux system but i amvery new to linux and not sure how this is possible can so,eone help me with the format or another solution. thank you

Your situation remotely similar to the op, please open a new post for yourselYou will recieve lots of information from other forum memebers. There is whole thread lurking around on ntfs vs ext4. [http://ubuntuforums.org/showthread.php?t=1786501&highlight=ext4](http://ubuntuforums.org/showthread.php?t=1786501&highlight=ext4). The op encypted his data, which makes accessing a hassle. Worse, he does know is it possible the run the data encryption software on linux.

shamz_71, please post details of the softare you use to encrypt your work. Or borrow someone computer who has windows and decrypt your work, so you can use it in linux.

---

### Post by shamz_71 on 2011-06-20
Its a built in software on the Hard disk by western digital.

---

### Post by shamz_71 on 2011-06-20
The data is not encrypted its password protected. The hardisk is password protected by a built in software. The disk is being detected..

---

### Post by nothing.halo on 2011-06-20
Have you tried mounting the drive a opening your documents and not opening the unlock.exe file?

---

### Post by shamz_71 on 2011-06-20
No idea how to mount the drive :S

---

### Post by idoitprone on 2011-06-20
open nautilus 

look for your drive on the left hand side

click the drive and it becomes mounted

or look for the usb symbol on the unity side panel

---

### Post by shamz_71 on 2011-06-20
i dont ve that application?
i will download...after searching i found many apps with same name

are you talkin abt this nautilus-pastebin ?

---

### Post by idoitprone on 2011-06-20
natulius is the gnome equivenlent to windows explorer. Remember explorer not internet explorer the thing that you use to browser your files when you open my computer.

---

### Post by shamz_71 on 2011-06-21
irrelevant message ?
How to solve the problem ?

---

### Post by shamz_71 on 2011-06-22
.........

---

### Post by Starfleet on 2011-06-22
Shamz, I see your problem. I'm no expert either but I can think of a couple of things. Firstly, as has been suggested, find someone with a Windows PC to switch off the password protection so it works on Linux. That could solve your immediate problem, but then the Windows PC probably needs to have a WD hard drive with the necessary software I guess. Or...visit the WD site and discuss this on their forum too. There will be others maybe with this problem. That is...if no one comes along with some further info on this site. I feel certain this is easily solvable in Linux without too much of a problem but not sure of the technique myself. Good luck.

---

### Post by shamz_71 on 2011-06-22
Thanks mate , i just did that and now problems solved

This is what i got from Western Digital support ,

a. Connect the WD external drive to a PC computer
b. Install the WD Smartware software came with it.
c. go to SETTINGS, the far right tap.
d. click on DRIVE SETTINGS.
e.  select SECURITY, enter your old password and just hit enter instead of enter the new password.
That would erase the password from the drive.




Is there any way/method using an application/software that can set a password to my passport and which will work in Linux And Windows

---

