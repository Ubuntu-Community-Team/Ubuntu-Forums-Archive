---
title: "New to Ubuntu/ubuntu 10.04"
date: 2010-06-22
forum: General Help
---

### Post by georgy70 on 2010-06-22
HI, I am fairly new to Ubuntu so please be gentle, I have my blonde moments, pardon the pun.

I had ubuntu 9.04 and upgraded to 10.04.  I downloaded directly to my computer and did not do a live cd. my hard drive looks like it is now on its way out.  It is quite a number of years old (at least 4) and my son tells me that is a very good long life for a hard drive.  I won't argue with a guy who grew up in the technological age. lol

Ok so my questions are as follows:

1.
how do I create a live cd with what I have on my hard drive so that I do not loose anything that i have on there? (i have it all set up as I would like it with all the stuff i downloaded from the software centre like skype etc)
2.
Can I just drag and drop or cut and paste the ubuntu onto the new drive? and if so would it work as if I installed it directly to there if i did it this way?

I have two hard drives in my computer, one only has the the ubuntu and its programs etc on it and the other hard drive has all my files on it. (this is they way the boy trained me up in the event the drive died -always looking out for his mum lol)

I am not too computer savvy so if you guys could possibly advise in lamen terms, or rather in advise as if you were talking to a really silly person.

thanks in advance.

Georgy

---

### Post by dcstar on 2010-06-22
> **georgy70 said:**
> 
.........
2.
Can I just drag and drop or cut and paste the ubuntu onto the new drive? and if so would it work as if I installed it directly to there if i did it this way?



**gparted** will allow you to "Cut and Paste" an existing partition onto another hard drive, so you can basically copy the whole existing setup to new hardware quite easily.

Do a forum or web search for detailed instructions.

---

### Post by georgy70 on 2010-06-22
> **dcstar said:**
> **gparted** will allow you to "Cut and Paste" an existing partition onto another hard drive, so you can basically copy the whole existing setup to new hardware quite easily.

Do a forum or web search for detailed instructions.


Thankyou so much for that, I shall give it a go and let you know how I went.  Have to wait a little while cause I have to get the hard drive and all the other bits and pieces on the list my boy has given me.

Georgy

---

### Post by warfacegod on 2010-06-22
I would suggest running some tests on the drive. The Disk Utility that comes with 10.04 has been known to throw false positives. Try gsmartcontrol.

Go to: Applications> Accessories> Terminal:

```
sudo apt-get install gsmartcontrol
```

Your password will appear blank, just type it in anyway and hit Enter.

Use gsmart's Extended Test.

---

### Post by georgy70 on 2010-06-22
> **warfacegod said:**
> I would suggest running some tests on the drive. The Disk Utility that comes with 10.04 has been known to throw false positives. Try gsmartcontrol.

Go to: Applications> Accessories> Terminal:

```
sudo apt-get install gsmartcontrol
```Your password will appear blank, just type it in anyway and hit Enter.

Use gsmart's Extended Test.


Silly question but what does this do or what is this for

---

### Post by warfacegod on 2010-06-22
It's for testing the HDD. Your boy says you have a failing drive. I'm not doubting him but the test that comes default with 10.04 has often been known to be wrong. Gsmartcontrol will test for bad sectors on your HDD and it is allot more reliable.

---

### Post by georgy70 on 2010-06-22
> **warfacegod said:**
> It's for testing the HDD. Your boy says you have a failing drive. I'm not doubting him but the test that comes default with 10.04 has often been known to be wrong. Gsmartcontrol will test for bad sectors on your HDD and it is allot more reliable.


thanks for that shall try.

---

### Post by georgy70 on 2010-06-22
> **warfacegod said:**
> It's for testing the HDD. Your boy says you have a failing drive. I'm not doubting him but the test that comes default with 10.04 has often been known to be wrong. Gsmartcontrol will test for bad sectors on your HDD and it is allot more reliable.

did this and it says all hard drives passed.  The reason why we presumed the hard drive was on its way out was because it kept freezing, the screen was coming up with spots etc and for the last two days I have had to restart the machine every 10 to 15 minutes cause of it freezing.  As I said earlier, I am not that technologically savvy so trust those with more knowledge than myself.

ta

Georgy

---

### Post by howefield on 2010-06-22
> **georgy70 said:**
> and the other hard drive has all my files on it.

Just wondering, do you mean like a backup drive, ie,  does this mean you have at least two copies of any file that you would not want to lose ?

---

### Post by georgy70 on 2010-06-22
> **howefield said:**
> Just wondering, do you mean like a backup drive, ie,  does this mean you have at least two copies of any file that you would not want to lose ?

One drive has ubuntu and its programs on it and no files saved on it and any files like letters etc are saved onto the other hard drive.  So only one copy of files and that is on the (is it called the slave drive?)

---

### Post by warfacegod on 2010-06-22
> **georgy70 said:**
> did this and it says all hard drives passed.  The reason why we presumed the hard drive was on its way out was because it kept freezing, the screen was coming up with spots etc and for the last two days I have had to restart the machine every 10 to 15 minutes cause of it freezing.  As I said earlier, I am not that technologically savvy so trust those with more knowledge than myself.

ta

Georgy

Off hand, I'd say you need to clean the computer. It also sounds like you are having problems with your video driver. Possible RAM issues as well. To test RAM, select memtest+86 from your GRUB2 menu. I suggest doing this before going to bed or work or something. It can take hours.

---

### Post by georgy70 on 2010-06-22
> **warfacegod said:**
> Off hand, I'd say you need to clean the computer. It also sounds like you are having problems with your video driver. Possible RAM issues as well. To test RAM, select memtest+86 from your GRUB2 menu. I suggest doing this before going to bed or work or something. It can take hours.


Where do i find the grub2 menu?

---

### Post by howefield on 2010-06-22
> **georgy70 said:**
> One drive has ubuntu and its programs on it and no files saved on it and any files like letters etc are saved onto the other hard drive.  So only one copy of files...

Ok, once you are sorted you might want to think about that. Given the reason for having your files on a drive separate to the OS, is

> in the event the drive died

All drives can die or even become corrupted, including the one with your files on it, and usually do when you don't have a backup. ;-) The way you have set your disks up is better than using one drive, but not by much, it's still a disaster waiting to happen.

Just wanted to mention it, good luck with the rest.

---

### Post by howefield on 2010-06-22
> **georgy70 said:**
> Where do i find the grub2 menu?

Press the shift key quickly after starting the computer, you should then get a boot screen (black screen with white text) with several choices on it.

---

