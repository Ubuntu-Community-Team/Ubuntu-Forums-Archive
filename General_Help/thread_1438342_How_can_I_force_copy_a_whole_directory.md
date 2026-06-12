---
title: "How can I force copy a whole directory?"
date: 2010-03-24
forum: General Help
---

### Post by cab_bae on 2010-03-24
Hello my name is Abraham and well I have a hard drive that I took out from a Ibook G4 so I can backup some of the data on it. How ever when I try to do it on GUI it doesn't let me copy the contents of any of the files in the user's folder. I tried editing the permissions inorder to allow me to read from the directory but it doesn't let me. So the question is how can I in the terminal do a force copy of a folder and all it's contents. The folder only contains pictures. Thanks in advance!;)

---

### Post by Megafag on 2010-03-24
> **cab_bae said:**
> Hello my name is Abraham and well I have a hard drive that I took out from a Ibook G4 so I can backup some of the data on it. How ever when I try to do it on GUI it doesn't let me copy the contents of any of the files in the user's folder. I tried editing the permissions inorder to allow me to read from the directory but it doesn't let me. So the question is how can I in the terminal do a force copy of a folder and all it's contents. The folder only contains pictures. Thanks in advance!;)

Is it possible that you cant do it because Ubuntu cant read from the mac filesystem HFS?

---

### Post by asmoore82 on 2010-03-24
HFS+("hfsplus") Mac filesystems store the standard Unix permissions and Linux honors them.

Open a single nautilus "File Browser" window with root privilege by running:
```
gksudo nautilus
```
either in "Run"(Alt+F2) or terminal

---

### Post by cab_bae on 2010-03-25
I already tried the gksudo nautilus and no luck, also ubuntu can read the HFS+("hfsplus")

---

### Post by cab_bae on 2010-03-25
well I think I solved my problem I just used cp -fr /source/location /destiny/location

f = force
r = recursive

then I edited the permissions for the folder and it's contents, and done!

---

### Post by TechMansoor on 2011-08-19
This did not work for me in trying to copy to a iMAC shared External drive.

The command I'm using is:

sudo cp -fr /home/mansoor sftp://programmingmac.local/Volumes/Time%20Machine%20Backups/Mansoor's%20Ubuntu%20WS%20Backup/ 


all it does is return:

>


and nothing happens...can anyone offer any insight?

---

### Post by Habitual on 2011-08-20
```
sudo cp -fr /home/mansoor /home/mansoor sftp://programmingmac.local/Volumes/"Time Machine Backups/Mansoor's Ubuntu WS Backup"
```

---

### Post by Habitual on 2011-08-21
use rysnc:

[http://www.thegeekstuff.com/2010/09/rsync-command-examples/](http://www.thegeekstuff.com/2010/09/rsync-command-examples/)

"Example 4. Synchronize Files From Local to Remote"

---

