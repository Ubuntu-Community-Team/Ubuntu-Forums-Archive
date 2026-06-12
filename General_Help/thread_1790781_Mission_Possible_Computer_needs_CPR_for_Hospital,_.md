---
title: "Mission Possible: Computer needs CPR for Hospital, Help Please!"
date: 2011-06-25
forum: General Help
---

### Post by Zerocool Djx on 2011-06-25
Hey everyone,

   Ok, if you all can help I would very much appreciate this! My mother is in the hospital and she is going to be there a few days or more :(. I have an old laptop I ussually use for command line stuff, but I want to be able to connect through skype to her. The problem is the computer is prolly 15 years old, LOL. It is a netbook-laptop. I need to find the best way to tweak the crap out of this thing to get it to run as well is it can. here is what I am working with. I am not even sure how to get info for hardware, but maybe some of you do.


Specs:

[Dell Latitude X200]("http://www.pcmag.com/article2/0,2817,1042033,00.asp")

What I need:

1) Graphic drivers, I don't know where to check for the hardware info. I am assuming that it's the standard card still in it considering it's a laptop. 

2) Audio drivers if they don't come with OS iso. I am sure alsa mixer will work tho.

3) A "readyboost" - Linux style option, which I have a feeling is going to be a swap area, but if there is a better more efficient way to do this I would love to hear it. I have a USB 2GB thumb drive I wanna use for ram that I think given the age will work better then the old chip in there anyway. 

4) Right now the hard drive is wiped, there is no operating system. I much like everyone can download any Linux OS, but I need to find the best, user friendly, light weight option possible. My mother isn't 100 years old or anything, but she's not as savy as me to say the least with computers so something easy to use would be a 50/50 with performance. I was thinking of putting on Ubuntu 9.10, but if there is an equivalent of say "Win XP Lite" out there I would love to try it.

Anyway I can over clock this thing, tweak it out to make it more efficient is good. I mean this is a dinosaur I am not going to pretend  it's anything other then what it is, but she only needs entertainment  and I want up to date min by min communication with her and I am home on  my computer all day so this seems like it will work. 


Anything anyone can think of would help a lot!. I plan on getting back to her in the hospital as soon as all this stuff is worked out and I can bring computer to her.


Thank you a head of time!

Z

---

### Post by Zerocool Djx on 2011-06-25
Sorry a head of time for the possible multiple bumps I might do, but I not want this thread to get lost and I wanna get back up there asap.

---

### Post by TeoBigusGeekus on 2011-06-25
You could try Slitaz, Damn Small Linux (not developed any more but still available afaik) or Puppy Linux.
If you want to stick to the ubuntu family, your best bet is Lubuntu.
If you think you can manage it, you could try an Arch linux installation with Openbox as the desktop manager.

---

### Post by Zerocool Djx on 2011-06-25
I was looking just now at Lubuntu with adding aviant windows manager for her so she can navigate really easy. But, from what I understand, Lubuntu doesn't have much to it hence the lightweight. I do need the drivers for the display. Any chance someone could help me find them?

---

### Post by Zerocool Djx on 2011-06-25
Also, she likes farmville on FB. is there any linux sourced game like that I can install for her?

---

### Post by TeoBigusGeekus on 2011-06-25
About the drivers: why don't you check out with a live cd/usb and see if your graphics and sound card are recognized automatically?

---

### Post by Zerocool Djx on 2011-06-25
most linux will have a default video card something in it. but on my home computer for example I needed to install extra drivers to get special effects working. I was wondering if this would be needed for this cause I am going to load movies on it so she can watch them via VLC.

---

### Post by TeoBigusGeekus on 2011-06-25
The pc, being quite old as you've mentioned, is more likely to have all its problems solved (linux wise) than your (newer I presume) system.
Give it a go.

---

### Post by Zerocool Djx on 2011-06-25
Thanks!

Also I found this for the "ready boost" a posting on here....

