---
title: "can i install ubuntu 11.04 on an hp pavilion ze4100"
date: 2011-09-19
forum: General Help
---

### Post by mark-oz on 2011-09-19
hello ubuntu forum community. i have recently taken interest in ubuntu due to the fact that my hp pavilion ze4100 always gets viruses and i am sick and tired of windows. 

i am trying to reistall an os on my hp pavilion ze4100 because i got an error message more specifically this one <windows root>\system32\ ntoskrnl.exe is missing please reinstall and continue
i dont have the windows cd so figured i might aswell try to get ubuntu on it. i dont care about the files on my laptop as they are of no importance. so my questions are

1| will ubuntu 11.04 run on my ze4100 
and 
2| do i have to fix the error i have on my laptop first to intall ubuntu

i thank any that can help me on this

ps i really want ubuntu 11.04
 this is my laptop hardware specs [http://reviews.cnet.com/laptops/hp-pavilion-ze4100-c/1707-3121_7-30584923.html](http://reviews.cnet.com/laptops/hp-pavilion-ze4100-c/1707-3121_7-30584923.html)

---

### Post by seawolf167 on 2011-09-19
The easiest way to check is to download and burn a Ubuntu LiveCD (the standard installation cd) then boot off it into a live environment and see if everything works. I'm going to go out on a [very thick] limb and say that everything should work for your computer, you'll probably just need to download drivers for your wireless card &/or graphics card.

Some notes:
-[md5sum ]("https://help.ubuntu.com/community/HowToMD5SUM")the iso image you downloaded
-burn the iso image you downloaded on your slowest burn setting
-ensure that you have cd/dvd booting enabled and as a higher priority than hard drive booting in BIOS (hit your key combo, usually [F2] to enter BIOS during POST

---

### Post by blueridgedog on 2011-09-19
> **mark-oz said:**
> 
1| will ubuntu 11.04 run on my ze4100 
and 
2| do i have to fix the error i have on my laptop first to intall ubuntu


1.  As seawolf167 mentioned, test with a LiveCD.  Give it a try and see what works and what issues you have.  In the long run, forum users can get most of the items working (though it is likely that all will work out of the box).

2.  No...if you do a complete install, your windows operating system and partitions will be removed.  You SHOULD backup any files you want to save as the hard drive will be erased using this method.

---

### Post by wildmanne39 on 2011-09-19
Hi, do you only have 256 mb of ram? or have you installed 1 gig? Your system is a little light for 11.04 it might run but I suspect poorly.

+1 for trying the livecd first.
Thank you

---

### Post by ajgreeny on 2011-09-19
If you do only have 256MB ram try Lubuntu or perhaps Xubuntu rather than the normal Ubuntu, as they are both lighter than Ubuntu, Lubuntu being the lightest.

---

### Post by mark-oz on 2011-09-19
thank guys i think ill try a light version like lubuntu or xubuntu the mount the livecd thanx ill see if it works

---

### Post by blueridgedog on 2011-09-20
Post back what you find so that others with similar issues can be guided in a selection.

Good luck!

---

### Post by mark-oz on 2011-09-20
okay so i i downloaded both ubuntu 11.04 and xubuntu 10.10 and used iso burner to put them on a livecd.i got two problems

with xubuntu the language select screen appears but i cant use the keyboard for some reason and it just wont respond.

with ubuntu it freezes on a screen that is a purple-ish hue and has 
a keyboar icon, equal symbol and a  shadow of a little man

i dont know what is going wrong i press f2 so that the disk boots first but besides that i have no idea what to do  i can post picture if needed

---

### Post by BlinkinCat on 2011-09-20
Did you check the ISO files with the md5sum as located in seawolf167's signature?

---

### Post by wildmanne39 on 2011-09-20
Hi, is your key board wireless I have that problem when I am installing with a wireless key board, I have to use a wired one until I get the system installed.

Also for the purple screen you most likely need nomodeset option here is a link on how to do that.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Did you ever tell us if you installed 1 gig of ram?
Thank you

---

### Post by mark-oz on 2011-09-20
> **wildmanne39 said:**
> Hi, is your key board wireless I have that problem when I am installing with a wireless key board, I have to use a wired one until I get the system installed.

Also for the purple screen you most likely need nomodeset option here is a link on how to do that.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Did you ever tell us if you installed 1 gig of ram?
Thank you

my laptop keyboard wont work, neither does the mouse. i ran md5sum on both ubuntu 11.04 and xubuntu 10.10 and they were fine i burned at 2x as it is the slowest burn speed and i press f2 in the post screen and changed the bios to boot from disk and i my computer keyborad still wont work 

also i have done nothing to my laptop so i cant figure out how much ram ihave because its old i can say its is stock hardware i have not installed any ram.

---

### Post by wildmanne39 on 2011-09-20
Hi, try the link with ubuntu, and how much ram do you have?
Thank you

---

