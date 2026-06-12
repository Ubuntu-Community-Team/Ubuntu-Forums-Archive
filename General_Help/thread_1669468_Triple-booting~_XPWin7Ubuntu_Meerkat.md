---
title: "Triple-booting~ XP/Win7/Ubuntu Meerkat"
date: 2011-01-17
forum: General Help
---

### Post by Taliathion on 2011-01-17
Couldn't find a forum that this would fit in, and I figure this would get seen quickly this way, so here goes.

I have Windows 7 installed, then Ubuntu Meerkat over that, but need to install XP for support for a couple games that won't work on Windows 7.

What, if any, extra steps must I take to have all three working in conjunction?

Thanks Muchly,
Tali

---

### Post by Taliathion on 2011-01-17
This has dropped off the main forum page, so:
Shameless self-bump.

---

### Post by Taliathion on 2011-01-17
I really hate doing this, but I don't want to break anything by installing XP...
*BUMP*

---

### Post by wilee-nilee on 2011-01-18
> **Taliathion said:**
> I really hate doing this, but I don't want to break anything by installing XP...
*BUMP*

Section 2 in this link to get your MS stuff booting together then grub will boot you to the MS boot choice.
[http://www.sevenforums.com/tutorials/8057-dual-boot-installation-windows-7-xp.html](http://www.sevenforums.com/tutorials/8057-dual-boot-installation-windows-7-xp.html)

So I assume your aware of the amount of primary partitions possible on a single HD, if not ask.:)

---

### Post by Taliathion on 2011-01-18
Bookmarked, need to do this tomorrow.
Thanks so much, I was worried there would be all kinds of extra steps to take to get this working.

As a point of interest, I installed Ubuntu twice at one point, one 32-bit, one 64-bit, so my boot menu was

Grub ->Ubuntu (Ubuntu Loads)
Grub -> Windows -> Windows 7 (Win7 Loads) OR
                          -> Ubuntu (Ubuntu Loads)

I removed the Ubuntu under the windows choice, and now have the boot menu

Grub -> Windows 7
Grub -> Ubuntu

Any chance any of my multiple installs will bork anything?

^^As clarification, I have GRUB as my loader, I assume this won't cause any problems, please correct me if otherwise.

Also, one last thing. I've often seen this as an issue, and I see this on this link too:
Using these methods can cause Windows 7 to become unboot-able, requiring a repair with the installation disk.
Buuuut, I have a laptop, so I don't have an install disk.
Will a set of disks made using the Asus (Bloatware) Recovery Burner work?

---

### Post by wilee-nilee on 2011-01-18
> **Taliathion said:**
> Bookmarked, need to do this tomorrow.
Thanks so much, I was worried there would be all kinds of extra steps to take to get this working.

As a point of interest, I installed Ubuntu twice at one point, one 32-bit, one 64-bit, so my boot menu was

Grub ->Ubuntu (Ubuntu Loads)
Grub -> Windows -> Windows 7 (Win7 Loads) OR
                          -> Ubuntu (Ubuntu Loads)

I removed the Ubuntu under the windows choice, and now have the boot menu

Grub -> Windows 7
Grub -> Ubuntu

Any chance any of my multiple installs will bork anything?

^^As clarification, I have GRUB as my loader, I assume this won't cause any problems, please correct me if otherwise.

Also, one last thing. I've often seen this as an issue, and I see this on this link too:
Using these methods can cause Windows 7 to become unboot-able, requiring a repair with the installation disk.
Buuuut, I have a laptop, so I don't have an install disk.
Will a set of disks made using the Asus (Bloatware) Recovery Burner work?

You can mess up here, so read the link carefully. Windows if you had installed XP then W7 you would be okay, but XP after is a problem or can be. Windows combines the bootloading together. If you get the MS correct though grub should pick up the MS combined boot.

I will say that you should be prepared for the worst possible situation, be backed up, and have the ability to reinstall if needed. If you have a W7 pro or above you can image the whole C drive to a external HD just to be safe.

---

### Post by Taliathion on 2011-01-18
Home Premium, alas.
But what I mean to say is that if I suffer utter failure for whatever  reason, will I be able to repair with recovery disks? I have a suspicion  I won't be able to, however, as I encountered a similar situation when  helping a friend with a Hackintosh setup, where we saw multiple pages  with people freaking out that they had destroyed Windows 7 on their  laptops and could not repair using home-made repair disks.

I understand what the article entails, including the section concerning repairing the Windows 7 listing with easyBCD, but what I guess I am ultimately asking is will I be able to use a non-install recovery disk set to repair if I ruin something with this?

---

### Post by wilee-nilee on 2011-01-18
> **Taliathion said:**
> Home Premium, alas.
But what I mean to say is that if I suffer utter failure for whatever  reason, will I be able to repair with recovery disks? I have a suspicion  I won't be able to, however, as I encountered a similar situation when  helping a friend with a Hackintosh setup, where we saw multiple pages  with people freaking out that they had destroyed Windows 7 on their  laptops and could not repair using home-made repair disks.

I understand what the article entails, including the section concerning repairing the Windows 7 listing with easyBCD, but what** I guess I am ultimately asking is will I be able to use a non-install recovery disk set to repair if I ruin something with this?**

To many variables for me to answer this part really. You can make a recovery disc with the W7 a one time and do a back up one time, shot for both with the home premium version.

---

### Post by Taliathion on 2011-01-18
Ok, so then, saying I make back-ups using proprietary or otherwise third party software, and use Asus's Recovery Disk program, couldn't I make multiple sets of each?
Or is it an actual limitation built into the great commercial terror that is Windows 7 designed to convince me to pay way too much for nothing special?

---

### Post by wilee-nilee on 2011-01-18
> **Taliathion said:**
> Ok, so then, saying I make back-ups using proprietary or otherwise third party software, and use Asus's Recovery Disk program, couldn't I make multiple sets of each?
Or is it an actual limitation built into the great commercial terror that is Windows 7 designed to convince me to pay way too much for nothing special?

So I have W7 pro, it has a anytime and as much as you want backup setup and full imaging of the C partition, or any other NTFS partition. There are free ones and paid for ones that will do the same, and I suspect will reload like the on board windows 7 backup with the OS still activated. I have one in my XP setup as well, it doesn't get installed automatically on the XP home install, but is on the XP disc for installation though.

Really I'm not a real knowledgeable person in this area, I have a Image of W7 it just saves time in upgrading, activating, and reinstalling any extras. I don't backup the Linux, I have two external drives where the media is backed up that is my insurance. 

If you want more solid advice on the W7 setup join the windows 7 forum they are quite active and you could get actual various backup programs information and better help then I can give.

---

### Post by Taliathion on 2011-01-18
Yeahhh...
I dislike Microsoft, so I don't wish to associate myself with them in any other way than using their bloated, poorly designed OS to play games.
But, regardless, I will do more research into Recovery, and I thank you muchly for your input, it has been most helpful.

---

