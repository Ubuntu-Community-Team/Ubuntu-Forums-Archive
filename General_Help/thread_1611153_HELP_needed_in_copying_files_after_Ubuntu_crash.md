---
title: "HELP needed in copying files after Ubuntu crash"
date: 2010-11-01
forum: General Help
---

### Post by ankit.madan on 2010-11-01
My Ubuntu Version 9.04 crashed so i booted using LiveCD.
Now, in an attempt to recover my data, i have plugged in my external HDD to copy from the previous 'Home' folder.

I am unable to copy all files, as there is an error : 'Error while copying...you do not permissions to read it'

So i'm trying the terminal for copying all of my data using the command:
sudo cp -r <original file location> <new file location>

The <original file location> is the HDD in the laptop showing as a mounted drive.
The <new file location> is the external USB HDD. 

Lets say:
<original file location> is media drive called '153.9 GB Media' inside which there is a 'home' folder which i need to copy
and
<new file location> is media drive called 'Backup Drive'

Now, since both the drives are mounted, what should i type in the <original file location> and <new file location>??

Since i have to copy a complete folder.. how should i go about it ? 

I'm new to Ubuntu..
Any Help would be much appreciated :(

Thanks..Ankit

---

### Post by maxsideburn on 2010-11-01
mounted media will be in the /media folder

---

### Post by ankit.madan on 2010-11-01
> **maxsideburn said:**
> mounted media will be in the /media folder

Sorry but i'll have to be told as a kid ... i have little clue about ubuntu ... simple instructions on how to go about my problem would be immense help ...

---

### Post by t0p on 2010-11-01
```

sudo cp -r /media/153.9\ GB\ Media/ /media/Backup\ Drive

```should do it, I think... though it might be **cp -R**, I'm not sure about that.

Another way to go about it would be to hit **Alt+F2** and type into the box that appears:

```
gksudo nautilus
```

That will open a Nautilus (File Manager) window with admin privileges.  Then you can simply copy and paste the files/folders across from one drive to the other.

---

### Post by ankit.madan on 2010-11-01
> **t0p said:**
> ```

sudo cp -r /media/153.9\ GB\ Media/ /media/Backup\ Drive

```should do it, I think... though it might be **cp -R**, I'm not sure about that.

Another way to go about it would be to hit **Alt+F2** and type into the box that appears:

```
gksudo nautilus
```

That will open a Nautilus (File Manager) window with admin privileges.  Then you can simply copy and paste the files/folders across from one drive to the other.

Thanks a Ton t0p!! Nautilus seems to have worked.. Currently copying files without permission error...

Thanks for the much needed help !

---

### Post by cipherboy_loc on 2010-11-01
My two cents: If you plan to use this to copy EVERYTHING (not just your personal files), it is best to use 
```
sudo cp /path/to/mounted/ubuntu/partition/* -prv /path/to/backup/drive/
```

This will preserve the file permissions as you copy the files. 
-p for preserve,
-r for recursive, and
-v for verbose.



Cipherboy

---

