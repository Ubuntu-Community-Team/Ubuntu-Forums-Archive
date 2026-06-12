---
title: "Wine and other programs.."
date: 2010-08-31
forum: General Help
---

### Post by speedracer2010 on 2010-08-31
Hello ALL. While new to UBUNTU and this forum I am not new to Linux. I have tried various versions over these past few years with very little positive results. I am TIRED of Windows (7) and am trying to convert once and for all. Before this can happen my data has to be able to be used by the original Win program or an alternative. So, I tried installing Filemaker Pro v9 and it seemed to install under Wine 1.2.0 but it would never start. ANY clue on what to do would be appreciated. Next I tried to install KEXI which was supposed to be in the KOffice suite. Installed but could NOT find the KEXI database program (whole reason for installing the suite). HOW do I install KEXI or is there another database program that resembles Filemaker?? I tried to install a program called MONEYDANCE which utillizes Java. It too appeared to install under Wine but would never run. Tried changing the run with selections to each one offered but it would not run under any. Again, any clue on how to make it run would be great. While UBUNTU seems to have taken larger strides in working (booted up fine, found my network, found all my hard drives and was even able to get a couple of printers recognized) it is this 'reluctance' in Linux to run 'outside' programs that is still a common thread. Once this is over come, Linux would easily overcome Win in the future. Sorry for my first post being long but I really could use the help in setting up my machine; wanted to give you all a bit of my background and hopefully will be asking many more questions in the future to which you all will be able to provide the answers. THANKS to ALL for any answers provided..

---

### Post by davidmohammed on 2010-08-31
according to the winehq database, filemaker pro v9 is gold rated.

How did you install wine1.2?

if you execute filemaker pro v9 from a terminal session, what errors are displayed?

KOffice is available in the repositories - I presume Kexi is installed automatically - no need to run from wine.

moneydance installation instructions are described [here]("http://moneydance.com/other")

Have you installed the restricted-extras package? e.g. ubuntu-restricted-extras if running ubuntu etc.  Again search in software-centre.  This would install java etc - possibly the reason why moneydance is not working.

---

### Post by speedracer2010 on 2010-09-01
- Yes I did see that filemaker pro was gold unfortunately, no one ever listed the steps on how they accomplished this. IF there were any 'steps' taken out of the ordinary..

- I tried to install it using the wine version 1.14.xx that came from the program install area. It appeared to install properly and I left configuration pretty much along as XP was selected. I then found a description on how to update with 1.2 did it and received NO error msg and when selection 'about' it now shows 1.2    IF it had NOT installed correctly would it let me know or would I be able to see the version info, etc. 

- I did not execute from a terminal session. I placed the cd with the program files in the drive and when it came up opened the drive looked for the install .exe  or setup.exe file and clicked on it. The install seemed to go ok. When it was done it said Filemaker installed successfully. When I went to WINE > applications installed > I saw Filemaker pro listed. When I clicked on it the little circle would spin but nothing ever happened and after several second the spinning circle stopped and that was it..

--I tried the moneydance install instructions - all 3 and could not get it to install at all. Left msg with their tech support no answer. Could NOT get the installation ICON to appear. The icon that did was exactly that an icon but did not do anything. 

- Went to the software centre and tried to install the restricted-extras package > selected install > started, received an error msg that it would install some non approved/accepted files and an OK. Clicked on the o.k. thinking it would continue on but it just stops dead. Tried several times and could never get those files to install. I checked and have a Java Control Panel and it stated that 1.6 is installed. 

This appears like Deja Vu all over again. I am stuck at the same places that I have been on earlier attempts. Can't get any programs to run. 

Hope this info helps. Any more thoughts or suggestions are welcomed. Have a great day..

speedracer

---

### Post by Mark Phelps on 2010-09-01
> **speedracer2010 said:**
> ... it is this 'reluctance' in Linux to run 'outside' programs that is still a common thread...

No ... it is folks that claim to be migrating TO Linux and whine on and on about how MS Windows programs won't work. THAT is the common thread here.

Ubuntu is one of the premier Linux distros that offer a free ALTERNATIVE to MS Windows, not a free VERSION of MS Windows.

