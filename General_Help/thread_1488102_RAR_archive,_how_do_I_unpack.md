---
title: "RAR archive, how do I unpack?"
date: 2010-05-19
forum: General Help
---

### Post by David Deu on 2010-05-19
Hi!
I'm looking for something to unpack RAR archives with. 
I actually installed 7zip which is supposed to do it, but from some reason It's not shown anywhere. (I'm quite new to the all Linux stuff so may be it's somewhere, but I don't know where to look for it). 
Anyway I would like to know about a solution for RAR archives.
Thanks,
David

---

### Post by linuxman94 on 2010-05-19
When you install 7zip, it integrates itself into file-roller (the default unpacking tool.)  So to upack a .RAR file, just open it.

---

### Post by stoneage on 2010-05-19
Right click on the archive and choose 'Extract Here'.

> man unrar in a Terminal for more information

---

### Post by David Deu on 2010-05-19
> **linuxman94 said:**
> When you install 7zip, it integrates itself into file-roller (the default unpacking tool.)  So to upack a .RAR file, just open it.
No it doesn't open.
Where can I check if it's integrated into the system at all? because it's not in the "right-click-menu".

---

### Post by linuxman94 on 2010-05-19
How did you install it?  Through Ubuntu Software Center? Terminal? Synaptic?

---

### Post by David Deu on 2010-05-19
> **stoneage said:**
> Right click on the archive and choose 'Extract Here'.

  It says " The archive format is not supported".

---

### Post by Spr0k3t on 2010-05-19
If you have the ability to extract the archive and file roller states it is not a supported archive... it's very possible the archive is corrupt.  Try creating an archive of the same type and extracting it.

---

### Post by David Deu on 2010-05-19
> **linuxman94 said:**
> How did you install it?  Through Ubuntu Software Center? Terminal? Synaptic?
First, through the software center, then:
```
 sudo apt-get install p7zip 
```

---

### Post by linuxman94 on 2010-05-19
> **spr0k3t said:**
> if you have the ability to extract the archive and file roller states it is not a supported archive... It's very possible the archive is corrupt.  Try creating an archive of the same type and extracting it.

+1

---

### Post by mb_webguy on 2010-05-19
You need to install the unrar package from the multiverse repository.  While I'd also suggest installing the p7zip-rar package, I'm not sure it integrates into File Roller.  Once you've installed unrar, you can right-click on the rar archive and open it with Archive Manager (File Roller).

---

### Post by David Deu on 2010-05-19
> **Spr0k3t said:**
> If you have the ability to extract the archive and file roller states it is not a supported archive... it's very possible the archive is corrupt.  Try creating an archive of the same type and extracting it.
I don't see the RAR option in the archive creating menu.

---

### Post by stoneage on 2010-05-19
> **mb_webguy said:**
>  While I'd also suggest installing the p7zip-rar package, I'm not sure it integrates into File Roller. 

Yes, make sure it is p7zip-rar you installed, and also install unrar, if you like (I thought it was installed by default :/)

EDIT - To create a .rar archive you need to install rar ?

---

### Post by David Deu on 2010-05-19
> **mb_webguy said:**
> You need to install the unrar package from the multiverse repository.  While I'd also suggest installing the p7zip-rar package, I'm not sure it integrates into File Roller.  Once you've installed unrar, you can right-click on the rar archive and open it with Archive Manager (File Roller).
I'm new in Linux so I would like to hear an expended explanation on what does that mean, Thanks.

---

### Post by David Deu on 2010-05-19
> **stoneage said:**
> Yes, make sure it is p7zip-rar you installed, and also install unrar, if you like (I thought it was installed by default :/)

EDIT - To create a .rar archive you need to install rar ?
Thank you!
I've Installed:
```
 sudo apt-get install p7zip-rar
  sudo apt-get install unrar 
```
and it's unpacked now!

but still in the create archive menu I couldn't find the RAR, (maybe I have to resart?)

---

### Post by stoneage on 2010-05-19
No, I think you just need to install rar, it is a different package.

Try > sudo apt-get install rar

---

### Post by 2hot6ft2 on 2010-05-19
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install rar unrar nautilus-open-terminal
```
then restart nautilus with
```
sudo killall nautilus
```
then go to the folder the rar(s) are in or the one that contains the folder the rars are in and right click and select Open in terminal and use this command
For multipart rars
```
find -type f -name '*1.rar' -exec unrar x {} \;
```
this works great if you have mulipart rars you can put them all in a folder and run that from the folder that contains the folder they are in and it will extract them all to the folder you open the terminal in.
If it's just a single rar you can use this instead
```
find -type f -name '*.rar' -exec unrar x {} \;
```
Enjoy
The difference between the 2 commands is the number "1" since in a multipart rar you don't want to run it against anything but the first one since each one after that is redundant and will just replace the file that was already extracted from the first one. That means you will have to answer if you want to replace it with every part after the first one.
:guitar:
I had a couple hundred multipart rars and this made it so simple to extract them all at once.

---

