---
title: "Allow executing file as program........"
date: 2011-04-22
forum: General Help
---

### Post by nostromo3030 on 2011-04-22
Hello :)
I am new to linux :( --Ubuntu 11.04
On the `Install Properties` Menu , I am not allowed to check the: Allow executing file as program........
What Am I doing wrong?
Thank you in anticipation
George

---

### Post by spikoley on 2011-04-22
That file is an .exe file for Windows.  Are you running Wine?

Check out this [guide]("https://help.ubuntu.com/community/FilePermissions") to file permissions.  Permissions are an important part of any *nix operating system and you should learn it.

---

### Post by TheHackOps on 2011-04-22
Open Terminal
cd to directory of file
sudo chmod filename.exe 777

---

### Post by cipricus on 2012-02-26
I have the same problem but when trying that command to start PDF-XChange I get this:
chmod: invalid mode: `PDFXCview.exe'
Try `chmod --help' for more information.

Anyways, isn't it there a general command to make all my win exe files runnable by wine without every time putting commands in terminal?

i used to have that but something changed I don't know why and how.

---

### Post by Karlchen on 2012-02-26
Hello, cipricus.

*PDFXCview.exe* is a Windows executable file. From the Linux perspective it is not an executable file. So executing ```
chmod +x /path/to/*PDFXCview.exe*
``` will not have the desired effect. Instead you need *Wine* to run this Windows executable *PDFXCview.exe*. ```
wine /path/to/*PDFXCview.exe*
```In order to be able to do so without typing this command in a terminal, you use the system default file-manager (I will assume it is *Nautilus)* and navigate to the folder where *PDFXCview.exe* has been stored.
You right-click on the filename [I]PDFXCview.exe.
[/I]From the context menu that will pop-up, you select, **Open with other application ...** (or whatever the original English text is, I am translating back from German, sorry)
A long list of known applications will be opened.
Scroll down till you find the application name **Wine Windows Application Launcher**.
Select it.
Tick the option **[x] Remember this application for DOS/Windows programs**.
Click the **[Open]** button.
Wine should be launched and try to launch the executable *PDFXCview.exe*.

From now on, whenever you wish to launch a Windows executable you right-click on its name in your Linux file-manager and select the item **Open with Wine Windows program launcher** from the context menu.

_Beware:_
Whether or not Wine will be able to launch the selected Windows executable file depends on a number of factors.
In case running an application in the described way does not work, you will have to open a terminal and execute the command ```
wine /path/to/executable_name.exe
``` in order to see any error messages which Wine may display.

HTH,
Karl

---

### Post by Mark Phelps on 2012-02-27
Experience running thing in Wine varies greatly.  See the link below to the WineHQ ratings page for the app you're trying to use:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5549]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=5549")

The Silver rating means that some features won't work.  You need to read through the testing results to see what others have learned.

---

### Post by forrestcupp on 2012-02-27
@ the OP, from the screen shot, it looks like the executable property is already checked. So what is the problem? Do you need to uncheck it?

> **Karlchen said:**
> Hello, cipricus.

*PDFXCview.exe* is a Windows executable file. From the Linux perspective it is not an executable file. So executing ```
chmod +x /path/to/*PDFXCview.exe*
``` will not have the desired effect. Instead you need *Wine* to run this Windows executable *PDFXCview.exe*. ```
wine /path/to/*PDFXCview.exe*
```In order to be able to do so without typing this command in a terminal, you use the system default file-manager
True, but in order to be able to run an .exe with Wine from nautilus, the file permissions has to be set to run as executable. It doesn't have to be executable to run it with the Wine command in a terminal, but it does have to be set if you want to just double click from Nautilus.

---

### Post by Karlchen on 2012-02-27
Hello, forrestcupp.

Confirmed. You are right. It should be stated that you have to do both: Assign the "x" attribute to the Windows executable file _and_ in Nautilus assign the operation **Open with Wine Windows program launcher **to this filetype (*.exe).

Kind regards,
Karl

---

