---
title: "Help with creating a launcher for EVE Online."
date: 2009-10-30
forum: General Help
---

### Post by Ziggirott on 2009-10-30
Hello everyone. I have only been using Linux  for two days so I can't figure out what the problem  I have is.I have EVE Online installed on Ubuntu 9.04. Everything is fine except when I launch from applications/wine/programs/eve/eve.exe I get a error message saying failed to change directory '/home/myname/.wine/dosdevices/c:/windows/temp/nskab26.tmp'(No such file or directory).
If I go to home folder and hit ctrl + h to see the hidden files an  go to .wine/drive c/program files/CCP/EVE/EVE.exe and launch w/WINE all is well. I was looking on Google and had found a page that had a directory path I copied into "create a new launch" and the new launcher  started EVE perfectly. The thing is I deleted it some how and can not find the page again. I'm looking for some help in fixing the pathway to launch EVE or the pathway I can copy into "create a new launch". I would really like to know both ways this way I can learn a little something but please keep in mind I have only been using Linux for two days. Thank you so much for your time. Ziggy

---

### Post by ajgreeny on 2009-10-30
Make a new launcher on your desktop or wherever you want it in the menus and in the command box enter ```
wine "/home/username/.wine/drive c/program files/CCP/EVE/EVE.exe"
``` making sure you keep the "" marks in the pathway.

Your problem results from the spaces in the folder names in the pathway of the file, which you can overcome either with the quotes or by using a backslash in the front of the space eg, ```
wine /home/username/.wine/drive\ c/program\ files/CCP/EVE/EVE.exe
```  You need the space after the first "wine" as that is the name of the application to run the file in the pathway .

---

### Post by Ziggirott on 2009-10-30
Now when I try and create a launcher I can't. I tried both commands but it still wouldn't work:( Any thoughts?

---

