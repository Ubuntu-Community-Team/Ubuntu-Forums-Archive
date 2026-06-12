---
title: "Some problems and a question"
date: 2012-05-04
forum: General Help
---

### Post by Costas100 on 2012-05-04
I have a Lenovo computer 500 GB HD divided in 4 partitions, one for XP Pro sda1 (NTFS) , one extended as sda2 which includes 2 small swap partitions and an sda6 (ext4)  partition where Mint 11 is installed, a Fat 32 (sda3) partition where I keep my files and finally one more Linux partition (Ext4) where Ubuntu 11.04 is installed.
All works reasonably fine, except for the minor problems that somehow are either resolved or I manage to get around them.
Now my question: for some very complex reason, I decided to replace the Mint 11 installation (nothing wrong with Mint 11 as a whole, but other reasons led me to discover Edubuntu 12.04 and I am thinking to use it in replacing Mint 11. I really have a question and a problem:
**Problem:** When I tried to use the live cd (Edubuntu 12.04 i386) in my 386 computer, initially it would not start and simply showed a black screen. After numerous trials and forced reboots. I managed to start it. There I had the left bar with some of the most popular software and the install link. When I searched for simple things like a text editor or other apparently installed (in the DVD) programs there were nowhere to be found. No links of any kind.  I am assuming that if installed all these will appear, I hope.
**Question:** Edubuntu 12.04 i386 is at a higher level than Ubuntu 11.04 which I will not replace. Will I face any problems with Grub if I install Edubuntu 12.04 over Mint 11 in sda6. If problems are possible, I would rather live with Mint, I begin to like it.
I wish to thank you all at Ubuntu, for your patience and support to this 74 years plus, senior, who has become Ubuntu addicted

Costas Lazarou
Toronto Canada

---

### Post by zombifier25 on 2012-05-04
> **Costas100 said:**
> 
**Problem:** When I tried to use the live cd (Edubuntu 12.04 i386) in my 386 computer, initially it would not start and simply showed a black screen. After numerous trials and forced reboots. I managed to start it. There I had the left bar with some of the most popular software and the install link. When I searched for simple things like a text editor or other apparently installed (in the DVD) programs there were nowhere to be found. No links of any kind.  I am assuming that if installed all these will appear, I hope.

This problem appears sometimes (dunno the exact cause). Click on the second icon at the bottom (which will bring you to the apps lens) will solve it (for me)
> **Costas100 said:**
> 
**Question:** Edubuntu 12.04 i386 is at a higher level than Ubuntu 11.04 which I will not replace. Will I face any problems with Grub if I install Edubuntu 12.04 over Mint 11 in sda6. If problems are possible, I would rather live with Mint, I begin to like it.

Grub should be able to detect all OSs. However, I'm a noob at this, so wait for someone else to answer ;)

---

### Post by Costas100 on 2012-05-04
> **zombifier25 said:**
> This problem appears sometimes (dunno the exact cause). Click on the second icon at the bottom (which will bring you to the apps lens) will solve it (for me)

Grub should be able to detect all OSs. However, I'm a noob at this, so wait for someone else to answer ;)
Thank you zombifier 25, I am now replying from the live CD (Edubuntu 12.04). I cannot find any icons on the bottom, in fact there is no bottom panel (bar). The only icons are in the left panel with a total of 12 icon and I tried them all including the one that prompts you install. In the top panel there is volume control, date and time, network stuff and chat links and in the left bar there are three additional icons, two for a couple of my usb mini hard disks and one for trash.

I am ready to give up on this version, thank you anyway

Costas

---

### Post by zombifier25 on 2012-05-04
> **Costas100 said:**
> Thank you zombifier 25, I am now replying from the live CD (Edubuntu 12.04). I cannot find any icons on the bottom, in fact there is no bottom panel (bar). The only icons are in the left panel with a total of 12 icon and I tried them all including the one that prompts you install. In the top panel there is volume control, date and time, network stuff and chat links and in the left bar there are three additional icons, two for a couple of my usb mini hard disks and one for trash.

I am ready to give up on this version, thank you anyway

Costas
I THOUGHT YOU WERE TALKING ABOUT THE SEARCH DASH!

Click on the first icon of the left panel, it will bring up a search menu for you and you can use it to search for any program you like.

---

### Post by grahammechanical on 2012-05-04
If you install Edubuntu in place of Mint then Edubuntu will put its Grub menu in place of the 11.04 Grub menu. Everything will work the same.

what you should then do is boot into 11.04 and in a terminal run  the command

```
sudo update-grub
```

That will put the 11.04 Grub back in control of booting into the OS. Otherwise if you remove Edubuntu you will not be able to boot. Unless the removal is a re-placement by an other Ubuntu.

Edubuntu has a different selection of programs tghat Ubuntu or Mint but you can install all the programs that would normally be in 11.04 and onwards.

I am sure it has a text editor. You open the Dash and type

> Gedit

Its icon should appear and then you press enter. I think that you are used to looking down menu lists for program names. It is all done differently in Ubuntu now. You can get used to it. Learning new stuff will keep your brain active. 

Regards from a 64 year old.

---

