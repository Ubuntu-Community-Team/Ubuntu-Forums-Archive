---
title: "accidentally deleted ubuntu from windows MBR."
date: 2010-08-17
forum: General Help
---

### Post by robb. on 2010-08-17
i installed ubuntu on my compaq presario V2309 using wubi.  it's been driving me nuts having to go through two boot menus every time i want to run ubuntu, which is now my preferred environment.

so i was fiddling with the boot settings and thought i had made a copy of the original.  unfortunately the changes were overwritten on the copy, so now i can only boot into windows.

would be easy to copy the text from your windows MBR that shows what i deleted?  is there a default way that wubi installs?

for example:
```
[boot loader]
timeout=20
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect
***ubuntu goes here***
```

thanks!
robb.

---

### Post by sydbat on 2010-08-17
> **robb. said:**
> i installed ubuntu on my compaq presario V2309 using wubi.  it's been driving me nuts having to go through two boot menus every time i want to run ubuntu, which is now my preferred environment.

so i was fiddling with the boot settings and thought i had made a copy of the original.  unfortunately the changes were overwritten on the copy, so now i can only boot into windows.

would be easy to copy the text from your windows MBR that shows what i deleted?  is there a default way that wubi installs?

for example:
```
[boot loader]
timeout=20
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect
***ubuntu goes here***
```

thanks!
robb.My first thought is - if Ubuntu has become your primary OS, create a separate partition for it to avoid future problems.

It is fairly easy to update your Windows MBR to include Ubuntu. As shown from your example, Windows MBR just needs to know where to look for another OS. This might be helpful to get you started - [https://help.ubuntu.com/community/DualBoot/Mbr](https://help.ubuntu.com/community/DualBoot/Mbr)

However, grub should be all you see when you boot up. There should be no other OS choice screen.

---

### Post by Cavsfan on 2010-08-17
After **sydbat** gets you fixed up and back to normal, you might want to take a look at the
tutorial in my signature. 
It is made with dual booting in mind although it works either way to have a custom maintenance free Grub2 screen.

And no updates will touch the custom settings...

---

### Post by sydbat on 2010-08-17
> **Cavsfan said:**
> After **sydbat** gets you fixed up and back to normal, you might want to take a look at the
tutorial in my signature. 
It is made with dual booting in mind although it works either way to have a custom maintenance free Grub2 screen.

And no updates will touch the custom settings...Cavsfan - thank you!! I've been looking for this kind of thing for awhile.

---

### Post by Cavsfan on 2010-08-17
> **sydbat said:**
> Cavsfan - thank you!! I've been looking for this kind of thing for awhile.

You are most welcome! :D It is really sweet! There is an example screenshot at the bottom of the tutorial of what my screen looks like.

I just have 3 lines:
[B]Ubuntu 10.04
Ubuntu 10.04 (recovery)
Windows 7[/B]

And all of the above can be what ever you want it to be as you control what is displayed. 
 And any Grub update will not touch the custom file that you setup.
I dual boot and have Windows 7 as the default for my son and my wife and got tired of 
editing grub and changing the default line every time a kernel was installed.
Not any more.
Help spread it around please. :) I think everyone could benefit by it whether they are dual booting or not.

---

### Post by bcbc on 2010-08-17
> **robb. said:**
> i installed ubuntu on my compaq presario V2309 using wubi.  it's been driving me nuts having to go through two boot menus every time i want to run ubuntu, which is now my preferred environment.

so i was fiddling with the boot settings and thought i had made a copy of the original.  unfortunately the changes were overwritten on the copy, so now i can only boot into windows.

would be easy to copy the text from your windows MBR that shows what i deleted?  is there a default way that wubi installs?

for example:
```
[boot loader]
timeout=20
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect
***ubuntu goes here***
```

thanks!
robb.
C:\wubildr.mbr = "Ubuntu"

