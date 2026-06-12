---
title: "Swap Partition in ubuntu?"
date: 2010-07-04
forum: General Help
---

### Post by COKEDUDE on 2010-07-04
Does ubuntu install a swap partition by default when installing partitions side by side? I don't see the swap partition. Or do I have to manually set my partition sizes if I want a swap partition? 

[IMG]http://lookpic.com/d2/i2/353/TvCwMzwt.png[/IMG]
[http://lookpic.com/d2/i2/353/TvCwMzwt.png](http://lookpic.com/d2/i2/353/TvCwMzwt.png)

---

### Post by SmokeyThePanda on 2010-07-04
I've only installed it without using the entire space once. However, I am quite sure it didn't set a swap partition. You will probably have to manually set your partitions.

---

### Post by krishnandu.sarkar on 2010-07-04
I think it did set the Swap partition which in whole is termed as "Ubuntu 10.04 LTS". BTW why don't you review your partition changes?? There is an checkbox at bottom which says something like Review your paritions before applying changes. Check it and you'll see the parition table. If it's not been created already create it manually. But probability is it's already created.

---

### Post by COKEDUDE on 2010-07-04
> **krishnandu.sarkar said:**
> I think it did set the Swap partition which in whole is termed as "Ubuntu 10.04 LTS". BTW why don't you review your partition changes?? There is an checkbox at bottom which says something like Review your paritions before applying changes. Check it and you'll see the parition table. If it's not been created already create it manually. But probability is it's already created.

I don't see a checkbox. Take a look at my image.

---

### Post by SmokeyThePanda on 2010-07-04
No, it hasn't created it. The top bar is what's currently on your system. (Unless you have already installed >.>) All that's listed is your XP partition. Set them up manually and use about 1GB for swap.(I think) Put the rest(or however much you want) towards ubuntu. Install and done. :p

---

### Post by -kg- on 2010-07-04
> **SmokeyThePanda said:**
> No, it hasn't created it. The top bar is what's currently on your system. (Unless you have already installed >.>) All that's listed is your XP partition. Set them up manually and use about 1GB for swap.(I think) Put the rest(or however much you want) towards ubuntu. Install and done. :p

Exactly.  At that stage in the installation, no partitions have been created.  It is only at the beginning of the installation, after setting everything up, that partitions will be created in which Ubuntu will be installed.

> I've only installed it without using the entire space once. However, I am quite sure it didn't set a swap partition. You will probably have to manually set your partitions.

It did create a swap partition.  Creating a Swap partition is a standard part of installing Linux.  Have you ever looked at your hard drive using GParted after installation or ran "sudo fdisk -l" in the terminal?  That is the only way you will be able to view a swap partition.  It is not displayed under Nautilus, not even if you run Nautilus from root.  It is also included in your fstab file, which you can view using the "cat /etc/fstab" command in the terminal.

COKEDUDE, you will be totally fine using "Install Them Side By Side", "Specify Partitions Manually", or, since you already have 48.6 GB of free space, you can use "Use the largest contiguous free space."  Any of the selections will create a Swap partition along with the "/" (root) partition, except for "Manual"...you'll have to create the Swap partition manually, along with the rest of the partitions.

The only reason you might want to use Manual partitioning is if you want a non-standard installation, like ext3 formatting instead of the default ext4 (for Lucid...if you're installing Karmic, you could choose ext4 instead of the default ext3) or if you wish to make other partitions, like a separate /home or other partitions, or if you wanted to not use the entire free space available for your installation so you could install another distro in that free space.

---

### Post by COKEDUDE on 2010-07-04
> **-kg- said:**
> Exactly.  At that stage in the installation, no partitions have been created.  It is only at the beginning of the installation, after setting everything up, that partitions will be created in which Ubuntu will be installed.



It did create a swap partition.  **Creating a Swap partition is a standard part of installing Linux.  Have you ever looked at your hard drive using GParted after installation or ran "sudo fdisk -l" in the terminal?**  That is the only way you will be able to view a swap partition.  It is not displayed under Nautilus, not even if you run Nautilus from root.  It is also included in your fstab file, which you can view using the "cat /etc/fstab" command in the terminal.

COKEDUDE, you will be totally fine using "Install Them Side By Side", "Specify Partitions Manually", or, since you already have 48.6 GB of free space, you can use "Use the largest contiguous free space."  Any of the selections will create a Swap partition along with the "/" (root) partition, except for "Manual"...you'll have to create the Swap partition manually, along with the rest of the partitions.

The only reason you might want to use Manual partitioning is if you want a non-standard installation, like ext3 formatting instead of the default ext4 (for Lucid...if you're installing Karmic, you could choose ext4 instead of the default ext3) or if you wish to make other partitions, like a separate /home or other partitions, or if you wanted to not use the entire free space available for your installation so you could install another distro in that free space.

I have :). When I installed Mint I was able to see and set my swap partition with slide bars, so I'm a bit surprised I can't see the swap partition and set it with slide bars. 

Yea I prefer not to manually set my partitions after my first experience doing it manually.

---

### Post by Elfy on 2010-07-04
If the machine you are installing on already has a swap partition that will get used. If not - then after the partition stage of the install you would see something like

/dev/sda5 is being used for swap
/dev/sda6 is being used for /

---

### Post by v1ad on 2010-07-04
what forestpiskie said is correct. but it is still better to do it manually.

---

### Post by Elfy on 2010-07-04
> **v1ad said:**
> what forestpiskie said is correct. but it is still better to do it manually.

Indeed - I always use manual partitioning on installs - but it would seem the OP had some issues with doing it that way.

> Yea I prefer not to manually set my partitions after my first experience doing it manually. I can understand someone not wanting to if problems occurred with setting partitions manually. Though I would also say that once the task is mastered it is much better to do it that way.

---

### Post by jimmers on 2010-07-04
I agree with v1ad, ever since Gutsy I have installed manually at the moment I am running
Swap     2.80 GiB
/           13.97 GiB
/Home   132.28 GiB, and I always back-up my Home Directory.

This is the way I prefer to install, wworks for me, but for you that is up to you.

Luck

---

### Post by SmokeyThePanda on 2010-07-04
> I can understand someone not wanting to if problems occurred with setting partitions manually. Though I would also say that once the task is mastered it is much better to do it that way.

My very first install of ubuntu, I tried to dual boot windows XP(originally on my system) with the new xubuntu OS. I ended up making the sizes too small by booting them side by side(Windows already took up most of my space) I had to go back and manually partition it. I ended up accidentally deleting my windows XP partition. Poof. Gone. :p I think I changed the type liiiikee /ext3 or whatever to something else and it deleted the entire partition. I then had to repartition it. Twas a very long night.

---

### Post by COKEDUDE on 2010-07-04
> **forestpiskie said:**
> Indeed - I always use manual partitioning on installs - but it would seem the OP had some issues with doing it that way.

I can understand someone not wanting to if problems occurred with setting partitions manually. Though I would also say that once the task is mastered it is much better to do it that way.

Its that I'm installing it for a friend and not on my computer. I wanna make sure I do it right on his computer. I don't trust my manual setting abilities yet. 

On my own computer I would love to test it out and figure it out for myself. I would love to learn how. Do you have a good guide on setting partitions manually? 

> **SmokeyThePanda said:**
> My very first install of ubuntu, I tried to dual boot windows XP(originally on my system) with the new xubuntu OS. I ended up making the sizes too small by booting them side by side(Windows already took up most of my space) I had to go back and manually partition it. I ended up accidentally deleting my windows XP partition. Poof. Gone. :p I think I changed the type liiiikee /ext3 or whatever to something else and it deleted the entire partition. I then had to repartition it. Twas a very long night.

I also had a fun experience when Installing Mint for my first time. I of course backed up my data. I unfortunately didn't know installing XP first would make life easier so I installed Mint first. Then I installed XP. I had a very difficult time fixing grub after that. I did figure out eventually after reading several guides :). I wanted to try out the manual partition method and I waisted about 10 GB of my HD and with the way I did it there is no way to fix it without starting fresh.

---

### Post by -kg- on 2010-07-04
> **SmokeyThePanda said:**
> My very first install of ubuntu, I tried to dual boot windows XP(originally on my system) with the new xubuntu OS. I ended up making the sizes too small by booting them side by side(Windows already took up most of my space) I had to go back and manually partition it. I ended up accidentally deleting my windows XP partition. Poof. Gone. :p I think I changed the type liiiikee /ext3 or whatever to something else and it deleted the entire partition. I then had to repartition it. Twas a very long night.

Like Forestpixie, I always manually partition my hard drive for an installation.  I can understand the confusion someone has with partitioning the first few times one attempts it.  I manually partitioned my hard drive the very first time I installed Ubuntu, but I had already been partitioning hard drives for many years (the first partitioning tool I used was Partition Magic Vers 5).

If you'd like to learn more, you can read at the link in my signature block.  While there may be better ways to partition, it's a simple guide on partitioning operations that will help someone with little knowledge on partitioning operations to understand the basics.  How far they take it afterwards is up to them.

One more thing:

I find the partitioning under "Manual" partitioning in the installer to be a bit counter-intuitive.  Another possibility for you is to create the partitions externally using Gparted, either from the ubuntu Live CD or the Gparted Live CD.  Once created, you can boot into the Ubuntu installer and choose the "Manual" method.  Once there, instead of creating the partitions (which are already there) you can just mark the mount points of the partitions you created.

Just a suggestion.  Any of the ways I mentioned will work...use what works for you.:)

---

### Post by -kg- on 2010-07-04
Seems you posted during the time I was composing my last message.

> Its that I'm installing it for a friend and not on my computer. I wanna make sure I do it right on his computer. I don't trust my manual setting abilities yet. 

By all means, then...use one of the other methods I suggested.  They should work well, especially considering the free space already exists.  Then your friend can learn to do all the experimenting with partitioning, if and when he or she is ready for it and wishes to do it.

---

