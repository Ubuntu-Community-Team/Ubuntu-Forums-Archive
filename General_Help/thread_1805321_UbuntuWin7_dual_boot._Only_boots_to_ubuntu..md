---
title: "Ubuntu/Win7 dual boot. Only boots to ubuntu."
date: 2011-07-15
forum: General Help
---

### Post by Jake_HT on 2011-07-15
Hi guys, new here. been doing a lot of reading since started using ubuntu. 
Now, for work, they have this crappy software that only works in internet explorer, and i couldn't get a working version in ubuntu, so now I am forced to dual boot. 

So I installed windows 7 on it's own partition (after ubuntu is installed). 

Of course, the MBR for windows ruins the linux booter, so you have to re-install GRUB to be able to boot into linux. 
I used this guide to save my linux install. 

[http://maketecheasier.com/restore-grub-2-as-the-main-bootloader/2010/05/05](http://maketecheasier.com/restore-grub-2-as-the-main-bootloader/2010/05/05)

Apparently that fix is supposed to make a menu where you can choose to boot ubuntu or windows..

BUT,

I have no menu. It boots right into ubuntu?? 

So how can I make the grub menu show up when I turn on my computer? I can't seem to get someone with this problem from googling. I know it's probably somewhere. 

Help? :D

---

### Post by Jake_HT on 2011-07-15
> **Jake_HT said:**
> Hi guys, new here. been doing a lot of reading since started using ubuntu. 
Now, for work, they have this crappy software that only works in internet explorer, and i couldn't get a working version in ubuntu, so now I am forced to dual boot. 

So I installed windows 7 on it's own partition (after ubuntu is installed). 

Of course, the MBR for windows ruins the linux booter, so you have to re-install GRUB to be able to boot into linux. 
I used this guide to save my linux install. 

[http://maketecheasier.com/restore-grub-2-as-the-main-bootloader/2010/05/05](http://maketecheasier.com/restore-grub-2-as-the-main-bootloader/2010/05/05)

Apparently that fix is supposed to make a menu where you can choose to boot ubuntu or windows..

BUT,

I have no menu. It boots right into ubuntu?? 

So how can I make the grub menu show up when I turn on my computer? I can't seem to get someone with this problem from googling. I know it's probably somewhere. 

Help? :D

Well, I feel stupid. I didn't do the last step on the guide, which was

[COLOR=#c20cb9]**sudo**[/COLOR] update-grub

So now it works. Hopefully this helps someone.

---

### Post by judedawson on 2011-07-15
'sudo' is the most important line in that command ;)

To see what else sudo can do, i would highly recommend searching this forum for a comprehensive overview. I have come across it before... I think it's in the archived forums...

I'm sure it'll be of great help and interest.

From,
Jude

---

### Post by Rubi1200 on 2011-07-16
Hi and welcome to the forums Jake_HT :)

Please mark this thread Solved using the Thread Tools near the top of the page.

By doing so, you share your valuable experiences with others who may find themselves in a similar situation.

Enjoy!

---

