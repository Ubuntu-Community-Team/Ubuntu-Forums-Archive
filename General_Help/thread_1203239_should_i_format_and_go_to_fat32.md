---
title: "should i format and go to fat32"
date: 2009-07-03
forum: General Help
---

### Post by starcraftmaster on 2009-07-03
hey guys
i got two hard drives
one drive with windows ME
and the other drive with Ubuntu 9.04

but windows me cant read the ext3 file system
so am thinking of formatting the ubuntu drive
and then reinstalling ubuntu in fat32

but i hear people saying thats not recommend
so is it alright if i just use fat32 for ubuntu ?

also if i do format in fat 32
do i have to format the swap in fat32 or ext3?

---

### Post by Idefix82 on 2009-07-03
Don't do it. Ext3 is a much better file system, it's more secure, it doesn't need to be defragmented and so on.

I would instead recommend you to boot into Linux and move data to the Windows partition whenever you need to share data.

There is a [Windows driver ]("http://www.fs-driver.org/")to read ext3 but Win ME is not mentioned on the compatibility list. To be honest, Windows ME is old and crap even by Microsoft standards. I'd venture to say that it will break down on you or will not satisfy your needs in a not too distant future. It would be a pity to then be stuck with a fat32 install of Linux.

---

### Post by Tclarkie on 2009-07-03
how big is the hard drive:guitar:

---

### Post by starcraftmaster on 2009-07-03
nah windows me is petty good
and i been using it for years

the windows me drive is 20gb
the ubuntu drive is 20 gb

i was woulding if i could parition the ubuntu hard drive so theirs 5 gb for ubuntu and then the other 15 gb formated in fat32 and uesd for space(whats the lowest disk space for ubuntu i should go ?)
is that a better idea?

---

### Post by Idefix82 on 2009-07-03
> **starcraftmaster said:**
> 
i was woulding if i could parition the ubuntu hard drive so theirs 5 gb for ubuntu and then the other 15 gb formated in fat32 and uesd for space(whats the lowest disk space for ubuntu i should go ?)
is that a better idea?

Yeah, that sounds like a better idea. 5GB will be enough if you don't have any large programs. Do more like 8 and 12 if you want to play safe.

---

### Post by starcraftmaster on 2009-07-03
well then can you tell me how i would do that ?
would i use a partition manager from windows or ubuntu
or format and reinstall ubuntu and tell it to only use 5gb space?
(if i have to reformat can you tell me how i can get my updates so i don't have to download them again after i reformat)

---

### Post by firemoth on 2009-07-03
Ok bud first off....Windows ME?!  How can you even connect to the internet without malware automatically installing itself?  Windows ME probably beats Vista in the crappiness factor, but at least Vista is more secure.  You do know it's not even supported anymore....you do know that it's very easy to get XP even if you don't wanna pay for it?  You do know that any reasonable person would run Windows 98 or even 95 before running ME, right?  Nothing personal, but I'm telling you this because I feel obligated to give someone crap for using Windows ME for their own good.

Ok, that aside...


[LIST]
[*]Linux uses ext3, and a Linux swap partition is simply Linux-swap formatted
[*]Please don't install Linux on a FAT32 partition (is that even possible?)
[*]Leave at least 8 GB (in my opinion) for your ubuntu, and format the other 12 GB or whatever as FAT32 so you can share that partition between OS's
[/LIST]
You don't have to reformat and reinstall..you can boot from ubuntu live-cd and use the partition editor thats included.  Simply select the partition and click resize.

---

### Post by HermanAB on 2009-07-03
Howdy,

Linux cannot install and run on FAT32.

FAT should not be lightly discarded.  It should be thrown - with great force.

---

### Post by starcraftmaster on 2009-07-03
> **firemoth said:**
> Ok bud first off....Windows ME?!  How can you even connect to the internet without malware automatically installing itself?  Windows ME probably beats Vista in the crappiness factor, but at least Vista is more secure.  You do know it's not even supported anymore....you do know that it's very easy to get XP even if you don't wanna pay for it?  You do know that any reasonable person would run Windows 98 or even 95 before running ME, right?  Nothing personal, but I'm telling you this because I feel obligated to give someone crap for using Windows ME for their own good.

Ok, that aside...


[LIST]
[*]Linux uses ext3, and a Linux swap partition is simply Linux-swap formatted
[*]Please don't install Linux on a FAT32 partition (is that even possible?)
[*]Leave at least 8 GB (in my opinion) for your ubuntu, and format the other 12 GB or whatever as FAT32 so you can share that partition between OS's
[/LIST]
You don't have to reformat and reinstall..you can boot from ubuntu live-cd and use the partition editor thats included.  Simply select the partition and click resize.


windows me is a fine os 
when it first came out people did not have the right drivers for it which made it not work fully right

and ubuntu CAN be installed on FAT32
it has the option for it i think
some one correct me if am wrong

---

