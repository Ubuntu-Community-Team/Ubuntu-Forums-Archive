---
title: "how do I install an exe file at ubuntu?"
date: 2009-07-25
forum: General Help
---

### Post by masoud23 on 2009-07-25
Hello!

I run Ubuntu 7.2 in my computer, when i download a exe file and try to open it I get this messeage "No application suitable for automatic installation is available for handling this kind of file." how do I install an exe file?

---

### Post by hetx on 2009-07-25
Depends on what it is, but WINE lets you run alot of Windows applications directly in Linux.

sudo apt-get install wine

---

### Post by jerome1232 on 2009-07-25
.exe are Windows executables, they don't run on Linux. What application is it your trying to run perhaps we can suggest an alternative that is native to Linux.

Most programs for Ubuntu are distributed as .deb packages (similiar to a .msi package for Windows), You can browse through a large amount of software pre-packaged for Ubuntu via Add/Remove or Synaptic Package Manager.

There is a program for Ubuntu called wine (Wine Is Not an Emulator) that can run some Windows progams, if you search for it in add/remove and install it, you may be able to run the Windows Executable.

Check WineHQ's database of apps to see if your program works with wine.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by lisati on 2009-07-25
"exe" files are usually designed for Windows, and won't work without help in Ubuntu. As hetx has pointed out, "[Wine]("https://help.ubuntu.com/community/Wine")" can be used to run some Windows programs. An alternative to using Wine is to look for a [Linux-friendly equivalent]("https://help.ubuntu.com/community/WindowsApplicationsEquivalents").

---

### Post by kirbon on 2009-07-25
wine is what you should use although its a little bit slow but wine lets you run windows programs on linux

---

### Post by RD1 on 2009-07-25
> how do I install an exe file?

Boot Windows.

Good luck

---

### Post by kirbon on 2009-07-25
go to terminal and try sudo apt-get install wine

---

### Post by masoud23 on 2009-07-25
The programs I want to install are windows explorer, to see how my web pages look like at explorer and then Crimson editor, I use Bluefish now for PHP programming and have some problem with it.

---

### Post by lisati on 2009-07-25
> **masoud23 said:**
> The programs I want to install are windows explorer, to see how my web pages look like at explorer and then Crimson editor, I use Bluefish now for PHP programming and have some problem with it.

Do you mean *Internet* Explorer (almost but not quite the same thing as Windows Explorer)? There's probably someone here who can offer some guidance.

---

### Post by irv on 2009-07-25
> **masoud23 said:**
> Hello!

I run Ubuntu 7.2 in my computer, when i download a exe file and try to open it I get this messeage "No application suitable for automatic installation is available for handling this kind of file." how do I install an exe file?
First, I see you are running a older version of Ubuntu. It's up to 9.04. If the hardware you are running Ubuntu on is high enough in specs you might want to update to a later version. If you do that you could install Virtualbox 3.0 and run Windows in that. While doing that you could run all the exe file you like. here is what my system looks like with Ubuntu 9.04 and Virtualbox 3.0 with WinXP SP3.
[ATTACH]122397[/ATTACH]

---

### Post by eandrade on 2009-07-25
if u need to run .net app's u can use mono which runs .net exe's

---

