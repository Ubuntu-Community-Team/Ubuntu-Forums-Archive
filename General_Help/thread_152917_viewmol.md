---
title: "viewmol"
date: 2006-03-30
forum: General Help
---

### Post by Hoffmann on 2006-03-30
Hello:

Have anyone installed viewmol?

I just installed it (by using Synaptic), but I got nothing if I type 'viewmol' on the terminal. Actually, I didn't see any viewmol inside the directories /usr/bin or /usr/local/bin. Moreover, I have no 'man viewmol'.

How can I lounch that program on Ubuntu?

Thanks,
Hoffmann

---

### Post by nanotube on 2006-03-30
from a terminal, do 
```
dpkg -L viewmol
```
this will show all the files that got installed by the package. from that you should be able to pick out where the executables are. :)

---

### Post by alancaerdydd on 2006-04-15
Hi Hoffman,

Did you manage to solve the problem with viewmol. I'm in a similar position.

I've checked the output for dpkg -L viewmol but still can't see an executable. my viewmol.desktop file says it should be in /usr/bin/viewmol but I can't find any such directory or file. Odd, synaptic tells me it's installed.

---

### Post by Hoffmann on 2006-04-15
[QUOTE=alancaerdydd]Hi Hoffman,

Did you manage to solve the problem with viewmol. I'm in a similar position.

I've checked the output for dpkg -L viewmol but still can't see an executable. my viewmol.desktop file says it should be in /usr/bin/viewmol but I can't find any such directory or file. Odd, synaptic tells me it's installed.[/QUOTE]

Hi alancaerdydd,

Unfortunately, I didn't solve the problem with viewmol. After running dpkg -L viewmol, I also see /usr/bin/viewmol. However, it doesn't run at all.
It seems like something is broken with viewmol.

Hoffmann

---

### Post by alancaerdydd on 2006-04-15
Many thanks hoffman, that was what I feared. 

I shall give it one last go compiling everything from source and if that doesn't work I'll put it on my ever increasing pile of programs which sound good but can't be made to work without a degree in computing...

I hope to try this tomorrow so I'll let you know how I get on.](*,) 

Alan

---

### Post by Hoffmann on 2006-04-15
[QUOTE=alancaerdydd]Many thanks hoffman, that was what I feared. 

I shall give it one last go compiling everything from source and if that doesn't work I'll put it on my ever increasing pile of programs which sound good but can't be made to work without a degree in computing...

I hope to try this tomorrow so I'll let you know how I get on.](*,) 

Alan[/QUOTE]

Hi Alan,

Sounds good. 
So, please, let me know if you get it or not.

Best,
Hoffmann

---

### Post by alancaerdydd on 2006-04-17
Well hoffman I'm not yet sure whether I'm getting anywhere or not. 

Clearly on the compile there were a lot of errors and warnings. Now some of these relate to updated syntax and I doubt are program terminators and I did get some parts of the prog to compile and give binaries but not viewmol itself (didn't even get an object code).

However there are some errors which are clearly catastrophic and most seem to relate to Xm.h which  the program make (via getmachine in the viewmol install) cannot find. 

This seems to be a header file associated with open motif but not certain.

I certainly don't have it on my system though I do have a file HvCallXm.h.

At this stage I don't know if these are related. However I suspect that this is just some simple path problem. Whilst i've printed out the errors from make and the makefile and getmachine its going to be days before I've gone through it all. I'm considering emailing Joerg Hill but I am very unsure if he's still around, I see little activity on the net after 2003/2004. Do you have a current email?

sadly I'm now in my usual situation where I need to get back to the bench but will hopefully get back to this v soon.

Alan

---

### Post by alancaerdydd on 2006-04-17
Update to my last post. I notice in the changelog that a member of the ubuntu staff, adam conrad,  has been involved with graphics libraries re viewmol. Whilst I hesitate to bother busy staff members, if joerg isn't contactable and we can't fix this ourselves then ...maybe worth thinking about. 

Alan

---

### Post by Hoffmann on 2006-04-17
Hi Alan,

Defenitely, something is wrong with MolView. I think you should talk to adam conrad as well.
I am also interested in another program, that doesn't work: Ghemical. By the way have you had problems with it too?

Hoffmann

---

### Post by chrishack14 on 2006-04-26
I just happened to run across this thread today and have had the same problem with viewmol.  However, I noticed that you also said that Ghemical does not work.  I assume that you are just installing the package through apt, and I also had problems with it crashing all the time when I had the official Ubuntu version installed.  However, I compiled the latest version (1.91) from source, and after great difficulty got it working.  Are you running the AMD64 version of Ubuntu?  That seems to be the source of most people's problems with Ghemical these days, as the code as it is currently written is not 100% 64-bit-friendly and has to be modified somewhat for such systems.  Anyway, if you're still having trouble I can try to write up the procedures I went through that got it to work for me if you think it might help.

---

### Post by Hoffmann on 2006-04-26
[QUOTE=chrishack14]I just happened to run across this thread today and have had the same problem with viewmol.  However, I noticed that you also said that Ghemical does not work.  I assume that you are just installing the package through apt, and I also had problems with it crashing all the time when I had the official Ubuntu version installed.  However, I compiled the latest version (1.91) from source, and after great difficulty got it working.  Are you running the AMD64 version of Ubuntu?  That seems to be the source of most people's problems with Ghemical these days, as the code as it is currently written is not 100% 64-bit-friendly and has to be modified somewhat for such systems.  Anyway, if you're still having trouble I can try to write up the procedures I went through that got it to work for me if you think it might help.[/QUOTE]

Hi chrishack14,

Since my machine is a EM64T, I started using the 64-bits version of Ubuntu. However, due to some problems and the need to chroot for 32-bits, I decided to uninstall  Ubuntu 64-bits. Then, I installed the 32-bits version of Ubuntu. In my opinion, that was a nice decision, since 32-bits works perfectly.
However, I still have problems which both Viewmol and Ghemical. Actually, I am more interested in Ghemical right now. So, if you could send me your procedure for getting Ghemical running, I will be very grateful.

Best,
Hoffmann

---

### Post by Hoffmann on 2006-04-28
[QUOTE=chrishack14]I just happened to run across this thread today and have had the same problem with viewmol.  However, I noticed that you also said that Ghemical does not work.  I assume that you are just installing the package through apt, and I also had problems with it crashing all the time when I had the official Ubuntu version installed.  However, I compiled the latest version (1.91) from source, and after great difficulty got it working.  Are you running the AMD64 version of Ubuntu?  That seems to be the source of most people's problems with Ghemical these days, as the code as it is currently written is not 100% 64-bit-friendly and has to be modified somewhat for such systems.  Anyway, if you're still having trouble I can try to write up the procedures I went through that got it to work for me if you think it might help.[/QUOTE]

Hi chrishack14,

I just compilled both Ghemical 2.00 and GTK-Gamess 2.00 on my machine. Those (last) versions, 2.00, are excelent. All is working fine now.:D 

Best,
Hoffmann

---

