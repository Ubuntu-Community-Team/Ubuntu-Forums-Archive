---
title: "Error occurred while loading the archive"
date: 2011-03-15
forum: General Help
---

### Post by etsah57 on 2011-03-15
I had been running a dual boot windows XP & Ubuntu. Graboid worked in both systems. I have now got rid of windows, upgraded to 10.10
I installed wine, winetricks & dotnet20, but when I click on my downloaded Graboid.exe file I get the following error:
Command line output
Archive:  /home/etsah57/.wine/GraboidVideoSetup-2.03b-Complete.exe
[/home/etsah57/.wine/GraboidVideoSetup-2.03b-Complete.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/etsah57/.wine/GraboidVideoSetup-2.03b-Complete.exe or
          /home/etsah57/.wine/GraboidVideoSetup-2.03b-Complete.exe.zip, and cannot find /home/etsah57/.wine/GraboidVideoSetup-2.03b-Complete.exe.ZIP, period

I am at a loss as to what to do.

---

### Post by ~Plue on 2011-03-15
its trying to open the .exe  with the archive manager (wrong file association)

right click the exe > open with other application > use custom command "wine" (without quotes) >> and check 'remember this application for....'

---

### Post by etsah57 on 2011-03-15
Thanks, that worked, but now it does not recognise my download folder
In Graboid I have told it to download to: 
c:\Program Files\Graboid\Completed
I get the error message that the folder doesn't exist, but it does.
Is this because the folder is in etsah57 .wine drive_c Program Files Graboid Completed
How do I tell Graboid this is the file?

---

### Post by etsah57 on 2011-03-15
I have tried both of the following paths, and neither works
\home\etsah57\.wine\drive_c\Program/Files\Graboid\Completed
 /home/etsah57/.wine/drive_c/Program\Files/Graboid/Completed
How do I write a correct file path in Ubuntu

---

### Post by ~Plue on 2011-03-16
according to the wine appdb, it looks like graboid would work.
'garbage' is the lowest rating an application gets. it means that "*Application cannot be installed, does not start, or starts but has so many errors that it is nearly impossible to use it*"

appdb entry:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=21613](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21613)
ratings definitions:
[http://appdb.winehq.org/help/?sTopic=maintainer_ratings](http://appdb.winehq.org/help/?sTopic=maintainer_ratings)

---

### Post by etsah57 on 2011-03-16
I checked the site you quoted, it was for a much earlier version of the program. I have used the latest version of the program very successfully. I now have it installed and running in Ubuntu 10.10, but it doesn't like the download path, and I've tried a number of different versions of a path but it still doesn't recognise the path. Ubuntu doesn't seem to like my c: drive or d: drive and that is what it seems Graboid is looking for. I was hoping for help in understanding how to write a download path

---

### Post by neoanderson004 on 2012-04-04
I tried as you said. but it says "Error launching installer". What would I do now??

---

