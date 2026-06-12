---
title: "Boot error"
date: 2011-12-04
forum: General Help
---

### Post by bobo123333 on 2011-12-04
After some issue with upgrade from 11.04 to 11.10 i was able to stable my system.
BUT, after boot and bios screen i get black screen (and short flash of some code line with [ok])
 
No logon screen - only black screen.
 
 
If I boot and click shift I get grub menu and choose some version.
Then I only get command line where i can login (no GUI) and call "startx" to get GUI.
 
How can i solve that and get normal boot to GUI.

---

### Post by *^kyfds( on 2011-12-04
i'm assuming it's a problem with your boot loader.

i'm going to have to ask a few questions:

-is this a problem with a recently installed version of ubuntu?

-are you running ubuntu on a dual boot, and how did you install it? (wubi, USB ect.)

- do you have any valuble files that could be considered important and could not be replaced (would you be able to erase them)?

-what are your system specs?

until you awnser, i would consider checking the ISO files (and redownloading it if need be),  then reinstalling.

---

### Post by bobo123333 on 2011-12-04
Thanks for the replay.
 
**-is this a problem with a recently installed version of ubuntu?**
No fresh install, I only upgrade from 11.04 to 11.10
 
**-are you running ubuntu on a dual boot, and how did you install it? (wubi, USB ect.)**
No - only ubuntu. 
 
**- do you have any valuble files that could be considered important and could not be replaced (would you be able to erase them)?**
I prefer not to reinstall since i have there lot of configrations of DB, http server etc. 
 
In general all was working just fine with 10.04.
The auto upgrafe to 11.10 was problematic and since then there a boot problem (black screen)

---

### Post by *^kyfds( on 2011-12-04
this is a complex issue, it seems.

because i'm pretty new to linux, i've already reached the edge of my experiences.

maybe message an experienced user and see what they think.

i'll do a bit of research in the meantime to see what i can find on this issue.

sorry dude, 

Thehumorouscheese.

---

### Post by Rubi1200 on 2011-12-04
Hi,
let's start by seeing the full specifications for the computer, especially RAM and graphics card.

Also, if you can, boot the computer with a LiveCD/USB and post the results of the boot info script.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by bobo123333 on 2011-12-04
Please see attached file - the result.txt
BY the way I run using the GUI and no liveCD.
I boot from grab - and run "startx" and done all via the GUI

thanks in advance

---

### Post by bcbc on 2011-12-04
What does this say - should have lightdm as the default as this replaced gdm for 11.10:
```
sudo dpkg-reconfigure lightdm
```

---

### Post by bobo123333 on 2011-12-05
Thanks,
 
I Got this warnings
 
root@ubuntu:~# sudo dpkg-reconfigure lightdm
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_NAME missing
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_PACKAGE missing
 
When i boot I get the grab menu, choose the last version and see all [ok] and the following lines :
starting load fallback graphics decives [ok]
starting load fallback graphics decives [fail]
.
.
starting lightdm display manager [ok]
**_ (flashing and stack here ....)**

**What should I do now?**

---

### Post by bobo123333 on 2011-12-05
What should I do now?

---

### Post by bcbc on 2011-12-05
You said there was an issue during the upgrade. What happened? You could try: 
```
sudo apt-get update
sudo apt-get upgrade -f

```

What graphics card do you have?
When you press shift, which entry do you choose? Recovery or an older kernel?

How about unity-greeter... is that installed?
```
sudo apt-get install unity-greeter
```

---

### Post by elliotn on 2011-12-05
try going to rescue mode and resume normal boot, if you are able to boot, remove any parkage that have NVIDIA in its name, if u have synaptic it could be easy, then reboot

---

### Post by bobo123333 on 2011-12-05
During the upgrade the pc stack and the only option was to do reboot.
 
**What graphics card do you have?**
Nvidia
BTW, i already reinstall the drivers using
 
apt-get install --reinstall nvidia-173
apt-get install --reinstall nvidia-current
 
```
sudo apt-get update
sudo apt-get upgrade -f

```
Done!
 
**When you press shift, which entry do you choose? Recovery or an older kernel?**
I tried all options.
I have: 2.6.38-11 and 2.6.35-28 and .27 and .25 and .24 and .22 (i think i should remove some but i do not know how)
 
**How about unity-greeter... is that installed?**
I do not think

---

### Post by bcbc on 2011-12-05
> **bobo123333 said:**
> During the upgrade the pc stack and the only option was to do reboot.
 
**What graphics card do you have?**
Nvidia
BTW, i already reinstall the drivers using
 
apt-get install --reinstall nvidia-173
apt-get install --reinstall nvidia-current
 
```
sudo apt-get update
sudo apt-get upgrade -f

```
Done!
 
**When you press shift, which entry do you choose? Recovery or an older kernel?**
I tried all options.
I have: 2.6.38-11 and 2.6.35-28 and .27 and .25 and .24 and .22 (i think i should remove some but i do not know how)
 
**How about unity-greeter... is that installed?**
I do not think
You should have a 3.0 kernel for oneiric.
Try 
```
sudo apt-get dist-upgrade -f
```

---

### Post by bobo123333 on 2011-12-05
It is working now!
Thanks for all the help!
 
I did not install versions 3.0, should I?
 
Best

---

### Post by bcbc on 2011-12-05
Great.

If you upgraded to 11.10 you should have a 3.0 kernel. So not sure whether your system thinks it's 11.10 or still 11.04. What does this say?
```
cat /etc/lsb-release
```

And do your software sources say oneiric or natty?

You could check /boot and see if there is a 3.0 kernel and initrd.img. If so, update the grub menu 
```
sudo update-grub
```

---

### Post by bobo123333 on 2011-12-06
```
cat /etc/lsb-release
```
Result in 11.10 - oneiric
 
 
**And do your software sources say oneiric or natty?**
How should I check it?
 
**You could check /boot and see if there is a 3.0 kernel and initrd.img. If so, update the grub menu **
As i mentioned before no 3.0 version on the list

---

### Post by bcbc on 2011-12-06
Probably the easiest check is to browse the file:
Alt-F2, gedit /etc/apt/sources.list

You can open software sources by clicking the top left Ubuntu icon in Unity and entering: software-sources (but mine doesn't show the release keyword so check in the sources.list instead).

You should see lines like:
```
deb http://archive.ubuntu.com/ubuntu **oneiric** main restricted
```

---

### Post by bobo123333 on 2011-12-06
i have this line...

---

### Post by bcbc on 2011-12-06
> **bobo123333 said:**
> i have this line...

Well I am at a loss.

---

