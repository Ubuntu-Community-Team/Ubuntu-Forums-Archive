---
title: "help..."
date: 2009-12-23
forum: General Help
---

### Post by shawnbe on 2009-12-23
so i download ubuntu now i cant delete it its there when i try to start up but i cant get it to work and it dosnt show up as a partition and i just want to get rid of it becuse it takes up a lot of room :sad:

---

### Post by lisati on 2009-12-23
Some clarification please.

Did you put it on CD? Did you install Ubuntu? If so, how?

---

### Post by houseworkshy on 2009-12-23
I'm guessing that what is on the rest of your system is windows.  Windows can't see file systems other than ntfs and fats.  Linux can.  So before despairing try going into linux and look the other way around.  You'll find that you can copy and paste etc. The other part of your system will show up as a media disc of whatever size, click on it and, after putting your linux password in it will mount and you can access it.  If your work is documents, pics, vids or sounds you are probably better of sticking with linux for a while.
If you do want to get rid of it then booting windows from it's cd and chooseing the  repair function should do it.  Once done you'd go into the disc management section, from the control panel and extend your partition ( windows will regard the area used by linux as unformated space ).
There is also a way of shrinking and expanding partitions on which I don't feel quaified enough to give good advice.  Maybe try starting a more descriptive thread than "help" would attract people with the nessesary expertese.  Something like "How do I shrink a partition on a windows/ubuntu duel boot" or "How do I remove Ubuntu from a duel boot with windows?" for example.
By the way I'm using an older version of Ubuntu ( 8.04 ) the latest ( 9.10) uses differant boot loader so, if you are on 9.10, it would be a good idea to wait before doing what I suggest as the situation may have changed. 
Good luck with whatever you choose to do.

---

### Post by shawnbe on 2009-12-23
i went to wubi not really knowing what to do and didn't put it on a disk and i want to get rid of it

---

### Post by lisati on 2009-12-23
> **shawnbe said:**
> i went to wubi not really know what to do and didn't put it on a disk and i want to is get rid of it

OK. If you used Wubi to install Ubuntu, you can remove Ubuntu from the Windows->Control Panel->Add/Remove Programs.

---

### Post by houseworkshy on 2009-12-23
Good point from lisati.  There is also the install inside windows, sorry I forgot that.  If you did it like that what I put above doesn't apply.

---

### Post by shawnbe on 2009-12-23
i cant find it in program files and all i want is to install dragon age but its taking all the room

---

### Post by synapsys on 2009-12-23
You're not listening.

> **lisati said:**
> OK. If you used Wubi to install Ubuntu, you can remove Ubuntu from the Windows->Control Panel->Add/Remove Programs.

---

### Post by shawnbe on 2009-12-23
i just wantto get rid of it i will do any thing just tell me what you want me to do and ill do it

---

### Post by audiomick on 2009-12-23
First of all, learn to use punctuation.
Secondly, go back and read post #5 again.

---

### Post by shawnbe on 2009-12-23
its not there

---

### Post by synapsys on 2009-12-23
Maybe this will help, scroll down to the** "****[SIZE=1]How do I uninstall it?"[/SIZE]**  section.

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by shawnbe on 2009-12-23
its not in the program files deleter ](*,) ](*,) ](*,)

---

### Post by houseworkshy on 2009-12-24
Sometimes I find my own concentration can be spoiled by frustration.  So just in case ; the "add remove" people are refering to is the one in windows not ubuntu.  If you got that and did use wubi ( a description of your boot up screen where you are given the choise between the two systems would confirm it ) I'd suggest posting a new thread such as "wubi install of ubuntu does not show up in add remove programs" would probably attract good advice as it's be a serious issue.

I hope you sort it "dragon age" looks very pretty.  If it isn't sorted soon, bearing in mind that it's Christmass and most forum members will be doing other things than being online, In the short term a search for "+linux  +games +ubuntu +free" will find a lot.  I like Vega Strike ( and it's various mods), nexius, tremulous, UFO AI, globulation, There are many of them. Not what you want I know but better than nothing in the meantime.  If you posted a thread with the title suggested it won't be long before someone sees it and posts a fix anyway.

---

### Post by shawnbe on 2009-12-24
i think im going to give up. you've all been a great help. i just cant get rid of it. again thanks for the help:KS
 
bye:guitar:

---

### Post by 3rdalbum on 2009-12-24
> **shawnbe said:**
> i think im going to give up. you've all been a great help. i just cant get rid of it. again thanks for the help:KS
 
bye:guitar:

Now: Note that when you remove Ubuntu, the bootloader screen will remain (it will show Windows and Ubuntu, even though Ubuntu doesn't exist anymore). This is normal. It can be changed, but Ubuntu will not be present on your hard disk anymore.

If you know that the Ubuntu file is still there, then just get rid of it. Put it in the Recycle Bin.

---

### Post by wirate on 2009-12-24
when you ran wubi, it asked you the partition you wanted to install ubuntu in. go to that partition, look for the folder named ubuntu. In there, there is an "uninstall" file. run it. even if this doesnt work, delete the folder straight away.

To remove ubuntu from startup, put in your windows installation cd, boot from it and run "fixmbr".
Hope this helps

---

