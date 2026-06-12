---
title: "BT wiped Ubuntu 9.10 install?"
date: 2010-03-13
forum: General Help
---

### Post by brickhead248 on 2010-03-13
Hello Ubuntu Forums peoples.

As with almost every time i try to simultaneously install two operating systems, i have incurred the wrath of GRUB. It's probably more to do with my laptop's terrible hard drive, but heres my problem:

I had a 9.10 install and a swap space on this hard drive, then i used GParted from the BT live CD to resize shrink the Ubuntu partition to make space for a BT install. I booted into Ubuntu just to make sure it was working fine. it was. Then i went back in to the BT live CD to install it on the free space.

When i booted up after install, the GRUB screen had changed (obviously), but now only the BT installation (which appeared as Ubuntu 8.10 for some reason) would boot, The previous Ubuntu installs had stopped working, and now came up with "file missing" or "file not found" (cant remember)

i tried fsck -v /dev/hda1 (where my 9.10 installation was), and it didnt seem to have any errors.

What's wrong with my computer (or GRUB)?

---

### Post by howefield on 2010-03-13
Forgive my ignorance (or stupidity), what is BT ?

You could try the following in terminal

```
sudo update-grub
```

---

### Post by louieb on 2010-03-13
What is BT?

Need more information - follow the [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280") and put the results.txt file in your next post.

---

### Post by brickhead248 on 2010-03-13
Sorry! i didnt realise people can't read my mind, you'll go "ahhhh" when i say this: BackTrack.
I'm using version 4

---

### Post by brickhead248 on 2010-03-13
so does anyone have any ideas? working install, installation on parallel partition causes GRUB to not find the kernel.

---

### Post by hansdown on 2010-03-13
It seems, that BT has installed the 8.10 bootloader.

When you first boot up, can you see the 9.10 kernel?

This tutorial is for a windows install, after ubuntu, but it should help.

[http://linux.dipin.info/2009/06/restore-grub-boot-loader.html](http://linux.dipin.info/2009/06/restore-grub-boot-loader.html)

---

### Post by 2hot6ft2 on 2010-03-13
The best way to do it is to install BT4 first.
Then install Ubuntu 9.10
If you use ext4 for the 9.10 install BT4 wont see it.
You have to boot into 9.10 and run update-grub for grub2 to show both BT4 and 9.10.

I triple boot. Win7 (beats me why since I never use it), BT4 and Ubuntu 9.10.

You can still edit menu.list in BT4 since it uses Grub legacy, and yes BT4 is using Ubuntu 8.10 as it's base now that's why it shows 8.10.

You can fix it by using the livecd to reinstall grub2 just be sure to point it to 9.10 when doing so NOT BT4 8.10

Using Ubuntu 9.10 livecd
Here assuming the Ubuntu 9.10 partition is sda8,and /boot partition is sda6 (if you have a separate /boot partition).
Boot up ubuntu from the livecd,open terminal and run:

First find out which partition is which with
```
fdisk -l
```
Then to install
```
sudo -i
```
```
mount /dev/sda8 /mnt
```
```
mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition
```
```
grub-install --root-directory=/mnt/ /dev/sda
```
Reboot removing the livecd in the process and once in 9.10 run
```
sudo update-grub
```

From the Grub 2 Guide

---

### Post by brickhead248 on 2010-03-13
> **hansdown said:**
> It seems, that BT has installed the 8.10 bootloader.

When you first boot up, can you see the 9.10 kernel?

This tutorial is for a windows install, after ubuntu, but it should help.

[http://linux.dipin.info/2009/06/restore-grub-boot-loader.html](http://linux.dipin.info/2009/06/restore-grub-boot-loader.html)
yeah, it's weired, i can find both kernels when i browse the hard drive on the live CD, but when i try find "vmlinuz-2.6.31-20-generic" it says file not found!

also, the tutorial says to run grub from the live CD, but my 9.10 doesn't have that package!

---

### Post by brickhead248 on 2010-03-13
> **2hot6ft2 said:**
> The best way to do it is to install BT4 first.
Then install Ubuntu 9.10
If you use ext4 for the 9.10 install BT4 wont see it.
You have to boot into 9.10 and run update-grub for grub2 to show both BT4 and 9.10.

I triple boot. Win7 (beats me why since I never use it), BT4 and Ubuntu 9.10.

You can still edit menu.list in BT4 since it uses Grub legacy, and yes BT4 is using Ubuntu 8.10 as it's base now that's why it shows 8.10.

You can fix it by using the livecd to reinstall grub2 just be sure to point it to 9.10 when doing so NOT BT4 8.10

Using Ubuntu 9.10 livecd
Here assuming the Ubuntu 9.10 partition is sda8,and /boot partition is sda6 (if you have a separate /boot partition).
Boot up ubuntu from the livecd,open terminal and run:

First find out which partition is which with
```
fdisk -l
```
Then to install
```
sudo -i
```
```
mount /dev/sda8 /mnt
```
```
mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition
```
```
grub-install --root-directory=/mnt/ /dev/sda
```
Reboot removing the livecd in the process and once in 9.10 run
```
sudo update-grub
```

From the Grub 2 Guide
i see what you mean, GRUB 1 isn't picking up the ext4 filesystem.

When i tried fdisk -l nothing happened
so i tried fdisk /dev/hda and it said:
unable to open /dev/hda1

so i tried lshw and the drive didnt even appear!

---

### Post by 2hot6ft2 on 2010-03-13
> **brickhead248 said:**
> i see what you mean, GRUB 1 isn't picking up the ext4 filesystem.

When i tried fdisk -l nothing happened
so i tried fdisk /dev/hda and it said:
unable to open /dev/hda1

so i tried lshw and the drive didnt even appear!
That's right 8.10 wont see the ext4.

Don't worry about 8.10 when reinstalling grub2 from the livecd once you boot into 9.10 and run update-grub it will find it and include it in the grub list. You don't need or really even want to mount the BT4 partition when doing it to keep from messing up.

---

### Post by brickhead248 on 2010-03-13
no, i mean when i ran the live CD it's not picking up the device at all!

---

### Post by brickhead248 on 2010-03-13
even though i could mount the devices

---

### Post by hansdown on 2010-03-13
> **brickhead248 said:**
> i see what you mean, GRUB 1 isn't picking up the ext4 filesystem.

When i tried fdisk -l nothing happened
so i tried fdisk /dev/hda and it said:
unable to open /dev/hda1

so i tried lshw and the drive didnt even appear!

This is** not** the best advice, but you may consider a fresh install, given the differences between grub1 and grub2.

---

### Post by 2hot6ft2 on 2010-03-13
> **brickhead248 said:**
> no, i mean when i ran the live CD it's not picking up the device at all!
which livecd? BT4 8.10 OR 9.10?

---

### Post by lisati on 2010-03-13
> **brickhead248 said:**
> Sorry! i didnt realise people can't read my mind, you'll go "ahhhh" when i say this: BackTrack.
I'm using version 4

Thanks. At first I thought you were referring to British Telecom, which wouldn't make sense since you're in Canada.

+1 to the questions by the other posters.

---

### Post by brickhead248 on 2010-03-13
9.10

@lisati: haha, wait... Canada?

---

### Post by 2hot6ft2 on 2010-03-13
I did a couple reinstalls before getting it right so you may want to back your stuff up and try installing fresh with BT4 being installed first then 9.10.

While you're at it you may want to consider using ext3 for the 9.10 install so you don't have the interoperability issues.

It doesn't take that long to do a fresh install and you'll start with a nice clean dual boot.

---

### Post by brickhead248 on 2010-03-13
well the issue for me is that it takes forever to do all the updates for 9.10 and configure all my packets how i like them. i can just install some extra packets on 9.10, and i'll have all the BT functionality that i need. i don't need a whole separate operating system. 

so how do i get 9.10 back??

---

### Post by lisati on 2010-03-13
> **brickhead248 said:**
> 9.10

@lisati: haha, wait... Canada?

Sorry about that, looking at the wrong profile info......

---

### Post by 2hot6ft2 on 2010-03-14
> **brickhead248 said:**
> well the issue for me is that it takes forever to do all the updates for 9.10 and configure all my packets how i like them. i can just install some extra packets on 9.10, and i'll have all the BT functionality that i need. i don't need a whole separate operating system. 

so how do i get 9.10 back??
If it's still there and ok then just run the instructions I gave earlier.
I have no way of knowing just what's been done or what state it's in at this point so good luck, it may or may not be that simple.

You'll find that it's a bit of a challenge/project getting the BT apps on 9.10 since BT uses a different directory structure than ubuntu but for the most part it can be done. I run a few of them on 9.10.

---

### Post by brickhead248 on 2010-03-14
right yeah sorry, 

i followed your instructions for putting GRUB back on, and 9.10 WORKS! 

thanks 2hot and hansdown!

---

### Post by 2hot6ft2 on 2010-03-14
> **brickhead248 said:**
> right yeah sorry, 

i followed your instructions for putting GRUB back on, and 9.10 WORKS! 

thanks 2hot and hansdown!
Glad to hear it the last one wasn't that easy for some strange reason, and they were just getting rid of windows.

---

### Post by brickhead248 on 2010-03-14
ahh, but it doesnt even see the BT4 boot. you'd think GRUB 2 would be backwards compatible with EXT3

---

### Post by 2hot6ft2 on 2010-03-14
> **brickhead248 said:**
> ahh, but it doesnt even see the BT4 boot. you'd think GRUB 2 would be backwards compatible with EXT3
It should just be a matter of running
```
sudo update-grub
```
While in 9.10
Yes grub 2 sees my BT4 install no problem, it will show up in grub as Ubuntu 8.10.

---

### Post by CharlesA on 2010-03-14
The command that 2hot6ft2 posted will get it working. BT4 will show up as "Ubuntu 8.10"

I just spent a couple hours tweaking the titles of Grub 2, so that it would say "Backtrack4" instead of "Ubuntu 8.10". What a pain in the butt. Editing menu.lst was so much easier.

---

### Post by brickhead248 on 2010-03-14
aha! once again, thanks

---

### Post by 2hot6ft2 on 2010-03-14
> **CharlesA said:**
> The command that 2hot6ft2 posted will get it working. BT4 will show up as "Ubuntu 8.10"

I just spent a couple hours tweaking the titles of Grub 2, so that it would say "Backtrack4" instead of "Ubuntu 8.10". What a pain in the butt. Editing menu.lst was so much easier.
I thought about doing that but like you said it was so much easier to just edit the menu.list.

---

### Post by brickhead248 on 2010-03-14
one more quick question... why do all 9.10 installations have a vmlinuz-2.6.31-20 and 14 kernel?

---

### Post by 2hot6ft2 on 2010-03-14
I guess that means your thread is solved and you can mark it that way using the Thread Tools at the top of the thread and enjoy.
:popcorn:

---

### Post by 2hot6ft2 on 2010-03-14
> **brickhead248 said:**
> one more quick question... why do all 9.10 installations have a vmlinuz-2.6.31-20 and 14 kernel?
Something new I believe. Ubuntu is going thru some changes lately. Other than that I really don't know.

---

### Post by 2hot6ft2 on 2010-03-14
You do know you can get rid of older kernels but should keep the 2 newest ones right? Just search by the number(s) in synaptic and be sure to remove both the image and header for the kernel number when removing a old kernel.

---

### Post by brickhead248 on 2010-03-14
which ones are the old ones? and what's the difference between an intrd image and a linux image

---

### Post by CharlesA on 2010-03-14
> **2hot6ft2 said:**
> I thought about doing that but like you said it was so much easier to just edit the menu.list.

Did you go with Grub .97 instead of Grub 2?

> **2hot6ft2 said:**
> You do know you can get rid of older kernels but should keep the 2 newest ones right? Just search by the number(s) in synaptic and be sure to remove both the image and header for the kernel number when removing a old kernel.

I edited the grub2 config to only show the last 2 kernels, but I didn't remove them. Does it make a difference there?

---

### Post by 2hot6ft2 on 2010-03-14
> **brickhead248 said:**
> which ones are the old ones? and what's the difference between an intrd image and a linux image
The one with the lowest number is the oldest and I don't know the difference between those 2 but I'll find out tomorrow by doing a search to find out. But that doesn't mean you can't search for it now and find out..;)

I'm off to bed now.

G'night

---

### Post by 2hot6ft2 on 2010-03-14
> **CharlesA said:**
> Did you go with Grub .97 instead of Grub 2?



I edited the grub2 config to only show the last 2 kernels, but I didn't remove them. Does it make a difference there?
About 172MB of difference is all per kernel. And you're not supposed to edit grub.cfg see the guide in my sig. Grub 2 Guide

"Did you go with Grub .97 instead of Grub 2?"

Grub2 on 9.10 keeps the grub in line.

---

### Post by CharlesA on 2010-03-14
> **2hot6ft2 said:**
> About 172MB of difference is all per kernel. And you're not supposed to edit grub.cfg see the guide in my sig. Grub 2 Guide

"Did you go with Grub .97 instead of Grub 2?"

Grub2 on 9.10 keeps the grub in line.

I wasn't editing grub.cfg. I edited 10_linux.

See here: [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by 2hot6ft2 on 2010-03-14
> **CharlesA said:**
> I wasn't editing grub.cfg. I edited 10_linux.

See here: [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
Good deal. That's a good guide too.

---

