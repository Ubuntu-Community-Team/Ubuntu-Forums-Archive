---
title: "Another Grub Rescue promblem!!!!!"
date: 2011-04-25
forum: General Help
---

### Post by Gowie47 on 2011-04-25
Alright so a couple days ago I was installing ubuntu on my windows 7 laptop. I installed it twice out of stupidity and after setting everything up on one of the installs I went into the linux partition software (can't remember what its called), and deleted the extra ubuntu install. This left a unallocated chunk of hd space that I now wanted merge with my windows partition. After doing a couple google searches it looked like I needed to do this from windows. So I shut down and booted back up to find the awfulllll grub rescue unknown filesystem screen. This thing is a pain in my ***. 

Now I have read many of the question and answers revolving around the grub rescue prompt and many have fixed the problem by using a liveCD to boot to linux and fixed the problem from there (I haven't read any further into it because this doesn't apply to me, yet atleast). I can't do this unfortunately because my roommate grabbed the ubuntu disk on his way out the door going home for easter. I have also since then ruined three disks trying to make a liveCD, its been such an epic fail. So i'm done with ruining my good DVD's that I use for burning games for this purpose and thought I would post here to see if any one could help me with this problem without using a liveCD. 

Now i have read in a forum somewhere, not sure if I am going to be able to find it again, that I can boot linux from the grub rescue prompt, by finding the ubuntu iso file that is somewhere on my hd. The problem with this is that the ls command in the grub rescue prompt is screwy. For example when i run the following commands this is what happens. 

```

error: unknown filesystem.
grub rescue> ls
(hd0)(hd0,msdos8) (hd0,msdos7) ... (hd0,msdos1)
Note: What is above, to my knowledge, is normal. But below is not.
grub rescue> ls (hd0,7)
error: unknown filesystem.

```

So this is my problem, I cant look at any of the subfolders of any of my partitions, not just the hd0,7 one. Anybody know why this is? or how I can fix it? Any help is appreciated! ThAnks!

---

### Post by wilee-nilee on 2011-04-25
I'm going to assume your running grub2 here is a manual boot in description.

Manual boot from grub prompt for grub2
set root=(hd0,X)    X=the partition # of OS 
linux /boot/vmlinuz(tab=kernel) root=/dev/sdaX 
initrd /boot/initrd(tab, then enter) 
boot (enter)

You really need a bootable usb flash or cd, the iso is imaged to to a cd, and will not work with a dvd. 

Many have not fixed this with a live cd; like 99.99% have.

If you get booted in and the hard drive is sda run in the terminal.
sudo grub-install /dev/sda
then
 sudo update-grub

---

### Post by conradin on 2011-04-25
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)
at Booting from the Rescue Mode

---

### Post by Rubi1200 on 2011-04-25
Hi,
please do the following so we can try and see what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Gowie47 on 2011-04-25
Hey thanks guys, I really appreciate the quick replies. 
wilee-nilee I tried what you suggested, the problem is that the linux /boot/vm... command/line returns unknown command.
as does initrd and boot. I can change the root and prefix through set however. Does this mean I am not running grub2? or whats going on here. I am going to read some of the forums posted below now but I don't see any of them fixing my problem. 

Again thanks for the help guys!

> **wilee-nilee said:**
> I'm going to assume your running grub2 here is a manual boot in description.

Manual boot from grub prompt for grub2
set root=(hd0,X)    X=the partition # of OS 
linux /boot/vmlinuz(tab=kernel) root=/dev/sdaX 
initrd /boot/initrd(tab, then enter) 
boot (enter)

You really need a bootable usb flash or cd, the iso is imaged to to a cd, and will not work with a dvd. 

Many have not fixed this with a live cd; like 99.99% have.

If you get booted in and the hard drive is sda run in the terminal.
sudo grub-install /dev/sda
then
 sudo update-grub

---

### Post by wilee-nilee on 2011-04-25
The manual login is tricky the actual spaces between every thing is important. I don't use the manual method as there are easier methods.

Really if you want this fixed and the best help available on the forum you need to follow Rubi1200's post.

With a bootscript posted and Ubuntu cd in your hand you are like there with a few commands if nothing is broken. If something is broken then your even better in shape as far as diagnosing.

Those of us that help in this specific area will help somebody pecking at their system without the correct tools up to a point, but by not using these tools you knock down the chances of getting help, I say this in just informing you. We all work for free here, I have no gain from helping you, why would I or anybody else be motivated to help a person who discards a most important tool a Ubuntu live cd.;)

Here is my best tool supergrub2 the one in the middle.
[http://www.bootproblems.com/](http://www.bootproblems.com/)

---

### Post by Gowie47 on 2011-04-25
Haha I'm sorry, saying it like that does make me come off like a **** and I apologize. I have since gotten this going by going to my College's tech office and we used a LiveCD there. So its all good now, but I do really appreciate your time and the help. And in the future I will make sure to do things the way people really recommend instead of trying to find a work around. Thanks again! 


> **wilee-nilee said:**
> The manual login is tricky the actual spaces between every thing is important. I don't use the manual method as there are easier methods.

Really if you want this fixed and the best help available on the forum you need to follow Rubi1200's post.

With a bootscript posted and Ubuntu cd in your hand you are like there with a few commands if nothing is broken. If something is broken then your even better in shape as far as diagnosing.

Those of us that help in this specific area will help somebody pecking at their system without the correct tools up to a point, but by not using these tools you knock down the chances of getting help, I say this in just informing you. We all work for free here, I have no gain from helping you, why would I or anybody else be motivated to help a person who discards a most important tool a Ubuntu live cd.;)

Here is my best tool supergrub2 the one in the middle.
[http://www.bootproblems.com/](http://www.bootproblems.com/)

---

### Post by wilee-nilee on 2011-04-25
> **Gowie47 said:**
> Haha I'm sorry, saying it like that does make me come off like a **** and I apologize. I have since gotten this going by going to my College's tech office and we used a LiveCD there. So its all good now, but I do really appreciate your time and the help. And in the future I will make sure to do things the way people really recommend instead of trying to find a work around. Thanks again!

Cool glad you have it fixed, it is easy to get frustrated.;)

---

