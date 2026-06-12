---
title: "2 Small problems &quot;Zimbra &amp; Synaptic package manager&quot;"
date: 2011-04-28
forum: General Help
---

### Post by Ominae on 2011-04-28
Hi all 

first the easyer problem to help me with i asume, dont realy know.

Synaptic Package Manager.
i recently tryed to follow a guid to install zimbra via the SPM by adding a reposortory now i find that it was outdated and no longet in use this means that i can no longer update or use SPM at all it says i need to remove the added reposatory but i do not know how to do this with out accsess to SPM.

:S

Zimbra
problem 2. i followed a more uptodate guide on these forums
[http://ubuntuforums.org/showthread.php?p=10634207](http://ubuntuforums.org/showthread.php?p=10634207)
on how to install however i do not know iff i have it right after install i get a white icon on the desktop with a padlock icon and when the program loads for the first time i just see the zimbra window with the red loading icon.


Any help for these 2 problems guys ???

thanx for all teh help

mark

---

### Post by Ominae on 2011-04-28
Here is a screene of the Update error after the dead reposetory was added


[IMG]http://i2.photobucket.com/albums/y8/Eloren/Screenshot.png[/IMG]


Also fixed the Zimbra problems it was due to the ROOT install so i swapped that up a lill found a 
simalar post in another thred

---

### Post by zvacet on 2011-04-28
You can remove repository by typing in terminal

```
gksudo gedit /etc/apt/sources.list
```

find repository with give you problems and delete it.Save and close file.

```
sudo apt-get update
```

To uninstall Zimbra look in created folder after extraction.There should be install file or read me file with instruction for installation/uninstallation.

---

### Post by Ominae on 2011-04-28
Thanx Zvacet

those 2 commands helped out tremendously :)
i now have the SPM working agen :) 

ohh i had zimbra uninstalled btw :) that is all good gave up with that

Chears agen 

mark

---

