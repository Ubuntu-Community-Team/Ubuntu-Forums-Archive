---
title: "data recovery from dual boot system"
date: 2012-03-09
forum: General Help
---

### Post by vishwanaya on 2012-03-09
I had dual boot on my lenovo laptop. Windows 7 ultimate and Ubuntu  10.10. I upgraded Ubuntu to 11.04. During the process the two partitions  were shown and was asked to change partitions, if any. I did not know  what can be the effect. I moved partition Ext partition as the other was  quite bigger. Later I found that windows not shown in grub. However  sudo fdiskl showed two NTFS partitions of windows (C and D drives) data  size. Since I did not have time to learn through internet and carry this  risky work wherein I could have lt my 80 GB data, I gave the work to an  expert. He charged hefty amount. Now the file names are seen on Windows  7 ultimate but files do not open. I guess he recovered data on windows  2008 service pack system with one month validity software SPWDR. Since  one more day of the software was still remaining, I tried to get the  data by myself. Neither his correctly named files open nor my .iso files  open. I searched for I net solution for .iso files. FreeFileViewer was  suggested as the solution. But this software just says something about  Codecs. Now how to get my files back. The file names with proper data  size is on my comp. and .iso files are also there. Further what? Can any  one help me out.

Dr Vishwajeet

---

### Post by Jon Monreal on 2012-03-09
If you're in Ubuntu, you should be able to open the ISO files using archive manager or 7zip. In Windows, you can use 7zip or Winrar.

---

### Post by Mark Phelps on 2012-03-11
You ran a lot of info together, so it's difficult to see what your current situation is and what you're trying to recover.

Different tools are needed to recover files from different filesystems. 

My own experience is that MS Windows tools are best at recovering files from MS Windows filesystems (i.e., NTFS); Linux tools are best at recovering files from Linux filesystems.

Without further details, we're just guessing.

---

### Post by vishwanaya on 2012-03-11
> **Jon Monreal said:**
> If you're in Ubuntu, you should be able to open the ISO files using archive manager or 7zip. In Windows, you can use 7zip or Winrar.
Dear Jon,
I have got data on Windows 7 Ultimate on Lenovo system. Data does not open with regular software which it used to open. For example, Windows Media player files initially open a window and without playing the video, return with message, [I]
Windows Media Player cannot play the file. The Player might not support the file type or might not support the codec that was used to compress the file.[/I]
I checked for solution on net and accordingly downloaded FreeFileViewer. Unfortunately it could not play the same. It is not only for this file, more importantly my pptx files are not opening which I use for teaching. I have put long time hours and about 10 years to prepare some of the files and research papers. Nothing is opening. Please help me out. Thanks for your response.
Dr. Vishwajeet

---

### Post by vishwanaya on 2012-03-11
> **Mark Phelps said:**
> You ran a lot of info together, so it's difficult to see what your current situation is and what you're trying to recover.

Different tools are needed to recover files from different filesystems. 

My own experience is that MS Windows tools are best at recovering files from MS Windows filesystems (i.e., NTFS); Linux tools are best at recovering files from Linux filesystems.

Without further details, we're just guessing.
Dear Mark,
Thank you for your response. Some of my files are recovered (so to say, actually not). Only I see the file names but can not open them. Some problem with codec, I guess from net surfi ng. For example, I see the media file with name on the screen. I try to open it with either with Windows Media Player or VLC media player. A window opens but it does not play the video. For me my pptx are very important. My 10 years hard work has gone in preparing teaching slides and research papers. One of the messages that I get is shown below.
*Windows Media Player cannot play the file. The Player might not support the file type or might not support the codec that was used to compress the file.*
Net Solution for pptx and docx files was to use FreeFileViewer. I downloaded it, yet for no use. It shows all funny symbols.
Can you guide on this?
Dr. Vishwajeet

---

### Post by vishwanaya on 2012-03-11
> **Jon Monreal said:**
> If you're in Ubuntu, you should be able to open the ISO files using archive manager or 7zip. In Windows, you can use 7zip or Winrar.
For pptx files, FreeFileViewer shows all funny symbols. It is not only for this file,  even my pdfx files are not opening. has it to do something with former 32 bit and new 64 bit software?
Thanks.

---

### Post by Mark Phelps on 2012-03-12
The pptx and docx filename extensions are the new "XML" file formats that MS introduced with Office 2007.  While Linux apps can work to some degree with these, only MS Office can actually handle them well.

And unfortunately, I don't believe there is any way to get PowerPoint 2007 working well in Linux, even using Wine or its derivatives.

See the WineHQ link below:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=13]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=13")

A silver rating means the app will barely work (some functions won't work), and garbage means it won't work at all.

---

