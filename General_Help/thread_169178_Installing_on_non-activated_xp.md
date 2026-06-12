---
title: "Installing on non-activated xp"
date: 2006-05-02
forum: General Help
---

### Post by dmuha on 2006-05-02
Hi everyone, I have a laptop that is running windows xp, but the trial period is up, and the windows xp is not activated, so I am not able to run windows. I want to install ubuntu, I have downloaded the live cd and tried that, but when i restart my laptop with the cd in, it still does not load. I have tried the regular install cd, and that does not load either. no matter what cd i have in, it takes me to the xp screen that tells me i must activate first. i think i need to edit my bios to allow support for cd-boot, but i dont know how to. any help is appreciated. thanks.

denny

---

### Post by JanDM on 2006-05-02
Hi, I think you have to change the boot order in the BIOS. 

When you boot your pc, do you see a message like this: "press ... to enter setup"? Press that key, and try to find an option like "boot device priority". Make sure your cd-drive is listed first, and save settings.

---

### Post by Selmi on 2006-05-02
i don't know laptops/notebooks, but on ordinary computer press del while booting to get to the bios and then usually in the first menu item there is possibility to define boot device order. for installing you should set first device to cd and second to harddisc

---

### Post by Teroedni on 2006-05-02
edit 
Its already been answered

---

### Post by dmuha on 2006-05-02
[QUOTE=JanDM]Hi, I think you have to change the boot order in the BIOS. 

When you boot your pc, do you see a message like this: "press ... to enter setup"? Press that key, and try to find an option like "boot device priority". Make sure your cd-drive is listed first, and save settings.[/QUOTE]

i have already goen into the setup (F2), and changed the CD Drive to be at the top of the boot device priority. still no luck...

---

### Post by JanDM on 2006-05-02
[QUOTE=dmuha]i have already goen into the setup (F2), and changed the CD Drive to be at the top of the boot device priority. still no luck...[/QUOTE]
How did you burn the downloaded iso file? When you browse the cd in windows, you see more than one, big file?

---

### Post by dmuha on 2006-05-02
[QUOTE=JanDM]How did you burn the downloaded iso file? When you browse the cd in windows, you see more than one, big file?[/QUOTE]

i tried two ways. first i burnt the iso file onto a cd. the i extracted the iso file on my computer, and burnt all of those files into the cd. neither worked. thirdly i tried the live cd, and that did not work either. although i was at least able to run the start.exe file, but all that told me to do was restart my computer with the cd in it.

---

### Post by JanDM on 2006-05-02
Okay, when you do it that way your cd isn't bootable.

What program do you use for cd-burning? 
In Nero there's an option like "write disc-image".

You can try to download a demo from [www.nero.com](www.nero.com).

---

### Post by dmuha on 2006-05-02
at this point i am willing to format the drive, but i do not have a floppy disk to create a boot disk. i have also been able to access windows by using safe mode and logging in as the admin....

---

### Post by Selmi on 2006-05-02
too late, it was answered

---

### Post by dmuha on 2006-05-02
well, i used nero.... should i burn the whole iso onto the cd? or should i extract the files into a seperate folder and burn them?

---

### Post by JanDM on 2006-05-02
[QUOTE=dmuha]well, i used nero.... should i burn the whole iso onto the cd? or should i extract the files into a seperate folder and burn them?[/QUOTE]
[this](http://help.ubuntu.com/starterguide/C/ch01.html#id2473365) will help, I think.

---

### Post by dmuha on 2006-05-02
okay.. so i followed those instructions, burnt the iso to a cd. and it worked :) i feel a little bit like an idiot.. so it is installing right now, i'm sure i'll find some other problems soon haha. 

thanks a ton for your help! i appreciate it.

denny

---

### Post by jimbob on 2007-03-03
Hey, where are the moderators ??
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

