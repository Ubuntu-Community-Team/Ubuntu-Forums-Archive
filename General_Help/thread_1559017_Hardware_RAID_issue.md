---
title: "Hardware RAID issue"
date: 2010-08-23
forum: General Help
---

### Post by miststlkr on 2010-08-23
I have an Asus M4A87TD Evo and used the BIOS utility to set up a RAID 5 array, but I can't seem to access it from within the system.   The BIOS shows it as being set up correctly, but I am not sure what I'm doing from here.  I imagine I have to mount it like any other drive?

---

### Post by john newbuntu on 2010-08-23
I think you have SATA raid (fakeraid).  Depending on your raid config in BIOS, windows may automatically recognize it and use the appropriate drivers.  However, Ubuntu sees each disk as it is(3 or more in your case).  Follow this article on installing Ubuntu on fakeraid systems.
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by miststlkr on 2010-08-23
hrm.  Not what I was hoping to hear, but thanks for the reply.   The link they provide to the HowTo assumes that I want to boot off of the RAID array.  In my case, I am booting off of an SSD and want the RAID array separate for storage only.  I'll look more into the fakeRAID tomorrow and see what I can come up with.  

This was to be my second array, the first was under windows and worked as intended [for a change...]  Thanks for your time answering stupid noob questions.

---

### Post by john newbuntu on 2010-08-23
Well in that case you need to set up you /dev/mapper device (gparted can help you here) and mount it in fstab to use the fakeraid for storage.

---

### Post by ronparent on 2010-08-23
Note that if you are using 10.04 the 'FakeRaidHowto' is out of date. How you would have to proceed is not currently documented. Currently gparted will not automatically see a raid and you have to employ a work around. Although an upstream fix is underway, it is still pending. Also in either 9.10 or 10.04 you shouldn't need to mount a raid partition to see it in the file browser unless for some reason dmraid is unable to see the partition - that would require fixing first. The question may be is your MB raid chip set supported by dmraid for raid 5 (it most likely is).

---

### Post by john newbuntu on 2010-08-23
@ronparent: This link indicates that gparted 0.5.0 does add support for dmraid: [http://gparted.sourceforge.net/news.php?alles=alles](http://gparted.sourceforge.net/news.php?alles=alles)  
Has this been revoked or is an older version shipped with Ubuntu 10.04? I know I should have checked the version in liveCD first.

---

### Post by ronparent on 2010-08-23
See [https://bugs.launchpad.net/bugs/600729](https://bugs.launchpad.net/bugs/600729)

It reportedly is fixed upstream but hasn't shown up yet in the distro, as far as I know. In answer to your question, in intent, it is supported and in fact will be as soon as the fix shows up in the distro. Meanwhile you either have to pre-create a formatted target partition or install kpartx to a live cd session prior to installing because otherwise the install will fail because gparted will not otherwise format a target partition during the install.

---

### Post by miststlkr on 2010-08-23
Thanks you, gentlemen.  My board uses a JMicron JMB361 SATA controller which does not seem to play well with others at the moment.  Oddly enough, when I disabled RAID earlier, I found both of the RAID setups that i had previously tried displayed in palimpsest.  I am tinkering with it now and trying to get it sorted.  I get an error just before the Ubuntu splash screen but it flashes by too quick to read.    As of right now, neither gparted nor palimpsest acknowledge any RAID arrays and the /dev/mapper/ directory is empty other than a file called "controller".  I will try a RAID10 or a JBOD to see if perhaps it is only level 5 causing the issues.


Thanks again for your help and suggestions!!


-- Update --
 Setting up as a JBOD gets recognized as a 2TB HDD by palimpsest with a device listing in the /dev/mapper/ directory... but it also lists a 500GB drive in the /dev/mapper/ location, not sure where that came from or what it is.   gparted recognizes neither at the moment.   Back to tinkering.  Thanks for pointing me in a direction.


-- Update 2 -- 
The JBOD was successfully partitioned and formatted by gparted when I ran it manually from the terminal using the location that palimpsest had for it.  It is currently mounted and functioning as a 2TB HDD [well... 1.82TB, but who's counting...] as far as Nautilus is concerned.   While common sense would say to be happy with what I have working here, I'm going to keep tinkering and see if I can get the level 10 array running.  That would narrow it down to a lack of support for level 5 I believe, yes?

---

### Post by ronparent on 2010-08-24
Yes and no. The command 'dmraid -l' shows support for level 5. I've noted glitches in fakeraid behavior, however, so that is not guaranteed (but should be)! 

The keys to ultimately getting it to work, if possible, are to 1) verify with the live cd that gparted recognizes the raid for the installer to work 2) accept that the grub boot loader install will probably fail and be prepared to fix grub from a live cd after the fact.

---

### Post by miststlkr on 2010-08-25
ronpartent - thanks for the help.  I won't have time to work on this tonight as I just got in from a 15 hour day and I have a good seven hours before I have to be back at it, but a quick look at the terminal using th command you mentioned (*dram -l*) gives me a list which is presumably brands of controllers followed by the levels supported for that brand, in which case my relevant line is ```
jmicron : JMicron ATARAID (S,0,1)
```  I'm not sure what the S stands for, but I am guessing that it would indicate that levels 10 and 5, while supported by my controller, are not [yet?] supported by dmraid for my setup.  Again, without hving had time to look into it at all, I dis also notice the line ```
pdc     : Promise FastTrack (S,0,1,10)
``` which caught my eve because all of the arrays in the /dev/mapper/ directory were listed as pdc _[string of apparently random characters], and pdc does seem to indicate that it supports level 10, though still not level 5.  If I am reading that display correctly, I would need an nvidia RAID controller/chipset in order to have a supported hardware raid 5 array through dmraid.  


I appreciate the food for thought and look forward to diving back into this tomorrow when I have some time and can focus a bit better.

Cheers!

---

### Post by ronparent on 2010-08-25
I read that S as a 5 (I know, confusing).

---

### Post by miststlkr on 2010-08-25
Perhaps.   Some of the other options specifically list a "5", not sure why they would have used an "S" instead on some.   I haven't had time to look into it yet though, maybe it is explained in the docs

---

### Post by ronparent on 2010-08-25
Your right. S is not 5. It stand for Span.

By the way, if you want to know more about dmraid, try 'man dmraid' in a terminal.

---

### Post by miststlkr on 2010-08-26
For those playing along at home, I used palimpsest to set up a fully software-based RAID 0+1 setup tonight.  I might try for a hybri hardware/software setup this wekeend when I next have time to mess with things since it doesn't appear that my controller supports nested raid arrays natively.  I suppose I might run a palimpsest benchmark on each variant [hardware, software and hybrid] to make this of some use to someone in the future.

As it stands, my software-only nested 0+1 array clocked in at:

Min Read: 48.5 MB/s
Max Read: 112.3 MB/sec
Avg: 90.5 MB/s


I doubt anyone cares, but I'll post how/what it changes when I set up the hybrid array in a couple days.



Cheers!

---

