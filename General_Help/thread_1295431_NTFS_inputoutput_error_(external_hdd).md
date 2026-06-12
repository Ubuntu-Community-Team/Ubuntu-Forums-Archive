---
title: "NTFS input/output error (external hdd)"
date: 2009-10-19
forum: General Help
---

### Post by deeck on 2009-10-19
Hi!
Im having troubles with a external hdd. One day the usb cable was disconnected accidentally from the hdd, after that (i suppose), i cannot enter into just one folder in the drive, the other ones are fine.

deeck@amstel:/media/IOMEGA$ ls
ls: no se puede acceder a sda3: Error de entrada/salida
intento_zambia  nigeria  nigeria_docs  sda3  System Volume Information
deeck@amstel:/media/IOMEGA$ cd sda3
bash: cd: sda3: Error de entrada/salida

Error de entrada/salida = input/output error.
It's NTFS.

I have been searching and the "solution" is formatting the drive again :S, but i don't want to loose the files into that folder :-/.

I connected it in Windows XP, and its tells me that "sda3 folder is illegible or corrupt".

Please help!
Thanks a lot!

---

### Post by Giblet5 on 2009-10-19
What *I* would do:

Boot into Windows.

Bring up Windows Explorer (Start/Programs/Accessories/Windows Explorer).

Right-click that external drive.

Click the "Tools" tab.

Click the "Check" button.

Allow it to "Fix Problems".

Click OK.
-----

What's left is what Windows could salvage. If files are missing or oddly truncated, look for some *.CHK files and see if they have the missing stuff in them...

---

### Post by Matt__ on 2009-10-19
couple of questions...

[LIST]
[*]where you transfering files when the cable was pulled?
[*]why is windows seeing a folder as sda3 which is a linux drive partition naming convention?
[/LIST]
other than than google data recovery applications and / or boot from live cd and see if that can read the folder.

---

### Post by deeck on 2009-10-19
> **Matt__ said:**
> couple of questions...

[LIST]
[*]where you transfering files when the cable was pulled?
[*]why is windows seeing a folder as sda3 which is a linux drive partition naming convention?
[/LIST]
other than than google data recovery applications and / or boot from live cd and see if that can read the folder.

1) no
2) its just a name, sda3 is the name of the folder.

---

### Post by Baelus on 2009-10-19
> **Giblet5 said:**
> What *I* would do:

Boot into Windows.

Bring up Windows Explorer (Start/Programs/Accessories/Windows Explorer).

Right-click that external drive.

Click the "Tools" tab.

Click the "Check" button.

Allow it to "Fix Problems".

Click OK.
-----

What's left is what Windows could salvage. If files are missing or oddly truncated, look for some *.CHK files and see if they have the missing stuff in them...

Agreed. Using chkdsk sounds like a good idea. From what I see, it looks like running chkdsk /r is the way to go, but that's what Giblet5 already suggested.

Here's the Microsoft support page with the chkdsk details if you want them:

[http://support.microsoft.com/kb/315265]("http://support.microsoft.com/kb/315265")

---

### Post by deeck on 2009-10-20
Did that and now in the drive there is a folder like "found.000", where are all the files i wanted.

Thanks a lot!
Solved :D

---

