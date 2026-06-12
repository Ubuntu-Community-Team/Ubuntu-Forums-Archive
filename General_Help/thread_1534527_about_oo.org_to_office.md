---
title: "about oo.org to office"
date: 2010-07-19
forum: General Help
---

### Post by bocaccio on 2010-07-19
I am curious does oo.org save to format of .docx and .ppt?
 
Thank you

---

### Post by AlphaLexman on 2010-07-19
Yes it will save files in both formats
I have heard some (rare) reports about certain particulars with .ppt files.

---

### Post by jarviser on 2010-07-19
> **bocaccio said:**
> I am curious does oo.org save to format of .docx and .ppt?
 
Thank you

Yes the latest OO does that, and also .pptx .xls .xlsx etc if you want.  Powerpoint/Presentation crossover is the one most likely to have a few unexplained mis-matches when you do small intricate diagrams using it as though it was cad-cam; our bedroom fitter provided a plan of a wardrobe (sorry, I should say closet?) in .ppt with small triangles as coat-hangers but these showed up twice as big as the wardrobe in OO Presentation. Also I drew up our central heating system in Powerpoint and maintained it in oo Presentation, and the odd text box went wild, and I could not get the lines to join cleanly as the resolution is less on OO, but in general they will cross over OK.  Actual office/classroom type presentations should cause no problems at all.

---

### Post by bocaccio on 2010-07-19
YOu all are making it very hard for me to find a reason to keep win7 on here!! heh. I'm dual booting ubuntu netbook rmx and win7.

---

### Post by jarviser on 2010-07-20
> **bocaccio said:**
> YOu all are making it very hard for me to find a reason to keep win7 on here!! heh. I'm dual booting ubuntu netbook rmx and win7.

If I said that I am runnning MS Office under Ubuntu using Wine 1.2, and I can drag and drop music to my Ipod using Rhythmbox in Ubuntu in BOTH directions, is there any need to ever use Windoze again?  I only keep my win7 to run my Canon scanner.

---

### Post by bocaccio on 2010-07-20
I may just instead of deleting 7 all together I'll decrease the space it uses. I'll probably do a killdisk and fresh install 7 and ubuntu; weird thing is on the boot screen i see 2 ubuntu 2 ubuntu recovery and 1 win7.

I don't know why i have 2 ubuntus

---

### Post by scouser73 on 2010-07-20
> **bocaccio said:**
> I may just instead of deleting 7 all together I'll decrease the space it uses. I'll probably do a killdisk and fresh install 7 and ubuntu; weird thing is on the boot screen i see 2 ubuntu 2 ubuntu recovery and 1 win7.

I don't know why i have 2 ubuntus

I would guess that the recurring Ubuntu entries are the old Kernels which can be removed with ease.

---

### Post by bocaccio on 2010-07-20
> **scouser73 said:**
> I would guess that the recurring Ubuntu entries are the old Kernels which can be removed with ease.
 
 
This is offtopic and if the mods do not like this will you be so kind to answer in a pm :D
 
Is there any way you can give me a hand getting rid of the correct kernel? And would you be able to tell me what i use to shrink the partition with 7 on it? It is around 125gb now and I think i wanna make it 80gb instead. I tried disk manager and i only was able to remove/erase not shrink. I tried to get gparted but must have been unsuccessful; sometime i dl stuff from synaptic or the software bank on ubuntu but can't find it once i have it.

---

### Post by jarviser on 2010-07-20
Don't think it's off topic. It's all Ubuntu.

I used Gparted tool to shrink the Win partition BUT better to blank it and reinstall Win7. 

Also use GParted downloaded and burnt the ISO to CD and boot from it. Not the one in the Ubuntu.

Use Synaptic Package Manager in System/Admin menu to remove all but the last two kernels. Each kernel has one normal and one recovery boot.  As you only have two kernels, leave it til you have three!

---

### Post by bocaccio on 2010-07-20
> **jarviser said:**
> Don't think it's off topic. It's all Ubuntu.
 
I used Gparted tool to shrink the Win partition BUT better to blank it and reinstall Win7. 
 
Also use GParted downloaded and burnt the ISO to CD and boot from it. Not the one in the Ubuntu.
 
Use Synaptic Package Manager in System/Admin menu to remove all but the last two kernels. Each kernel has one normal and one recovery boot. As you only have two kernels, leave it til you have three!
 
 
 
What does blank it mean? I was gonna erase the partition but i thought if you use 7/linux that 7 has to be installed first and linux second because the boot loader will conflict the grub (something like that; i hope i explained it right)
 
I think i can try to do what your talking about I'd just do a search in synaptic for Kernel and hopefully i'd either see two or 4 that look similar or the same and just delete two of them. I was messing with some kinda kernel to get vbox running last night; now just gotta figure out what i need for the os to run (windows that is..); what kinda disc or .iso i need to run from vbox...
 
While your being so kind would you mind posting a link or something for me to look at to get tightvnc running? i'll be using from my netbook(unr) to my dekstop (win7). 
I think i'll have to portforward probably my linksys router and also my dsl modem. Been a long time since i've port forwarded but i think i can still do it. 
 
 
 
