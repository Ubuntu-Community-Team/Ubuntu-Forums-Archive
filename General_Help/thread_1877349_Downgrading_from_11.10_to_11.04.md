---
title: "Downgrading from 11.10 to 11.04"
date: 2011-11-07
forum: General Help
---

### Post by joeturtle on 2011-11-07
I've been playing around with Ubuntu 11.10 since the stable was released, and although it has the potential to be an amazing operating system, many apps that worked fine on 11.04 have gotten much slower while others refuse to work properly at all. (Notably: Audacity freezes when loading an MP3 and GIMP runs much slower. Pithos loads to a white screen and becomes a CPU hog). So until all these problems are fixed (or at least a majority of them), I'm going to have to stick with an operating system that I know works with all of these apps. 

But I'm stuck as to how I should downgrade my operating system. I'm away from home and have limited access to anything, really. All I have is one 4GB flashdrive. And I have about 20GB of files that I would like to be carried over to the new OS. What would be the best way to do this? I was thinking about using harddrive partitions. Setting up enough space for Ubutnu 11.04 and all the files I need, copying them over there and then deleting the 11.10 partition. The only problem with this is that I've never partitioned anything before. (And I don't even know if this is the best choice for me or not to do...maybe there is an easier option I don't know about?)

So I'm asking what do you suggest I do? What programs should I use? And all that type of thing...

Also, I might want to dual-boot 11.04 and 11.10 (11.10 works fine for tasks like websurfing and really do like the Gnome 3 shell a lot...). How would you suggest I set that up? I'm a near-noob when it comes to things like this, so any help would be appreciated!

Thanks so much for your help!

---

### Post by pavi_elex on 2011-11-08
Can you download iso file of ubuntu 11.04, then using only pen drive you can install 11.04 without erasing drive data, only file system data will be removed.

---

### Post by elliotn on 2011-11-08
partition your drive and install 11.04 then move your files to the new partition

---

### Post by linuxaddix on 2011-11-08
11.04 was my favorite ubuntu but 11.10 is really nice.i have gimp and it runs the same speed as any other distro.i see a lot of complaints about people saying this and that is laggy.in my opinion i think one should really look at the way they set up their swap/or partitions.ive noticed that using the erase entire disk option from installation screen sets up a crazy swap area.maybe you have a conflicting hardware.its not the distro its your set up.thats just mho.

---

### Post by Hylas de Niall on 2011-11-08
> **linuxaddix said:**
> 11.04 was my favorite ubuntu but 11.10 is really nice.i have gimp and it runs the same speed as any other distro.i see a lot of complaints about people saying this and that is laggy.in my opinion i think one should really look at the way they set up their swap/or partitions.ive noticed that using the erase entire disk option from installation screen sets up a crazy swap area.maybe you have a conflicting hardware.its not the distro its your set up.thats just mho.

I think there may be a lot of truth there.
If the problems were rooted in 11.10 itself, folk would all be having very similar issues.
I have 11.10 set up on three vastly different machines* and it runs beautifully on all three, straight out the box (i'm no CLI guru, more's the pity).

*Lubuntu 11.10 on a 7 year old laptop
 Ubuntu 11.10/Unity(3D) on a 3 year old netbook
 Ubuntu 11.10/Gnome Shell on a 2 year old bog standard desktop

---

### Post by castrojo on 2011-11-18
Don't boot off the 11.04 CD to do this, it won't work, please see this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/891711](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/891711)

---

### Post by nipunshakya on 2012-01-23
> **linuxaddix said:**
> 11.04 was my favorite ubuntu but 11.10 is really nice.i have gimp and it runs the same speed as any other distro.i see a lot of complaints about people saying this and that is laggy.in my opinion i think one should really look at the way they set up their swap/or partitions.ive noticed that using the erase entire disk option from installation screen sets up a crazy swap area.maybe you have a conflicting hardware.its not the distro its your set up.thats just mho.
Mate, even i had to downgrade from 11.10 to 11.04. reason?? well thats coz my machine often hangs up...it was almost like using a p-II computer here.Eg: When i try to copy a file and play audio at the same time, the process that gets started later gets hung up and then, bam....after few seconds or so, the black screen would turn to working screen again.Swap area was good enough too.But the startup and shutdown time was irregular. In ubuntu 11.04 earlier, i had a shutdown time of 3 seconds. After installing ubuntu 11.10, it would load in 1 min 15 secs, 20 secs late than my previous 11.04. 
I did a manual partition before installing linux 11.10 but still i had those errors. So there is no point of blaming just the hardware only.

---

### Post by nipunshakya on 2012-01-23
@joeturtle :

hi. if you have a flash drive, i suggest you create a live usb, boot from it, select the ubuntu 11.10's root(marked as '/') partition ,format it and then install ubuntu 11.04 to it. If you need more details regarding partition schemes, look [HERE]("http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/")

Hope that helps. Ask freely if u need any assistance regarding the installations ..

Regards,WinuxUser

---

### Post by xyzzyman on 2012-01-23
> **WinuxUser said:**
> @joeturtle :

hi. if you have a flash drive, i suggest you create a live usb, boot from it, select the ubuntu 11.10's root(marked as '/') partition ,format it and then install ubuntu 11.04 to it. If you need more details regarding partition schemes, look [HERE]("http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/")

Hope that helps. Ask freely if u need any assistance regarding the installations ..

Regards,WinuxUser

DO NOT LISTEN TO WINUXUSER!! As you have everything on one partition that will cause you to lose all 20GB's of your data!!

---

### Post by nipunshakya on 2012-01-23
> **xyzzyman said:**
> DO NOT LISTEN TO WINUXUSER!! As you have everything on one partition that will cause you to lose all 20GB's of your data!!

OK i have assumed that JOETURTLE has made 3 partitions in his current OS:  / , /home and swap-area. So if he just formats the / area, how on earth will he affect his /home and loose all his data? make me clear at this point MR. xyzzyman

---

### Post by overdrank on 2012-01-23
Ok the op (original poster) has not responded since posting this thread. So maybe wait for the op's input. :)

---

### Post by nipunshakya on 2012-01-23
I guess that would be fine admin, even i don't know why people take it personally when it comes to suggesting some good piece of advice. I just suggested what i actually did when downgrading from 11.10 to 11.04 myself...and worked perfect for me...just don't know why people don't use polite way of arguing instead of making it a harsh way.

---

### Post by xyzzyman on 2012-01-23
> **joeturtle said:**
> The only problem with this is that I've never partitioned anything before.

^^^

11.04 and 11.10 default to just a / partition and a swap partition. He'd have had to set the partitions up to have a seperate home partition. He also already said he had just a 4GB USB drive.

---

