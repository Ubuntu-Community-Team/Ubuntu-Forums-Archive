---
title: "help with rars"
date: 2010-01-24
forum: General Help
---

### Post by tbird79 on 2010-01-24
Ok, sorry for the insanely noobish question here, and also sorry if I have posted this in the wrong section. I just installed Ubuntu for the second time, first time was like 2 years ago and my pc was an oddball and some stuff was just not supported properly. Anyways..

I've got the latest build of Ubuntu installed, everything is working fine, just one problem.

I have many, many, many files that are archived in multiple .rar's. Like .r01, .r02, etc... I have them all copied over to the harddrive, but cannot extract what is in them. Also, I have some of these .rar's archived in a single .rar because of windows being stupid and not letting me copy them to my external drive as the names of them were too long for windows to handle. Those .rar's will extract a couple of the .r01, etc.. files, but not all of them. 

I don't understand what is going on. Please help this utter noob!

---

### Post by warfacegod on 2010-01-24
Go to: System> Admin.> Synaptic search and install unrar and unzip. That should help get them open at least.

---

### Post by Leppie on 2010-01-24
do they actually open properly in windows?

---

### Post by lukeiamyourfather on 2010-01-24
If sections of the archive sequence are missing then you're out of luck. However if they are a complete sequence you should be able to extract them with unrar in Linux. Cheers!

---

### Post by tbird79 on 2010-01-24
OK! THANK YOU! I had already installed unrar-free through the terminal, but I see in the synaptic package manager that it can't handle some .rar types. The standard non-free version worked though! Awesome! 

Does it work like it does on Windows, where, after the trial program, you can still use it but it just nags you with a pop up, or do you have to pay? As this is an essential program for me, I wont' mind paying for it if I have to.

Thanks again! 

BTW, this Ubuntu is incredibly awesome! I just came from Vista, and WHAT A DIFFERENCE!

---

### Post by warfacegod on 2010-01-24
> **tbird79 said:**
> OK! THANK YOU! I had already installed unrar-free through the terminal, but I see in the synaptic package manager that it can't handle some .rar types. The standard non-free version worked though! Awesome! 

Does it work like it does on Windows, where, after the trial program, you can still use it but it just nags you with a pop up, or do you have to pay? As this is an essential program for me, I wont' mind paying for it if I have to.

Thanks again! 

BTW, this Ubuntu is incredibly awesome! I just came from Vista, and WHAT A DIFFERENCE!

Nope, no nagging, no paying (unless you want to donate), you'll probably forget you installed by next week.

---

### Post by sisco311 on 2010-01-24
> **tbird79 said:**
> 
Does it work like it does on Windows, where, after the trial program, you can still use it but it just nags you with a pop up, or do you have to pay? As this is an essential program for me, I wont' mind paying for it if I have to.


unrar-nonfree is [free as in beer]("http://en.wikipedia.org/wiki/Gratis_versus_Libre"). :)

[file:///usr/share/doc/unrar/copyright]("file:///usr/share/doc/unrar/copyright")

---

### Post by Uncle Spellbinder on 2010-01-24
Various compression/extraction and encoding/decoding utilities...
```
sudo apt-get install unace rar unrar zip unzip p7zip-full p7zip-rar sharutils aish uudeview mpack lha arj cabextract file-roller libuu0
```

---

### Post by Ordes on 2010-01-24
unrar multiple files:

$ unrar x file.rar   (the first in list of x.01 x.02)

$ unrar x -e file.rar   >> -e extract to current directory


might need to install unrar...

---

