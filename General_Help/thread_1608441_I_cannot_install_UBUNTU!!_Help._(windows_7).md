---
title: "I cannot install UBUNTU!! Help. (windows 7)"
date: 2010-10-29
forum: General Help
---

### Post by SamVib on 2010-10-29
So I decided to try something new and fresh. I wanted to try ubuntu.

So I download the 64bit version from here. blah blah blah.

I made a 25GB partition.

I then Wubi found out I didn't need the original file since it was downloading something else.

I installed it, rebooted. Windows comes up with a promt:
Boot from:
Windows 7
Ubuntu

I click on Ubuntu. This comes up:
[http://dl.dropbox.com/u/10997679/2010-10-25%2004.03.17.jpg](http://dl.dropbox.com/u/10997679/2010-10-25%2004.03.17.jpg)
[http://dl.dropbox.com/u/10997679/2010-10-25%2004.03.12.jpg](http://dl.dropbox.com/u/10997679/2010-10-25%2004.03.12.jpg)


I am fairly new and I don't know what to do. :( I did research and nothing really showed.

I then burned the said 64bit version and tried to do a Live CD but it didn't reboot into ubuntu.


I really want to try ubuntu? any help? I will be back. I am going to re-install again..maybe that will help.

---

### Post by dasan on 2010-10-29
Its recommended to install directly and use grub 
boot in live cd to check u'r peripharals

---

### Post by SamVib on 2010-10-29
Could you elaborate more? Sorry I am a complete newb.

---

### Post by ivarn on 2010-10-29
Delete the new partition (you can use windows disk manager)
And boot from the live cd and click install.

---

### Post by Vigh on 2010-10-29
wont that erase his windows system though? i have completely switched to ubuntu now, but when i dual booted i used two HDDs and just selected boot sequence from the bios, seemed to be the safest way to do it, without over-writting either of the OS

---

### Post by wilee-nilee on 2010-10-29
Hang you might be getting a response to the wubi problem.;)

If you want to dual boot don't just install as suggested get some help on the forum so that if there is a non standard bootloader on there or some other possible problems like having the max amount partitions already.

---

### Post by SamVib on 2010-10-29
brb going to try to install from the live cd

---

### Post by wilee-nilee on 2010-10-29
So lets just confirm some stuff since you do have a live cd boot it then go to the bootscript link in my sig and download it put it on the desktop, you can just drag it from the places-download folder in the top dropdown menu to the desktop, then run this command in the ubuntu terminal.
```
sudo bash ~/Desktop/boot_info_script*.sh 
```

This will create a file of text come back to your thread hit the post button then the (#) in the reply panel you will see code tags generated put the text in between.

This is pretty straight forward and will give us the total picture of what we really need to know. Post if this is confusing it was for me the first time I ran the script.;)

---

### Post by gtardini on 2010-10-29
I do not see any error message in your snapshots. What is wrong with those screens? 
As for burning CDs: did you burn them as "image" or did you just copy the .iso file? In the second case it will not boot. Any CD-burning software gives you the option "burn as image", that's necessary.

---

