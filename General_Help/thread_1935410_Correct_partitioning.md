---
title: "Correct partitioning"
date: 2012-03-04
forum: General Help
---

### Post by LightReccon on 2012-03-04
Hi guys.

Just installed Ubuntu for the first time and I'm not quite sure that the Ubuntu installer did a good job at partitioning my ssd during installation. 

Take a lookat my partitions here. Shouldn't there just be a main partition (ubuntu) and then a swap partition of at least 8 gb (I have 4 gb of ram)?

I've searched this site and linuxforums but couldn't find an answer. 

Looking forward to your replies :)

---

### Post by cryptotheslow on 2012-03-04
The partition scheme looks fine. It has created the root partition as a primary partition then created an extended partition (sda2) to put the swap partition (sda5) in.

Using an extended partition is sensible as it allows you to create more than the limited 4 primary partitions. i.e. the extended partition takes up one of the possible 4 primary partitions but many logical partitions can be created within it.

However - what does that exclamation mark next to sda5 say when you click on it?

Also - do you intend to hibernate your PC? (This will determine the required size of your swap rather than the now somewhat outdated advice to make it 2x size of RAM).

---

### Post by LightReccon on 2012-03-04
Thank you for your quick reply.

Ah, I see :)

Well, this is what it says. Anotherthing that I find strange is that it puts my ssd at 111,79 gb total capacity but it's a 128 gb drive. What's up with that??

---