[http://ubuntuforums.org/showthread.php?t=395435](http://ubuntuforums.org/showthread.php?t=395435)


Looks promising, but if she disconnects the USB drive will it kill the OS system? If so, can someone help me with a Terminal App that I she can click to turn that on and off?

---

### Post by TeoBigusGeekus on 2011-06-25
You don't need this kind of solution (read the last post on that thread).
The machine has 30gb of space; you can make your swap partition 2gb or something and everything will be fine.

---

### Post by Zerocool Djx on 2011-06-25
I thought a USB might work faster, but if that's the case I'll go for it.

So,... manual installation? Been a while since I did that.

Jump to 2:55 on this video

[http://www.youtube.com/watch?v=GhnLk3gviWY](http://www.youtube.com/watch?v=GhnLk3gviWY)

Just like this right?

---

### Post by TeoBigusGeekus on 2011-06-25
Right.
Even if you don't get it right the first time, you could try again - (l/x/k)ubuntu installs in less than half an hour nowadays.

---

### Post by Zerocool Djx on 2011-06-25
Does making a dock like rocket dock on a Linux machine make it more usable? Does it have any performance draw backs? Or should I just leave traditional icons on the desktop. I plan on filling the HD with movies for her.

---

### Post by TeoBigusGeekus on 2011-06-25
The less you install, the more responsive the system will be.
So, no docks, no compiz, no cubes, etc.
A vanilla installation of lubuntu would be fine.
Also consider an external hd for the movies.

---

### Post by walt.smith1960 on 2011-06-25
How much RAM does your X200 have now?  The PC Mag. article indicates they came with 256 meg. According to the memory advisor at Crucial, your X200 can add 512 meg. RAM for a total of 640. 
[http://www.crucial.com/store/listparts.aspx?model=Latitude%20X200%20Series]("http://www.crucial.com/store/listparts.aspx?model=Latitude%20X200%20Series")
Lubuntu should be happy with that.  $74.99 seems expensive, though so you might shop around.  I hope your Mom gets well soon.

---

### Post by TeoBigusGeekus on 2011-06-25
> **walt.smith1960 said:**
> I hope your Mom gets well soon.

^^^^This.

---

### Post by Zerocool Djx on 2011-06-25
> **TeoBigusGeekus said:**
> ^^^^This.

thank you!

CPU Speed: 800Mhz
It says system memory : 640MB

still the 30 GB HD though..

---

### Post by Zerocool Djx on 2011-06-25
> **TeoBigusGeekus said:**
> 
Also consider an external hd for the movies.

Will the HD be to slow to play them or you just saying for space issues?

---

### Post by TeoBigusGeekus on 2011-06-25
> **Zerocool Djx said:**
> Will the HD be to slow to play them or you just saying for space issues?

Just for space issues.

> System memory: 640MB

Is this the laptop's ram? If it is, then you won't have many problems.

---

### Post by Zerocool Djx on 2011-06-25
> **TeoBigusGeekus said:**
> Just for space issues.



Is this the laptop's ram? If it is, then you won't have many problems.

I think so,..  I still gonna make 2GB swap area tho.


I mounted an ext4 file system is that ok?

---

### Post by TeoBigusGeekus on 2011-06-25
Ext4 is faster. Go with it.

---

### Post by Sylslay on 2011-06-25
If HDD is fast enough, then Ubuntu will work fine.

My cousin had IBM R31 with ubuntu, 512Ram, P3 800, and sagate 40gb/4200rpm.

I was able to make skype phonecall on that system, ofcourse qullity bit worse then on p4-m 1.6GHZ.

BTW. 6 years old cousin got 40 native games on it and enyoy it. All without 3D, only 

[http://en.wikipedia.org/wiki/Simple_DirectMedia_Layer](http://en.wikipedia.org/wiki/Simple_DirectMedia_Layer)


Last game installed was "Battle of Wesnoth" LOL. 200MB instaled!!!

Recomendede upgrade: becosuse speed of Yours hdd could be a bottleneck.
Samsung 40GB 'MP0402H' 2.5" ATA100 HDD - 5400rpm, 8MB Cache for upgrade.
Or 80GB,

[http://www.getpartsonline.com/mp0402h.html](http://www.getpartsonline.com/mp0402h.html) 

As a worldwide leader in storage technology, Samsung brings you the SpinPoint M series of 2.5" hard disk drives. With capacities of 40GB, 5,400 RPM, Ultra ATA 100 support, and fluid dynamic bearing spindle motor technology built into each drive, there is a SpinPoint M series hard disk for every need. What's more, each drive is GMR Head Technology with Wireless Suspension Design and features Silentec Hybrid Latch Technology TM and SilentSeekTM technologies to keep your drive running quietly. Only Samsung offers this combination of technology in our performance line of hard disk drives: the SpinPoint M series.


or any 5400rpm , hdd,

---

### Post by Zerocool Djx on 2011-06-25
> **TeoBigusGeekus said:**
> Ext4 is faster. Go with it.

10-4, thanks so much for your help! :)



> **Sylslay said:**
> If HDD is fast enough, then Ubuntu will work fine.

My cousin had IBM R31 with ubuntu, 512Ram, P3 800, and sagate 40gb/4200rpm.

I was able to make skype phonecall on that system, ofcourse qullity bit worse then on p4-m 1.6GHZ.



I had Ubuntu 9.10 and 8.10 on it before and it ran, but since I have a desktop and this thing is so old I wanted to squeeze the most out of the thing performance wise.

Good to know about skype calls! Much cheaper then paying for hospital room phones. $9 a day that insurance don't cover! what rip off! That's practically 3 months service with Skype to call out!

Good to know about hard drive, tho I don't think I'll do that, if I spend any money it will be for a new netbook.

---

### Post by Zerocool Djx on 2011-06-25
one more thing,.. the computer has an on board wifi card, being a dell I think it's a broadcom card. I was wondering about drivers for that. Sorry just trying to think ahead while this OS system installs.

---

### Post by TeoBigusGeekus on 2011-06-25
> **Zerocool Djx said:**
> one more thing,.. the computer has an on board wifi card, being a dell I think it's a broadcom card.

Oops...
Cross your fingers...

---

### Post by Sylslay on 2011-06-25
I had an old laptop and use wi-fi on PCMI card or USB.
All wit Ra2500 chip.

First try and then worry about wi-fi.

BTW:

MY COUSIN'S LAPOTP GOT [COLOR="Red"]10.04 UBUNTU[/COLOR] INSTALED WITH LATEST UPDATE. 
BEST VERSION OF ANY OS/UBUNTU IMHO.
AND HIS OLD GPU INTEL 830 IS MORE RESPONSIVE THEN INTEL GPU 845 ON MOBO WITH 2.5GZ CPU :-).

IN THIS CASE HDD IS BOTTELNECK AND SOME TIME SOMEONE HAD SPARE HDD, 
I AGREE WITH YOU THAT IS NOT WORTH TO SPEND EXTRA CASH ON THIS LAPTOP.
IS WORTH ALL TOGETHER ABOUT 50 EURO ON EBAY IN Eu

---

### Post by Zerocool Djx on 2011-06-25
worse case I have a alfa awus036h wireless adapter I can loan her while she is there.

---

### Post by bruno9779 on 2011-06-25
I tinkered with one of those while working in a tech support centre.

I remember it having the infamous broadcom b43xx family wifi card. (google search seems to confirm this).

I also remember getting it to work after several attempts. It is possible, just don't give up.

In case you couldn't get it to work with the hospital's access points, consider buying a linux compatible USB wifi dongle. They are cheap and always come handy.

EDIT: I didn't see your last reply. Give it a go with the b43 drivers, but do not expect too much from that

---

### Post by Zerocool Djx on 2011-06-25
> **bruno9779 said:**
> I tinkered with one of those while working in a tech support centre.

I remember it having the infamous broadcom b43xx family wifi card. (google search seems to confirm this).

I also remember getting it to work after several attempts. It is possible, just don't give up.

In case you couldn't get it to work with the hospital's access points, consider buying a linux compatible USB wifi dongle. They are cheap and always come handy.

EDIT: I didn't see your last reply. Give it a go with the b43 drivers, but do not expect too much from that

Need drivers for the broadcom card, I think i have them but well see. Alfa works out of the box. I do notice a nice improvement in performance tho with Lubuntu.

---

### Post by Zerocool Djx on 2011-06-25
nm

---

### Post by Zerocool Djx on 2011-06-25
crap,.. I got to go with regular Ubuntu. Lubuntu's kernal is empty. :( more time wasted

---

### Post by Sylslay on 2011-06-26
Well ,,,,, 
what a pity.

try wi-fi card on liveCD,

Regular Ubuntu 10.04 with 

sudo apt-get install ubuntu-restricted-extras

does the job :guitar:

---

### Post by walt.smith1960 on 2011-06-26
> **Zerocool Djx said:**
> crap,.. I got to go with regular Ubuntu. Lubuntu's kernal is empty. :( more time wasted

Kernel empty? How's that? It wouldn't boot?

---

### Post by Zerocool Djx on 2011-06-26
> **walt.smith1960 said:**
> Kernel empty? How's that? It wouldn't boot?

when I tried to compile drives with the ./configure , make, install make... etc make isn't in the kernal. Which is kinda a issue for them. I uninstalled it because of it. 

I also found out how to get the brodcom card working. It seems ubuntu black listed it, why? I have no idea. but after installing ubuntu I unblack-listed it and installed the driver and now it is working.

I got the X200 up and running putting movies on it now then going to visit her.

---

