---
title: "I am in desperate need of help!!"
date: 2011-01-31
forum: General Help
---

### Post by majinsarek on 2011-01-31
Hi,

  ok so my Tech teacher installed Ubuntu on my laptop for me so that i could try to program with Objective-C in the terminal. It didn't work. Just the other day i tried to remove the partition to make space for other things that i needed on my computer. 

I also made my Vista portion take of the part that was controller by Ubuntu. Now when i run i get a message that says

error: no such partition.
grub rescue> 

IDK what to do, i have no cd to instal it again, oh yeah and in 2 and a half hours, i won't have a computer because the one that i am on now goes back to my co-op, PLEASE HELP ME

---

### Post by majinsarek on 2011-01-31
bump

---

### Post by Lukiwuki on 2011-01-31
The linux Bootloader is still in the MBR (Master Boot Record)
Reinstall the Vista Bootloader into the MBR.
Should work with a Vista instalation disk and system repair.

---

### Post by majinsarek on 2011-01-31
how do you do that? I have very little knowledge of actually installing an OS and even less knowledge on Linux

---

### Post by Swagman on 2011-01-31
But he said he has no installation disk.

Try using [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Elfy on 2011-01-31
Firstly - please do not bump your thread this quickly - once in 24 hours.

Second - please use sensible thread titles - you'll find that all the threads here are from people needing help.

---

### Post by majinsarek on 2011-01-31
how would i go about getting that onto my computer though.. i can't load anything,

edit: sorry fore, I'm freaking out because i literally have 2 hours left to fix this before im without any form of a working computer

second edit : is there not just a temporary fix that i can just like ignore it for now and go back to windows vista? basically all i need on for right now is to get important files off.. I'm planning buying a new laptop.. even if i have to do it every time i turn my computer on i have to put the code in thats fine.. like a bypass code is all i need...

---

### Post by drewsus on 2011-01-31
you need to start downloading the ubuntu live cd right this second and hope you have a fast enough connection and a blank cd/ usb stick with at least 700mb of free space. 
Go here and click Start Download:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
And either burn it to disk or use [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) to make a live usb from windows. note that the usb needs to be formatted to fat32 and *I think using this tool, it will wipe the info on the stick*. 

Then look at this post (and make sure to read at least the first reply as well):
[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

But be quick! As you said, you dont have much time.

**Edit1:** Also, from the Live CD/USB you can access the files on your Windows partition. It will be a drive on the left when you open the filemanager (Nautilus). [COLOR="Blue"]Then, if you have an external drive, you can just transfer everything there. [/COLOR]
Example: 
[IMG]http://i.imgur.com/Nwub4.jpg[/IMG]

---

### Post by majinsarek on 2011-01-31
thank you very much :) its gonna cut it close lol, it's gonna take like an hour and a bit, I will post again when it's done :)

Edit: will i have troubles making downloading the file from a mac and using it on windows?
second Edit: thanks for the picture, it will help :)

---

