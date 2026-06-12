---
title: "Shared Folder Permissions"
date: 2009-12-08
forum: General Help
---

### Post by shifterdriver13 on 2009-12-08
Hi all! I'm trying to share a folder across my network from my xubuntu system, but when I go to the properties of the folder it won't let me change the group and others permissions from read only, and I'd like to be able to write to it from the other computers on my network. I'm running xubuntu 9.10 with all the available updates, if that makes any difference. It worked great with 9.04, but I don't know what changed. If anyone could explain how to do this, preferably without terminal as I'm not very technically oriented that way, it would be much appreciated.
 
         Thanks much in advance!

---

### Post by firsttimeuser on 2009-12-08
sudo chmod a+r /dirname

---

### Post by shifterdriver13 on 2009-12-09
Okay I got it to work up to the dirname, how do I find that and type it in correctly?

---

### Post by iMisspell on 2009-12-09
Like firstimeuser posted, this would be terminal, sorry.

Lets say the folder you want to share is named 'ShareMe' and the path to that folder would look like:
/First_Folder/AnotherFolder/ShareMe/

Open up terminal
key in:
```
cd /First_Folder/AnotherFolder
```
That will move you to the "holding" folder of ShareMe

Now in the terminal you would execute what firsttimeuser posted (add the -R).
```
sudo chmod a+r -R ShareMe
```

But note, that command will only make the 'ShareMe' folder readable for every one, not writable.

The following would make it readable and writable along with all Files and Folders INSIDE 'ShareMe'.
```
sudo chmod a+r+w -R ShareMe
```


You will also have to set up Samba or something (to enable sharing, the above will only set up permissions), not sure what xubuntu has built in as ive never used xubuntu before. 



_

---

### Post by shifterdriver13 on 2009-12-09
It worked great, thank you!!!

---

