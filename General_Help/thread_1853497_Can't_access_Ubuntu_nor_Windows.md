---
title: "Can't access Ubuntu nor Windows"
date: 2011-10-02
forum: General Help
---

### Post by rymdgris on 2011-10-02
For some reason I wrote this in the terminal:

su root
entered password
rm -rf /
(or maybe it was: rm -rf *)

Now I guess I shouldn't have done that according to what a more experienced Ubuntu user said, but the problem now is that I have no access to neither Windows or Ubuntu and lots of valuable data is stored on this harddisk.

I should maybe mention that Ubuntu was installed using Wubi also, and that I have tried removing the harddisk and connected it on an external drive, but then all I saw was an Ubuntu folder that had a .fuse_hidden file within it and nothing else. I've also tried running the Windows installer DVD but it can't repair the boot problem.

What it says as an error is this to insert my Windows installation disk and restart to run "Repair". 

The file it says is \ubuntu\winboot\wubildr.mbr, and status is 0xc000000f

Info is: The selected entry could not be loaded because the application is missing or corrupt


My version is 10.04. Any help would be much appreciated as I am shaking with the fear I've lost something very valuable here :(

---

### Post by rymdgris on 2011-10-02
By the way, the faulty Windows boot says:

Status: 0xc000000f
Info: The boot selection failed because a required device is inaccessible

Doesn't help any though if I do put in the installation disk...

---

### Post by Mark Phelps on 2011-10-02
You have no access to Ubuntu because, most probably, your entry of the RM command removed most, if not all, of it! Why you would even think of entering such a command, without checking here first, especially when you have valuable data on your drive, and (apparently) NO backup of that data, is a real mystery!  What were you thinking??

The first thing to find out at this point, is what is REALLY left on your drive.

Boot into an Ubunty desktop CD, use the Try Ubuntu option, and once you get to a desktop, open the different fileystems to see what is still there.

If the Windows filesystem is still there, you can copy the files off to an external drive and at least, recover them.

If the windows filesystem is gone, that's a much harder problem to overcome.

---

### Post by Rasa1111 on 2011-10-02
and THIS is what happens when you enter dangerous commands when you have no idea what you're doing!

Hope you learn a lesson. 

I'd also like to know what on earth made you enter that command without knowing what it does..
or without even googling it first!?!? 

Hope you get your stuff back..
but I wont hold my breath. :/ 

good luck

---

