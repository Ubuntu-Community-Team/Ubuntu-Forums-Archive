---
title: "Installing software (matlab)"
date: 2009-07-10
forum: General Help
---

### Post by maygoo on 2009-07-10
I'm trying to install matlab although the forums out their are good I'm not as advanced.
I can get to the correct directory but when I try to use an installing command I get stuck,
the file that I need to load has no extension and when I try things such as ./configure make or make install it doesn't work (I suspect all those command need to work together)
If anyone could give me a hint that would be awsome.

---

### Post by michy99 on 2009-07-10
Have you tried the instructions found here?

[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

What have you done so far and where are you stuck at?

---

### Post by maygoo on 2009-07-13
no I hadn't thanks :)

---

### Post by maygoo on 2009-07-13
well, I switch users in the terminal to be logged in as root(I'm not sure if I'm using the correct lingo), I can get to the directory that my install file is in (folder I copied the files in or cdrom), then when I try any other instaling commands (make ) I get errors, no target fle specified, I think I'm missing something.... not I'm very new to ubuntu :), I have tried other stuff and get permission denied erors as well, 
thank you for your input.

---

### Post by carml on 2009-07-13
Maybe you need the build-essential package,you need to be connected to internet then go to Applications->Accessories->Terminal and type ```
sudo apt-get install build-essential 
``` then type your password,don't worry if you don't see it,that's a securty feature.
If you need more help just post here and someone will answer you.

---

### Post by maygoo on 2009-07-13
actually I had already done that,but I somehow managed to get futher because of the math works link you sent me. I have encountered another problem, my computer processor is missing SSE2 instruction (I'm doing this on a pentium 3). I might be geting my hands on a  pentium 4 in the very near future until then I am going to try and get around thi problem and/or try to install lab windows, another programming software :)
this one has tarballs how exciting, thanks for your help.

---

### Post by maygoo on 2009-07-13
by the way just to let you know and anyone else who reads this thread here are the problem I was having, although I don't know why....
~/ was not recongnizing /home/Username

---

### Post by maygoo on 2009-07-14
New problem!!!!

trap: ###: SIGINT: bad trap, I'm getting a lot of these while trying to install LabView, 
Does anyone know what they mean?

---

