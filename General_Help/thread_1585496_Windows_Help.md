---
title: "Windows Help"
date: 2010-09-30
forum: General Help
---

### Post by uzzo2 on 2010-09-30
Hi guys, please don't castrate me for posting this one, I need some advice on my XP box.I have an old Dell Dimension 2400 with XP that has a WD 40GB model# WD-XL80SD-2 that has run out of space now matter how hard I try and keep it clean. I called Tigerdirect this morning and ordered a Hitachi 500GB hard drive model# OF10381, here's my dilemma. I really want to just do away the old hard drive and use the new one but it seems as if there's not a real good way to copy the entire hard drive including the OS. I have been told that you can use a program such as norton ghost to do it. I do though have a Windows 7 disc, I am going to use a SATA host PCI card to connect the new HD. I am just wondering if I should back everything up from the old HD except for the OS. And then unplug the old HD and just do a fresh install with the Windows 7 disc. Here's the PCI card I ordered, [http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=1082348&SRCCODE=WEBLET03SHIP&cm_mmc=Email-_-WebletMain-_-WEBLET03SHIP-_-03ship](http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=1082348&SRCCODE=WEBLET03SHIP&cm_mmc=Email-_-WebletMain-_-WEBLET03SHIP-_-03ship)
 Thanks in advance for any advice.

---

### Post by CharlesA on 2010-09-30
If you are going to be using a sata drive instead of an IDE drive, cloning the OS onto the new drive will probably not work, since it won't have the drivers to access the hard drive.

Worth a shot, I suppose.

---

### Post by searchfgold6789 on 2010-09-30
Your hard drives are:
<40gig with windows 7>
<500gig empty>
What you wanna do is, plug in both (you can do this, correct? I dunno!), boot Windows from the 40gig and get the drivers on there.
Then boot a linux live CD. Copy the partition on the 40gig to the 500 gig.
Unplug the 40gig. Boot from the Windows 7 dvd and choose your language and keyboard etc. Choose the repair option.
Type: ```
bootsect /nt60 ALL
X:\windows\system32>bootrec /FixMbr 
```
Reboot.
Register Windows again if prompted.
Have fun and good luck,
 - search

---

### Post by uzzo2 on 2010-09-30
> **searchfgold6789 said:**
> Your hard drives are:
<40gig with windows 7>
<500gig empty>
What you wanna do is, plug in both (you can do this, correct? I dunno!), boot Windows from the 40gig and get the drivers on there.
Then boot a linux live CD. Copy the partition on the 40gig to the 500 gig.
Unplug the 40gig. Boot from the Windows 7 dvd and choose your language and keyboard etc. Choose the repair option.
Type: ```
bootsect /nt60 ALL
X:\windows\system32>bootrec /FixMbr 
```
Reboot.
Register Windows again if prompted.
Have fun and good luck,
 - search

I wasn't planning putting Linux on this computer, I have a separate box that is dedicated to Linux. I have them networked, the 40GB HD is plugged into an IDE header. I bought a PCI card that will convert for the SATA drive.

---

### Post by CharlesA on 2010-09-30
Do you want to transfer the existing install of XP to the new drive or just install 7 on it?

The OP looks like you just want to transfer the install to a larger drive.

Check out clonezilla, but I don't know if XP will boot off of a SATA card without the drivers.

---

### Post by uzzo2 on 2010-09-30
> **CharlesA said:**
> Do you want to transfer the existing install of XP to the new drive or just install 7 on it?

The OP looks like you just want to transfer the install to a larger drive.

Check out clonezilla, but I don't know if XP will boot off of a SATA card without the drivers.
I want to do whatever is going to be easier, I am wondering if I can plug the new SATA HD in via the PCI card and back up all the files from the old HD onto it. Then, unplug the old HD and do a fresh install with the Windows 7 disc. The 7 disc my MIL gave to me, it was an upgrade she got for her HP that originally came with Vista. For some reason they sent her 2 of them and she gave me one. I don't have a problem with XP other than the obvious reasons that I put Linux on the computer that I built myself from a barebones kit. I have very little experience with Vista, but from what I did see I didn't like it at all. I haven't even seen Windows 7 yet so I can't give an opinion one way or the other.

