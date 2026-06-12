---
title: "Need help with Ubuntu 9.10"
date: 2010-02-06
forum: General Help
---

### Post by angree on 2010-02-06
Hey guys, new ubuntu user here.   I must have done soemthing that shouldn't have been 

done, although i cant figure out what it was.  i was doing some updates installed 

something, canceled it halfway through the DL.  now my machine is messed up.  text on 

web pages blinks randomly, my mp3 player wont play longer then 10 secs worth of 

music.  when i reboot it goes to a black screen, and when i have the live cd in it wont boot 

from it.  i dont even get my bios boot up text.  im faily computer savvy, but this problem   

is just wierd.   i've tried to install win7 as well, and it wont boot off the CD.  If anyone

can help with this issue, i give many thanks in advance.

Angree the NooB

---

### Post by samantha_ on 2010-02-06
> **angree said:**
> Hey guys, new ubuntu user here.   I must have done soemthing that shouldn't have been 

done, although i cant figure out what it was.  i was doing some updates installed 

something, canceled it halfway through the DL.  now my machine is messed up.  text on 

web pages blinks randomly, my mp3 player wont play longer then 10 secs worth of 

music.  when i reboot it goes to a black screen, and when i have the live cd in it wont boot 

from it.  i dont even get my bios boot up text.  im faily computer savvy, but this problem   

is just wierd.   i've tried to install win7 as well, and it wont boot off the CD.  If anyone

can help with this issue, i give many thanks in advance.

Angree the NooB

Boot to recovery mode, and select "root shell"
type in
```

sudo dpkg --configure -a
sudo apt-get upgrade

```

---

### Post by angree on 2010-02-07
Tried it, it didn't do anything...


xxxxxxx@xxxxxxx-laptop:~$ sudo dpkg --configure -a
[sudo] password for xxxxxxx: 
xxxxxxx@xxxxxxx-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


what now???

i dont really like to shutdown my laptop, especially now that im not sure if it will come back up or go to blank screen....

---

### Post by angree on 2010-02-07
> **samantha_ said:**
> Boot to recovery mode, and select "root shell"
type in
```

sudo dpkg --configure -a
sudo apt-get upgrade

```


I'd like to just reinstall since i dont have any info that needs saved..any suggestions?

---

### Post by jken146 on 2010-02-07
It won't boot from CDs eh?  Can you get as far as the memory test on the live CD?

