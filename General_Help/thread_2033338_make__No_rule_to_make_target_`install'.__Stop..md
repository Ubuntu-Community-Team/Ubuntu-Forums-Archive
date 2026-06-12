---
title: "make: *** No rule to make target `install'.  Stop."
date: 2012-07-26
forum: General Help
---

### Post by Yayoushiko on 2012-07-26
Uh ok so i am new to Linux and this is my first time Inatalling Something from a Tar.Gz file.
And so i Extracted the FIle's out of the Tar.Gz and then i went into the Terminal and typed this.

cd /home/dillon/Downloads/etherape-0.9.12
then i Typed 
./Configure 
And then i typed 
Make 


But when i type make i get this message "make: *** No rule to make target `install'.  Stop."
I also get that message when i type "Sudo make install"

---

### Post by jwbrase on 2012-07-26
First of all, the EtherApe package exists in the Ubuntu repositories, so you should be able to install it through Software Center without having to bother with compiling it. Is there any specific reason you have not to do that?

Secondly, are you sure you typed everything correctly? Linux is case-sensitive about most things so "Configure" is different from "configure". 

After you type "./configure", type "ls | grep Makefile" (make sure "Makefile" has an upper-case "M") to check if the Makefile was successfully generated. If configure worked properly, you should see:

> Makefile
Makefile.am
Makefile.in

If you just see:

> Makefile.am
Makefile.in

then configure didn't work correctly, and we'll have to figure out why.

---

### Post by Yayoushiko on 2012-07-27
> **jwbrase said:**
> First of all, the EtherApe package exists in the Ubuntu repositories, so you should be able to install it through Software Center without having to bother with compiling it. Is there any specific reason you have not to do that?

Secondly, are you sure you typed everything correctly? Linux is case-sensitive about most things so "Configure" is different from "configure". 

After you type "./configure", type "ls | grep Makefile" (make sure "Makefile" has an upper-case "M") to check if the Makefile was successfully generated. If configure worked properly, you should see:



If you just see:



then configure didn't work correctly, and we'll have to figure out why.
Lol i didn't even think about looking in the software center -Facepalm-

ANd i had no idea Linux was case sensitive that was probably my problem thank you :).

---

