---
title: "grub rescue broken"
date: 2010-07-18
forum: General Help
---

### Post by fortyseven05 on 2010-07-18
ok. ive been looking all over the place and i cannot find where anyone else has posted this. this is what happened:
  i have a dual boot windows 7/ kubuntu system. i was adjusting the partitions through windows, trying to get rid of the kubuntu partition so i could start over from scratch with it. apparently this wasnt the way to do it  =(
  in anycase, now when i reboot, my computer goes straight to grub rescue. ive found plenty of information on what to do in that sitation, but nothing that says what to do when NONE OF THE COMMANDS WORK. and that is my problem. i am completely lost and i know pretty much nothing about grub and im just getting into linux. im pretty good with windows and know only enough about linux and ubuntu to realize they are very different creatures from windows, so you guys are probably gonna have to move pretty slow with me, so i ask for your patience and apologize for my incompetance before hand. thanks for any help

---

### Post by petrus250 on 2010-07-18
I had the same problem but with lots of ubuntu, I fixed it by changing the booting order in bios, sorry I cannot help more but I do recall having to do that and then wiping every disk and reinstalling.
hope this helps

---

### Post by fortyseven05 on 2010-07-18
i would love to be able to do that. but like i said, it goes straight to grub rescue. is there something i can do to make it so i can change the boot order? if i could do that, i could just reinstall ubuntu from my flash drive and probably fix the problem...

---

### Post by 23dornot23d on 2010-07-18
BIOS settings - as it boots either del key or F10

it should quickly display as it boots .... just hold the key down ..... f10 possibly


________________________________________________

Boot up from a UBUNTU CD and re-install it in a clean partition ....... 
then you should be able to set your boot loader back again.

Have you tried this once already ..... why were you deleting it from within Windows ?

---

### Post by fortyseven05 on 2010-07-18
> **23dornot23d said:**
> Boot up from a UBUNTU CD and re-install it in a clean partition ....... 
then you should be able to set your boot loader back again.

Have you tried this once already ..... why were you deleting it from within Windows ?

well... i read on another forum that deleting the partion was the fastest and easiest way to get rid of kubuntu. i wanted to replace kubuntu 9.10 with ubuntu 10. 
 i dont have an actual boot disk tho. all i have is my usb flash drive. thats what ive been using to install ubuntu so far. up to this point it hasnt really made much sense to get a disk becuase ive been uninstalling and trying different distros, so i would just change out which one was on the flash drive and go to town. so. no disk.

---

### Post by 23dornot23d on 2010-07-18
Ok what computer is it you are using ..... 
Acer is F2 to get to the BIOS to change the boot settings ..... or can you boot the flash ok now.

You may have deleted the boot information, it should come back again with a clean install
of Ubuntu 10.04 ..... 

I believe that is what you are installing.

I always install from CD direct to a separate partition.

---

### Post by fortyseven05 on 2010-07-18
I have an asus.

---

### Post by 23dornot23d on 2010-07-18
Looking on the BIOS search 
del seems to be the key to use to get to the BIOS settings
to change the boot order ....

How did you boot from the flash drive before ..... it should already be set that way
if you have been doing it previously ?

Can you boot from the flash .... how are you logged on at the moment in Windows ?

---

### Post by fortyseven05 on 2010-07-18
Well that's part of what I don't understand. I haven't. Changed my boot order, but its not booting the flash drive. Lemme try del real quick

---

### Post by 23dornot23d on 2010-07-18
Can you burn a live CD if this is the system you are going to install it may be worth having one.

Is the Flash ok can you check it from Windows .... 

I have only used flash a couple of times so if that is the way you install it .... it may be worth someone
else helping you out here ..... sounds like the flash may be the problem.

---

### Post by fortyseven05 on 2010-07-18
Del didn't work, but f2 did. Boot sequence still had removable device and first, so the only thing I can think of is my flash drive must have gotten messed up. Ill try redoing it and trying again. Otherwise, ill go ahead and use my wifes computer to make a disk. 
 Just to clarify tho, did I just delete grub or what? What got messed up? I was under the immpression that grub had its own little partition.

---

### Post by fortyseven05 on 2010-07-18
> **23dornot23d said:**
> Looking on the BIOS search 
del seems to be the key to use to get to the BIOS settings
to change the boot order ....

How did you boot from the flash drive before ..... it should already be set that way
if you have been doing it previously ?

Can you boot from the flash .... how are you logged on at the moment in Windows ?

Oh to answer your question, I'm not logged in on windows, I've been using my fancy pants droid (smiley face)

---

### Post by 23dornot23d on 2010-07-18
If you deleted the partition from windows with the boot files in it for GRUB2

They are usually on the one partition unless you specify otherwise.

then when you rebooted they were no longer there to find .......

so you could go no further
_________________________________________________________
I set mine (/) (/home) and (swap)

so that there are 3 separate partitions ..... 

(/) is the root for all the system files etc
(/home) is for all your data ..... desktop etc ....
(swap) space is just used for memory overflow I think .....
__________________________________________________________
  ..... but they can be created again when you re-install

---

### Post by fortyseven05 on 2010-07-18
I thought so. Is there a way to put grub on its own partition?

---

### Post by 23dornot23d on 2010-07-18
There is a (/boot)
that you can set up ..... but I have never done it this way ......

I usually have it in the root directory ,,,,, you could try to research it .....

but usually when you remove a system the boot goes with it and then you create
a new one ...... 

I have 13 separate systems on my laptop (+2 USBs ) and they all boot individually from one menu
but if I add another system .... 

I just do a update-grub from the main one - and then it rebuilds to add the new one.

---

### Post by lordskid on 2010-07-18
If you have the live cd you can just boot from cd. and set up your ubuntu.
if you just wanted to go ubuntu 10.04 from kubuntu check this site:
[http://psychocats.net](http://psychocats.net)

or google ubuntu pure gnome...

---

