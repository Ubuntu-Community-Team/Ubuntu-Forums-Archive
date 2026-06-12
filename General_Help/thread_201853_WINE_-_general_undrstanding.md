---
title: "WINE - general undrstanding"
date: 2006-06-22
forum: General Help
---

### Post by Optiker on 2006-06-22
I've installed WINE on my Kubuntu Breezy inatallation, and tried installing a couple of programs that are included in the WINE utility that helps with installations - can't remember what it's called since I'm not at that computer. Success was mixed...one worked, one never did. But, installing using that utility didn't help me with installing any others that weren't included in that utility.

I have several much more ambitious hopes (City of Heroes, World of Warcraft, IrfanView, others) that I'd like to try under WINE, but aren't in that listing, so will need to follow some other i nstallation process.

I've been intimidated so far by not understanding in general terms, how WINE works relative to installation processes and structure. Can anybody help with a simple, concise description of things like:

(1) what and where is the folder structure when using WINE? Is there a complete and independent folder structure of the Windows software within the Linux partition, or does WINE access the Windows software folder structure in the Windows partition? If it doesn't access the Windows partition and needs its own partition and installation in the Linux partition, I assume that means it then needs about the same amount of drive space as the installation in Windows. Ouch!

(2) To install a Windows program - IrfanView for example - is it installed using the Windows software under some WINE shell of some kind?

(3) How do I install a Windows app - again, IrfanView as an example? Simple and step-by-step please!  :)

I've dug around various places including the WINE web site, browsed many threads on this and other forums, and haven't been able to get a good understanding of WINE and the installation process. Am I missing some web-based information that gives a simple, step-by-step installation process, or does that kind of thing not exist?

Thanks!
Optiker

---

### Post by 0okie on 2006-06-22
Wine, from my handle on it creates it's own windows directory. So, lets say you had a tower that didn't have windows at all wine would just go and create that set of files/folders when you ran it for the first time in the terminal.

I'm new to Linux myself and am having a pain with Wine myself lol. To find where Wine made it's little folder go to your Home folder, hold the ctrl button down and then hit H. This will display your hidden folders (be careful!) and down near the bottom you should find a folder called ".wine" that's what wine made and it has windows .dlls and folders there. So yes, it's in the linux partition and it's only 21.7MB on my computer.

I hope that helps you with that question.

---

### Post by SteveF on 2006-06-22
I'll answer inline as best as possible:

[(1) what and where is the folder structure when using WINE? Is there a complete and independent folder structure of the Windows software within the Linux partition, or does WINE access the Windows software folder structure in the Windows partition? If it doesn't access the Windows partition and needs its own partition and installation in the Linux partition, I assume that means it then needs about the same amount of drive space as the installation in Windows. Ouch!]

Wine will create a folder under your home folder called .wine (for you to see it make sure you can view hidden files in Konqueror or in a command prompt, use ls -a from your home folder).  Under that folder will be another folder called drive_c which equates to a Windows C:.  Wine will create the windows and system folders as well as Program File.  When you install applications, they will go here (just like in Windows).  You can specify another folder during most installs (depends on how the install was written).  But for your perspective, treate everything under drive_c the same as you would the C drive in Windows.

[(2) To install a Windows program - IrfanView for example - is it installed using the Windows software under some WINE shell of some kind?

(3) How do I install a Windows app - again, IrfanView as an example? Simple and step-by-step please!  :)]

To run any program under wine, from the command line enter:
wine <app_name>

For app_name, it is the EXE that you are tyring to execute.  If that EXE is not in your current folder, you will need to provide a fill path to the EXE using either Linux or Windows notation.  To install ifranview (I think the install is something like iview398.exe) and assuming you downloaded that file to download under your home folder, you would enter:
wine iview398.exe     (assuming you are in downlaod)
or
wine ~/download/iview398.exe    (if you are not currently in download)
or
wine z:\download\iview398.exe   (if wine has mapped the z drive to your home folder - I forget off-hand what drive , if any, wine maps to your home folder, that can be changed using winecfg).

To execute irfanview once installed (assuming it is installed in program files irfanview) you would execute any of the following:

wine iview_32.exe   (if you are in the irfanview folder)
wine '~/.wine/drive_c/Program Files/irfanview/iview_32.exe'  (Linux way)
wine 'c:\program files\irfanview\iview_32.exe'                     (Windows way)

I don't usually use the Windows way, so it may not work the way I wrote because I haven't tested that in a while.

You will need to manually add any apps you want to run to your menus as the Windows installer will not update them for you.

I don't know if that is the information you're looking for, just let me know.

Steve
I've dug around various places including the WINE web site, browsed many threads on this and other forums, and haven't been able to get a good understanding of WINE and the installation process. Am I missing some web-based information that gives a simple, step-by-step installation process, or does that kind of thing not exist?

Thanks!
Optiker[/QUOTE]

---

### Post by bukwirm on 2006-06-22
To run any program in wine, just type 'wine *program_name*'.

To install a program, just run its installer in wine.

You may want to check out the wine website for a list of programs known to work with wine.

---

### Post by Optiker on 2006-06-22
The three replies so far are a good start for me to go back and try again. I think you've pretty well answered my questions, and I think I'm ready to try. I'll probably use Irfanview as a test since I use it a lot in Windows and would miss not having it in Linux. If I can manage that, then I'll try others.

