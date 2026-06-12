---
title: "Ubuntu 9.10 Hangs when i open it !!!"
date: 2010-02-17
forum: General Help
---

### Post by JML13 on 2010-02-17
[LEFT][B][COLOR=Blue]Hey everbody !![/COLOR]
I want to try[COLOR=Red] Ubuntu 9.10[/COLOR] it's my first experience !!
I have a Dimension 5100 Dell with [COLOR=Red]Xp professional[/COLOR] and i have 2 Hard Disk
the first :C: 52 Go --> Xp
             [COLOR=Red]E:  100 Go ---> Where i intal it ubuntu 9.10[/COLOR]
and the second one where i keep my Data : D: 500 Go[/B]

[CENTER][IMG]http://img43.imageshack.us/img43/5918/sshot2u.jpg[/IMG]
[/CENTER]
 
[B]i do all the stuff  and make the swap partition and change the system file of E: to Ext 4 and instal Ubuntu 9.10 and everything goes well , but when i open Ubuntu, it [COLOR=Red]hangs [/COLOR]after about 3 minutes .. and i dont know why!! 
So please someone help me out !![/B]
[/LEFT]

---

### Post by mörgæs on 2010-02-18
How does the machine work, if you boot with a live CD?

---

### Post by woodmaster on 2010-02-18
what's your graphics card/driver?

---

### Post by JML13 on 2010-02-19
> **mörgæs said:**
> How does the machine work, if you boot with a live CD?

**same thing !!?**

> **woodmaster said:**
> what's your graphics card/driver?

**ATI Radeon X300 SE 128 MB HyperMemory**

---

### Post by JML13 on 2010-02-19
[CENTER][FONT=Courier New][SIZE=5][COLOR=Red]**Someone help me out please !! **
[/COLOR][/SIZE][/FONT][/CENTER]

---

### Post by JML13 on 2010-02-19
**Ubuntu 9.10 Hangs when i open it !!!** 			
 			 			 		   		 		 		[B][COLOR=Blue]Hey everbody !![/COLOR]
I want to try[COLOR=Red] Ubuntu 9.10[/COLOR] it's my first experience !!
I have a Dimension 5100 Dell with [COLOR=Red]Xp professional[/COLOR] and i have 2 Hard Disk
the first :C: 52 Go --> Xp
             [COLOR=Red]E:  100 Go ---> Where i intal it ubuntu 9.10[/COLOR]
and the second one where i keep my Data : D: 500 Go[/B]

[CENTER][IMG]http://img43.imageshack.us/img43/5918/sshot2u.jpg[/IMG]
[/CENTER]
 
[B]i do all the stuff and make the swap partition and change the system file of E: to Ext 4 and instal Ubuntu 9.10 and everything goes well , but when i open Ubuntu, it [COLOR=Red]hangs [/COLOR]after about 3 minutes .. and i dont know why!! 
So please someone help me out !![/B]

---

### Post by JML13 on 2010-02-19
**Ubuntu 9.10 Hangs when i open it !!!** 			
 			 			 		   		 		 		[B][COLOR=Blue]Hey everbody !![/COLOR]
I want to try[COLOR=Red] Ubuntu 9.10[/COLOR] it's my first experience !!
I have a Dimension 5100 Dell with [COLOR=Red]Xp professional[/COLOR] and i have 2 Hard Disk
the first :C: 52 Go --> Xp
             [COLOR=Red]E:  100 Go ---> Where i intal it ubuntu 9.10[/COLOR]
and the second one where i keep my Data : D: 500 Go[/B]

[CENTER][IMG]http://img43.imageshack.us/img43/5918/sshot2u.jpg[/IMG]
[/CENTER]
 
[B]i do all the stuff and make the swap partition and change the system file of E: to Ext 4 and instal Ubuntu 9.10 and everything goes well , but when i open Ubuntu, it [COLOR=Red]hangs [/COLOR]after about 3 minutes .. and i dont know why!! 
So please someone help me out !![/B]

---

### Post by nightwolf2k5 on 2010-02-19
Does it actually hang or does it display a blank screen?

---

### Post by mörgæs on 2010-02-19
If the live CD does not give a good result, I wouldn't bother installing. Have you tried other versions than 9.10?

---

### Post by mörgæs on 2010-02-19
- and by the way: Don't shout. It does not bring a solution closer.

---

### Post by mikewhatever on 2010-02-19
What do you mean by 'when I open Ubuntu'. Are you trying to open it like you would firefox, by clicking an icon?

---

### Post by cariboo on 2010-02-19
Please don't create multiple threads on the same subject. I have merged your three threads.

---

### Post by JML13 on 2010-02-20
> **nightwolf2k5 said:**
> Does it actually hang or does it display a blank screen?

it's hang !!!

> **cariboo907 said:**
> Please don't create multiple threads on the same subject. I have merged your three threads.
  i open it  when i choose betwen ubuntu and xp !!!

---

### Post by Silent Warrior on 2010-02-20
It would be good to have some log output, but that might be difficult, I suppose. But you could try pressing Escape while booting Ubuntu, and you should hopefully see a bunch of text scroll by. (Ideally, you should consider editing the boot-parameters through the boot-menu and remove any 'silent' or 'quiet' you find, preferably along with 'splash', but I don't feel confident enough to provide guidance on how to do that.)
When you get that output, look for 'Error:', 'WW', 'EE', 'FAIL', and be sure to report what it's trying to do when it actually hangs. If you've got some kind of Ubuntu-like graphics, at least the bootloader is working with the correct HDD.

I don't know if you installed it correctly, though. It could just be lost in translation, but it looks to me as if you MANUALLY formatted your target-drive, THEN opened the installer. The recommended way is, I think, doing any formatting through the installer (when possible - sometimes it isn't, but this doesn't seem to be the case for you). So: How exactly did you format?

Also, as mörgæs said, mind your netiquette. You don't need to make several topics, you don't need to bump it every fifteen minutes or whatever - this isn't IRC or instant messaging.

---

### Post by JML13 on 2010-02-20
> **Silent Warrior said:**
> It would be good to have some log output, but that might be difficult, I suppose. But you could try pressing Escape while booting Ubuntu, and you should hopefully see a bunch of text scroll by. (Ideally, you should consider editing the boot-parameters through the boot-menu and remove any 'silent' or 'quiet' you find, preferably along with 'splash', but I don't feel confident enough to provide guidance on how to do that.)
When you get that output, look for 'Error:', 'WW', 'EE', 'FAIL', and be sure to report what it's trying to do when it actually hangs. If you've got some kind of Ubuntu-like graphics, at least the bootloader is working with the correct HDD.

I don't know if you installed it correctly, though. It could just be lost in translation, but it looks to me as if you MANUALLY formatted your target-drive, THEN opened the installer. The recommended way is, I think, doing any formatting through the installer (when possible - sometimes it isn't, but this doesn't seem to be the case for you). So: How exactly did you format?

Also, as mörgæs said, mind your netiquette. You don't need to make several topics, you don't need to bump it every fifteen minutes or whatever - this isn't IRC or instant messaging.


[CENTER][FONT=Courier New][SIZE=3][COLOR=Blue][B][SIZE=3][COLOR=RoyalBlue]Thank you for your answer silent warrior, first of all i want to apologize about repeating my thread...
and for your question how did i format it!! before instaling Ubuntu the system file is NTFS and after that i format it with the ubuntu cd to the file system Ext4 !!
 i will try your first solution if not i will try Ubuntu 9.04 and i hope it will work!! thank you agian mate !! :D[/COLOR][/SIZE]
[/B][/COLOR][/SIZE][/FONT][/CENTER]

---

