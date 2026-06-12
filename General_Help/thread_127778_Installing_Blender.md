---
title: "Installing Blender"
date: 2006-02-09
forum: General Help
---

### Post by SonAsylum on 2006-02-09
I want to install blender on my computer running Ubuntu but when i double click on the file absalutly nothing happens. I am completely new to this whole thing and could really use some help. As i understand i should be able to download and install it using an application within Ubuntu but i can not get on the internet with that computer. I had to download it on one computer and transfer it over.

---

### Post by taurus on 2006-02-09
There is a version on repo so the easiest thing to do is to use either synaptic or apt-get,

sudo apt-get install blender

---

### Post by jazzgossen on 2006-02-10
That works, or if you are not yet comfortable using the terminal, just go to the Applications menu, Add Application, look around under Graphics; Blender should be there.

---

### Post by cotcot on 2006-02-10
If you right mouse click on the downloaded file and choose unpack (or extract) you get then blender in a directory blender... . Move to that directory (cd blender...) and type "blender -w" to start blender. The "-w" is to keep the task bar of your desktop.

---

### Post by SonAsylum on 2006-02-10
The version i am installing is a newer one then the one that is listed. I cannot however connect with that computer to the internet and download and install an update. I had to manuly download the entire version on another computer, burn it to a disk, and then copy it from the disk to the other computer. When all of this is done and i try the windows way of installing it and double click on the executable file nothing happens.

---

### Post by jazzgossen on 2006-02-13
The windows way? You did download the Linux install file, I hope? If double-clicking the file doesn't work, there mast be something wrong with the default program settings on your installation. 

To set the default handler of bz2-zipped files to Archive Manager, right clock the file, choose properties, click on the "open with" tab, and choose Archive Manager from there (if it's not available, I think it should be, you can install it from the Applications menu). Then you should be able to double-click the file, extract its contents, and then follow cotcot's instructions.

If that fails, and/or you want to do it in text mode instead, you can open a terminal, cd to the directory where the file is, type "bunzip2 filename", "tar -xvf filename", cd to the newly created blender directory, and start it with "blender -w" from there.

---

### Post by cotcot on 2006-02-13
You can add a file of your hard disk to your repository list, add the blender download to that file and get blender with synaptic after reload of the repository. 

You do not need to "install" it (configuration etc), it is enough to unpack the downloaded file. When you unpack and go to the unpacked directory you will find the binary for blender. This means you only have to go to the directory (cd) and type "blender" or "blender -w". It is this way I use to have blender on a USB stick and use together it with a live CD wherever i need it.

---

### Post by SonAsylum on 2006-02-14
Thanks all for your help. It was a combo of problems. First in the terminal i was not using the right commands then when i did i found out i did not have a certain package installed. After i installed the package and double clicked or typed in the command in the terminal i was able to run the program. My only question is why doesn't Ubuntu tell me when i double clicked on the program that i did not have this package installed? Why can i only see that when i am using the terminal?

---

### Post by taurus on 2006-02-14
The error message should be logged in ~/.xsession-errors if you run an app by clicking on it!  But if you run from a terminal, then the error message will be printed directly to whichever terminal that you execute it...

---