e.g. (ignore the fact that my windows is on the second partition)
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"
```

---

### Post by robb. on 2010-08-18
> **sydbat said:**
> My first thought is - if Ubuntu has become your primary OS, create a separate partition for it to avoid future problems.

this sounds like a great idea.  here's the rub.  i have a 60GB HDD, which because of wubi only has 16GB free.  i'd like to put windows on the first 35GB and leave 25GB to ubuntu, but 10GB of wubi stand in my way.

i have found a [howto](http://ubuntuforums.org/showthread.php?t=1519354) to migrate wubi to a partition, but there are two problems with that.  the first is that i can't currently access my wubi install.  and the second is the space issue.

i suppose i could think of worse fates.  am i stuck deleting wubi and starting over with a fresh partition?

thanks.

robb.

---

### Post by sydbat on 2010-08-18
> **robb. said:**
> this sounds like a great idea.  here's the rub.  i have a 60GB HDD, which because of wubi only has 16GB free.  i'd like to put windows on the first 35GB and leave 25GB to ubuntu, but 10GB of wubi stand in my way.

i have found a [howto](http://ubuntuforums.org/showthread.php?t=1519354) to migrate wubi to a partition, but there are two problems with that.  the first is that i can't currently access my wubi install.  and the second is the space issue.

i suppose i could think of worse fates.  **am i stuck deleting wubi and starting over with a fresh partition?**

thanks.

robb.Possibly. Do you have anything important on the wubi install? 

If not, then uninstall it via Windows Add/Remove Programs. Then repartition your HDD.

If so, I am not sure what options there are for recovering a failed/corrupt wubi installation.

---

### Post by robb. on 2010-08-18
you know, i suppose i don't have anything special on there short of a set of bookmarks in firefox.  maybe i'll go with ubuntu studio.

thanks!

robb.

---

### Post by oldfred on 2010-08-18
I do not have wubi, but saved this:
boot.ini entry:
c:\wubildr.mbr="Ubuntu-Linux"

You can mount your wubi install from a liveCD or another install:
How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

---

### Post by robb. on 2010-08-18
thanks, **oldfred** and **bcbc**.  i decided to install on a separate partition.  i'm now working my way through the **cavsfan** tutorial for GRUB2.

thanks.

robb.

---

### Post by bcbc on 2010-08-18
> **robb. said:**
> thanks, **oldfred** and **bcbc**.  i decided to install on a separate partition.  i'm now working my way through the **cavsfan** tutorial for GRUB2.

thanks.

robb.

No prob :)

I recommend keeping at least two kernels in the grub menu. Sometimes - for whatever reason - a kernel update doesn't boot, and it's handy to have the most recent one available. If you are comfortable booting from a grub prompt, that's not an issue.

---

### Post by Cavsfan on 2010-08-19
> **robb. said:**
> thanks, **oldfred** and **bcbc**.  i decided to install on a separate partition.  i'm now working my way through the **cavsfan** tutorial for GRUB2.

thanks.

robb.

Glad to hear you got it all working and that you're using my tut! 
If you want to see all of the kernels just don't make **/etc/grub.d/10_linux**  unexecutable.

At the bottom I mention that you should wait a while before making the normal files unexecutable. 
And I leave that up to you. But, at least the top 2 or 3 entries will not change.

And it now shows how to make the font larger too. Spread the word - everyone should use it!

---

### Post by bcbc on 2010-08-19
> **Cavsfan said:**
> Glad to hear you got it all working and that you're using my tut! 
If you want to see all of the kernels just don't make **/etc/grub.d/10_linux**  unexecutable.

At the bottom I mention that you should wait a while before making the normal files unexecutable. 
And I leave that up to you. But, at least the top 2 or 3 entries will not change.

And it now shows how to make the font larger too. Spread the word - everyone should use it!

Well problems usually only occur when a new kernel update is released. However, meierfra has a guide that shows how to hide the main grub menu for everyday use, but have it available if you have problems. [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

---

### Post by Cavsfan on 2010-08-20
> **bcbc said:**
> Well problems usually only occur when a new kernel update is released. However, meierfra has a guide that shows how to hide the main grub menu for everyday use, but have it available if you have problems. [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

I rely on the latest kernel and have never even had to use the recovery mode, but it's there in 
case I need it. That is all I really care to see. And it has been working smoothly like that for me.

I did say (in your quote) that you can leave  **/etc/grub.d/10_linux **executable and that way you 
can have the last 10 kernels display. It is totally up to each individual what they want their GRUB menu 
to look like...

---

### Post by bcbc on 2010-08-20
> **Cavsfan said:**
> I rely on the latest kernel and have never even had to use the recovery mode, but it's there in 
case I need it. That is all I really care to see. And it has been working smoothly like that for me.


My initial comments weren't directed at you or your guide. Just a caution for the OP who could be staring at a grub prompt. You'll see the same advice offered elsewhere on the forums.

You can incorporate something like this in your own guide or not - that's entirely up to you. But note that if a new kernel is released, and it's buggy, then the recovery mode won't work either (they both run the same kernel). If you are comfortable booting from the grub prompt, that's not a big issue, but not everyone knows how to do this.

---

### Post by Cavsfan on 2010-08-20
> **bcbc said:**
> My initial comments weren't directed at you or your guide. Just a caution for the OP who could be staring at a grub prompt. You'll see the same advice offered elsewhere on the forums.

You can incorporate something like this in your own guide or not - that's entirely up to you. But note that if a new kernel is released, and it's buggy, then the recovery mode won't work either (they both run the same kernel). If you are comfortable booting from the grub prompt, that's not a big issue, but not everyone knows how to do this.

Thanks.

---

