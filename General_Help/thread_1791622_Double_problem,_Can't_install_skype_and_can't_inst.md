---
title: "Double problem, Can't install skype and can't install anything on Ubuntu SoftwareCen."
date: 2011-06-27
forum: General Help
---

### Post by ShelbyMan on 2011-06-27
**Problem with Skype Installation**

The program hh.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience.

This can be caused by a problem in the program or a deficiency in Wine. (Note can't uninstall wine tell u more about that problem later) You may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application.

If this problem is not present under Windows and has not been reported yet, you can report it at [http://bugs.winehq.org](http://bugs.winehq.org).

[B]Problem with Ubuntu Software Center - Installation of apps and Uninstallation
[/B]
An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Thank you for reading my problems.:popcorn:

---

### Post by mtbower07 on 2011-06-27
Why not install the Linux Skype Version?

---

### Post by mtbower07 on 2011-06-27
As for your App Center


See thread [http://ubuntuforums.org/showthread.php?t=1632545]("http://ubuntuforums.org/showthread.php?t=1632545")

---

### Post by ShelbyMan on 2011-06-27
Thanks for the link mate

---

### Post by trizrK on 2011-06-27
Yes install the linux version of skype. 
I believe its a .deb file so it should a quick and painless install..
Here's the link: [http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/)
I defiently recommend getting the Linux version to avoid Wine problems
An even quicker way is through the terminal:
[B]sudo apt-get install skype
[/B]Good luck.

---

### Post by ShelbyMan on 2011-06-27
Still same problem, tried both solutions

---

### Post by mtbower07 on 2011-06-27
Skype or Software Center?

---

### Post by ShelbyMan on 2011-06-27
Both

---

### Post by mtbower07 on 2011-06-27
With the Skype are you using the Windows version or Linux? If you go to your Synaptic Package Manager it should be in your repositories. You can install it from there. I am looking for a solution to your Software Center.

---

### Post by ShelbyMan on 2011-06-27
When i try to open Sypnatic package manager it comes up with 
-------------------------------------------------------------------------
Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application 1st.

but it dosent seem to be open i looked on system monitor

---

### Post by mtbower07 on 2011-06-27
Is the Software center open or is there a program installing through your terminal? If not, do a complete shutdown. Turn machine back on and try Synaptic again.

---

### Post by ShelbyMan on 2011-06-27
new error 

E:dpkg was interrupted, you must manually run 'sudo dpkg--configure -a to correct the problem.
E:_cache->open() failed, please report

---

### Post by mtbower07 on 2011-06-27
Did you run 'sudo dpkg--configure' -a in a terminal?

---

### Post by ShelbyMan on 2011-06-27
Ye i did but said comment not found

---

### Post by mtbower07 on 2011-06-27
Is there a space between dpkg and the dashes like this                  "sudo dpkg --configure -a." There should be.

---

### Post by ShelbyMan on 2011-06-27
Ah that was the problem thanks mate, now what to do with sypnatic package manager?

---

### Post by mtbower07 on 2011-06-27
In the quick search box type "skype". On skype right click and mark for install. then click apply.

---

### Post by ShelbyMan on 2011-06-27
Thanks bro your a pro :KS

---

### Post by ShelbyMan on 2011-06-27
now gotto wait for the slow download unfortunatly

---

### Post by mtbower07 on 2011-06-27
AFTER your skype installs close synaptic and open software center. Does that work for you?

---

### Post by ShelbyMan on 2011-06-27
Sigh 8 minutes remaining for download

---

### Post by mtbower07 on 2011-06-27
Glad to be able to help! If your problems are solved please mark the thread as solved.

---

### Post by sunasia on 2011-06-27
Ok tell you my experience , I had problems today with skype I reinstalled  it ,( Deleted and installed again from Skype website) But when skype opens after signing in it closes, It will not stay open , furthermore its no longer avaible in my Download centre of applications, Figure that one out:roll:

---

