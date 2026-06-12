---
title: "issues with gparted on live cd 9.04"
date: 2009-09-10
forum: General Help
---

### Post by raven01 on 2009-09-10
First off... sorry if this is a re post because i have been looking for a while.

Anyway..

I am dual booting my xp and 9.04. all fine and dandy except for one little issue with the partition editor. I am not sure why but basically when i open it up from the ubuntu live cd it freezes. it wont let me re size my windows partition or do anything. the only thing i have been able to make it do is take off the boot flag. but it wont let me close the flag menu for the drive or re enable the boot flag. so i have to hard restart.

any ideas? if i am kind of unclear just say so and i will try to make it more clear.

thanks guys

-raven

---

### Post by earthpigg on 2009-09-10
i suggest four things:

0. you made a good back up of all of your data before doing anything with partitions, right? _***right?***_

1. defrag windows partitions before modifying them.

2. use windows tools to manage partitions with windows installed on them. look at #9 [here]("http://gparted.sourceforge.net/faq.php") for why.

> Unless you are very lucky, you&#8217;ll be greeted with this horrible error message saying &#8220;Windows Failed to start. A recent hardware or software change might be the cause.&#8221;

3. run fsck on your linux partitions. (no need to run badblocks at this point, unless you want to.)

4. run scandisk on your windows partitions. (no need to check for physical errors at this point, unless you want to.)


edit: 0a. try right clicking on the partition and selecting 'unmount partition' if you aren't doing that already....

---

### Post by rbc on 2009-09-10
This is not really a straightforward answer to your question, but I have always had better luck with the GParted Live CD, rather than using Gparted of the Ubuntu Live CD

---

### Post by raven01 on 2009-09-10
yea the thing is funny. this windows install is literally 2 days old. but thanks guys ill try the live cd for gparted first and if that doesnt work ill look at windows tools.

still no idea why out of no where it is freezing like that. any ideas to it?

edit:  and yea im using xp not vista so i have not looked for windows partitioning software ;)

---

### Post by louieb on 2009-09-10
Just wondering how much ram and what CPU? Kinda sounds like the PC has just enough to boot the Ubuntu live CD. 

BTW: the boot flag for some unknown reason means something to windows - it wants it set on  its partition.  Linux does not care if the boot flag is set or not. 

My favorite CD for running Gparted is the System Rescue CD, another good one is the PartedMagic live CD.

---

### Post by raven01 on 2009-09-10
Have a asus a7n8x-e deluxe board
2.5 gig ram
amd 2500+barton
120 gig hdd.

see here is the thing i have dual booted once but i couldnt get the linux partition to obtain more than 2 gig of the free space  (guessing i did something wrong ;p )

and yea i know the boot flag needs to be on. i was trying to see what would work and not work. so i had to reload the live cd and hope that i would be able to turn the boot flag on again which obviously it was able to lol.

but yea the iso just finished for the gparted live disk so i might try that in a lil bit or tomorrow.

---

### Post by raven01 on 2009-09-11
ok well i used the live disk of gparted to resize and that went well. now....my actual ubuntu disc is stalling on me and freezing when ever i try to install. disc integrity said its fine. any ideas?

---

### Post by louieb on 2009-09-11
> **louieb said:**
> Kinda sounds like the PC has just enough to boot the Ubuntu live CD. 
> **raven01 said:**
> Have a asus a7n8x-e deluxe board
2.5 gig ram -amd 2500+barton -120 gig hdd.

lol - lots more that enough.  and the board has Nvidia graphics - are you using the on board display connection? That should work. And with that I'm out of guesses why the live CD is having problems.

---

### Post by bruno9779 on 2009-09-11
I had a similar issue lately

I installed ubuntu 9.04 amd64 on a new system (that had never seen Windoze or any other os) and gparted from ubuntu live CD worked just fine, resize and all.

the i tried to install winxp on an empty partition but Win refuses to write to the MBR if it has been created by another OS

so I had to format the HD usind win tools, and win created the MBR anew and all worked

**Here is where the problem started**

Since the MBR has been re-written by Win, Gparted "resize" and "move" functions are unusable or limited.

Normally in Gparted you get to choose how many block to leave before and after a partition, but now only before.

I started the ubuntu live CD and accessed Gparted from there, and everything was as normal. I set everything there and the reboot and install Ubuntu

---

### Post by raven01 on 2009-09-11
i just finished down loading a new iso so im going to do a slow burn on it and see if that works.


Edit:   ok yea that did the same thing. this time i did a 4x burn and everything...still same freezing issue.

         im starting to think that my cdrom being on the slave might be causing some issues. possibly.  i have to find that dumb jumper diagram before i kill this thing.

---

### Post by raven01 on 2009-09-11
well i hit the nail on the head and won.

I managed to switch my cdrom off of the slave secondary to master secondary. (other dvdrom busted so never did the right thing lol)    how it worked before when i formated and installed before is beyond me.

but i did notice that it did run a little less slugish. but still. the fact remains that even tho a cdrom drive is not the master shouldnt mean linux should fail in that way.

but i am 100% dual booted the right way with everything in the right order. now i can start enjoying my newly stable system haha.

thanks for all the help everyone.

-Jeremy

---

