---
title: "Ubuntu destroyed my thumbdrive"
date: 2011-07-03
forum: General Help
---

### Post by ettin on 2011-07-03
I got ubuntu 11 to install on my x86 desktop computer as a live install, then i plugged a 4gb ntfs usb drive into it and it worked for a few minutes and then just disappeared. So i plugged it into my windows machine and it now says windows cant read the drive even though it shows up as present. I tried some drive recovery tools but none of them read it. Now ive lost a drive and all my data, i guess ubuntu does have a price.

---

### Post by Keypel on 2011-07-03
Is it possible that the drive is no longer formated in ntfs and that being the reason the M$ windblows OS can't read it?

---

### Post by ettin on 2011-07-03
I tried a raw drive recovery tool and it says that there is no partition, so ubuntu just randomly deleted my drive partition. I dont know what to do, i had alot of stuff on there that would take forever to recover.

---

### Post by Keypel on 2011-07-03
> **ettin said:**
> I tried a raw drive recovery tool and it says that there is no partition, so ubuntu just randomly deleted my drive partition. I dont know what to do, i had alot of stuff on there that would take forever to recover.

I would try pluging the thumb drive into a working linux system and then try reading it.

If the drive is still in ntfs, I have a few recovery tools you could try. If the drive is now in ext4, then recovery might be difficult.

---

### Post by CajunPirate on 2011-07-03
Ubuntu has a very powerful recovery program available. I used it to recover files from a external hd that crashed. It works with both FAT 32 and NTFS. Here's the link, let me know if you need more help:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by jtarin on 2011-07-03
> **ettin said:**
>  then i plugged a 4gb ntfs usb drive into it and it worked for a few minutes and then just disappeared.Plug your drive into Ubuntu and issue the command ```
lsusb
``` and post the results. After that you might do a [little research]("http://tldp.org/HOWTO/Partition/recovering.html") while you waiting for a reply.

---

### Post by ettin on 2011-07-03
Windows says the filesystem is unknown.

---

### Post by Keypel on 2011-07-03
> **ettin said:**
> Windows says the filesystem is unknown.

My question is, what does a linux system say...

I have a feeling the drive is no longer ntfs, which is why windows is not reading it.

---

### Post by ettin on 2011-07-03
Holy **** im trying to turn my computer back on and it just runs at full speed with a blank screen. It was just working a moment ago when i booted into windows to check the usb, what the hell did ubuntu do to my god damn system.

---

### Post by dFlyer on 2011-07-03
> **ettin said:**
> I got ubuntu 11 to install on my x86 desktop computer as a live install, then i plugged a 4gb ntfs usb drive into it and it worked for a few minutes and then just disappeared. So i plugged it into my windows machine and it now says windows cant read the drive even though it shows up as present. I tried some drive recovery tools but none of them read it. Now ive lost a drive and all my data, i guess ubuntu does have a price.

I don't see how ubuntu could distroy your usb drive without you doing something to it like formating it or not unmounting it when you removed the drive.

---

### Post by ettin on 2011-07-03
Its was working until i went to install flash and then go back into firefox and then suddenly the drive wasnt there. WHY THE HELL IS MY COMPUTER NO LONGER BOOTING??????????????

---

### Post by flipper T on 2011-07-03
2 things

a quick look at your post history shows that you tried ti install ubuntu on the usb...were you going to mention this salient fact in this thread


secondly, that thread was closed because you were trolling...


trolling again ?

---

### Post by ettin on 2011-07-03
Wow, ive never been treated so poorly by a community before. Not only has your shoddy software destroyed my thumbdrive and my computer, but as expected when something goes wrong you defend it like its my fault and then censor me and lock my threads. Bullies, all of you.

---

### Post by flipper T on 2011-07-03
> in most ways, two-headed trolls fight like normal trolls, but with added strength and perception (much like an ettin)

