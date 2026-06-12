---
title: "How can I install the GENEDOC software to my ubuntu 11.04?"
date: 2011-07-05
forum: General Help
---

### Post by norman205 on 2011-07-05
I want to install the [GENEDOC]("ftp://ftp.psc.edu/biomed/genedoc/gdsrc262.zip") software; I use Ubuntu 11.04. How can I do it?

---

### Post by grahammechanical on 2011-07-05
The link that you give offers an opportunity to download a zip file. That suggests to me that the program is a Windows program. The Genedoc homepage says this:

> A Full Featured Multiple Sequence Alignment Editor, Analyser and Shading Utility for WindowsWhat you are wanting to download is the source code for the program. I have no idea what you can do with that. Notice, the supported platforms.

> GeneDoc was written using Microsoft Foundation   Classes and Microsoft Visual C++, so I currently have 16  and 32 bit versions   for computers running Intel based PC's. GeneDoc runs under Windows 3.X , Windows/95 and Windows/NT versions of Microsoft   Windows. Russell Malmberg has successfully recompiled the program on a DEC Alpha running Windows/NT so there is a version for that platform as   well. Pittsburgh Supercomputing Center is running Genedoc on SGI platforms with a MS/Windows emulator package.The best that I can suggest is that you install from the Ubuntu Software Centre the program called Wine. And then try using Wine to install the Windows executable program that is downloaded from the fourth link on the homepage. The program is called gd322700.exe. Download it into a folder that you create called Genedoc and then use Wine to run the program. If you load the Wine Uninstall programs utility you will find that it becomes the Add/Remove programs utility. 

This may not work. Here is a link to the Wine homepage

[http://www.winehq.org]("http://www.winehq.org/")

Regards.

---

### Post by norman205 on 2011-07-05
Please have a look to [this link]("http://www.nrbsc.org/gfx/genedoc/gdsrc.htm").

---

### Post by grahammechanical on 2011-07-05
Hi.

I did look at the page the first time. Did you notice this comment?

> Russell Malmberg has successfully recompiled the program on a DEC Alpha  running Windows/NT so there is a version for that platform as   wellThe person who wrote the program is allowing others to have access to the source code under the provisions of that license (the GPL). This means that you or anyone else can do what Russel Malmberg has done. That is recompile the source code to run on different types of computer processors and under different operating systems. Anyone who does that has to conform to the terms of the GPL or they will be breaking the law.

Do you wish to produce a Linux version of this software? Do you want someone else to do it for you? Then you need the source code to do it. And that zip file has the source code. If you simply want to run the program in a Linux operating system then you need something like Wine and the Windows exe file.

I am using Wine to run a Windows program. Not all Windows programs will run good under Wine because the Windows OS and many Windows programs are not open source like this one. And the Wine developers are working in the dark.

Regards

Hi again. Here is what you do:

1) Open the Ubuntu Software Centre and search for Wine. Install the Microsoft Windows Compatibility Layer (meta package).

3) Download the file gd322700.exe from the GeneDoc homepage. It is the third link down, where it says OK. OK. Put the file in its own folder.

4) Restart.

5) In the Dash search for Wine and run configure wine.

6) Repeat the search for wine and run Uninstall Wine software.

7) Click the Install button and browse to the Genedoc folder and click open.

8 ) Change the files of type from Installation Programs to Programs (* exe). the Genedoc file gd322700.exe should show up in the box. Select it and click Open.

9) Click Install and when the installation has finished close the dialog box.

10) To run Genedoc type Genedoc in the Dash and click the icon.

I know that all of this works because I have just done this from start to finish on another installation of Ubuntu that I have on my system. I have the GeneDoc program open on my desktop in Unity right now.

Regards again

---

### Post by norman205 on 2011-07-10
Thank you very much. It works.

---

