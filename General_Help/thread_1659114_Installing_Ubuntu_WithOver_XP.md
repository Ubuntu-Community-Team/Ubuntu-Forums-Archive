---
title: "Installing Ubuntu With/Over XP?"
date: 2011-01-03
forum: General Help
---

### Post by Sarge1533 on 2011-01-03
Greetings folks! I'm new to the site and have had an Ubuntu disk in my drawer for a couple of months now. As I continue, please keep in mind I am SOMEWHAT computer literate. I am currently running XP Pro and am sick of it. Here's my questions...
1) Can I install Ubuntu over XP or do I have to install it in a seperate partition?
2) If I just pop the disk in, will it do the majority of the work for me (and I won't have to bother you with more questions)?
3) Can I expect any conflicts with running other programs/software and hardware like printers or would I have to run them under XP?

I have an external HD and am running 1.5 gigs of RAM on a Dell Dim E520. Any answers or directions to other posts to answer these questions VERY much appreciated!!

Thanks ahead of time :)

---

### Post by mick222 on 2011-01-03
Just pop the disc in try the click install at the live desktop answer a few questions ,Where are you , what keyboard layout ,time , username,password , install alongside xp and your there . 

    You will have to set up printers  etc after install when running it is completely seperate from xp.
If you are comfortable with partitioning set up two partitions ext4 or ext3 and a swap of about 1gig / for ubuntu about 15 gb /home for home whatever you can afford,and /swap. About 30min tops.

    By the way what version of ubuntu do you have

---

### Post by Sarge1533 on 2011-01-03
> **mick222 said:**
> Just pop the disc in try the click install at the live desktop answer a few questions ,Where are you , what keyboard layout ,time , username,password , install alongside xp and your there . 

    You will have to set up printers  etc after install when running it is completely seperate from xp.
If you are comfortable with partitioning set up two partitions ext4 or ext3 and a swap of about 1gig / for ubuntu about 15 gb /home for home whatever you can afford,and /swap. About 30min tops.

    By the way what version of ubuntu do you have

Thanks for the answer Mick...I just opened the envelope the Ubuntu Disk came in and it say's "Version 9.10 Desktop Edition".

---

### Post by mick222 on 2011-01-03
10.10 is the latest but 10.04 is long term support you can either use the disk and after install upgrade or download from [http://www.ubuntu.com/](http://www.ubuntu.com/) 
   
If you want more help post your system specs or try the live cd remember linux is slow from a live cd.
   
 By the way the numbers refer to the date it was released.

---

### Post by Sarge1533 on 2011-01-03
MAYDAY!!! MAYDAY!!! I'm going down!!!

I ran the install disk in the try it before you install it mode. I liked it so decided to install it next to Windows. It took about 30 minutes to install but now won't run....here's what I get...

When I choose to boot the Ubuntu Generic OS, I get a flashing screen asking me for my password. When I try to enter the password an error message that say's a bunch of numbers and "Too Much Work For IRQ19" pops up!! Ubuntu will not load!! tried it 4 times before booting into Windows. I hope this wasn't a mistake!!!:evil:

---

### Post by rbishop on 2011-01-03
Have you only tried booting into Ubuntu normal? or have you tried the other options in your OS selection menu?  Other than Windows of course.

---

### Post by temporos on 2011-01-03
Hey, Sarge! ):P

Okay, first, are you sure caps lock wasn't activated when you tried? What about the number lock? It doesn't matter how experienced you are with computers; everyone gets caught by this every once in a while. :rolleyes:

Otherwise, what are the choices that GRUB gives you when you power up? If you have it installed alongside Windows, then it should show you *four* options:
[LIST=1]
[*]Windows XP Professional
[*]Generic Ubuntu OS
[*]Ubuntu 10.04.1 OS
[*]Ubuntu 10.04.1 OS Netbook Edition
[/LIST]
Yeah, I found this odd, too. If you choose "Generic," then you're basically asking to boot into a "safe" session where none of your system modifications will be saved at logout. The other two are essentially the same system session, but the UNE has a pretty GUI designed specifically for netbooks. On your Dimension, you'd probably do better with an "Ubuntu 10.04.1 OS" session (although, I do know a few individuals who use the UNE on their desktops).

Hope this helps! :)

---

### Post by Sarge1533 on 2011-01-03
> **temporos said:**
> Hey, Sarge! ):P

Okay, first, are you sure caps lock wasn't activated when you tried? What about the number lock? It doesn't matter how experienced you are with computers; everyone gets caught by this every once in a while. :rolleyes:

Otherwise, what are the choices that GRUB gives you when you power up? If you have it installed alongside Windows, then it should show you *four* options:
[LIST=1]
[*]Windows XP Professional
[*]Generic Ubuntu OS
[*]Ubuntu 10.04.1 OS
[*]Ubuntu 10.04.1 OS Netbook Edition
[/LIST]
Yeah, I found this odd, too. If you choose "Generic," then you're basically asking to boot into a "safe" session where none of your system modifications will be saved at logout. The other two are essentially the same system session, but the UNE has a pretty GUI designed specifically for netbooks. On your Dimension, you'd probably do better with an "Ubuntu 10.04.1 OS" session (although, I do know a few individuals who use the UNE on their desktops).

Hope this helps! :)

Remember, I have installed the 9.10 Version and was gonna update it to 10 when it was up and running. I tried to write down the options but the program chose Ubuntu for me too fast. The options I got were something like...
1)Ubuntu Generic
2) Ubuntu Recover (which I tried running and it still didn't work)
3) some kind of mem test
4) Windows XP

When it ask's me for the password, as soon as I try to enter it, it say's...
[40.615354]Serial8520: Too Much Work For IRQ19

Any press of any key automatically returns the same error message. I'm not liking this!! I had no auto caps lock...only num lock which is automatic in the boot sequence. I shut it off...still the same!!!

---

### Post by temporos on 2011-01-03
Whoops... Sorry 'bout that. I didn't notice when you said you were using Karmic. I just assumed Lucid. #-o Yeah, you got me. The only thing I can think of is that either the Windows boot loader is interfering somehow, or something's messed up in the BIOS? :-k

I'll defer to my more knowledgeable forumites.

---

### Post by mick222 on 2011-01-04
Are you connected to the internet via wireless if so your wireless drivers could be the problem try connecting via ethernet or try booting into recovery mode without networking.
 Personally I would download either 10.04 lucid or 10.10 maverick and install one of them.

---

### Post by Sarge1533 on 2011-01-04
> **mick222 said:**
> Are you connected to the internet via wireless if so your wireless drivers could be the problem try connecting via ethernet or try booting into recovery mode without networking.
 Personally I would download either 10.04 lucid or 10.10 maverick and install one of them.

OK Mick...Now, Can I just download Ver. 10 and install it OVER the version 9.10 I have installed or do I have to remove ver. 9.10 FIRST?? I am NOT running I-net via a wireless setup...I am direct into Ethernet. Very strange because the "try it first" version on the disk I ran to see if I liked it before I installed it ran fine!! I'm stumped:confused:!!

---

### Post by mick222 on 2011-01-04
I think we need to find out whats wrong first 
  If you can't boot into ubuntu at all, boot from live cd go to [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) download it and run it in terminal as in this post [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280) just follow the instructions. Or from windows go to control panel disk management  and post the graphical output.

---