---

### Post by CharlesA on 2010-09-30
I don't think you can upgrade directly to 7 from XP, but I could be wrong.

It would probably be easier to just clone the drive and then go from there. In any case, you'd still have all yer data on the old hard drive, so if something happens or gets messed up, you can just clone it over again.

---

### Post by Mark Phelps on 2010-09-30
OK, so you have two Win7 disks, right? Do you have two serial numbers as well?

Because if you don't, you will NOT be able to activate your copy -- since the other copy has (apparently) already been activated in upgrading the HP.

And, once again, you should be going to the Windows7 forum  to get Win7 advice -- because they would have told you (as I am about to) that you CAN update directly from XP to Win7, you just can't do it directly with MS software.

Laplink makes a product that allows you to perform the old XP-to-Vista in-place upgrade but now with XP-to-Win7.  MS used to provide this same software for Vista, but they bought out the only other company that did it, and then discontinued both products! Laplink, however, is back into the business of providing upgrade software.

---

### Post by uzzo2 on 2010-10-01
Okay, sounds like I just need to clone the old hard drive and just keep XP, thanks guys.

---

### Post by HermanAB on 2010-10-01
Well, you are going through all the painful problems of running an old OS on new hardware.  The way around that is to virtualize it.  In the long run, you will do better with Linux as the OS and Windows in a VM on either VMware Player or Virtualbox.

---

### Post by uzzo2 on 2010-10-01
> **HermanAB said:**
> Well, you are going through all the painful problems of running an old OS on new hardware.  The way around that is to virtualize it.  In the long run, you will do better with Linux as the OS and Windows in a VM on either VMware Player or Virtualbox.
Sounds complicated to me, I have very limited computer tech skills. I have to keep things as simple as possible, the box that I have Linux installed on was a barebones kit that I built myself. Before that, as far as I had ever went inside a computer was adding a stick of RAM to this XP box.

---

### Post by uzzo2 on 2010-10-19
Well guys, I finally got around to adding the new HD, I tried cloning the old one with clonezilla and couldn't get it to work right for some reason. So then I downloaded Macrium Reflect which is much more user friendly, but you had to back it up to a portable storage device. I tried several times backing it up on DVD's but I kept getting read errors. I went ahead and ordered 2 new optical drives for it. I installed them sunday and did it all over again, backed it up onto 5 DVD's. I went through the verification process and then went to restore it all. It got to last disc and gave another error. I gave up on Macrium and downloaded clonezilla live again, I was able to get it to work this time. The only problem is that it's showing the new HD the same size as the old one for some reason. It's also trying to boot from the old drive for some reason. At bootup, I get a error that says "primary drive 0 not found, press F1 to continue or F2 to run the setup utility. You can press F1 and it boots right up so I guess that's not a real big deal. I was just wondering if anyone has any experience with this particular problem and clonezilla.

---

### Post by marshmallow1304 on 2010-10-19
Depending on how you cloned the old partition, the new partition might be the same size, so you have a 40 GB partition on a 500 GB hard drive.  You can boot up a LiveCD of Ubuntu or any distro with GParted and use that to resize the partition to fill the disk.

I'm guessing that the "primary drive 0 not found" error is due to the BIOS expecting an IDE drive.  You can probably go into the BIOS setup and set Primary Drive 0 to "Disabled" or "None" to get rid of that.

---

### Post by uzzo2 on 2010-10-19
> **marshmallow1304 said:**
> Depending on how you cloned the old partition, the new partition might be the same size, so you have a 40 GB partition on a 500 GB hard drive.  You can boot up a LiveCD of Ubuntu or any distro with GParted and use that to resize the partition to fill the disk.