If you're so sick of Win7, then you need to move AWAY from it -- not handicap yourself by trying to get a bunch of MS Windows apps working.

---

### Post by davidmohammed on 2010-09-01
please open a terminal session and type the following

sudo apt-get update && sudo apt-get upgrade

are there any errors reported? - copy and paste stuff in a reply using CODE Tags (# icon in the reply toolbar)

For the restricted extras - assuming that you are trying to install ubuntu-restricted-extras please type

sudo apt-get install ubuntu-restricted-extras

are there any errors displayed?  if so please reply in CODE tags

For Filemaker Pro,

in a terminal session please type

cd .wine/drive_c... to the folder containing filemaker pro.  Hint - press the TAB key to autocomplete e.g. cd .wine/drTAB will autocomplete .wine/drive_c

when you navigate to the Filemaker pro folder containing the Filemaker .exe please type

wine <name of exe>
e.g.

wine filemakerpro.exe

Are there any errors displayed?  If so, please reply here in CODE Tags.

For Kexi - assuming the apt-get update stuff above works successfully

sudo add-apt-repository ppa:kubuntu-ppa/beta 
sudo aptitude update
sudo aptitude install kexi

---

### Post by speedracer2010 on 2010-09-02
Thank you for responding and your patience. The first two operations went without a hitch and NO error codes. I am afraid Filemaker Pro did not fare well. I reinstalled the program and then went to a terminal session as requested. When I entered "wine filemakerpro.exe I received the following error, "Cannot find L "C:\\windows\\system32\\filemakerpro.exe" I then copied filemakerpro.exe to the windows\system32 folder. When I entered the command again nothing happened - received same error code. When I did a dir of the folder it printed out "FileMaker\ Pro.exe" NOT "filemakerpro.exe" When I entered "wine FileMaker\ Pro.exe" I get "err:module:attach_process_dlls "odbc32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\FileMaker\\FileMaker Pro 9\\FileMaker Pro.exe" failed, status c0000005"

Lastly, when trying to get Kexi after entering your line I got the following" couldn't find package "Kexi' however the following package contain KEXI in their name  libkexiv2-8  libkexiv2-8.dev  No package will be installed. I tried sudo aptitude install libkexiv2-8 and it installed something but there is no kexi installed nor an icon for the program.... any ideas??

Hope this helps you out. IF you need any more info please ask. I await your cures to the problem.
Thanks again..
speedracer2010

---

### Post by davidmohammed on 2010-09-02
Hi there,
  I assumed that since you installed KOffice, you must be running kubuntu...

So that you can use KEXI, you need some parts of KDE before you can install it.

See [here]("http://www.psychocats.net/ubuntu/kde") - 

after installing KDE, run

sudo aptitude install kexi

I would recommend that you continue your wine issues with filemaker pro as a new post in the [wine subforum]("http://ubuntuforums.org/forumdisplay.php?f=313")

For moneydance - I have just downloaded the link "Linux installer (x86 processor, includes Java) "

From command line I did

cd Downloads
sh moneydance_linux_x86wj.sh

this installed to a directory called "moneydance"

I then typed

cd ~/moneydance

to start the application I did
. ./Moneydance

Obviously you can create a launcher in the menu or on your desktop to run this as a icon/menu option.

---

### Post by speedracer2010 on 2010-09-02
Sorry for the confusion. I did install Koffice but when I noticed it didn't have KEXI I uninstalled it. I figured it must be a separate program as it wasn't in the Koffice suite. I am running Ubuntu not Kubuntu. I read somewhere that other versions of linux use KDE while Ubuntu doesn't. So, am I going to cause any problems by installing the KDE parts? Would it be better to look for a program that is more 'native' to Ubuntu and utilizes what is normally used GNOME (?). Can you recommend another simple database (don't use as a relational currently just use as a flat file system)? Thank you for the moneydance info I will try as well as moving my Filemaker go the other wine forum.. THANK YOU FOR ALL YOUR HELP!!

---

### Post by davidmohammed on 2010-09-03
I dont know of any flat-file based databases - but I'm sure there are a few.  Suggest open Software Centre and search for "database".  For example, OpenOffice Base is part of the OpenOffice suite of software.

---

