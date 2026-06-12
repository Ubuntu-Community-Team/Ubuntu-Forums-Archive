---
title: "The easy way to securely erase data on old hard disc"
date: 2012-07-29
forum: General Help
---

### Post by satimis on 2012-07-29
Hi folks,

I have several 40G hard drives which I'm prepared to dump.  Before giving them to my friends what will be the easy way to securely erase all data on them.

I'm prepared performing following steps.

1)
attache the hard drives to a PC

2)
boot up the PC with a USB drive

3)
run:
$ fdisk -l | grep '^Disk'
$ fsck -f -y /dev/hdx1

x is the device number of the hard drive, such as a,b,c etc.

Can above steps permanently erase all data on the hard drive?


Just found;
Use an Ubuntu Live CD to Securely Wipe Your PC’s Hard Drive
[http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/](http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/)

Can it work?  TIA

B.R.
satimis

---

### Post by FatFrog on 2012-07-29
you could use Active@ KillDisk... it's bootable and wipes HDD's to DoD 5220.22-M standard... 

Also, it's free!

---

### Post by Stonecold1995 on 2012-07-29
Using fsck like that may erase the data, but not irrecoverably.  If you want secure deletion, use dedicated secure-erasing programs.  The program "Wipe" is most likely already installed on your system, so all you have to do is use it.  Assuming you are not booting *from* the drives (i.e. the drives are external drives and don't have an OS on them) you can clear them with the command "sudo wipe /dev/hdx".  The Wipe utility may take a very long time to clear drives, but it is very secure.  You could also use this with the -q flag to reduce the security slightly, but speed the process up.

If you don't want to use Wipe for some reason, you can also use the utility Shred.  To erase a drive with Shred, use "sudo shred /dev/hdx".

Another option is the "secure-delete" package (install with "sudo apt-get install secure-delete").  It installs several utilities, but the one you'll need is called srm.  To do that, use "sudo srm /dev/hdx".

If you are very serious about security, you could also use Nwipe, which is a fork of Dwipe (the program used by the famous [DBAN]("http://dban.org/") utility, which is another option you could use) to securely erase data.  I don't think Nwipe comes installed on Ubuntu, but you can use a live CD that has Nwipe (I think PartedMagic has it).  Nwipe is also extremely secure.  If you do choose to use DBAN or Nwipe, the most secure configuration is to use the Gutmann method with the ISAAC algorithm as the PRNG.  Nwipe took a little more than 100 hours for a 750 GB hard drive, so a 40 GB hard drive should be a lot quicker.

The quickest (but least secure) method to overwrite a whole hard drive would be to use DD.  You can either blank the hard drive with 0's using "sudo dd if=/dev/zero of=/dev/hdx" or with random data using "sudo dd if=/dev/urandom of=/dev/hdx".  Note that using DD is not very secure, although it will prevent casual recovery of data.

For more info you can look for things [here]("https://www.google.com/search?q=linux+securely+erase+whole+hard+drive").

**If you can't decide on which of these options to use, just do "sudo wipe /dev/hdx".**

---

### Post by satimis on 2012-07-29
> **FatFrog said:**
> you could use Active@ KillDisk... it's bootable and wipes HDD's to DoD 5220.22-M standard... 

Also, it's free!

Thanks.

Where can I download its Linux version?

B.R.
satimis

---

### Post by satimis on 2012-07-29
> **Stonecold1995 said:**
> Using fsck like that may erase the data, but not irrecoverably.  If you want secure deletion, use dedicated secure-erasing programs.  The program "Wipe" is most likely already installed on your system, so all you have to do is use it.  Assuming you are not booting *from* the drives (i.e. the drives are external drives and don't have an OS on them) you can clear them with the command "sudo wipe /dev/hdx".  The Wipe utility may take a very long time to clear drives, but it is very secure.  You could also use this with the -q flag to reduce the security slightly, but speed the process up.

If you don't want to use Wipe for some reason, you can also use the utility Shred.  To erase a drive with Shred, use "sudo shred /dev/hdx".

Another option is the "secure-delete" package (install with "sudo apt-get install secure-delete").  It installs several utilities, but the one you'll need is called srm.  To do that, use "sudo srm /dev/hdx".

If you are very serious about security, you could also use Nwipe, which is a fork of Dwipe (the program used by the famous [DBAN]("http://dban.org/") utility, which is another option you could use) to securely erase data.  I don't think Nwipe comes installed on Ubuntu, but you can use a live CD that has Nwipe (I think PartedMagic has it).  Nwipe is also extremely secure.  If you do choose to use DBAN or Nwipe, the most secure configuration is to use the Gutmann method with the ISAAC algorithm as the PRNG.  Nwipe took a little more than 100 hours for a 750 GB hard drive, so a 40 GB hard drive should be a lot quicker.

The quickest (but least secure) method to overwrite a whole hard drive would be to use DD.  You can either blank the hard drive with 0's using "sudo dd if=/dev/zero of=/dev/hdx" or with random data using "sudo dd if=/dev/urandom of=/dev/hdx".  Note that using DD is not very secure, although it will prevent casual recovery of data.

For more info you can look for things [here]("https://www.google.com/search?q=linux+securely+erase+whole+hard+drive").

**If you can't decide on which of these options to use, just do "sudo wipe /dev/hdx".**

Hi,

Thanks for your detail advice.

Will "sudo shred /dev/hdx" takes longer time than dd?

$ sudo dd if=/dev/zero of=/dev/hdx

the latter of which has been run by me many times in the past.

B.R.
satimis

---

### Post by Stonecold1995 on 2012-07-29
> **satimis said:**
> Hi,

Thanks for your detail advice.

Will "sudo shred /dev/hdx" takes longer time than dd?

$ sudo dd if=/dev/zero of=/dev/hdx

the latter of which has been run by me many times in the past.

B.R.
satimis

Yes, Shred will take longer than DD, but it is also much more secure (DD was designed for speed and low-level operations, Shred was designed for security).  Shred is less secure than other utilities like Wipe, srm, and Nwipe/DBAN, but it is a bit faster.  Unless you suspect your hard drives will be in the hands of someone with digital forensics knowledge and/or you have highly illegal incriminating evidence on your hard drive, then I think Shred alone is fine.

---

### Post by papibe on 2012-07-30
Hi satimis.

This may be interesting to you: there's a podcast show called TechSnap that talks about IT security, and system and network administration. In this episode: [TechSnap Episode 31]("http://www.jupiterbroadcasting.com/13756/how-malware-makes-money-techsnap-31/"), they talk in deep all sorts of methods to securely delete information from a hard disk.

The relevant discussion starts at 0:31:30.

Regards.

---

### Post by asmoore82 on 2012-07-30
> **Stonecold1995 said:**
> Yes, Shred will take longer than DD, but it is also much more secure

This is nonsense. There is nothing more secure to be done than simply overwriting all the data 1 single time. Overwriting with zeros with dd will be fairly quick and 1000% secure. Nothing in the history of computing has ever been able to recover any data that was overwritten. There are many popular myths about this and they are just that: myths. No private entities nor government agencies have the power to recover overwritten data. Anyone can recover "deleted" files; but not overwritten data. This subtle difference fuels the myths.

I, myself, would still be spreading such nonsense if it weren't for some informative posts on ubuntuforums. Thankfully, someone pointed me in the right direction: [http://bleachbit.sourceforge.net/documentation/shred-files-wipe-disk](http://bleachbit.sourceforge.net/documentation/shred-files-wipe-disk)

Even the information in the video above is mostly, you guessed it, **nonsense**; perpetuating the myths. Did I mention the bleachbit info linked immediately above is really, really good stuff?

---

### Post by Stonecold1995 on 2012-07-30
> **asmoore82 said:**
> This is nonsense. There is nothing more secure to be done than simply overwriting all the data 1 single time. Overwriting with zeros with dd will be fairly quick and 1000% secure. Nothing in the history of computing has ever been able to recover any data that was overwritten. There are many popular myths about this and they are just that: myths. No private entities nor government agencies have the power to recover overwritten data. Anyone can recover "deleted" files; but not overwritten data. This subtle difference fuels the myths.

I, myself, would still be spreading such nonsense if it weren't for some informative posts on ubuntuforums. Thankfully, someone pointed me in the right direction: [http://bleachbit.sourceforge.net/documentation/shred-files-wipe-disk](http://bleachbit.sourceforge.net/documentation/shred-files-wipe-disk)

Even the information in the video above is mostly, you guessed it, **nonsense**; perpetuating the myths. Did I mention the bleachbit info linked immediately above is really, really good stuff?

I think you are misunderstanding the fundamental reason secure deletion matters.  It's not that there is a danger of law enforcement or crackers getting their hands on data and somehow retrieving it.  It's that once a hard drive is in their hands, they can keep it for as long as they'd like, including long enough that technology matures to the point where it *can* retrieve single-pass overwritten data.  Peter Gutmann proved that simple deletion was NOT sufficient to remove data, and that actually overwriting it was necessary.  Back then, people would say "There's no need to overwrite it.  As soon as you "delete" it it's gone for good!", but it turned out it WAS possible.  So anyone who still has old hard disks from that time can easily recover data that was thought to be permanently deleted at the time.

While it is true that *presently* no agency has the technology to recover such data, how can you say for sure that in the future a method to recover such data won't be discovered?  After all, OP is planning to give the drives away, where they may sit until technology can recover single-pass overwritten data.  Overwriting data, even with the way overkill Gutmann method, cannot do any harm.  It takes a little bit longer, but that's the only downside.

---

### Post by Cheesemill on 2012-07-30
Just boot from a Live CD and then use dd to write 0's to the disk.
```
sudo dd if=/dev/zero of=/dev/sdX
```1 pass of 0's is enough to prevent any data recovery, no need to waste any of your time doing multiple passes with random data.

Please read this article:
[http://www.nber.org/sys-admin/overwritten-data-guttman.html](http://www.nber.org/sys-admin/overwritten-data-guttman.html)

---

### Post by Stonecold1995 on 2012-07-30
> **Cheesemill said:**
> 1 pass of 0's is enough to prevent any data recovery, no need to waste any of your time doing multiple passes with random data.


Please read this article:
[http://www.nber.org/sys-admin/overwritten-data-guttman.html](http://www.nber.org/sys-admin/overwritten-data-guttman.html)

With today's technology, but who's to say a method to recover data won't be discovered in the next 20 years?  Why take the chance?

---

### Post by SVEN1 on 2012-07-30
> **Stonecold1995 said:**
> With today's technology, but who's to say a method to recover data won't be discovered in the next 20 years?  Why take the chance?

By the time they find a method, at my age it won't matter....LOL

---

### Post by satimis on 2012-07-30
Hi all,

A further question.

Running;
# dd if=/dev/zero of=/dev/sdx bs=1M

will take long time to complete.

# dd if=/dev/urandom of=/dev/sdx bs=1M
even takes much longer time.

How to check its progress? Instead of only seeing the cursor blinking. TIA

satimis

---

### Post by mörgæs on 2012-07-30
> **satimis said:**
> Thanks.

Where can I download its Linux version?

B.R.
satimis

You can download an ISO file and burn a CD just like Ubuntu:
[http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm)

---

### Post by Stonecold1995 on 2012-07-30
> **mörgæs said:**
> You can download an ISO file and burn a CD just like Ubuntu:
[http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm)

IMO an open-source and more popular alternative like DBAN would be more trustworthy than something proprietary like this.

---

### Post by Elfy on 2012-08-01
Off topic posts all removed.

While you were all enjoying arguing amongst each other you forgot the last post the OP put here.

---

### Post by Grenage on 2012-08-01
> **satimis said:**
> Hi all,

A further question.

Running;
# dd if=/dev/zero of=/dev/sdx bs=1M

will take long time to complete.

# dd if=/dev/urandom of=/dev/sdx bs=1M
even takes much longer time.

How to check its progress? Instead of only seeing the cursor blinking. TIA

satimis

While dd is running, issue the following command form another terminal:

```
killall dd -USR1
```

That will present (in dd's terminal) the current progress.

> **Elfy said:**
> Off topic posts all removed.

While you were all enjoying arguing amongst each other you forgot the last post the OP put here.

Touché.

---

### Post by satimis on 2012-08-01
> **Grenage said:**
> While dd is running, issue the following command form another terminal:

```
killall dd -USR1
```

That will present (in dd's terminal) the current progress.



Hi Touché,

I got it.  Thanks

Edit:
A further question.

On terminal-1
running dd

On terminal-2
running;
$ sudo killall dd -USR1

The output will be printed on terminal-1.  But it is NOT continueously.

Is there a way to generate a progressive bar?


B.R.
satimis

---

### Post by Stonecold1995 on 2012-12-20
> **satimis said:**
> Hi Touché,

I got it.  Thanks

Edit:
A further question.

On terminal-1
running dd

On terminal-2
running;
$ sudo killall dd -USR1

The output will be printed on terminal-1.  But it is NOT continueously.

Is there a way to generate a progressive bar?


B.R.
satimis

You could try dcfldd.
```
sudo apt-get install dcfldd
```
It won't display an actual progress bar, but it will give the progress in a smooth manner.  dcfldd accepts the same command line parameters as dd for the most part, so it can be used the same way.

---

### Post by dcstar on 2012-12-21
> **Stonecold1995 said:**
> 
..........
Peter Gutmann proved that simple deletion was NOT sufficient to remove data, and that actually overwriting it was necessary.
..........

Stop repeating myths.

Gutmann himself has stated that his original work only applied to the hard disk technologies of the time, and was quickly made redundant by far more advanced hard drive encoding techniques.

Why do people continually parrot misinformation on this topic, the level of ongoing ignorance is astounding. Is it that they watch too many TV shows and movies and actually believe the fiction that data can be recovered so easily, are people that gullible?

There is a reason that there is a specific "Secure Erase" function built into ATA hard drives, it is there because it actually works unlike the (basically useless) multi-pass "wipes" that the ignorant continually tell people to use.

---

### Post by Stonecold1995 on 2012-12-21
> **dcstar said:**
> Stop repeating myths.

Gutmann himself has stated that his original work only applied to the hard disk technologies of the time, and was quickly made redundant by far more advanced hard drive encoding techniques.

Why do people continually parrot misinformation on this topic, the level of ongoing ignorance is astounding. Is it that they watch too many TV shows and movies and actually believe the fiction that data can be recovered so easily, are people that gullible?

There is a reason that there is a specific "Secure Erase" function built into ATA hard drives, it is there because it actually works unlike the (basically useless) multi-pass "wipes" that the ignorant continually tell people to use.
Yes I know.  I was corrected on that earlier but the thread started getting that earlier so a mod removed the off-topic conversation.

I still recommend at least 3 passes though for hard drives if time is not an issue (I can be paranoid so personally I use Gutmann method most of the time) because, first of all I have no idea what the NSA is capable of, and second of all it could become easy to extract "cleanly" overwritten data in the future.  It's not from movies that I get this, but the fact that it is known that the NSA has far superior technological capabilities than we do now (TEMPEST and related attacks, etc).

How are the multi-pass wipes "useless"?  They can take a long time but they still get the job done very well (although I think sometimes they miss a small portion at the beginning and end of the partition, or something like that, but who keeps sensitive data there anyway?).  The ATA secure erasure ability is only secure because it catches the small portion that utilities like dd can miss, and because it's done completely by the drive's firmware, so interrupting the process once it has started is very hard (you can turn the drive off of course but as soon as it's powered on again it'll finish clearing the drive).  But other than that ATA secure erasure has pretty much the same effect as using dd.

---

### Post by Ubuntwerp on 2013-02-18
I have fiddled with this question for a bit when trying to securely erase my laptop hdd before selling it and ended up using dd to delete its contents. One reason was that Dban doesn't seem to run, whether it was booted from a cd or usb-stick. 
Thus I used a live cd.

Firstly, I used a dd command as described earlier in this thread  with /dev/urandom and then a dev/zero, effectively making a two pass deletion method.
I think this is good enough to prevent people form trying to grab identity information or personal photos from the hdd. Maybe a forensic lab, might still be able to retrieve some data, but this is not what i am expecting from a normal buyer to get into. 

With regards to the question of how long a dd run takes; I simply aborted the dd after a few minutes with control-c , wrote down the message that was generated in which it said (for example) " speed 9 Mb /sec". 
Then I just divided the size of the whole hd by this amount, conversed the seconds into hours, and it gave 14 hours, which was more or less accurate.
In the second run (filling up with zeros is apparently a lot quicker) I received a 60 Mb /s  and did this again, with again accurate results.
Since, I think, speed is mostly determined by processor speed, especially in the first run; this method based on the first few minutes and extrapolating gives good results in guessing the total amount of time needed.

In the end, I think this is a fairly easy way, usually you will have a live-cd at hand, and also secure for most purposes.

---

### Post by Stonecold1995 on 2013-02-18
I saw recently something about the dangers of one-pass overwriting being due to the fact that the write head doesn't always move over the *exact* same spot on the platter as it had when it wrote the data, leaving a sort of shadow of the previous data.  Even though the head is controlled by super-precise servo motors, it's path still varies very, very slightly, I would not put it passed the NSA to be able to read this almost insignificant "slippage".  I think it's sort of like cleaning your car windshield at a gas station.  You make a bunch of passes over the windshield. getting it wet, but then when you try to dry it off, there's always those thin stripes you've missed that you have to go over again, and it's really easy to see the exact path you've went over, so you have to go over it a few times before the lines are no longer visible.  The same kind of thing can happen with a hard drive's magnetically-coated platter.  Now, a hard drive head is FAR more precise than your hand, but it will still leave some very thin streaks which may be possible to detect with extremely advanced equipment.  Even if there's been no *reported* cases of data recovery after a successful one-pass write, that doesn't mean that it doesn't happen secretly.  I mean, the CIA got away with Project MKULTRA for many years, so I don't think it would be that hard for the NSA to keep their capabilities secret.  That's why I use multiple passes, to minimize the risk that they will be present, and may make the deleted data safe for another 20 years (hopefully).

> **Ubuntwerp said:**
> Firstly, I used a dd command as described earlier in this thread  with /dev/urandom and then a dev/zero, effectively making a two pass deletion method.
I think this is good enough to prevent people form trying to grab identity information or personal photos from the hdd. Maybe a forensic lab, might still be able to retrieve some data, but this is not what i am expecting from a normal buyer to get into.
One pass is usually enough to prevent *software* data recovery, so your average joe stealing a laptop (or even a professional) will be unable to recover personal data.  The only time I'd recommend more than one pass is if you want to protect from government-type organizations.

---

### Post by dcstar on 2013-02-19
> **Stonecold1995 said:**
> 
..........
One pass is usually enough to prevent *software* data recovery, so your average joe stealing a laptop (or even a professional) will be unable to recover personal data.  The only time I'd recommend more than one pass is if you want to protect from government-type organizations.

Please cite **one** credible report of any "government-type organization" that has recovered data from a wiped hard disk surface?

**TV shows and movies do not count, they are fiction.**

Plenty of organisations can recover data that some dumb Windows user "deleted", and many others can recover data from broken drives but there is little or no credible evidence that anyone actually successfully uses the theoretical process of somehow recovering magnetic data patterns that have been overwritten.

Anyone with knowledge and experience in magnetic materials knows how difficult - if not impossible - this sort of thing is, and that automatically disqualifies 99.9% of those who comment on this subject.

---

### Post by fdrake on 2013-02-19
all previous methods are valid and should get the job done. But if you you are still suspicious pass the HDDs throught the 45-Tesla-Hybrid Magnet. Should be enought, I think. :D
[http://www.dump.com/strongestmagnet/](http://www.dump.com/strongestmagnet/)

---

### Post by kurt18947 on 2013-02-19
I've read through this thread but am not an expert.  I'm certain that if I had anything on a hard drive that would be of interest to any 3 letter organization (FBI, NSA, CIA etc), I wouldn't worry about erasing and reusing that disk.  Risk prison to save $50? Don't think so.  Disassemble,  pulverize the platters and mix the shards in with used cat litter, spend some quality time with an oxyacetylene torch etc. etc.  Those methods require little technical expertise and are 100% effective.

For 'normal' situations, I'm pretty sure any of the methods discussed above are adequate.  I've used DBAN if I suspected a drive may have malware on it that may survive a reformat.

---

### Post by Stonecold1995 on 2013-02-19
> **dcstar said:**
> Please cite **one** credible report of any "government-type organization" that has recovered data from a wiped hard disk surface?

**TV shows and movies do not count, they are fiction.**
Give one credible report that you can read data off a computer screen through a wall meters away.  Oh wait, that came from the NSA and was declassified by *them*, if they haven't declassified it who knows, we may be having an argument about THAT.  You are correct in that there have been no "credible reports", but with anal virginity on the line, I'd rather not take chances with an organization with far superior technology (not that I have anything on my computer worth the NSA possibly giving away their forensic capabilities, or the money and time).  I'd gladly take that extra pass or two, it's not like there's any downside but taking a little longer (and an imperceptibly small increase of wear on the drive).  I can guarantee the NSA has the capability do do things most of us would call impossible. (as has been proven with declassified document after declassified document).  To say something is impossible NOW and in the near FUTURE just because there is no easy contemporary (and non-classified) way to do so seems to me to be incredibly naive.

The NSA's capabilities aren't just in Hollywood movies, they DO have very advanced technology, and that's only what they're letting on.  Hell, I wouldn't even be surprised if the NSA could capture decryption keys just by tapping into a house's whole power supply (it is known that you can get the internal state of a CPU by reading the power fluctuations, but the NSA may be able to do this from a block away).  In the future I also wouldn't doubt they could do the same thing, but from satellite.

**Why is it that you claim multiple passes is so unnecessary?  Why are you so sure are you that the NSA doesn't have the technology to do so, or won't acquire the technology in the near future.**

---

### Post by mörgæs on 2013-02-19
Everyone, please post sources and documentation or refrain from posting.

---

### Post by Stonecold1995 on 2013-02-19
> **mörgæs said:**
> Everyone, please post sources and documentation or refrain from posting.
OK then.

From Bradly Manning's case ([http://www.wired.com/threatlevel/2011/12/manning-assange-laptop/):](http://www.wired.com/threatlevel/2011/12/manning-assange-laptop/):)

> Johnson testified that he found two attempts to delete data on Manning&#8217;s laptop. Sometime in January 2010, the computer&#8217;s OS was re-installed, deleting information prior to that time. Then, on or around Jan. 31, someone attempted to erase the drive by doing what&#8217;s called a &#8220;zerofill&#8221; &#8212; a process of overwriting data with zeroes. Whoever initiated the process chose an option for overwriting the data 35 times &#8212; a high-security option that results in thorough deletion &#8212; but that operation was canceled. Later, the operation was initiated again, but the person chose the option to overwrite the information only once &#8212; a much less secure and less thorough option.

All the data that Johnson was able to retrieve from un-allocated space came **after** that overwrite, he said.

Also from [http://www.ehounds.com/atty/FAQ_Whitepaper/8.pdf:](http://www.ehounds.com/atty/FAQ_Whitepaper/8.pdf:)
> [The] US Department of Defense in the clearing and sanitizing standard DoD 5220.22-M recommends the approach "Overwrite 
all addressable locations with a character, its complement, then a random character and verify"
However, according to Wikipedia, that is no longer used.  Now, physically destroying or degaussing the drive is necessary, apparently multiple passes isn't secure enough from them.

Overkill?  Probably.  Bad to do?  Not unless you're running short on time or have a drive that's about to break.  So what's the problem with doing a few extra passes just to be sure?  One pass is generally sufficient, but to say it's absolutely 100% invincible is foolish.

**EDIT:** I may have misunderstood the Manning issue (or maybe not, I don't know if it means the data was present, was overwritten, and recovered, or simply that it was overwritten once in the past but new data was put on, and THAT was recovered), but the fact that the DoD is paranoid enough to take measures above that of software overwriting still stands.

Another thing, according to the Center for Magnetic Recording Research, in [http://cmrr.ucsd.edu/people/Hughes/documents/QandAforwebsite10212008_000.doc](http://cmrr.ucsd.edu/people/Hughes/documents/QandAforwebsite10212008_000.doc) it says that, while one pass is usually sufficient, more passes DO help slighly more.  Not much, yes, but slightly, and that's my whole point.  However, even then it may be recoverable to some extent (which multiple overpass won't help much with) because "it does not do much to the remaining track edges where most of the very low level distorted remnant data remains after an overwrite".

---

### Post by dcstar on 2013-02-20
> **Stonecold1995 said:**
> 
...........
Why is it that you claim multiple passes is so unnecessary?  Why are you so sure are you that the NSA doesn't have the technology to do so, or won't acquire the technology in the near future.

Because the byte pattern you send to the drive **is not** the byte pattern that gets written to the drive - and has not been for decades now.

Hard drives from the past 20+ years use various encoding algorithms and you have no direct control about what gets written to the disk. Gutmann said this basic fact made his method no longer valid decades ago but people keep citing his now invalid method (out of pure ignorance and lack of understanding, it seems).

Sending "zeros" to a drive results in a pseudo-random pattern being written to the disk surface, sending "ones" results in a different pseudo-random pattern, sending anything results in a particular pseudo-random pattern that is later decoded to recover the original data.

Doing multiple passes does not guarantee that every area of the disk surface is overwritten and just one pass of anything is enough to scramble any previous magnetic pattern.

Perhaps we won't need hard drives in the future once the aliens land from outer space and shower us with their advanced technology, eh?

---

### Post by Stonecold1995 on 2013-02-20
> **dcstar said:**
> Because the byte pattern you send to the drive **is not** the byte pattern that gets written to the drive - and has not been for decades now.
What does that have to do with anything?  How does that relate to whether or not data is recoverable?

> **dcstar said:**
> Hard drives from the past 20+ years use various encoding algorithms and you have no direct control about what gets written to the disk.
Yes, they do.  An operating system CAN tell a hard drive to write a specific pattern of bytes, or to OVERWRITE a specific pattern of bytes.  The operating system can control that (unless it's a SSD, which has a controller that works almost 100% independent from the OS).

> **dcstar said:**
> Sending "zeros" to a drive results in a pseudo-random pattern being written to the disk surface, sending "ones" results in a different pseudo-random pattern
What does that have to do with anything either?

> **dcstar said:**
> Doing multiple passes does not guarantee that every area of the disk surface is overwritten
But as I stated above, and as was stated in my references (CMRR, etc), it DOES provide slightly more security.

> **dcstar said:**
> just one pass of anything is enough to scramble any previous magnetic pattern.
Enough to prevent any form of recover ever, now or in the near future?  As I sead in my last post:
> Another thing, according to the Center for Magnetic Recording Research, in [http://cmrr.ucsd.edu/people/Hughes/d...212008_000.doc](http://cmrr.ucsd.edu/people/Hughes/d...212008_000.doc) it says that, while one pass is usually sufficient, more passes DO help slighly more. Not much, yes, but slightly, and that's my whole point. However, even then it may be recoverable to some extent (which multiple overpass won't help much with) because "it does not do much to the remaining track edges where most of the very low level distorted remnant data remains after an overwrite".
**Are you saying that is untrue?**  Where's your evidence that this "low level distorted remnant data" that remains does not actually exist, contradicting the CMRR?  Furthermore, you also have not addressed the OTHER evidence I've given, with the Manning case (assuming I haven't misunderstood it)?

> **dcstar said:**
> Perhaps we won't need hard drives in the future once the aliens land from outer space and shower us with their advanced technology, eh?
I wish.  We're going to have to wait until WE make better technology (and I try to use SSDs mostly anyways).

[b]Before we go on, just so we can be on the same track, let me get this straight.  You are saying:
-A multiple-pass overwrite provides absolutely NO extra security than single-overwrite.
-It is physically impossible to recover single-pass overwritten data for any contemporary or near-future forensics technology.
-Even if you have the time, using two or three passes instead of one is still not worth it whatsoever.

Is this what you are saying, or am I misunderstanding something?[/b]

---

### Post by fdrake on 2013-02-20
off topic : love the line! :D
> 
 but with anal virginity on the line, I'd rather not take chances


back to the topic:

1. the operating sys has no direct-low level control of the drive : the drive itself has a chip that process your inputs. You cannot know for sure what it is writen, you system is able to read it, because the manufactured chip reads it for the OS.

2. I don't think you have a clear idea how data are stored in index-inodes in the disk by a UNIX system ..  

3. Do no think that the NSA is an Omniscient being that can achive/resolve any tech or math problem. They are not. Just because they have bigger and more powerfull computers wont help in this situation.  

4. worrying/(paranoia) is not good for your health.

---

### Post by Stonecold1995 on 2013-02-20
> **fdrake said:**
> 1. the operating sys has no direct-low level control of the drive : the drive itself has a chip that process your inputs. You cannot know for sure what it is writen, you system is able to read it, because the manufactured chip reads it for the OS.
I know I cannot know for sure, but the drive won't typically encode what it's writing, right?  I was reading yesterday about the forensic implications of HDDs vs SSDs, that a severely damaged HDD can have its platters taken out, and put on a spin rack where data can be read, but damaged SSDs lack a functioning controller, so, like you said, there is no way to know for sure what is written (or where).  If a hard drive's magnetic platter can be taken out, and read on a different device (and all hard drives are able to be read the same way, unless they use encryption), then how does that affect your claim that the "manufactured chip reads it for the OS" and that what it writes is different from what it is told to write?  In that case, wouldn't it act exactly like an SSD where even single-pass overwriting is impossible because even the operating system is unaware of where on the drive data is written to?

> **fdrake said:**
> 2. I don't think you have a clear idea how data are stored in index-inodes in the disk by a UNIX system
That is correct.  If I am missing key information that invalidates my claims, please enlighten me.

> **fdrake said:**
> 3. Do no think that the NSA is an Omniscient being that can achive/resolve any tech or math problem. They are not. Just because they have bigger and more powerfull computers wont help in this situation. 
I do not think they can do that, but I DO think they have technology some years ahead of consumer (or even professional) technology.  Of course powerful computers won't help here, but if they can do things like pick up data from a computer screen or wires through a wall, know where a video was created because of minute fluctuations of a power supply's inaudible hum, build a supercomputer in Utah that can crawl and index the deep web (and not just publically available onion or i2p sites), create ECHLEON to spy on nearly all (or all) wireless communication and that we STILL don't know the range and capabilities of, create literal invisibility cloaks for the visible (and below) spectrum, and work on building (and may already possess) quantum computers that make the K-computer look like the ENIAC with down syndrome, then I think it would be foolish to say "well, I never heard of anyone being able to recover overwritten hard drive data in consumer, non-security focused devices, and I am so sure that it is impossible, why even try?"  Which is what I'm seeing here.  A false sense of security is worse than no security at all (and before anyone says that my preference for 2/3-pass overwrites is a false sense of security, I admit that it is not invulnerable to potential data recovery, but I prefer taking even little steps that may help, but at least keep me on my toes).

> **fdrake said:**
> 4. worrying/(paranoia) is not good for your health.
But assuming a specific anti-forensics technique is invulnerable and not enhanceable can lead to even greater health risks, and when the only downside of an extra pass is a little longer wait time, then I'll happily do that.

---

### Post by dcstar on 2013-02-20
> **Stonecold1995 said:**
> 
..........
[b]Before we go on, just so we can be on the same track, let me get this straight.  You are saying:
-A multiple-pass overwrite provides absolutely NO extra security than single-overwrite.
-It is physically impossible to recover single-pass overwritten data for any contemporary or near-future forensics technology.
-Even if you have the time, using two or three passes instead of one is still not worth it whatsoever.

Is this what you are saying, or am I misunderstanding something?[/b]

[LIST=1]
[*]Yes, because even though there is a theoretical possibility of some remnant magnetic pattern on the fringe areas of a track there has been no evidence that anyone has actually effectively used this in the real world - **not on TV shows or fantasy movies** - to recover any data. One pass of anything will effectively mask any previous data on the surface of a modern hard disk.

Just think about it, after one pass of anything then random quantities of areas on the hard disk surface will be "flipped" from one to zero and another random quantity will not have been changed at all (because that is how hard drive encoding works). If it was actually possible, anyone trying to recover any data from the fringes of surface areas will not be able to tell what was written on the last pass and what was not - meaning that the writing of one pass of anything effectively scrambles whatever was there previously.

People also need to realise that reading data off a hard disk surface is already not a trivial task that requires precision engineering to recover the tiny magnetic states on a fully written track - trying to recover a magnetic state many magnitudes smaller on the fringes of a track may be theoretically possible but will be so difficult in practice to be practically impossible - heads on a hard disk are designed to read the main track, not the tiny fringes adjacent to tracks.

Even using the analogue level of a magnetic signal to try and determine the signal state of the previous state is rendered useless by the scrambling of a single pass of anything - you just don't know if that previous state was from before that last write or from the one before that (or the one before that etc etc......).


[*]Lemme see, nope - sorry, my Crystal Ball can't tell me that future.
[*]Why not make it 20 or 100 passes just to be safer? All you will be doing is having some tiny area of fringe magnetism on the disk surface with an already unusable random pattern possibly replaced by another random pattern - how much randomness do you need to keep achieving exactly the same result?
[/LIST]

The best way to "wipe" any hard drive (for future reuse) is to use the embedded ATA "Secure Erase" function that has direct access to the magnetic surface and is specifically designed for this take. I do not know its algorithms but I assume that it does what it is advertised to do and will satisfy the paranoia of most sane people.

The best way to wipe any hard disk that will never be used again is to physically bend the platters - like with a big hammer, and "one pass" is more than sufficient in this case.

---

### Post by fdrake on 2013-02-20
> **Stonecold1995 said:**
> 
But assuming a specific anti-forensics technique is invulnerable and not enhanceable can lead to even greater health risks, and when the only downside of an extra pass is a little longer wait time, then I'll happily do that.

No-one said that is impossible, we are stating that is hard / or hard to believe . For example you can ipotise that all HDD manufacturesrrs got together around the table with the CIA NSA KGB and so on  to make a deal with them . They might save data on the side on a hidden disk that the costumer does not know , that would make recovery patrially possible.

What I mean is that anything is possible (even that we are in the MATRIX, how  can you argue that!?), sure but in that is not how the tech world measures stuff: we like to think of how EASY and how HARD is to do a certain think.

I do have a relative in the FBI and a couple of friends working for homeland security, and theyr biggest weapon is not technoly. Most of the time they do to make pople believe that they actually know more then they actually do in reality. 

Btw: even with a quantum computer it is improbable(i don't say impossible because I did not research that deeply the matter, but for sure would be very hard to do even so) to crack an RSA encryption).

Everything is possible in theory. And that is why the wheight of this discussion/argument about the disk recovery think has kinda lost sense.


also regarding a dd zero fill :
> 
Be very careful with this information. I work in the HDD industry and I CAN confirm that off-track reads can recover over-written data.

Some recovery methods use this trick to set the head +/-10% off-track, then read, move it off-track a little more, then read. At some point you will be able to recover what was laid down before the zero fill.

Use random when possible. Zero is okay for meta-data and MBR erasure. I recommend several random passes to obliterate the original data.

Also, zero does not mean cleared recorded bits on an HDD. Zero has a bit pattern just like any other number.


from [http://askubuntu.com/questions/21501/possibility-of-recovering-files-from-a-dd-zero-filled-hard-disk](http://askubuntu.com/questions/21501/possibility-of-recovering-files-from-a-dd-zero-filled-hard-disk)

---

### Post by Stonecold1995 on 2013-02-20
> **dcstar said:**
> [LIST=1]
[*]Yes, because even though there is a theoretical possibility of some remnant magnetic pattern on the fringe areas of a track there has been no evidence that anyone has actually effectively used this in the real world - **not on TV shows or fantasy movies** - to recover any data. One pass of anything will effectively mask any previous data on the surface of a modern hard disk.
Please tell me where I said I'm getting my facts from TV shows?  I never mentioned anything about TV shows or fantasy (it would be sci-fi btw) movies once.

> **dcstar said:**
> Just think about it, after one pass of anything then random quantities of areas on the hard disk surface will be "flipped" from one to zero and another random quantity will not have been changed at all (because that is how hard drive encoding works). If it was actually possible, anyone trying to recover any data from the fringes of surface areas will not be able to tell what was written on the last pass and what was not - meaning that the writing of one pass of anything effectively scrambles whatever was there previously.
Even if it's called "binary", it's not like there are physical areas of the hard drive with a quantum the size of one bit, which can either be "full 1" or "full 0".  It can be "mostly magnetized one way so that the read head perceives is as binary 1", or the other way around.

> **dcstar said:**
> People also need to realise that reading data off a hard disk surface is already not a trivial task that requires precision engineering to recover the tiny magnetic states on a fully written track - trying to recover a magnetic state many magnitudes smaller on the fringes of a track may be theoretically possible but will be so difficult in practice to be practically impossible - heads on a hard disk are designed to read the main track, not the tiny fringes adjacent to tracks.
Theoretically possible is all that matters.  Our technology has increased more than a *billion* fold in a very short time (hell, my computer has more than a hundred *BILLION* times more memory than the Atari 2600).  Back then people probably argued whether or not it was *physically possible* to have a chip with 10 MB of memory!  Imagine in the future, especially with the possible technological singularity just around the corner in the next few decades, do you still think magnetic remnant will be undetectable?


> **dcstar said:**
> Even using the analogue level of a magnetic signal to try and determine the signal state of the previous state is rendered useless by the scrambling of a single pass of anything - you just don't know if that previous state was from before that last write or from the one before that (or the one before that etc etc......).
That's simply untrue.  If the pass is of non-random data, the only thing you need is the ability to know if the previous state was changed or stayed the same across a pass.  A hard drive's write head does NOT flip the magnetic polarity of the platter's coating by exactly 180 degrees, it simply doesn't.  Assuming the magnetic force exerted by the write head remains fairly consistent, you can theoretically tell what the previous bit was.  You can do that with floppy drives (and still can), the ONLY difference that matters between a floppy disk and a hard drive is the fact that a hard drive is so much more dense.


> **dcstar said:**
> [*]Why not make it 20 or 100 passes just to be safer? All you will be doing is having some tiny area of fringe magnetism on the disk surface with an already unusable random pattern possibly replaced by another random pattern - how much randomness do you need to keep achieving exactly the same result?
If I could do 100 passes without a significant amount of time being taken, I would if I had a hard drive that I felt may be subject to extensive and massively-funded forensic examination now or in the future, I I would do so.  Of course, if I needed that level of anti-forensics I would physically destroy the drive.

> **dcstar said:**
> The best way to "wipe" any hard drive (for future reuse) is to use the embedded ATA "Secure Erase" function that has direct access to the magnetic surface and is specifically designed for this take. I do not know its algorithms but I assume that it does what it is advertised to do and will satisfy the paranoia of most sane people.
It doesn't have any special algorithms.  It just wipes 

There's no need to be sarcastic, nor is there a need to imply that I am insane (paranoid maybe, but not insane).  The only thing I am trying to say is that there IS a difference, however small, between one and multiple-passes, and that one pass isn't the perfect, invincible anti-forensics measure you are claiming it to be.



**Also, if you say it is impossible to retrieve data from a single-pass overwrite, please explain this quote from Wikipedia's page on Manning:**
> Johnson said there had been two attempts to delete material from the MacBook. The operating system was re-installed in January 2010, and on or around January 31, 2010, an attempt was made to erase the hard drive by doing a "zero-fill," which involves overwriting material with zeroes. The material was overwritten only once, which meant it could be retrieved.[65]

---

### Post by fdrake on 2013-02-20
[QUOTE=Stonecold1995;12519692
**Also, if you say it is impossible to retrieve data from a single-pass overwrite, please explain this quote from Wikipedia's page on Manning:**[/QUOTE]
that is because they used a zero fill if they had used instead a COSTUMIZED-random fill the result would have been different. see my prev link.

COSTUMIZED-random number == where you costumize the kind of seed to be used.

we are in a certain contest. A regular user wont need all these worries and thoughts. None of us, not even you Stonecold1995, so why worring so much about it ? Even if someone wanted to recover your HDD after a dd fill , they must have  a really , REALLY, REALLY good reason (even the goverment, because they are lazy) to waste so much time and money on it. If you don't trust your hdd then use a live cd for you stuff and don't save anything . And don't try to start with the RAM cool attacking, then !!! :D

---

### Post by Stonecold1995 on 2013-02-20
> **fdrake said:**
> No-one said that is impossible, we are stating that is hard / or hard to believe . For example you can ipotise that all HDD manufacturesrrs got together around the table with the CIA NSA KGB and so on  to make a deal with them . They might save data on the side on a hidden disk that the costumer does not know , that would make recovery patrially possible.
I remember reading something like that in the man page for srm (or wipe, or some other utility like that), and yeah, while I don't think that is very likely, I see no way I can physically address that short of not using computers.  Actually, the NSA makes their OWN processors for that VERY reason.

> **fdrake said:**
> What I mean is that anything is possible (even that we are in the MATRIX, how  can you argue that!?), sure but in that is not how the tech world measures stuff: we like to think of how EASY and how HARD is to do a certain think.
I cannot be sure I'm not in The Matrix.  However, that just uses the fact that nothing can be scientifically proven, only disproven to a certain extent.  I've read up a lot about the possibilities of a virtual reality, but I cannot do anything about it, I don't try to do anything about it.


> **fdrake said:**
> I do have a relative in the FBI and a couple of friends working for homeland security, and theyr biggest weapon is not technoly. Most of the time they do to make pople believe that they actually know more then they actually do in reality. 
The FBI really doesn't have vastly superior technology.  The FBI mostly has technology that everyone else does, just they have access to higher quality, because of their money.  The CIA has even more access (to a scary level, considering the horrendous things they were able to keep hidden for so many decades), and the NSA dwarfs the rest.

> **fdrake said:**
> Btw: even with a quantum computer it is improbable(i don't say impossible because I did not research that deeply the matter, but for sure would be very hard to do even so) to crack an RSA encryption).
It will be a long time before the whole keyspace of RSA can be cracked like it has with DES.  Also, with a quantum computer, even the keyspace of 4096 bit RSA (and few people use that level of security) will not be immune to a computer billions of times more powerful than current computers.  The only thing that can truly stand the test of time is a properly implemented OTP, or an encryption scheme which would take more memory than there is available in the entire universe (or more energy to decrypt than there is available free energy in the universe).

> **fdrake said:**
> Everything is possible in theory. And that is why the wheight of this discussion/argument about the disk recovery think has kinda lost sense.
That is not true at all.  I don't even want to get into it, but physics dictates that there ARE things that are patently impossible.  For example, breaking the laws of thermodynamics in Newtonian physics, or recovering information which has passed near a black hole, physical properties in a second dimensional plane, etc.  And other things which are exceedingly unlikely now or in the near future, like reaching near-light speed, or mind control using radio waves from satellite distance (although that is theoretically possible).


> **fdrake said:**
> also regarding a dd zero fill :

from [http://askubuntu.com/questions/21501/possibility-of-recovering-files-from-a-dd-zero-filled-hard-disk](http://askubuntu.com/questions/21501/possibility-of-recovering-files-from-a-dd-zero-filled-hard-disk)
Many of those comments are saying that it IS possible to recover data, just difficult.  And I'm saying that multiple passes gives a SLIGHT improvement in security.

---

### Post by fdrake on 2013-02-20
> **Stonecold1995 said:**
>  The only thing that can truly stand the test of time is a properly implemented OTP, or an encryption scheme which would take more memory than there is available in the entire universe (or more energy to decrypt than there is available free energy in the universe).

.
the RSA already does that but that does not mean it is impossible, some code require 5 or more times the entire time of the univers to be cracked or would require computers with a size bigger then the universe itself. Don't f*** with the prime numbers !!! :D

> That is not true at all. I don't even want to get into it, but physics dictates that there ARE things that are patently impossible. For example, breaking the laws of thermodynamics in Newtonian physics, ... not true : in Newtonian (Classis) physics states that an object cannot have 2 different states at the same time. In quantum mechanics it does. You see it depends from the contest we are using. We have to agree on the contest of the discussion. I can always go out of your contest to prove my argument. 
:D

Descartes would say I am sure about nothing but that I am thinking "Cogito ergo sum". That is in the end , truly, our only point of observation. We don't know anything for sure  ... .

---

### Post by Stonecold1995 on 2013-02-20
> **fdrake said:**
> that is because they used a zero fill if they had used instead a COSTUMIZED-random fill the result would have been different. see my prev link.

COSTUMIZED-random number == where you costumize the kind of seed to be used.

we are in a certain contest. A regular user wont need all these worries and thoughts. None of us, not even you Stonecold1995, so why worring so much about it ? Even if someone wanted to recover your HDD after a dd fill , they must have  a really , REALLY, REALLY good reason (even the goverment, because they are lazy) to waste so much time and money on it. If you don't trust your hdd then use a live cd for you stuff and don't save anything . And don't try to start with the RAM cool attacking, then !!! :D
Oh that clears a LOT up.  I had thought people were claiming that a single pass completely erases data no matter what.

Also, I'm not too worried about cold-boot because DDR3 RAM remains on for a few seconds.  I've tried installing the TRESOR kernel patch but it's only for the 2.6 kernels (I think), and downgrading from 3.6 to 2.6 isn't worth it just to protect a few seconds of vulnerability.

Yes I know I don't have to worry about these kinds of attacks or forensic techniques, I'm just arguing that it IS possible, and not so highly improbable as to be completely put out of mind.  Same reason I don't spend money on a faraday cage to block TEMPEST, or take time memorizing ultra-long random passwords for every account, etc.

---

### Post by Stonecold1995 on 2013-02-20
> **fdrake said:**
> the RSA already does that but that does not mean it is impossible, some code require 5 or more times the entire time of the univers to be cracked or would require computers with a size bigger then the universe itself. Don't f*** with the prime numbers !!! :D
Wow, that's pretty amazing.  At how many bits in size?

> **fdrake said:**
> not true : in Newtonian (Classis) physics states that an object cannot have 2 different states at the same time. In quantum mechanics it does. You see it depends from the contest we are using. We have to agree on the contest of the discussion. I can always go out of your contest to prove my argument. 
:D
I said specifically, "in Newtonian physics" because the laws of thermodynamics are "fuzzier" in quantum physics.

---

### Post by mörgæs on 2013-02-20
I believe the thread has served its purpose. 
Closing.

---

