---
title: "Mathtype, MS Word, and LibreOffice problems"
date: 2012-06-26
forum: General Help
---

### Post by thedoctor81877 on 2012-06-26
I am running Lubuntu 12.04 on my netbook, and currently use LaTeX for math typesetting. However, I am trying to obtain a job authoring solution guides for math textbooks, and the company I would be working for uses MathType exclusively. I can type in LaTeX, then import into MathType - but this company also requires the solutions to be in .doc format. 

SO, I really need to be able to use MS Word, and Excel on my linux machine. Also, I cannot afford any cost of product keys for MS Word, Excel, etc. 

My contact rep for the company said to try downloading MS Office 2010 Starter (and sent me a link for that) and use that. I did, but Wine could not open the file at all. Otherwise, I will have to paste MathType equations into something like LibreOffice as an OLE - and in that case, the company cannot edit said equations, if need be. 

So, any help/solution to this problem will be greatly aprecaited. Thanks,

-Michael Dykes

---

### Post by thedoctor81877 on 2012-06-26
Here is the error message I get when trying to open MS Starter 2010 with Wine:

The files needed to start your MS Office 2010 Starter Edition cannot be loaded. Please check your internet connection and try again.

---

### Post by mastablasta on 2012-06-26
have you tried using an online option?
What if you save as .doc in libre office?
 
Do you maybe have winetricks installed? apparently you need to install it without without them: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=22248](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22248)
 
> 
Install to a clean wineprefix following the instructions in the Microsoft Office (Installer only) entry. After installing: 

[LIST=1]
[*]Set riched20.dll to native to get around bug 14980. Do not install it with winetricks; Office installs its own version.
[*]For versions of Wine prior to 1.3.34, disable Protected View to get around bug 25492. (File=>Options=>Trust Center=>Trust Center Settings=>uncheck everything)&shy;
[*]Native msxml6 is needed to get around bug 30251. Delete the fake msxml6.dll from Wine's system32 before installing msxml6, as the msxml6 installer will not overwrite the fake dll if it is present (winetricks will do this for you). 

[/LIST]perhaps what is missing are some .dll files.

---

### Post by thedoctor81877 on 2012-06-26
I have tried installing the Starter Edition without using Wine Tricks, only Wine Program Launcher, but to no avail. Also, how do I (once I have downloaded native msxml6.dll files from MS, how do I add them to my Wine configuration? 

I am still a bit new to this, so please be patient and any help I am thankful for.

-Michael D

---

### Post by pbrane on 2012-06-26
Have you seen this?
[http://extensions.libreoffice.org/extension-center/texmaths-1]("http://extensions.libreoffice.org/extension-center/texmaths-1")

---

### Post by thedoctor81877 on 2012-06-26
I have, but the issue here is the company I am hoping to work for specifies that the 'equations' and math parts of these solutions be in MathType so 'they' can edit it. They mention that there is a plugin to convert/insert TeX code into MathType, but then the equations they want int MathType form and saved in a .doc (MS Word 1997-2003, I believe) format. Hence the problems I am experiencing. Thanks for the idea though.

-Michael D

---

### Post by thedoctor81877 on 2012-06-26
Is there a way I can accomplish what I 'need' using AbiWord, or possibly a web-based solution using that software? Thanks again.

-Michael D

---

