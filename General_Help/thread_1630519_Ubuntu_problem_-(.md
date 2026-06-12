---
title: "Ubuntu problem :-(??"
date: 2010-11-25
forum: General Help
---

### Post by Windows 7 User on 2010-11-25
Ok I am an absolute beginner to Linux and ubuntu. So let's get started. Yesturday, I downloaded the ubuntu iso from the website. I installed onto my windows 7 thinkpad. It went all fine when I tried booting it into ubuntu for the first time. ( I dual booted my laptop) it loaded all sorts of weird white text. So I rebooted the laptop and selected windows 7. And deleted all od the Linux/ubuntu stuff. I installed it again. This time, the installation got interrupted I turned on my laptop again, it didn't boot into ubuntu or windows7. It went to some kind of command prompt thing And saying:

Grub rescue> no such partition

I don't know how to fix it. Please help me! I got lots of important documents in my laptop!!

Any help will be greatly appreciated

Thanks thanks thanks:-)

P.S sorry if I misspelled anything! I typed this on my iPhone

---

### Post by dino99 on 2010-11-25
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by WorMzy on 2010-11-25
Firstly: Don't panic. Your documents should be fine, assuming you partitioned the drive correctly. You're getting that grub prompt because of two reasons:
1) When you installed Ubuntu the first time, you also installed the grub bootloader -- because the windows bootloader cannot boot Linux operating systems, but grub can boot both Linux *and* Windows operating systems.
2) Since you deleted the Ubuntu partition, now grub can't find all of it's files, so it doesn't know where your OSs are.

Put the Ubuntu CD in the drive and boot from it again. Delete the failed Ubuntu installation's partition and start the installation again. Oh, and plug your laptop into a power source so that the install doesn't get interrupted again.

Once it's installed, grub will work again, and you'll be able to boot into either OS. If you get "all sorts of weird white text" again when booting Ubuntu, post it here, and we may be able to tell you what you need to do to get it working.

---

### Post by mendhak on 2010-11-25
Is it possible that the "weird white text" you're referring to is the GRUB loader? 

Did it look like this?
[http://www.howtogeek.com/wp-content/uploads/2007/09/image55.png](http://www.howtogeek.com/wp-content/uploads/2007/09/image55.png)

Did you look at the menu options there, and was Windows one of the options?  It's alright if it isn't there either, because you can boot into Ubuntu then go into your grub config file and add Windows there.

---

### Post by smeelkin on 2010-11-25
just for the record, that "weird white text" is totally normal. it just tells you what it is doing, its called a terminal. windows just shows a loading screen, without writing anything. next time you see it, just wait. its totally normal for it to do so. ;)

two tips:
1. don't panic.
dont do things too quickly, that will never work. ask the ubuntu forums first.
2. force shutdown. NO
using windows, you will often find a need to shut everything down by holding the power button. dont do that it linux. your files might be corrupted

welcome to ubuntu!

---

### Post by Windows 7 User on 2010-11-26
Ok thanks everybody I will try that later. 

Thanks:-)

---

### Post by Windows 7 User on 2010-11-26
Ok I tried to install and stuff but it dosent have the option "install alongside other windows' it just says format and use whe drive?_?

Any help will be appreciated thanks:-)

---

### Post by mastablasta on 2010-11-26
because it can't see windows since you destroyed the GRUB.
 
i think the easiest way would be to fix main boot record (using windows recovery disk), boto in windows and start all over agian (creating partition etc.). and it would also help if you checked one of the manual out there at least the instalation part.

---

### Post by tajiknomi on 2010-11-26
[SIZE=2]You can get your win-7 Boot Menu via win-7 ***repairing disk***,if you haven't Win-7 disk,you can download only Repairing-CD from here [/SIZE][http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

[SIZE=2]Then you will have to burn it on a CD and boot from repairing-Cd, Choose the ***Command-prompt*** in Repairing menu, and write their...


[B]bootrec.exe /fixboot

bootrec.exe /fixmbr[/B]

Exit......Reboot
 *If you are Lucky,you will get your win-7 boot option*;)[/SIZE]

---

### Post by Windows 7 User on 2010-11-26
Ok thanks everybody for your time i will try it NOW!

thanks :-)

---

### Post by Windows 7 User on 2010-11-27
it worked so how do I safely install ubuntu? (without any risks and stuff?) 

approx how much GB do I need?

(I got a 160GB HDD but I just have 141 usable and I used up 90GB of it so how much will ubuntu need?)

I need so save some for windows too

---

### Post by tajiknomi on 2010-11-27
> **Windows 7 User said:**
> it worked so how do I safely install ubuntu? (without any risks and stuff?) 

approx how much GB do I need?

(I got a 160GB HDD but I just have 141 usable and I used up 90GB of it so how much will ubuntu need?)

I need so save some for windows too

[SIZE=2]1) Safest is that you have to backup your Desire Partition

2)The size of your root partition will vary depending on what you install or plan to install. Check your distribution's documentation, and reserve enough space for a *maximum* installation, plus  *at least* 100MB more for ***temporary space*** and installation  of ***new software***. 

If you plan to download and try out lots of software,  leave more space.[/SIZE]

[SIZE=2]/HOME should be Given much space(I think)>Depend on the Music/Movies etc you have.......
Moreover...
*it is not necessary to create a separate partition for [SIZE=3]/home[/SIZE]. If you do not, it will reside on the root partition like everything else*[/SIZE].
[SIZE=2]
[/SIZE]

---

### Post by Spyderkid on 2010-11-27
I would say you would need no more than 10GB of hard drive

---

