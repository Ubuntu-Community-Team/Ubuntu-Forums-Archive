---
title: "Installing new hard drive in Ubuntu"
date: 2010-10-01
forum: General Help
---

### Post by blackbird3216 on 2010-10-01
Hi. I was recycling an old computer of mine (more than 12yrs old), and I took out its 20gb hard drive (its so small! Can't believe you can buy 1TB hard drives for $80 nowadays). I thought it would be a great idea to use it in order to backup my documents/photos/music/etc. (this might actually be a difficult task, because my photos are in RAW format, and my music is in FLAC. I will probably need to buy a larger HD). 

In any case, I have never had more than one hard drive in any of my computers. I don't know how to install it(sure, its a quick Google search, but some advice couldn't hurt), and I especially don't know the process of adding it into Ubuntu. I have not looked at the HD for more than 10yrs, so for all I can tell, it might have serious nostalgic value, or even a virus or two. Regardless, I don't think its worth looking at. It needs to be formated. However, I have some concerns. 

1. How do I format it without having it mount? (It might have viruses, trojans, etc. sure, its Linux, but I don't want it on my computer). 
2. How do I add it to the operating system so that it does not continue to popup everytime I login (a la flash drives. Whenever, I plug in a flash drive, it pops up. I don't want this to happen with my backup HD)
3. What file system should I format it to? For my main HD, I am using EXT4, on a Karmic system. 
4. I need a simple method in order to automatically backup my files. I am thinking about "Back in time", but as I've said, I have never done ANY backup whatsoever. It is time to start. If I use "Back in time", then if I lose a file in my main HD, how do I retrieve it? Do I simply go Places---computer---Filesystem2(or whatever it is in Ubuntu) and grab it there, or do I need to use the BIT utility? 

Thank you for answering all of my questions. I am very grateful.

---

### Post by cj.surrusco on 2010-10-01
I really wouldn't advise using a 12 year old hard drive as a backup, chances are that drive is nearing the end of it's life, and you could lose that data very easily.

If you're sure that you want to use it, just pop it into your PC. Obviously, plug in the molex power and the IDE cable. It won't automatically mount in Ubuntu, plus you wouldn't have to worry about viruses. Windows viruses won't run in a Linux environment. Then you can use a disk manager to format it. I would use ext3 or ext4, they are both up-to-date and pretty good. 

As far as backing up, you have plenty of options. Using backintime is probably the easiest solution, and you would be able to set it up however you want it.

---

### Post by Goolie on 2010-10-02
Just pop it in like mentioned above.

Filesystem: ext3, or ext4, you're using solely Ubuntu I assume.

You wno't have to worry about cleaning it out before installing it, I don't think anything will be jumping out like ticks to your main HDD, but you can boot into a specific program that can format the drive for you from outside your OS if you prefer that route.

I agree, a 12 year old HDD is way overdue for it's end of life.  I guess it depends on how much use it has, too little use, and she'll have trouble starting like a car, too much use, well, twelve years on a car without a tune-up is pretty bad, eh?  Sorry, cars just make sense in this scenario, best way I could think of it! Lol!

You could just set your home folder to that HDD, or you could just every now and then drag + drop your specific documents onto it.

I don't really back up my Ubuntu installation.  I just drag and drop any important MUST have documents on my external hard drive.  Resume, videos, pictures, and music.

---

### Post by dcstar on 2010-10-02
> **cj.surrusco said:**
> I really wouldn't advise using a 12 year old hard drive as a backup, chances are that drive is nearing the end of it's life, and you could lose that data very easily.
........

Use it solely for Swap, that would be the only thing I'd risk on worn-out old hardware like that.

---

### Post by blackbird3216 on 2010-10-09
Well, the real problem with using a new hard drive for the computer is that the computer is pretty old on its own. The computer is almost 3 years old, but I find that it runs fast enough on linux so that I can delay upgrading for another year or two. The computer has a 320gb hd, which is pretty small for today's standards. 

It would be pretty ridiculous to buy a 1tb hard drive for "backup", since it would be bigger than the main. I would love if I could get a 120gb or so for backup, and I bet those don't cost anything. 

I was thinking of one solution. I have an even older PC that runs on Windows XP. That box is nearly 7yrs old. It has a 120gb hard drive, but it only uses 10gb on it. I was thinking, maybe I could just reinstall windows on that old 20gb HD, then format the 120gb to use as backup. I don't know how smooth this will be though.

---

### Post by blackbird3216 on 2010-10-11
Anyone?

---

