---
title: "Trouble with wine and Excel 2007 on Windows 7 partition"
date: 2010-07-18
forum: General Help
---

### Post by xtheunknown0 on 2010-07-18
I'm running Lucid.

I sudo apt-get remove'd wine1.2 . I then sudo apt-get install'ed wine. I run wine /media/c/Program\ Files/Microsoft\ Office/Office12/EXCEL.EXE 
and I get [http://sites.google.com/site/xtheunknown0/linux-1](http://sites.google.com/site/xtheunknown0/linux-1)

How do I get EXCEL working?

TIA,
xtheunknown0

---

### Post by ronnielsen1 on 2010-07-18
> I'm running Lucid.

I sudo apt-get remove'd wine1.2 . I then sudo apt-get install'ed wine. I  run wine /media/c/Program\ Files/Microsoft\ Office/Office12/EXCEL.EXE 
and I get [http://sites.google.com/site/xtheunknown0/linux-1](http://sites.google.com/site/xtheunknown0/linux-1)

How do I get EXCEL working?


Assuming wine installed correctly and you followed the advice of winehq (Google windowsprogramyouwanttoinstall winehq) it could be that it can't find the program you're looking for. I believe that the files are actually located at ~/.wine/drive_c/Program\ Files/Microsoft\ Office/Office12/EXCEL.EXE
> After installing, set riched20.dll to native (needed for some dialog  boxes to display properly). It is not necessary to install the dll, as  Office installs its own version. Do not set this override globally  unless you have Office installed in a separate wineprefix.
   To use the thesaurus, install winetricks wsh56js.            

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12812](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12812)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

---

### Post by Mark Phelps on 2010-07-18
> **xtheunknown0 said:**
> I run wine /media/c/Program\ Files/Microsoft\ Office/Office12/EXCEL.EXE ...
Looks like you're trying to run Excel directly from Win7 without installing it via Wine.

I don't believe you can do that. But I could be wrong.

You would do better going to the Wine subforum with questions like this.

---