I'm guessing that the "primary drive 0 not found" error is due to the BIOS expecting an IDE drive.  You can probably go into the BIOS setup and set Primary Drive 0 to "Disabled" or "None" to get rid of that.
I really don't remember clonezilla giving me any options as far as partitioning goes. So you're saying that an ubuntu live CD with GParted will reformat the new HD to show the rest of the space on the drive? How do I find this program and do I actually have to install it or can I just run it from the disk?

---

### Post by marshmallow1304 on 2010-10-19
Just boot the Ubuntu CD as if you were going to install, but click the "Try without installing" option.  Then run System->Administration->GParted.  If your partition is indeed too small, right click it and click Resize/Move.  Drag the slider to fill the unused space, click OK, then apply.  If you're concerned about messing something up, post a screenshot of GParted before you do anything.

---

### Post by uzzo2 on 2010-10-19
> **marshmallow1304 said:**
> Just boot the Ubuntu CD as if you were going to install, but click the "Try without installing" option.  Then run System->Administration->GParted.  If your partition is indeed too small, right click it and click Resize/Move.  Drag the slider to fill the unused space, click OK, then apply.  If you're concerned about messing something up, post a screenshot of GParted before you do anything.
Okay, thanks a heap for the advice my friend, I am downloading 10.04 now. I'll burn the CD in the morning and give it a shot, if I have any trouble, I'll post it here.

---

### Post by sandman6471 on 2010-10-20
Just back up what you want to keep off the 40gb drive to a dvd or a usb drive. Do a clean install of windows 7 on your new drive. Then just copy your saved data over to your new windows 7 drive. Seems easier to me and no headaches with trying to transfer a complete system over, which you take a chance on not booting anyway. Besides XP is a good system but, it is on it's way out.

Linux is Great......
Take Care Everyone....

---

### Post by uzzo2 on 2010-10-20
> **sandman6471 said:**
> Just back up what you want to keep off the 40gb drive to a dvd or a usb drive. Do a clean install of windows 7 on your new drive. Then just copy your saved data over to your new windows 7 drive. Seems easier to me and no headaches with trying to transfer a complete system over, which you take a chance on not booting anyway. Besides XP is a good system but, it is on it's way out.

Linux is Great......
Take Care Everyone....
Well, I have already cloned the old HD to the new one with clonezilla. As I was saying in a previous post, it cloned it but when you go to My Computer and right click on drive C and properties. It shows it being the same exact size as the old HD for some reason. I suppose I could just backup all the files and folders and do a fresh install of Windows 7. I just haven't seen yet, I am just wondering if it's better than vista. Please don't get me wrong, I love this Linux machine I built a couple of years ago. I just upgraded about a month ago from ubuntu 8.04, I let a guy talk me into trying Mint 9. I lost everything when I made that switch. I kept having graphics issues that I couldn't get resolved with NVIDIA. I followed a post over on another thread on upgrading the NVIDIA drivers. It wouldn't let me do that without disabling the nouveau driver. I didn't read all of the directions associated with that and went to synaptec manager and unistalled 2 packages related to nouveau. That was a BIG mistake, I lost everything again. I had to start all over again with downloading ubuntu 10.04, I posted that on the same thread. Another guy replied that I should go ahead and upgrade to 10.10, I was thinking good god, I can't do this again. He told me how to do it from the terminal without losing anything. I am still trying to learn Linux even though it's been a couple of years now. When everything is working right, it's a much superior OS to Windows IMO. I just don't know enough about it yet, my windows machine is my security blanket I guess is what I am trying to say.

---

### Post by uzzo2 on 2010-10-20
> **marshmallow1304 said:**
> Just boot the Ubuntu CD as if you were going to install, but click the "Try without installing" option.  Then run System->Administration->GParted.  If your partition is indeed too small, right click it and click Resize/Move.  Drag the slider to fill the unused space, click OK, then apply.  If you're concerned about messing something up, post a screenshot of GParted before you do anything.
That did the trick, I wound up after everything was said and done.
Total size: 454GB
Free Space: 433GB

Worked like a charm, thanks again!

---