Thanks for your help!!!

---

### Post by jarviser on 2010-07-21
Start a new thread for the port forwarding problem.

I should have said "format" not "blank"!  What I meant was that it is possible with GParted CD to simply shrink an existing Windows partition provided you defragment it first, however there have been problems with the windows being unusable afterwards, hence the normal advice is not to shrink Win7 but to reinstall on a smaller partition using the format option in the Win7 install. Try the shrink first and see if it still boots. 
Problem is if you install Ubuntu and then find the Win7 is corrupted, if you re-install Win7 it kills the Ubuntu Grub.

The remaining Ubuntu partitions can be created using GParted boot CD or using the Ubuntu install.

Latest downloadable GParted ISO is, I believe, 0.5.2-1

Re Synaptic and the Kernels, look for the kernel you want to remove by number and you just need to mark the single instance in Synaptic for complete removal. Both Normal and Recovery options will be removed from Grub automatically in the single action.

As I say always keep the latest two kernels.

So say that Grub boot shows you have kernels 
2.6.32-23 (normal and recovery)
2.6.32-22 (normal and recovery)
2.6.32-21 (normal and recovery)

put *linux-image-2.6.32-21* in the synaptic quick search box, and the solid green box will show it is installed. Click on the box and mark it for removal and then Apply

---

### Post by bocaccio on 2010-07-21
I think i fixed the kernels; and kde works but i cant login

background is blue

there is a box that has my name-laptop

login
pw

blue arrow down and red button to logout/shutdown/enter konsole..etc..

says my username is root..thus i have no clue what the pw is.

---

### Post by jarviser on 2010-07-21
> **bocaccio said:**
> I think i fixed the kernels; and kde works but i cant login
....

I do hope you only deleted kernels older than the last two. I did say keep the last two kernels. Sounds like you uninstalled them all.

You should not have the user name Root, you should have created a new user name when you installed, with a password.

I suggest you re-install Ubuntu from scratch, ensure you create a user name other than Root, with password as requested during install, and leave the kernels alone til you have more working knowledge of Linux.

---

### Post by bocaccio on 2010-07-21
> **jarviser said:**
> I do hope you only deleted kernels older than the last two. I did say keep the last two kernels. Sounds like you uninstalled them all.

You should not have the user name Root, you should have created a new user name when you installed, with a password.

I suggest you re-install Ubuntu from scratch, ensure you create a user name other than Root, with password as requested during install, and leave the kernels alone til you have more working knowledge of Linux.

I'll do this another day; dont have time now. I deleted two kernels i tried to find buplicates. I found two images and two headers they were alike so i deleted one each. Obviously i did it wrong. It shouldn't take long to put ubuntu back like i have it from a fresh install though.

---

### Post by bocaccio on 2010-07-21
[B]Jarviser:

[/B]I am over halfway there. I booted gparted. Now i have to figure out what i need to make the remainder of the disk that i shrunk from win7. I made ti fat32 cause i thought it would be visible in ubuntu if i did so. Now I just made two partitions in win7. Hey at least I am doing better than i was!! 

Oh yeah i blanked unr and 7 though cause i am trying to get KDE on here and i deleted the wrong kernel cause i had two of ubuntus on my boot screen. Anyways I started fresh and i'll work on this some more tomorrow before i goto work.




btw; in my experience linux ppl are much more helpful than windows ppl; not trying to be funny either. Windows person would tell you to use google or even give you a link showing you how they searched on google or some ****.

---

### Post by jarviser on 2010-07-21
If you want KDE instead of Gnome, install Kubuntu not Ubuntu. I prefer Gnome

If I were you, use GParted to delete all partitions apart from Win7 and the small system reserved bit at the start of the disk and when installing Ubuntu use the option to use all remaining space. 

If you want to do it manually, this is what my partitions look like

[IMG]http://www.jarviser.co.uk/jarviser/images4/linuxdiskformat.png[/IMG]

1) system reserved
2) Windows
3) Extended
  3a) /home 250GB  for files
  3b) /     32GB for Linux
  3c) /swap  6GB for swap space

---

### Post by bocaccio on 2010-07-21
I think i got it under control. I fresh installed 7 and ubuntu and now i actually have more menus at the top of the screen than before on ubuntu...i guess thats another minor prob to get rid of.
 
I shrunk 7 with gparted live usb and made the 35gb that i shrunk to fat32 and now i think i have to go back and make it ext4 and i'll just rename it something like "data" to use for stroage on linux. I wanted it to where 7 would not see it at all.
 
Is Kubuntu as compatible as ub netbook remix is? I have an asus eee 1005peb. And was originally looking for something that will run very fast and unr does this very well; so maybe i'll just get accustomed to gnome instead.
 
If i didn't already say it..Thanks for your help!!! I can't wait for the day that I am answering questions too.

---

### Post by jarviser on 2010-07-21
> **bocaccio said:**
> ...
 
Is Kubuntu as compatible as ub netbook remix is? ....

I don't know either distro, sorry.  

You will have re-installed several times before you are comfortable, it's part of the learning curve, and the best way out of a hole.

---

