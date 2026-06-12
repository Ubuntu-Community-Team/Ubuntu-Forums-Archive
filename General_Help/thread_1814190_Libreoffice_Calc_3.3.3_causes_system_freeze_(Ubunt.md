---
title: "Libreoffice Calc 3.3.3 causes system freeze (Ubuntu 11.04)"
date: 2011-07-29
forum: General Help
---

### Post by waldo000000 on 2011-07-29
Hi,

I frequently (i.e. after 10-20 minutes of use) get a complete system freeze when using LibreOffice Calc 3.3.3, on Ubuntu 11.04. At the time, I have an *.ods file open, and the freeze happens at various times, for example just after pressing the Page Up button. After the freeze occurs, nothing responds, not even Ctrl+Alt+F1, and I have to force power off my laptop.

I have no idea how to debug this problem, as there's no error message, no error log (that I know of??)... A quick google didn't help me either.

Could someone please help me debug this problem, e.g. suggesting where to look for log files, etc? I'm happy to provide more information, I'm just not sure what is relevant at this early stage.

Thanks in advance for your help,
Roy

---

### Post by qmater001 on 2011-08-06
same here.

---

### Post by mx597turbo on 2011-08-06
LibreOffice 3.4.2 is available for download directly from the website: [http://www.libreoffice.org/download/]("http://www.libreoffice.org/download/")

It has to be installed manually. Here is a howto:
[http://linuxforums.org.uk/ubuntu/upgrading-libreoffice-to-3-4-1-in-ubuntu-11-04/]("http://linuxforums.org.uk/ubuntu/upgrading-libreoffice-to-3-4-1-in-ubuntu-11-04/")

If that doesn't work, you can always switch to OpenOffice until the issue is solved.

---

### Post by gdgilda on 2011-08-08
FWIW, I've also seen a hang using calc (3.3.2 instead of 3.3.3) and can easily recreate.  I've documented how to recreate it in this thread:
[http://ubuntuforums.org/showthread.php?t=1813246](http://ubuntuforums.org/showthread.php?t=1813246)

Glenn

---

### Post by opodaniel on 2011-08-09
Same Problem hapens to me
- I have disabled compiz
- Installed LibreOffice 3.4.2 from deb files
- Removed .libreoffice foder

New things I found on Internet and need to test 
Tools/options/view uncheck Use AntiAliasing and Use hardware acceleration.

My Hardware : SoniVaio SA with SandyBridge CPU 
Using Intel HD integrated Graphics  (radeon card is switch off and blacklisted)
I think it is related with the bad/unfinished support for Intel HD graphics in SB.

Same problems in Mint 
[http://forums.linuxmint.com/viewtopic.php?f=47&t=77851&p=456737](http://forums.linuxmint.com/viewtopic.php?f=47&t=77851&p=456737)

---

### Post by waldo000000 on 2011-08-25
> **opodaniel said:**
> New things I found on Internet and need to test 
Tools/options/view uncheck Use AntiAliasing and Use hardware acceleration.

Have you tried this yet? I still get freezing even with 3.4.2.

---

### Post by mehrdad_v on 2012-04-21
> **waldo000000 said:**
> Hi,

I frequently (i.e. after 10-20 minutes of use) get a complete system freeze when using LibreOffice Calc 3.3.3, on Ubuntu 11.04. At the time, I have an *.ods file open, and the freeze happens at various times, for example just after pressing the Page Up button. After the freeze occurs, nothing responds, not even Ctrl+Alt+F1, and I have to force power off my laptop.

Roy

Hello,

On an Ubuntu derivative (Linux Mint) forum [http://forums.linuxmint.com/viewtopic.php?p=452827](http://forums.linuxmint.com/viewtopic.php?p=452827) I have seen a recommendation that this fix works:

For LibreOffice:
under the Tools->Options->LibreOffice->View menu, turn off "Use Anti-Aliasing"
(If that doesn't work, try also turning off "Use hardware acceleration")

and for OpenOffice
under the Tools->Options->OpenOffice.org->View menu, turn off "Use Anti-Aliasing"
(If that doesn't work, try also turning off "Use hardware acceleration")

This has worked for me.
Hope these fixes help.

---

### Post by rewyllys on 2012-04-21
LibreOffice 3.5.2 is available in 32-bit and 64-bit debian versions from [http://www.libreoffice.org/download/?nodetect]("http://www.libreoffice.org/download/?nodetect")

LO 3.5.2 fixes many of the problems associated with earlier versions.

I found it easy to install 3.5.2 in my laptop and in my desktop from the debian package.

---

