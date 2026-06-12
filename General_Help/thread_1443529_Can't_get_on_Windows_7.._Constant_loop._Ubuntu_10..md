---
title: "Can't get on Windows 7.. Constant loop. Ubuntu 10.04 Beta 1"
date: 2010-03-31
forum: General Help
---

### Post by xxhopingtearsxx on 2010-03-31
Hello. I've tried Ubuntu several times, didn't really like it, but then decided to give it another go. Wubi didn't work on 10.04 Beta, so I decided to just use Grub. I've tried just installing it from the CD before but failed 2-3 times by accidentally removing my Windows partition, but a Youtube video helped guide me through it which I just skimmed through but thankfully no one and nothing was hurt. Well, I went on Ubuntu, played around and saw that on a 20 inch monitor that I just got, it's not so bad. I decided I wanted to go to Windows 7 and just.. you know, use it. I restarted my computer, saw grub, saw Windows 7 and clicked it. Funny, it took me to the Windows Boot Manager. It happened before (the Windows partition i removed last time was Vista but I also had Windows 7 RC). I thought, "Hey, this isn't so bad." clicked to go to Windows 7. Saw the splash screen, then it restarted. Tried again, did the same thing. So, I decided to use being locked out of Windows 7 as a chance to use Ubuntu and get to know it better. Well, I decided I want Windows 7 back, but I have no idea what to do. I have no repair discs because Toshiba decided that if they are going to make a $299 laptop with the best specs I've ever had in a computer, they need to remove something so they didn't give me any discs. I don't want to go and call Toshiba to do something.

I googled some help, and found that it was made for people who know what the hell they were talking about. So, I'm just asking here. I'm kind of a noob, so just talk to me like that. Please hurry. I've asked for help in the Ubuntu forums before and I know sometimes response is slow and fast, but there's always people eager to help, and I'm just hoping to God that it's fast.

---

### Post by xxhopingtearsxx on 2010-03-31
..BUMP.
I really need help.

---

### Post by nikoloz17 on 2010-03-31
if u don't wanna pay 250 $ for new Windows, than just download ISO from some torrent, burn it with ubuntu and install.

if you can't find ISO i can help you later:popcorn:

---

### Post by xxhopingtearsxx on 2010-03-31
That is really the least helpful post I have ever received.

---

### Post by Mark Phelps on 2010-03-31
10.04 is still in Beta testing and will be for a while yet.  

Beta-related questions should be posted to the proper forum: Development & Programming, Lucid Lynx Testing.

I will be asking the mods to move this thread there.  Look there for any further responses.

If you're asking about repairing Win7 -- perhaps you should asking in the right forums: sevenforums.com -- a Win7 forum.

---

### Post by xxhopingtearsxx on 2010-03-31
Oh, well.. No.. just forget it.
I'm just going to smash my computer with a hammer.
Thank you for your speedy response.

---