It sounds like perhaps a RAM issue (erratic blinking behaviour, etc.) rather than broken installation (if you stopped it half way through the *download* and not the actual installation then you can't have done any harm).

---

### Post by angree on 2010-02-07
> **jken146 said:**
> It won't boot from CDs eh?  Can you get as far as the memory test on the live CD?

It sounds like perhaps a RAM issue (erratic blinking behaviour, etc.) rather than broken installation (if you stopped it half way through the *download* and not the actual installation then you can't have done any harm).


heh, bad newqs is it might have been half way through the install, i just canceled it....not sure if it was the DL or the install...   and no if i boot with a boot cd in it stays blank screen, no text at all, no bios to try to switch the boot order, no bios at all..its wierd.   its not always blinking text, and most if the time my gmail wont geneate text unless i scroll off screen then back on but it only stays for a second or so.......   i know i prolly sound like a noob, but im brand new to ubuntu...started it about 2-3 weeks ago..and thought i was doing good with it hehe

---

### Post by jken146 on 2010-02-07
To get into the BIOS setup, try jabbing at the delete, F1, F2 keys (it's probably one of those) when the computer first comes on.

Also, I've just remembered that there should be an option for the memory test at the GRUB menu (below the Ubuntu options). If Ubuntu is the only OS on the computer and you don't see the menu, press escape when you see "Loading GRUB" or a similar message.

I hope that last para made sense.

---

### Post by angree on 2010-02-07
> **jken146 said:**
> To get into the BIOS setup, try jabbing at the delete, F1, F2 keys (it's probably one of those) when the computer first comes on.

Also, I've just remembered that there should be an option for the memory test at the GRUB menu (below the Ubuntu options). If Ubuntu is the only OS on the computer and you don't see the menu, press escape when you see "Loading GRUB" or a similar message.

I hope that last para made sense.


im not familiar with GRUB, is that the log in screen?

---

### Post by jken146 on 2010-02-07
No before Ubuntu starts. [http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

---

### Post by angree on 2010-02-07
No way to get into BIOS, there is no text at boot up at all.  My system was working well for about 3 weeks with no issues.  I cant figure out how to do the memory test.  If i boot with no DVD in the drive it will boot up (with no boot up text or anything), if i boot with a disc in it seems to go in to a loop of spinning up then spinning down for about 1-2 minutes then it wont spin at all and wont finish booting.  i only have 1 HDD so there is no way i could just format and install again, which is what i'd like to do heh.. anything else you can think of i can try??  i'm at a loss right now!

Thanks

Angree the NooB

---

### Post by serpentracer on 2010-02-07
so you just get a blank screen with and without a disk in the cd/dvd rom?

I had a older compaq laptop running xp that started doing that.  but it ended up bing a bad sector on the hard drive.
thought for sure it was a memory problem though. I took the hard drive out and then I could see the bios flash.  then I turned it back off put the drive back in, and booted from the windows install disc, and ran check disk (chkdsk) and it fixed my problem.

the only reason I'm posting this is telling you to try to remove the harddrive and see if you get the bios screen.

---

### Post by jken146 on 2010-02-07
One other thing you could try is booting from a USB stick.

---

### Post by TriadHonor on 2010-02-07
Maybe the hard disk, maybe the ram.
First of all be sure that the BIOS don't lock all to prevent damage, it can happen on some BIOS.

If you can't do nothing why don't try an old Windows 98 solution to avoid BIOS lock ?

Take away the power from the PC, then open the case and take off the BIOS battery.
Press the power button for 1-2 minutes, to descharge the accumulators.

Put the battery on again and then the pc to the power, power on and look if it works.

---------

If you don't want to try this solution maybe, as they said, try a **chkdsk **on your hard disk from another pc.
Try to change the ram position and a mem test if you can.

---

### Post by Jackzor on 2010-02-07
> **TriadHonor said:**
> Maybe the hard disk, maybe the ram.
First of all be sure that the BIOS don't lock all to prevent damage, it can happen on some BIOS.

If you can't do nothing why don't try an old Windows 98 solution to avoid BIOS lock ?

Take away the power from the PC, then open the case and take off the BIOS battery.
Press the power button for 1-2 minutes, to descharge the accumulators.

Put the battery on again and then the pc to the power, power on and look if it works.

---------

If you don't want to try this solution maybe, as they said, try a **chkdsk **on your hard disk from another pc.
Try to change the ram position and a mem test if you can.

There is a jumper on the motherboard for that. Just to make that go faster look for that.There would be three pins sticking straight up with a jumper on two of them. Move the jumper to the other pin and try to turn the computer on. It most likely will do nothing. Then move it back. Computer boots up with all bios setting back to default.

That is on every computer including laptops.
 Now. Have you  reset the ram. Try pulling all the ram out of the computer and putting it back in one stick at a time...  One stick. Try booting. If it doesn't work then try another stick. Untill you run out of sticks to try of one of them works. It really  sounds like a ram issue to me.

---

### Post by angree on 2010-02-08
> **Jackzor said:**
> There is a jumper on the motherboard for that. Just to make that go faster look for that.There would be three pins sticking straight up with a jumper on two of them. Move the jumper to the other pin and try to turn the computer on. It most likely will do nothing. Then move it back. Computer boots up with all bios setting back to default.

That is on every computer including laptops.
 Now. Have you  reset the ram. Try pulling all the ram out of the computer and putting it back in one stick at a time...  One stick. Try booting. If it doesn't work then try another stick. Untill you run out of sticks to try of one of them works. It really  sounds like a ram issue to me.


hmm, I've tried all of that now with nothing working.  I can still boot into ubuntu without a disc in the drive, however i still don't have any boot text showing up.  im pretty sure its not a memory or hdd issue.  

Could it be a BIOS issue not recognising the monitor?  

I am using an HP DV9335NR laptop.  specs are:

Intel core 2 duo 1.73mhz
2gb ram
160gb hdd
nvidia GO7600 vid card.

---

### Post by TriadHonor on 2010-02-08
You can try with another monitor, but if it some days ago works, it must work now.

But it can be.

If it is not HD or RAM issue so maybe some partition go wrong, are them all good ?

---

### Post by jken146 on 2010-02-08
If you can boot into Ubuntu, then you must go past GRUB at some point. Try to get into that (you'll have to press escape at some point -- it's right before Ubuntu starts loading) and then you should see the menu where you can test your RAM.

Not being able to see any BIOS messages is worrying. Test your RAM, and if you get errors, test it again one stick at a time.

---