### Post by cryptotheslow on 2012-03-04
The size "difference" is not a difference at all it is just down to whether the size is displayed in GB or GiB (Gigabyte or Gibibyte) [http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

Are you still booting from the LiveCD (or USB) or are you booted into the actual installation at this point?

---

### Post by LightReccon on 2012-03-04
I'm running a clean, single boot installation of Ubuntu 12.4.

---

### Post by cryptotheslow on 2012-03-04
Do you intend to hibernate the PC at any point?

---

### Post by LightReccon on 2012-03-04
If its possible I will, yeah. I had trouble with closing the lid causing it to crash so I chose to have it do nothing upon closing the lid and then locking the screen after 5 minutes. That way it doesnt go to sleep but the screen is not on for ever.

BTW, is there a lot of stuff missing in terms of functionality in the 12.4 vs last stable release?

---

### Post by cryptotheslow on 2012-03-04
Ahh... another question... did you take the option to encrypt your home during the install process?

Also what is the make / model of the PC?

As for 12.04 - I've been running it on a laptop here for about 2 months now and other than the odd quirky glitch now and again as software is updated it's been fine. However - as with any alpha / beta software - live in the expectation that it will completely hose itself at any given moment and keep good backups if there is anything important on the machine. Functionality-wise 12.04 seems complete for my purposes.

---

### Post by LightReccon on 2012-03-04
Yay, my newbish questions cometh, hehe.

Yup, I chose that. Does that reduce speed? Sound pretty self explanatory now that you mention it...

It's an Asus Zenbook Ux21e.

Think I might do a fresh install and not choose to encrypt.

---

### Post by cryptotheslow on 2012-03-04
Encrypting makes no noticeable performance difference on modern hardware and for a laptop is a very sensible choice thanks to them being so easily lifted by thieves.

The reason I asked was that when you take the option to encrypt your home, the swap partition also gets encrypted. I am not 100% on this, but I believe the swap is encrypted in place i.e. in the 4GB partition you see there - but because it is encrypted GParted cannot determine what it is. It is also not mounted in the typical way so shows as unmounted. (This is my understanding but may not be reality :D ).

If you open a Terminal (Ctrl Alt T) and enter:
```
cat /etc/fstab
```

you should note a couple of lines like this:
```
# swap was on /dev/sda5 during installation
#UUID=b43187e0-1f18-4d29-ae6e-398b0717deb0 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```

Your UUID value will be different. Note the 2nd line is commented out with a #. During the installation the swap partition is created unencrypted initially and that entry made in fstab. Then when you take the option to encrypt the entry is superseded by the one below which basically pipes the now encrypted partition through mapper.

The laptop I have 12.04 on is also an Asus (X54H) and also would not suspend / sleep correctly on closing the lid initially. Have a look at post #2 here:
[http://ubuntuforums.org/showthread.php?t=1916751](http://ubuntuforums.org/showthread.php?t=1916751)

That workaround there cured it for me. Apparently it is quite a common problem on Asus laptops.

---

### Post by LightReccon on 2012-03-04
Hehe, well I live on an island in Denmark. We have no crime :)

Ah, that makes sense. I just understand why it need to think at all when i navigate my folders. I ought to just jump up instantaneously. However this could be due to the UI. I don't know:)

Have a look at this screen shot.

---

### Post by cryptotheslow on 2012-03-04
That fstab looks normal. Also GParted shows the same warning for my swap too (screenie attached).

What is the output of:
```
mount -l
```

And yes - particularly with an SSD you should get no delay navigating between directories at all.

---

### Post by cryptotheslow on 2012-03-04
Oh - something just came to mind. Partition alignment to sectors is apparently very important for performance on SSDs. It may be worth checking out:

[http://www.linux-mag.com/id/8397/](http://www.linux-mag.com/id/8397/)
[http://www.wwpi.com/index.php?option=com_content&view=article&id=8840:ssd-storage-demands-proper-partition-alignment&catid=99:cover-story&Itemid=2701018](http://www.wwpi.com/index.php?option=com_content&view=article&id=8840:ssd-storage-demands-proper-partition-alignment&catid=99:cover-story&Itemid=2701018)
[http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance](http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance)

You can resize or move partitions to align them using GParted from a LiveCD / USB if necessary.

I'm no expert on this so do some reading first :D

---

### Post by Khayyam on 2012-03-04
> **cryptotheslow said:**
> The partition scheme looks fine. It has created the root partition as a primary partition then created an extended partition (sda2) to put the swap partition (sda5) in. Using an extended partition is sensible as it allows you to create more than the limited 4 primary partitions. i.e. the extended partition takes up one of the possible 4 primary partitions but many logical partitions can be created within it.

Yes, but you can have 3 primary and 60 logical (with IDE) so there is no real reason to use extended unless you need more than 4. Even if you create 3 primary you can still expand to 60 logical, so it's really not that 'sensible' unless the requirements are >3. The advantage of primary partitioning for systems with <4 partition requirements is that everyone can count, and they needn't wonder about the limitations of primary partitions when presented with 1=sda1, 2=sda5.

Ultimately it doesn't matter, partitions are partitions whether primary or logical, but its not 'sensible' when only 2 or 3 partitions are required.

best ... khay

---

### Post by LightReccon on 2012-03-04
Thanks for your replies. Very helpful. I think Ill give this beta a coupe of more days and then install last stable release :)

I guess, if I do a clean install, the Ubuntu installer will partition my disk in a way that is most optimal?

---

### Post by Khayyam on 2012-03-04
> **LightReccon said:**
> I guess, if I do a clean install, the Ubuntu installer will partition my disk in a way that is most optimal?

The jury is out on that one ... it will do it, which is enough.

best ... khay

---

### Post by oldfred on 2012-03-04
If you are not going to have Windows on the SSD, you may want to consider using gpt in place of MBR as suggested by the Arch link below. 

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) - SSD
[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)
[]("https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT")

---

### Post by LightReccon on 2012-03-04
Wouw, thank you. I can see that alignment is pretty important, if not essential.. I'm gonna have to track down some Linux techie to help me with this stuff. I'm not confident fiddling with partitioning and so on, especially as ssd's have limited write as I can understand.

---

### Post by Khayyam on 2012-03-04
> **LightReccon said:**
> [...] I'm gonna have to track down some Linux techie to help me with this stuff. I'm not confident fiddling with partitioning and so on, especially as ssd's have limited write as I can understand.

This depends on what class the SDD is, some information can be found on [Anandtech](http://www.anandtech.com/show/2738).

best ... khay

---

### Post by cryptotheslow on 2012-03-04
> **Khayyam said:**
> Yes, but you can have 3 primary and 60 logical (with IDE) so there is no real reason to use extended unless you need more than 4. Even if you create 3 primary you can still expand to 60 logical, so it's really not that 'sensible' unless the requirements are >3. The advantage of primary partitioning for systems with <4 partition requirements is that everyone can count, and they needn't wonder about the limitations of primary partitions when presented with 1=sda1, 2=sda5.

Ultimately it doesn't matter, partitions are partitions whether primary or logical, but its not 'sensible' when only 2 or 3 partitions are required.

best ... khay

So for the Ubuntu installer to set it up that way on an empty drive is 'sensible' as it has no way of knowing what else you may want to install at a later time or what requirements that something else may have as regards needing a primary partition or not - so 'sensible' not to tie up a primary partition just for swap.

---

### Post by LightReccon on 2012-03-04
Guys, just reinstalled with 11.10 with no encryption. Take a look at my partitions here.Looks much better to me and it hasn't crashed or lagged at all. Guess Asus Zenbook + 12.4 is a bad mix :)

---

### Post by Khayyam on 2012-03-04
> **cryptotheslow said:**
> So for the Ubuntu installer to set it up that way on an empty drive is 'sensible' as it has no way of knowing what else you may want to install at a later time or what requirements that something else may have as regards needing a primary partition or not - so 'sensible' not to tie up a primary partition just for swap.

Yes, "it has no way of knowing", but it does it anyway, so "sensible" to whom? Not the user because "know" it or not, it doesn't matter. That's precisely the problem I have with it. The user is removed from the equation, and then the decision made by the installer is presented as "sensible". Its not sensible in any meaningful sense of the word, because "it" has no understanding. If it were inadvisable to use primary partitions then no one would, but most people infact do, because their needs are such that they need nothing more than the two, three, or four, partitions provided by primary partitioning.

Anyhow, I'm not going to loose any sleep over it, its an issue that has very little to be argued either way, however, the idea that computing should be left to computers, and that 'users' are a problem requiring 'sensible' solutions, is one that has become so widespread, and self-fulfilling, that I think its time it was seriously challenged. The question of "usability" has become more a question of "disability", and we all look to solutions provided by something more capable than ourselves. But human "capabilities" are not innate, they are gained in the process of doing, making, practice, etc .. and in the absence of doing, making, practice, etc, you have this nexus of 'disablity interfaces' (which is very much the direction that computing has taken since the advent of the personal computer, because the model is not bi-directional, but interface => user ... where "interface" could be replaced with "service provision" and what-have-you).

No doubt another discussion ... and no doubt I digress ...

best ... khay

---

### Post by LightReccon on 2012-03-05
Great debate :) I doub't such a thing could have happened on a Windows forum ,hehe.

---

