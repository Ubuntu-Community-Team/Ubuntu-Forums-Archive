---
title: "Dual Boot - WIN 7 and Linux using bcdedit"
date: 2010-11-11
forum: General Help
---

### Post by vikrang on 2010-11-11
I want to add Linux partition to WIN 7 boot menu..What I exactly want is that the welcome screen of Ubuntu should directly appear on selection of the item in the menu just like "Starting Windows..."...I can do it with EasyBCD but I want to use the native Win utils from command prompt..The startup is not smooth with EasyBCD there are verbose messages appearing like ("finding partition (hd0,0),,,etc before the ubuntu screen comes up...it is just a cosmetic change I want and absolutely there is no loss of functionality currently...I do not want the GRUB at MBR as I keep tampering with distros (uninstall-reinstall etc ) and I do not want to screw up WiN.
Should I use utils like GAG,Smart Boot manager , PLOP etc?
 
 
I did the following as suggested in many tutorials ( copy first 512 bytes of a partition and reference it to the Win menu)..But on selection a blank screen appears .
 
1. bcdedit /create /d "UBUNTU LUCID" /application boot sector
2.bcdedit /set {ID} device partition=c:
3.bcdedit /set {ID} /path \linux.bin ( This file I copied from Ubuntu after mounting C: (sda1) using dd if=/dev/sda3 of=/mnt/linux.bin bs=512 count=1 ..sda3 is Ubuntu partition (boot and root same part)
4.bcdedit /displayorder {ID} /addlast
5. bcdedit /timeout=15
 
**My doubt is to copy the first 512 bytes of a Linux partition should I log in from boot CD and do the operation or log into linux and as root do the above? **
 
I had WIN XP earlier and there is a fantastic utility called " Bootpart" which does the above easily by peeling 512 bytes and adding to boot.ini...It was fabulous and I got what I wanted..Sadly there is no version for Win Vista/7...
 
Dunno where I am going wrong

---

### Post by wilee-nilee on 2010-11-12
So why I must ask is just using grub2 a problem?

---

### Post by vikrang on 2010-11-12
Pl read my other query titled " GRUB2 as Master Boot Loader"...
 
[http://ubuntuforums.org/showthread.php?t=1619571](http://ubuntuforums.org/showthread.php?t=1619571)
 
I thought cramming too much into 1 post would be difficult for comprehension:(

---

### Post by wilee-nilee on 2010-11-12
> **vikrang said:**
> Pl **read my other query titled " GRUB2 as Master Boot Loader"...**
 
I thought cramming too much into 1 post would be difficult for comprehension:(

That is a fair ideal, but how about a link since **YOU** need the help.;)

---

### Post by vikrang on 2010-11-12
Done!! ..
 
Sorry....:) ...I am pretty new and so far have restricted only to writing plain text...So I have to Xplore how to add links/scrshots/attachment etc.....

---

### Post by wilee-nilee on 2010-11-12
I had read the other link before I read this one and just said to myself, this person is looking for a free tutorial on things you have to find out by just searching for the information, and trial and error. Thats what I have done anyway. 

Of course asking questions is good, and since this is such a large forum, you will probably get some answers but in the meantime check out this site I suspect all the answers are there. Look closely even though Ubuntu is mentioned scroll down and you will be amazed at the amount of info there.
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by vikrang on 2010-11-12
Thanks ....
 
I will go through the link...Looks like it has a lot of info...
 
In fact you can say I am plain lazy to search for things in google... 
 
If i ask Qns maybe I will get a readymade solution from an expert online!!
 
:P

---

### Post by wilee-nilee on 2010-11-12
> **vikrang said:**
> Thanks ....
 
I will go through the link...Looks like it has a lot of info...
 
In fact you can say I am plain lazy to search for things in google... 
 
If i ask Qns maybe I will get a readymade solution from an expert online!!
 
:P

Don't tell anybody I will deny saying it;) but from a pure psychological perspective just ask less questions, the first thread I just went yeah right. With less complexity and parsed out with different questions set at different times you will get more answers like flies to sugar water. Those of us who like to help are suckers for this method, or some are anyway, now once you have the attention of somebody go for the hard questions, there are lots of members that are amazingly knowledgeable that like to get people set up and understanding things, and will stick with it until you are set.

---

### Post by vikrang on 2010-11-12
Guess you have had a lot of beans ,No wonder they are hidden!!
 
Nice One:P 
 
Will learn the tricks of the trade

---

### Post by Computer Guru on 2010-11-13
> **vikrang said:**
> I want to add Linux partition to WIN 7 boot menu..What I exactly want is that the welcome screen of Ubuntu should directly appear on selection of the item in the menu just like "Starting Windows..."...I can do it with EasyBCD but I want to use the native Win utils from command prompt..The startup is not smooth with EasyBCD there are verbose messages appearing like ("finding partition (hd0,0),,,etc before the ubuntu screen comes up...it is just a cosmetic change I want and absolutely there is no loss of functionality currently...I do not want the GRUB at MBR as I keep tampering with distros (uninstall-reinstall etc ) and I do not want to screw up WiN.
Should I use utils like GAG,Smart Boot manager , PLOP etc?
 
 
I did the following as suggested in many tutorials ( copy first 512 bytes of a partition and reference it to the Win menu)..But on selection a blank screen appears .
 
1. bcdedit /create /d "UBUNTU LUCID" /application boot sector
2.bcdedit /set {ID} device partition=c:
3.bcdedit /set {ID} /path \linux.bin ( This file I copied from Ubuntu after mounting C: (sda1) using dd if=/dev/sda3 of=/mnt/linux.bin bs=512 count=1 ..sda3 is Ubuntu partition (boot and root same part)
4.bcdedit /displayorder {ID} /addlast
5. bcdedit /timeout=15
 
**My doubt is to copy the first 512 bytes of a Linux partition should I log in from boot CD and do the operation or log into linux and as root do the above? **
 
I had WIN XP earlier and there is a fantastic utility called " Bootpart" which does the above easily by peeling 512 bytes and adding to boot.ini...It was fabulous and I got what I wanted..Sadly there is no version for Win Vista/7...
 
Dunno where I am going wrong

This is what EasyBCD does automatically when you DON'T use the checkbox for "GRUB isn't installed to the MBR"

It's only when you use the checkbox that you get text on the screen.

---

### Post by vikrang on 2010-11-16
Thanks ..will try out what you have suggested

---

