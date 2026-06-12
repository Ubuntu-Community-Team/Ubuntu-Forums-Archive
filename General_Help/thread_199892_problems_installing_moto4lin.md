---
title: "problems installing moto4lin"
date: 2006-06-19
forum: General Help
---

### Post by busdriverneal on 2006-06-19
i am trying to install [moto4lin]("http://moto4lin.sourceforge.net/wiki/Main_Page") and keep getting an error saying:

libusb 0-.1-4 dependecies not found

so i downloaded the libusb 0-1-4 and tried to install it, but i get an error:

previous version allready installed

so... what do i do.. i assume i allready have the libusb files that i should

libusb-0.1.so.4.4.2
libusb-0.1.so.4

are these the correct ones? how do i use moto4lin?? thanks for the help ;-]

---

### Post by Glass_Onion on 2006-06-19
There's a great HowTo for installing it [here](http://www.ubuntuforums.org/showthread.php?t=56253&highlight=moto4lin). 

Unfortuantly the configure and run sections don't help one bit. I can't get it to work. My computer doesn't seem to want to create the ttyACM0 node needed to comunicate with my mobile which is pretty anoying. Someone else here should be able to help with that though?

---

### Post by Ocxic on 2006-06-19
when you plug in your mobile phone check dmesg for where/what it is named in /dev for me it was ttyACM0

---

### Post by busdriverneal on 2006-06-19
i tried the install help page you suggested but get nothing when trying to cvs moto4lin.. everything works up until:

#Installing moto4lin 
We are going to get the moto4lin source from a cvs repository. You might get an error from cvs at this stage, ignore and proceed. Asked for password? Just press Enter.
Code:
~$cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin login
~$cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin co -P moto4lin

after which i get nothing.. it calls for my password and i hit enter without typing anything and it just sits there.. doing nothing.. so.. 

i do have moto4lin.deb on my desktop that i downloaded from somewhere but when i try to intall it i still get the lib error.. i followed the instructions on the helper and all the lib stuff installed up untill the moto4lin part.. so.. help!

---

### Post by Glass_Onion on 2006-06-20
I tried the cvs commands that howto uses and they didn't work. I used the two cvs commands from the Moto4lin wiki and they worked perfectly.

```
cvs -d:pserver:anonymous@moto4lin.cvs.sourceforge.net:/cvsroot/moto4lin login
cvs -z3 -d:pserver:anonymous@moto4lin.cvs.sourceforge.net:/cvsroot/moto4lin co -P moto4lin
```

I don't really have much of an idea on what could help you with the lib errors though. Sorry.

---

### Post by MikB on 2007-02-24
There's also a good HOWTO on how to compile moto4lin and p2kmoto here:

[http://www.computechgroup.com/?p=284]("http://www.computechgroup.com/?p=284")

But despite loading it with "sudo moto4lin" and updating the list, unplugging and plugging in before and after loading up - I still cannot get moto4lin to move past...

> [info] Phone is unpluged. Please connect it
[info] Phone pluged as AT
Try to connect
[error] Unable to connect

Can anyone throw me a bone?

---

