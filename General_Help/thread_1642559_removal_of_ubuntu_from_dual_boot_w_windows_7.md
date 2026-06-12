---
title: "removal of ubuntu from dual boot w/ windows 7"
date: 2010-12-10
forum: General Help
---

### Post by Glasgow.Tony on 2010-12-10
i was using windows 7 and started to get sick of windows completely, so i installed ubuntu and was dual booting between the two.. somewhere down the line i had made a mistake (can't remember exactly what) and instead of properly fixing the issue i decided to re-install ubuntu, but in doing so i now have created another partition and another install of ubuntu, so i have 2 ubuntu's an a windows 7. i would like to remove the 2 ubuntus and remove the partitioning to return to just having windows 7 installed and then i intend to install ubuntu studio. i have done some searching on this issue and i am still not entirely sure what needs done and how to do it without messing anything up.

i have read that i need to run *fdisk /mbr* from a windows command prompt and that this will fix the master boot record and return it to only having the option to boot into windows, but i also read that this can cause problems if the disk has more than 4 partitions (which it does, courtesy of 3 OS's and a couple of storage partitions).

so in summary: remove both ubuntu installations and return the disk to the partitions that were there before i installed ubuntu the first time.

any help greatly appreciated. would like to get this sorted out and eventually just get rid of windows altogether. there are a few windows programs that i will miss, but ubuntu studio seems to have most of them covered so after a bit of learning and adapting there will hopefully be no need for the unstable, expensive, non-secure heap of crap that is microsoft windows.

---

### Post by argedion on 2010-12-10
Either use Ubuntu live CD or G-parted live and delete the partitions you need to delete then fix mbr. Do note you should make sure you have everything backed up to an external device incase anything goes wrong.

---

### Post by Hippytaff on 2010-12-10
I'm not sure if there is an iso of ubuntu studio, thought I think there is. If so download it and burn it to cd. Then boot from cd. Choose to install. During the install process you will be asked about partitioning choose manual. Then you can choose to delete partitions. Delete the ones that the ubuntu is installed on then you can install ubuntu-studio on the remaining space. Think about having a seperate /home partition :-)

---

### Post by Glasgow.Tony on 2010-12-10
ok thanks guys. that seems simple enough. i do have the iso of ubuntu studio burnt to disc already, i should probably have figured out that i could just boot from it and remove the partitions then install into that space.

ty :)

---

### Post by Hippytaff on 2010-12-10
> **Glasgow.Tony said:**
> ok thanks guys. that seems simple enough. i do have the iso of ubuntu studio burnt to disc already, i should probably have figured out that i could just boot from it and remove the partitions then install into that space.

ty :)

The things I could've figured out and then kicked myself after posting...check out my Debian thread
[http://ubuntuforums.org/showthread.php?t=1640252](http://ubuntuforums.org/showthread.php?t=1640252)
 What kind of moron am I? :roll:

That's what is so good about the Ubuntu community above all other Linux communities :-)

---

