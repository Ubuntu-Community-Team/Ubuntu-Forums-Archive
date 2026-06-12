---
title: "Wave out recording on UBUNTU....."
date: 2006-05-07
forum: General Help
---

### Post by maduranga on 2006-05-07
:-({|=  hello ppls....

 Are there any audio capturing program wich can record the audio play by the ubuntu? ( i mean, capturing the Wave out mix)

plz reply me soon..
Maduranga

---

### Post by Ramses de Norre on 2006-05-07
I think audacity can do that, but it doesn't work well on all systems.

---

### Post by maduranga on 2006-05-07
hii...
 thx 4 da reply, i install the Audacity. But when i start it i'm getting an error message :  
" There was an error initilizing the audio i/o layer. You will not be able to play or record audio.

Error : Host error"

 have any idea about that?? 

--Maduranga--

---

### Post by Ramses de Norre on 2006-05-07
```
sudo apt-get install aoss
aoss audacity &
```
Should work, you'll want to change the menu entry to aoss audacity too.

---

### Post by maduranga on 2006-05-07
maduranga@ubuntu:~$ sudo apt-get install aoss
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package aoss
maduranga@ubuntu:~$

i'm getting that error on the terminal when i gave the command. And, this is what i'm getting wehn i try to play audio.. plz. check that out..

---