### Post by xxhopingtearsxx on 2010-04-01
Here's my solution:
If you have a Windows 7 disc.. if you don't, I'm sorry but that sucks.. Then use an Ubuntu Live CD to install Ubuntu completely over your harddrive.. I had to back up everything one by one on my SD and USB drives because my external harddrive cable was bitten by my cat who I still love very, very much <3.. Then install Windows 7. My drivers or drives (whatever it's called) wasn't showing in the Windows 7 installation before and it did after I did this solution.

---

### Post by Jeffster999 on 2010-04-01
When you get to the win boot manager try to get into safe mode (F8) if it starts in safe then you can manipulate the computer as needed. 

If you have probs still lemme know...Ubuntu I can't help so much but Windows I might be able to.

---

### Post by Jeffster999 on 2010-04-01
Sorry about the smiley there.. it is the F8 key

---

### Post by Mark Phelps on 2010-04-01
> **xxhopingtearsxx said:**
> Here's my solution:
If you have a Windows 7 disc.. if you don't, I'm sorry but that sucks...

IF you have Win7, a blank CD, and few minutes time ... you can easily make your OWN Win7 Repair CD by using the Backup function to create and burn your own Win7 Repair CD.

MS added this feature to Win7 to deal with the situation in Vista where OEMs wouldn't provide a Win7 boot CD, thus depriving folks of any way to repair Vista boot problems.

---

### Post by SnickerSnack on 2010-04-01
> **Mark Phelps said:**
> IF you have Win7, a blank CD, and few minutes time ... you can easily make your OWN Win7 Repair CD by using the Backup function to create and burn your own Win7 Repair CD.

MS added this feature to Win7 to deal with the situation in Vista where OEMs wouldn't provide a Win7 boot CD, thus depriving folks of any way to repair Vista boot problems.

I was going to recommend something like that, but from reading earlier posts, I suspect the recovery partition has been overwritten.  If it hasn't, then he can just use it, no need to make discs.

xxhopingtearsxx: If you have deleted the windows recovery partition, then I recommend calling toshiba and telling them that you need installation discs.  They will usually send them to you for free (maybe you'll have to pay shipping, though).  However, whether they send them (for free) or not may be determined by what reason you give for needing them.  I read an article somewhere detailing how Lenovo decides whether to send discs, along with a list of reasons that are likely to get you discs.  You should look for something similar on toshiba, or even just the article on lenovo if you can't find one about toshiba.

Also, I found this in 5 seconds of googling: [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/) ;););)  Maybe that will be enough.

It's my experience that windows is very finicky.  It does not like to be installed second, so what I've always had to do (iirc) is to install linux, then windows, then fix grub.  So, I don't think your situation is uncommon.

---

### Post by mullinsn2000 on 2010-04-01
Not sure if it will work with your Toshiba, but my Toshiba Satellite laptop w/ Vista it did.  Shut down the computer > Hold down the 0 (zero) key while pressing the power button > Let off the ) key > when the Toshiba screen appears press and hold 0 (zero) again > follow instructions.  This brought up a built in recovery program for me.  I was able to reinstall Vista (fresh install) without any discs.

---

### Post by SnickerSnack on 2010-04-02
> **mullinsn2000 said:**
> Not sure if it will work with your Toshiba, but my Toshiba Satellite laptop w/ Vista it did.  Shut down the computer > Hold down the 0 (zero) key while pressing the power button > Let off the ) key > when the Toshiba screen appears press and hold 0 (zero) again > follow instructions.  This brought up a built in recovery program for me.  I was able to reinstall Vista (fresh install) without any discs.

That is almost certainly the recovery partition I spoke of.

---

### Post by Mark Phelps on 2010-04-02
> **SnickerSnack said:**
> I was going to recommend something like that, but from reading earlier posts, I suspect the recovery partition has been overwritten.  If it hasn't, then he can just use it, no need to make discs.


Well ... yes and no.  

OEM-installed recovery disks/partitions all to often come with few or no options other than totally replacing the entire contents of the Vista/Win7 OS partition ...

Which is OK is you want to wipe out all your files, settings, apps, and data -- and start over completely from scratch.

The Repair CDs, however, will only allow you to repair a broken boot loader situation.  They do not overwrite and apps or user data.

So, if you just want access to Vista/WIN7 back -- the Repair CD is the way to go.

---

### Post by SnickerSnack on 2010-04-03
> **Mark Phelps said:**
> Well ... yes and no.  

OEM-installed recovery disks/partitions all to often come with few or no options other than totally replacing the entire contents of the Vista/Win7 OS partition ...

Which is OK is you want to wipe out all your files, settings, apps, and data -- and start over completely from scratch.

The Repair CDs, however, will only allow you to repair a broken boot loader situation.  They do not overwrite and apps or user data.

So, if you just want access to Vista/WIN7 back -- the Repair CD is the way to go.

Right.  I hadn't really given much thought to that distinction.

From his description it seemed like the bootloader might have been working fine, but windows itself had the problem.

---