source :[http://dungeonsdragons.wikia.com/wiki/Two-Headed_Troll](http://dungeonsdragons.wikia.com/wiki/Two-Headed_Troll)



2 headed trolling...nice

---

### Post by grahammechanical on 2011-07-03
Well done flipper T!

Here is another quote from the same link

> Ettins are giantkin born with two heads. They are unkempt, brutish,  slovenly giants, fairly dull despite the two brains working on the  single body. Each head controls one half of the body, so if the two  quarrel, little can actually get done.

I also saw the previous post and was about to say something.

Regards.

---

### Post by d3v1150m471c on 2011-07-03
Find the mount point by issuing the following command with the usb inserted or a different usb:
```

df -h

```Make sure you don't input the mount point of your harddrive for the next command. On my system my usb is /dev/sdb1 so in the next command we'll drop the 1 and use /dev/sdb:
```

sudo parted /dev/sdb

```From there you can type help for a list of options. if you want to restore the ntfs filesystem, within parted you will likely use:
```

mkfs 1 ntfs

```
[COLOR=DarkRed]**^^^**[/COLOR] [COLOR=DarkRed][B]This will erase all the data on the usb drive ^^^

[/B][COLOR=Black]I had to do this to repair and even use my external hd after my system crashed while writing a backup to it. Works perfectly now.[/COLOR]
[/COLOR]

---

### Post by flipper T on 2011-07-03
> They are dirty and disgusting, reeking of their own body odors, as they  never bathe if they can help it. Their skin ranges in human tones, but  is frequently caked in dirt and grime, making them grey, green, or some  other unhealthy pallor. The heads of ettins are recognizably human, but  distorted with poor hygene and furious violence, leaving them thuggish  and ugly, with mouths full of rotten, yellowing teeth, and dirty,  vermin-infested hair.

my longstanding dislike of all things d&d is being challenged by dungeonsdragons.wikia.com


:)

---

### Post by Rasa1111 on 2011-07-03
> **dFlyer said:**
> I don't see how ubuntu could distroy your usb drive without you doing something to it like formating it or not unmounting it when you removed the drive.


Exactly.

Ubuntu doesnt just delete things or perform crucial operations like that without you telling it to do so.

Maybe its being a noob is what "has a price" , hmm OP? 
i know, I was a total newb like, 20 months ago. and messed a couple things up,
and everything I messed up was due to my own ignorance. lol
Dont blame your own ignorance on Ubuntu. 
:rolleyes:

---

### Post by flipper T on 2011-07-03
Rasa1111 your insistence on using actual _**facts**_ in this thread is slightly worrisome and could easily be perceived as bullying the OP.

please cease & desist.



:lolflag:

---

### Post by jtarin on 2011-07-03
> **ettin said:**
> Wow, ive never been treated so poorly by a community before. Not only has your shoddy software destroyed my thumbdrive and my computer, but as expected when something goes wrong you defend it like its my fault and then censor me and lock my threads. Bullies, all of you.I've never helped someone before that refuses to follow instructions. In all your naivete you do what a normal immature person in your position does. Blame something or someone else for your faults. Follow instructions and get off the "shoddy software soap-box" and perhaps we can help you help yourself and back out of this embarrassing situation you have got into.

---

### Post by Rasa1111 on 2011-07-03
> **flipper T said:**
> Rasa1111 your insistence on using actual _**facts**_ in this thread is slightly worrisome and could easily be perceived as bullying the OP.

please cease & desist.



:lolflag:

haha ! :lolflag:

Should I apologize? lol  :P

> Holy **** im trying to turn my computer back on and it just runs at full  speed with a blank screen. It was just working a moment ago when i  booted into windows to check the usb, what the hell did ubuntu do to my  god damn system.and another :lolflag: mixed wit a little bit of :rolleyes: 

The question is, [I]"What did YOU do to your g.d. system?"

[/I]Anywayflipper T, 
I think you're right.
[IMG]http://img.photobucket.com/albums/v439/c5zilla/Forum/5191troll-o-meter.jpg[/IMG]
:mad:

---