I have browsed the listings in the WINE website, as well as watching several different forums regarding how well various programs work under WINE. As far as I can tell, I just saw a post today that reported that the Irfanview developer is quoted as saying it works under WINE, and from the City of Heroes forums, it's reported to work well. Various posts regarding World of Warcraft are mixed - some say it works great, some have problems.

It's interesting that I've read some posts that report that City of Heroes, and some others, seem to run better under WINE in Linux than in their native Windows environment. Interesting! Some highly recommend Cedega rather than WINE, but I'll try WINE first.

Thanks again!
Optike

---

### Post by Optiker on 2006-06-25
Steve...OK - tried it with IrfanView. Have iview398.exe in /home/optiker/Downloads, and in terminal, enter the following, with the result shown:
------------------------------------
optiker@optiker-desktop:~/Downloads$ wine iview398.exe
err:module:import_dll Library mfc42.dll (which is needed by L"Z:\\home\\optiker\\Downloads\\iview398.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\optiker\\Downloads\\iview398.exe" failed, status c0000135
optiker@optiker-desktop:~/Downloads$
---------------------------------------------
Now what?

Thanks!
Optiker

---

### Post by SteveF on 2006-06-25
[QUOTE=Optiker]Steve...OK - tried it with IrfanView. Have iview398.exe in /home/optiker/Downloads, and in terminal, enter the following, with the result shown:
------------------------------------
optiker@optiker-desktop:~/Downloads$ wine iview398.exe
err:module:import_dll Library mfc42.dll (which is needed by L"Z:\\home\\optiker\\Downloads\\iview398.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\optiker\\Downloads\\iview398.exe" failed, status c0000135
optiker@optiker-desktop:~/Downloads$
---------------------------------------------
Now what?

Thanks!
Optiker[/QUOTE]

I just tried it and I got the IrfanView setup screen.  Did you get that screen or did you just get the errors shown in the post?  Also, what do you get when you enter:
wine --version

Unfortunately I don't use the build that comes with Kubuntu or Ubuntu.  I added the [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) repository in order to get newer Wine versions.  I'm running 0.9.16.  But I have run older ones and did not have problems with IrfanView.

Also could be a problem with your setup.  If you enter winecfg at a command prompt, you'll get a GUI to set some settings for wine.  In the drives tab, what do you have entered for the path?

Steve

---

### Post by Optiker on 2006-06-26
[QUOTE=SteveF]I just tried it and I got the IrfanView setup screen.  Did you get that screen or did you just get the errors shown in the post?

***When I tried to run it, I got what is shown in my reply to you, not the setup screen.***

Also, what do you get when you enter:
wine --version

***If I recall, it's 0.9.9, but not sure since it's on my computer at home and I'm replying from work.***

Unfortunately I don't use the build that comes with Kubuntu or Ubuntu.  I added the [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) repository in order to get newer Wine versions.  I'm running 0.9.16.  But I have run older ones and did not have problems with IrfanView.

Also could be a problem with your setup.  If you enter winecfg at a command prompt, you'll get a GUI to set some settings for wine.  In the drives tab, what do you have entered for the path?

***As mentioned above, it's at home, so I will trty to remember to check those things at home tonight and reply then.***

Steve[/QUOTE]

Thanks for the reply...was beginning to think this thread had died without resolving the problem.

Optiker

---

### Post by mannheim on 2006-06-26
[QUOTE=Optiker]Steve...OK - tried it with IrfanView. Have iview398.exe in /home/optiker/Downloads, and in terminal, enter the following, with the result shown:
------------------------------------
optiker@optiker-desktop:~/Downloads$ wine iview398.exe
err:module:import_dll Library mfc42.dll (which is needed by L"Z:\\home\\optiker\\Downloads\\iview398.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\optiker\\Downloads\\iview398.exe" failed, status c0000135
optiker@optiker-desktop:~/Downloads$
---------------------------------------------
Now what?
[/QUOTE]

I haven't much Wine experience, but what I have done when error messages like this appear is copy the missing windows dll from a real Windows installation (in this case something like C:\WINDOWS\SYSTEM32\mfc42.dll) and put it in the corresponding place in the wine drive, e.g. /home/optiker/.wine/drive_c/windows/system32/mfc42.dll

---

### Post by mannheim on 2006-06-26
Having written that, I just tried installing irfanview, and had the same experience as SteveF. I don't have a copy of mfc42.dll in my wine directories, and still irfanview installed without complaint. It seems to run fine too.

For info, I think my wine install is pretty much default. If I run "winecfg", and look at the various tabs there I see:

[LIST]
[*]Applications tab: "Default Settings", Windows version: "Windows XP"
[*] Libaries tab: everything blank
[*] Drives tab: [LIST]
[*] C: ../drive_c
[*] D: /cdrom
[*] Z: /
[/LIST]
[/LIST]

---

### Post by Optiker on 2006-06-26
mann...copying the dll is a simple enough thing to try - should have thought f it myself.

However, since you had the same experience as SteveF, I will first check and compare my winecfg info to yours and see if there's a match.

Thanks!
Optiker

---

