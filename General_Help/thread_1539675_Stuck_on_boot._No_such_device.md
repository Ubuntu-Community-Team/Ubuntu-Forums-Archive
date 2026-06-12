---
title: "Stuck on boot. No such device"
date: 2010-07-26
forum: General Help
---

### Post by addyc on 2010-07-26
I am having a problem with my laptop that I installed Ubuntu 9.10 on. I get a 

"Error: NO such devices: ###################"

# = letters and numbers. 

I am a COMPLETE noob when it comes to linux so please, be as descriptive as possible.. I put in some recovery discs, but they're not loading it looks like.. I still get the Error. I did searches, but I couldn't figure out what everyone was talking about.

I installed off Wubi, so I don't have a live cd to boot off of. 

This all occured after I rebooted. I can't even get into my Windows vista partition.

I do not have the vista recovery discs nor do I have the vista disc. 

Please help me?

I have no disc burner so I cannot make a live CD to boot off of. 

I am freaking out, all my hard work is on my Vista partition.

---

### Post by bcbc on 2010-07-26
> **addyc said:**
> I am having a problem with my laptop that I installed Ubuntu 9.10 on. I get a 

"Error: NO such devices: ###################"

# = letters and numbers. 

I am a COMPLETE noob when it comes to linux so please, be as descriptive as possible.. I put in some recovery discs, but they're not loading it looks like.. I still get the Error. I did searches, but I couldn't figure out what everyone was talking about.

I installed off Wubi, so I don't have a live cd to boot off of. 

This all occured after I rebooted. I can't even get into my Windows vista partition.

I do not have the vista recovery discs nor do I have the vista disc. 

Please help me?

I have no disc burner so I cannot make a live CD to boot off of. 

I am freaking out, all my hard work is on my Vista partition.
Don't worry, likely your data is all there... did you run some updates the last time you were in Ubuntu? Do you remember anything unusual? Any request to install grub or select /dev/sda? 

when you boot and see the no such device you end up at a grub> prompt. enter the following:
```
search.file /ubuntu/disks/root.disk
```

Let me know the result..

---

### Post by addyc on 2010-07-26
> **bcbc said:**
> Don't worry, likely your data is all there... did you run some updates the last time you were in Ubuntu? Do you remember anything unusual? Any request to install grub or select /dev/sda? 

when you boot and see the no such device you end up at a grub> prompt. enter the following:
```
search.file /ubuntu/disks/root.disk
```Let me know the result..

Yes if I remember correctly there was some sort of GRUB update it wanted me to do. I installed it. However I did have the option to skip it.

Let me try your suggestion. I will edit this post.

I am actually not at Grub>Prompt. it says Grub Rescue>

And I typed in what you told me to and it said Uknown command.

---

### Post by bcbc on 2010-07-26
> **addyc said:**
> Yes if I remember correctly there was some sort of GRUB update it wanted me to do. I installed it. However I did have the option to skip it.

Let me try your suggestion. I will edit this post.

I am actually not at Grub>Prompt. it says Grub Rescue>

And I typed in what you told me to and it said Uknown command.

ok how about entering "ls" (that's small case LS, without the quotes).

edit: also what version of grub is it?

---

### Post by addyc on 2010-07-26
> **bcbc said:**
> ok how about entering "ls" (that's small case LS, without the quotes)

The response it gave me was (hd0)

---

### Post by addyc on 2010-07-26
> **bcbc said:**
> ok how about entering "ls" (that's small case LS, without the quotes).

edit: also what version of grub is it?

I BELIEVE I updated it to 2. I'm not sure.

---

### Post by bcbc on 2010-07-26
I would have expected to see some partitions listed. Also apparently grub rescue only has a limited set of commands (I guess that's why the search.file didn't work).
So it doesn't look like grub rescue is going to get you very far to solving this (I was hoping you could manually boot your wubi install).

Anyway, if the first thing you see when you boot is grub, it means you installed the grub bootloader to your drive MBR. This does not work with wubi installs. You need to restore the windows bootloader.

You can replace it with a windows repair CD/DVD. For XP you have to run fixmbr, with vista/7 it's bootrec.exe /fixmbr

That should get you booting normally again. You could also do it with a live cd, but since you don't have one, go with your windows disks.

---

### Post by addyc on 2010-07-26
> **bcbc said:**
> I would have expected to see some partitions listed. Also apparently grub rescue only has a limited set of commands (I guess that's why the search.file didn't work).
So it doesn't look like grub rescue is going to get you very far to solving this (I was hoping you could manually boot your wubi install).

Anyway, if the first thing you see when you boot is grub, it means you installed the grub bootloader to your drive MBR. This does not work with wubi installs. You need to restore the windows bootloader.

You can replace it with a windows repair CD/DVD. For XP you have to run fixmbr, with vista/7 it's bootsect.exe /fixmbr

That should get you booting normally again. You could also do it with a live cd, but since you don't have one, go with your windows disks.


I actually just remembered my backup of all my work. If I just reinstall a fresh copy of windows and then wubi install ubuntu would you suggest me to stay away from updating grub so it doesn't happen again?

Also trying the bootsect.exe /fxmbr right now.

---

### Post by bcbc on 2010-07-26
> **addyc said:**
> I actually just remembered my backup of all my work. If I just reinstall a fresh copy of windows and then wubi install ubuntu would you suggest me to stay away from updating grub so it doesn't happen again?

Also trying the bootsect.exe /fxmbr right now.

You really shouldn't have to reinstall windows. Likely it's just your drive MBR you need to fix. At the worst, it'll be your bootsector as well

---

### Post by addyc on 2010-07-26
> **bcbc said:**
> You really shouldn't have to reinstall windows. Likely it's just your drive MBR you need to fix. At the worst, it'll be your bootsector as well

I just done a quick google and found this article on what to type in the terminal
[http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/](http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/)

Now it's on the windows memory diagnostics tool, and running tests.

---

### Post by bcbc on 2010-07-26
> **addyc said:**
> I just done a quick google and found this article on what to type in the terminal
[http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/](http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/)

Now it's on the windows memory diagnostics tool, and running tests.
sorry I think it's bootrec.exe /fixmbr 

Here's another link that knows better than me :)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by addyc on 2010-07-26
> **bcbc said:**
> sorry I think it's bootrec.exe /fixmbr 

Here's another link that knows better than me :)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)


It is running the diagnostics right now. It's taking a while! In the mean time. How do I avoid this problem when I reinstall linux? Or do I have to?

Both Ubuntu and Vista are working now! Thank you so much c:

---

### Post by bcbc on 2010-07-26
> **addyc said:**
> It is running the diagnostics right now. It's taking a while! In the mean time. How do I avoid this problem when I reinstall linux? Or do I have to?

WUBI installs seem particularly vulnerable to grub updates (package grub-pc specifically). I don't think they test very much on WUBI.

I guess you could avoid updating, but sometimes that's not ideal. Maybe the answer is to do a direct install to partition instead if you want to continue using Ubuntu. It doesn't make you immune to this sort of thing - if you monitor the ubuntuforums you'll see that many 'normal' ubuntu installs end up at grub prompts too, but generally you'll get better help as most forum users have never used wubi.

---

### Post by bcbc on 2010-07-26
> **addyc said:**
> It is running the diagnostics right now. It's taking a while! In the mean time. How do I avoid this problem when I reinstall linux? Or do I have to?

Both Ubuntu and Vista are working now! Thank you so much c:

Oh great - that must be a relief :)

---

