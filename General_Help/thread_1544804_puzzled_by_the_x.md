---
title: "puzzled by the x"
date: 2010-08-03
forum: General Help
---

### Post by CROLMAC on 2010-08-03
hello, people of ubuntu. I have a problem in my eeepc 900, and have searched a bit and not found something similar.
   Here it is:I had a 700 surf and in it an 8gb sd card. I had a crash or two, and being a newbie I had left the card once in my machine while reinstalling an ubuntu distro; my husband recuperated what he could, and I ended up with 2 files to which I was deemed not having rights. ( they have an x on them and no permission) 
   My son broke the screen of that one, and I found this 900. I installed lucid lynx, no problem, and then inserted my 8gb sd card, and all of a sudden, found the x marked file in the home section (the extra 16gb ssd memory in this model).
   I would love either to be able to be able to open it as it contained music I like, or get rid of it. the other one disappeared.
    Also, I am puzzled as I couldn't find this file in my 8gb card, and at loss to how it got in my new netbook, although I do use occasionally 2 usb memories which I used to save some things from the old eeepc...please be gentle, I am still, after a year of fiddling with these computers,  quite a newbie.

---

### Post by Darkness Des on 2010-08-03
Press Alt+F2. In the box that pops up, type in 
```
gksudo nautilus
```
and enter your password. Browse to wherever the file is stored. Right click it, go into properties, and change the permissions so that you can access it. Then close the file browser.

---

### Post by CROLMAC on 2010-08-03
thank you, the solution was simple,and now I noticed something which my teensy brain probably couldn't process at the time: is there a file which is normal to ubuntu but is called lost+found? Maybe I was wrong to try take it out? it was empty when I managed to get into it and I couldn't send it to trash,it just went elsewhere (to the file system) although I can open it now. Sorry, said I was very newbie

---

### Post by drpjkurian on 2010-08-03
Ubuntu distro normally have a folder named lost & found

---

### Post by CROLMAC on 2010-08-03
what is it for? it was empty. Did I damage anything? I just booted, everything seems ok...it was on the 16gb extra memory, the other one on the 4gb ssd is still there..

---

### Post by WorMzy on 2010-08-03
This explains what lost+found is, and when it's used: [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

---

### Post by CROLMAC on 2010-08-04
thanks a lot, I really thank you for your patience, hope I'll learn a little quicker next time . Take care

---

