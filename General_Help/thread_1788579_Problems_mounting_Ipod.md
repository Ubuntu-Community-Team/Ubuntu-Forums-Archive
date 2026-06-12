---
title: "Problems mounting Ipod"
date: 2011-06-22
forum: General Help
---

### Post by hoshino. on 2011-06-22
I've been having a nightmare mounting my iPod to 11.04.
It's just one of the older 4gig ipods I've been desperately trying to mount on as my only computers run Ubuntu.

First it wouldn't even try, it gave me the superblock error. Then I stupidly:mad: proceeded to format the iPod with disk utility, thinking that the file format was to fault. Now, it does appear in my home folder, but clicking on the iPod icon, it gives me- "unable to mount Ipod : mount: special device /dev/sdc2 does not exist".

What do I do?

Sorry if this is not right section within the forums to ask this, but i desperately need help.

edit: I am a bit confused as in the disk utility it shows that the device for my ipod is dev/sdb, but the error it gives me says /dev/sdc2

---

### Post by haqking on 2011-06-22
> **hoshino. said:**
> I've been having a nightmare mounting my iPod to 11.04.
It's just one of the older 4gig ipods I've been desperately trying to mount on as my only computers run Ubuntu.

First it wouldn't even try, it gave me the superblock error. Then I stupidly:mad: proceeded to format the iPod with disk utility, thinking that the file format was to fault. Now, it does appear in my home folder, but clicking on the iPod icon, it gives me- "unable to mount Ipod : mount: special device /dev/sdc2 does not exist".

What do I do?

Sorry if this is not right section within the forums to ask this, but i desperately need help.

edit: I am a bit confused as in the disk utility it shows that the device for my ipod is dev/sdb, but the error it gives me says /dev/sdc2

try the answers provided here

[http://ubuntuforums.org/showthread.php?t=104273](http://ubuntuforums.org/showthread.php?t=104273)

---

### Post by hoshino. on 2011-06-22
...and when i do sudo mkdir /dev/sdc2 and then sudo mount -t /dev/sdc2 the ipod icon disappears from the home folder altogether. Tried the same with with /dev/sdb... although i dont think now that i have idiotically formatted my ipod that the solution can be as quick.

---

### Post by hoshino. on 2011-06-22
> **haqking said:**
> try the answers provided here

[http://ubuntuforums.org/showthread.php?t=104273](http://ubuntuforums.org/showthread.php?t=104273)

as much as I tried all that, it didn't work. I've been trying again and been trying to make sense out of it but so far no good

---

### Post by hoshino. on 2011-06-22
Hoorah i got it to mount, I ran dmesg and that gave me an idea that the fact that it wasnt formated to FAT was at fault and it was. It finally didnt give me any errors formatting it to FAT and i got it to mount and transfer files. BUT. The actual iPod now says "Use iTunes to restore"


........great:frown:

---

### Post by haqking on 2011-06-22
> **hoshino. said:**
> Hoorah i got it to mount, I ran dmesg and that gave me an idea that the fact that it wasnt formated to FAT was at fault and it was. It finally didnt give me any errors formatting it to FAT and i got it to mount and transfer files. BUT. The actual iPod now says "Use iTunes to restore"


........great:frown:

cool good job, mark the thread as solved ;-)

---

### Post by hoshino. on 2011-06-22
it is sort of solved...

gtkpod doesn't recognize it though.
it works as some sort of flash drive at the moment. which doesnt really do much. theres no interface on ipod. i tried resetting it. no luck.

---

### Post by life in color on 2011-06-23
Try updating libgpod and gtkpod. Ipod Nanos are tricky if thats what you have, if you ask me you should just sell your newer iPod and get a 30gb iPod Classic 5th Generation, it supports video and supposedly works good with Linux, I'm going to do so ASAP.

---

### Post by hoshino. on 2011-06-23
> **life in color said:**
> Try updating libgpod and gtkpod. Ipod Nanos are tricky if thats what you have, if you ask me you should just sell your newer iPod and get a 30gb iPod Classic 5th Generation, it supports video and supposedly works good with Linux, I'm going to do so ASAP.

oh yeah, its a nano... I fixed it!! took me a few hours.
but here it is: the whole problem seems to have come from the filesystem that my ipod used- it had never been used on anything else than Mac OS, therefore the filesystem must have been HFS+, which Ubuntu didn't want to recognise. That's all it was. I'm not smart enough with all this to explain why, but now my ipod works perfectly and I will tell you how:

i said i formatted it, therefore corrupting the whole ipod, obviously, which was not really necessary (useless step). Forget about gtkpod, banshee, amorok or any other linux software helping you out- they were useless with my nano. Dont try to to install iTunes either, its a major waste of time, not that it doesnt work, but it wont support any additional devices. And its unstable and WAY to complicated for it to be even remotely worth it.

What i did was i installed _Virtualbox_. It is an amazing little software. Installing the bad old XP Pro was a breathe and so was installing iTunes. After that I of course ran into the old problem of XP not accepting the USB. My ipod would show up, but cant do anything with that. After spending a good few hours and trying to fix things, stumbling on useless instructions and explanations, i ran into this:

[http://www.brighthub.com/hubfolio/matthew-casperson/articles/77025.aspx](http://www.brighthub.com/hubfolio/matthew-casperson/articles/77025.aspx) Go to step 3.

All sorted!
After that, forget about XP. My nano works just perfectly fine on Ubuntu as it is. Go to Banshee or whatever have you and sync all the music you want. :D

---

### Post by life in color on 2011-06-23
You got your nano to work with Ubuntu?!?!? please help everyone seems to find solutions for their ipod nano's but I've spent hours and nothing works! Should I re-format/restore it since it ran on windows and has like over a thousand songs installed? I would use VirtualBox but I don't have any Windows iso's!

---

