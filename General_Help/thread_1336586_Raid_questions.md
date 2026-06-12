---
title: "Raid questions"
date: 2009-11-24
forum: General Help
---

### Post by PlugInPrius on 2009-11-24
My setup
Ubuntu 9.10 64bit desktop
Intel ich10r

Test environment
1 250BG sata boot drive 
2 250BG sata in raid 1 as data drives  

What I will be running after testing 
2 Intel X25E 32BG in raid 0 as boot drive 
2 250BG sata in raid 1 as data drives  

I know a little bit about Linux since I have been playing with it since around RedHat 5. This will be my first attempt at using Linux as my main OS. I just tried Fedora 12 and I could not get the Nvidia drivers to work and when I tried to configure the raid 1 it mess it up so bad my BIOS lock up when trying to initialize the drives. Dont know why but I had to partition and format the drives before the BIOS would even boot past the drives.  

Anyway to my raid questions.  

I'll try to keep the rest short and to the point and not go into the issues I was having with raid setup.  

Do I need to have the Intel raid BIOS setup to use raid in Linux? Or should I just leave the drives alone and not put them in a raid in the Intel BIOS? Since this is software raid is there an advantage or disadvantage to using the BIOS to setup the raid?

When I had the raid 1 setup in the Intel BIOS Linux would see it in /dev/mapper/blahblah_Lable but I would also see the individual drive partitions as /dev/sda1 and /dev/sdb1  

Now my question is does this /dev/mapper/blahblah_Lable actually act as a raid 1? Is my data safe and will Linux rebuild the array if there is a failure?

I've seen guides on creating raid arrays using mdadm to combine the sda1 and sdb1 into /dev/md0 and then mounting /dev/md0. Is this something I would still need to do if I have /dev/mapper/blahblah_Lable mounted or am I safe with just the /dev/mapper/blahblah_Lable?    

During installation I believe Ubuntu seen the raid 1 as a whole. Am I safe to assume that it will see my raid 0 when I go to install it on that?

---

### Post by Cracauer on 2009-11-24
> **PlugInPrius said:**
> Do I need to have the Intel raid BIOS setup to use raid in Linux? Or should I just leave the drives alone and not put them in a raid in the Intel BIOS? Since this is software raid is there an advantage or disadvantage to using the BIOS to setup the raid?


No. IMHO, Linux md is far superior to any mainboard RAID. Intel's mainboard RAID might not be as horrible as NVidia's, but still.

> **PlugInPrius said:**
> 
When I had the raid 1 setup in the Intel BIOS Linux would see it in /dev/mapper/blahblah_Lable but I would also see the individual drive partitions as /dev/sda1 and /dev/sdb1  

Now my question is does this /dev/mapper/blahblah_Lable actually act as a raid 1? Is my data safe and will Linux rebuild the array if there is a failure?


Not automatically. You'll have to have the appropriate tools to do that.

This is all garbage, IMHO. If you use the Linux md RAID then you have *one* set of well-tested tools that you use on all your RAID systems, no matter who's chipset is on the mainboard. You'll keep that for the rest of your life instead of mucking around with mainboard specific knowledge.

> **PlugInPrius said:**
>  I've seen guides on creating raid arrays using mdadm to combine the sda1 and sdb1 into /dev/md0 and then mounting /dev/md0. Is this something I would still need to do if I have /dev/mapper/blahblah_Lable mounted or am I safe with just the /dev/mapper/blahblah_Lable?    


You only need one. I prefer Linux md.

 > **PlugInPrius said:**
> 
During installation I believe Ubuntu seen the raid 1 as a whole. Am I safe to assume that it will see my raid 0 when I go to install it on that?

No idea how well Ubuntu handles that but it should be pretty easy to plug it in even if it isn't by default.

---

### Post by PlugInPrius on 2009-11-24
I just want to make sure I get this right.

There really is no benefit in setting up the raid in the BIOS right? Its mostly a convince for windows or any OS to see a single drive?

So what I should do is turn off the raid function in my BIOS and let the drives be normal sata drives?

Then setup my raid 0 and raid 1 during the Ubuntu install?

---

### Post by whoop on 2009-11-24
> **PlugInPrius said:**
> I just want to make sure I get this right.

There really is no benefit in setting up the raid in the BIOS right? Its mostly a convince for windows or any OS to see a single drive?

So what I should do is turn off the raid function in my BIOS and let the drives be normal sata drives?

Then setup my raid 0 and raid 1 during the Ubuntu install?

There are actually some disadvantages when compared to software raid (unless you want to multiboot with windows and use raid on both os's).

The most significant disadvantage of fake raid is, that it is not supported by Ubuntu, it uses (often) proprietary drivers and is therefore (in some occasions) less flexible. I.e. what happens if you move your (fake) raid array to another machine, will another chipset be able to read it?

The difference in performance is negligible as fake raid uses the cpu also.

It is possible to create a software raid on an existing ubuntu install as I demonstrated here:
[http://ubuntuforums.org/showthread.php?t=1165328](http://ubuntuforums.org/showthread.php?t=1165328)

---

### Post by PlugInPrius on 2009-11-24
Since I will not be dual booting with windows (I'll actually be using vmware for my few windows needs) I wont need the BIOS raid? 

Ok so it looks like my plan is to disable BOIS raid. Start Ubuntu and create the raid 0 on my two X25E drives. Install Ubuntu on the raid 0. After the install configure the raid 1.

If this sounds good I think I will give it a try in the morning after I back everything up.

---

### Post by whoop on 2009-11-24
> **PlugInPrius said:**
> Since I will not be dual booting with windows (I'll actually be using vmware for my few windows needs) I wont need the BIOS raid? 

Ok so it looks like my plan is to disable BOIS raid. Start Ubuntu and create the raid 0 on my two X25E drives. Install Ubuntu on the raid 0. After the install configure the raid 1.

If this sounds good I think I will give it a try in the morning after I back everything up.

You don't need the BIOS/fake raid, in fact some (me being amongst them) advise against using it, because of the reasons I described earlier. Software raid is ideal in absence of a real raid controller.
If you are doing a clean install you might want to use the alternate cd:
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by PlugInPrius on 2009-11-24
Thanks. I will be doing a fresh install. I have the alternate CD downloaded and ready to burn when I get home.

It looks like this should be pretty easy once I disable the BIOS raid.

---

### Post by Cracauer on 2009-11-25
Sounds right. Sorry for not checking back earlier.

---

### Post by PlugInPrius on 2009-11-26
I would like to say thanks again.

I was able to get Ubuntu installed and all my programs configured and working.



Good by Microsoft! Well all most. I have not found a good alternative to a few apps.

UltraVNC - Need to connect to UltraVNC Repeaters

Money - I'm currently testing Kmymoney. Seems like it will work. I will just miss some of the stuff in Money.

Some games.

Adobe products
Photoshop - I think I can use Gimp for 99% of my needs
Premiere - Have not found a good Linux alternative
Encore - Have not found a good Linux alternative
Dreamweaver - Have not found a good Linux alternative
Acrobat - Have not found a good Linux alternative. I use it to scan documents, OCR, and save to PDF.


But all those will just have to be questions on another topic.

---

