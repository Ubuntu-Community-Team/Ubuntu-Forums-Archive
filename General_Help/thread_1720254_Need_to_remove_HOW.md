---
title: "Need to remove HOW??"
date: 2011-04-03
forum: General Help
---

### Post by Smaug95swe on 2011-04-03
Ok so when i installed a program called Platinum arts sandbox from the Programcentral Something happend so My update bugged so i have to download a part patch but that just stops all the time Just goes from 1mb to ---- Kb/s and wont go up anymore... so why is that happening?

But i think i know another way i can fix this... By deleting the program (The terminal even mentions it when i try to update... but just stops) So my question is how do i find this folder/program so i can delete it and then how do i delete it :confused:

Sorry for writing so wierd... havent slept

---

### Post by simar.mohar on 2011-04-03
Hello
 
If you have installed the program using .deb file, then probably you can remove it using synaptics package manager. Its lying in your System>Adminstrator. Synaptics package manager handles the removal process automatically and makes sure that it happens cleanly.
 
Otherwise use the command line alternative using
 
```
 
$ sudo apt-get remove <package name>

```

---

### Post by Smaug95swe on 2011-04-03
When i tried it... it said i had to configue dpkg manually via sudo dpkg but i dont know where to go from here... So ok ive found where the folder is /Var/cache/platinumartssandox (called something like that)

all i need to do now is to Delete it but i cant... i have to do it via the terminal and ive forgot the code (Pretty new to linux)

---

### Post by Niocora on 2011-07-29
Jusy open a terminal and type:
sudo apt-get remove sandboxgamemaker

---

### Post by akoskm on 2011-07-29
> **Smaug95swe said:**
> When i tried it... it said i had to configue dpkg manually via sudo dpkg but i dont know where to go from here... So ok ive found where the folder is /Var/cache/platinumartssandox (called something like that)

all i need to do now is to Delete it but i cant... i have to do it via the terminal and ive forgot the code (Pretty new to linux)

If you are new to Linux you can forget about these methods of removing programs right now. Most of the installation data is tracked by the package manager and you can remove the whole by a singe command as explained above.
Of course there is also a GUI way to do it, though *synaptic* (but the terminal way is obviously easier).
I saw that you wrote /Var... Linux is case-sensitive, pay attention to this and always check twice what you typed in when you follow someone else terminal commands.
Oh, Hi in Linux world!

---

