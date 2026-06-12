---
title: "Truly Portable?"
date: 2009-07-11
forum: General Help
---

### Post by TeamJ on 2009-07-11
Hi
I have been trying out various versions of Ubuntu, and rested on the netbook remix. Small, fast and intuitive, it has fully replaced Vista despite the fact my computer has free Home Premium OEM.
The next step, I thought was to make it portable. I am using it on a large 17" desktop replacement laptop, but I would like to be able to boot off it at friends' houses or school.
The installation USB doesn't save settings or programs, as well as locking off a lot of space. I can use the "Live USB creator" to transfer Kubuntu and Ubuntu editions to a memory stick, enabling it to leave space available and save settings, but even when I have converted the IMG to an ISO it will not do the equivalent to netbook remix.
I have considered installing it to a USB stick but I thought that running an operating system designed to run off a fast internal storage device would be slow when running off a USB storage device
So basically I am asking if there is a way to have a portable version of Ubuntu Netbook Remix that boots off a USB and still saves settings and programs to that USB, similar to the way it is possible to convert Live CDs to Live USBs on other versions of Ubuntu

---

### Post by bodyharvester on 2009-07-11
> **TeamJ said:**
> So basically I am asking if there is a way to have a portable version of Ubuntu Netbook Remix that boots off a USB and still saves settings and programs to that USB, similar to the way it is possible to convert Live CDs to Live USBs on other versions of Ubuntu

great question!

i myself am new to ubuntu and have no idea but i hope someone does!):P

although maybe if you use 2 usb's one with ubuntu and the other with your programs you could do that, i guess, but updates and so on would be troublesome

EDIT: if you have 2 usb's and try this out let me know how it works out for you!

thanks

---

### Post by TeamJ on 2009-07-11
Yeah I am a complete n00b
I would rather not go down that route, first of all I don't know how to move the programs and secondly it doesn't quite fit in with my current arrangement. I have a 16GB flash drive with the U3 Launchpad. I would rather be able to have them both, but the IMG thing doesn't allow you to keep anything from before and the Launchpad installer automatically reformats. there is not much I can do in the way of backup because of the partitioning, boot info, autorun, etc. (I am not sure if you know how the U3 Launchpad works). And of course, I would rather keep my other 15 GB of space!
Also, I have noticed the Live USB has certain things disabled and other disadvantages. I will experiment with installation to a USB, but I anticipate it to be quite slow... I once tried to install Hackint0sh to a USB and it took a whole 27 hours to load the login screen!
At the moment I have installed Vista on my smaller drive, I guess I need to have a transition period where I get used to it and have Vista as a safety zone. and also I don't know how to Dual Boot (the grub bootloader and command-line stuff confuses me - I need a nice easy GUI which is why I chose Ubuntu in the first place). I am experimenting with VMware and stuff so I can investigate it without restarting.
Also, I know this is unrelated but I don't want to start a whole new thread, any advice on beryl? It confuses me what with Compiz and Compiz Fusion and Emerald. Is it available for netbook remix? or Kubuntu? and will it work if it hasn't found a graphic driver? (I can't get VMware Tools to work)

---

### Post by bodyharvester on 2009-07-11
i wont be too muhc help here, but i think we should all be grateful that there is an OS which was designed for netbooks, Micro$oft hasnt even started yet...

> **TeamJ said:**
> I once tried to install Hackint0sh to a USB and it took a whole 27 hours to load the login screen!

27 hours? i cant wait 27 minutes;)
i love ubuntu because its so much faster than Window$

> **TeamJ said:**
> and also I don't know how to Dual Boot (the grub bootloader and command-line stuff confuses me

i suggest howtogeek.com for help dual booting, ive seen a number of articles on that

> **TeamJ said:**
> Also, I know this is unrelated but I don't want to start a whole new thread, any advice on beryl? It confuses me what with Compiz and Compiz Fusion and Emerald. Is it available for netbook remix? or Kubuntu? and will it work if it hasn't found a graphic driver? (I can't get VMware Tools to work)

search the whole forum for it (beryl, that is), if there is nothing you can find dont be afraid to start a new thread and ask for help, nobody is gonna tell you to stop opening threads and with the right title someone knowledgeable will find it

good luck

):P

---

### Post by TeamJ on 2009-07-11
I know. I hate Micro$oft as a company, but I still am hooked on their products. I guess there is a transition period when you switch over. one day the whole world will be Open source - I would love that. I have to say my favourite is OS X but it is also an annoying corporation. It is too expensive and plays annoying tricks. and it can't share it's operating system, you have to buy a crappy, expensive mac.
But anyway, thanks for your advice, I will dual-boot right away! and I don;t know why I didn't think of searching the forums. but I will get the rest sorted and step out of the virtualised world first.

---

### Post by TeamJ on 2009-07-11
ok I have successfully migrated,  I think this time it is permanent, but I am still hoping to go portable soon... has anyone else got any ideas? I haven't yet tried installing to USB but I have noticed that there is something special about the IMG. It is often unreadable or unmountable and took a long time to convert to ISO. when it did it was unbootable. so any help?

---

### Post by earthpigg on 2009-07-11
> 
So basically I am asking if there is a way to have a portable version of Ubuntu Netbook Remix that boots off a USB and still saves settings and programs to that USB, similar to the way it is possible to convert Live CDs to Live USBs on other versions of Ubuntu

it sounds like you have sucessfully created a USB startub disk that is able to save settings and programs and whatnot... can you clarify what you are asking for help with?

> It is often unreadable or unmountable and took a long time to convert to ISO. when it did it was unbootable. so any help?

have you tried usb startup disk creator using the regular ubuntu .iso?

once you get it up and working, you can install ubuntu-netbook-remix to the usb drive just like any other program in the repos:

> sudo apt-get install ubuntu-netbook-remix

---

### Post by bodyharvester on 2009-07-11
> **TeamJ said:**
> ok I have successfully migrated,  I think this time it is permanent, but I am still hoping to go portable soon... has anyone else got any ideas? I haven't yet tried installing to USB but I have noticed that there is something special about the IMG. It is often unreadable or unmountable and took a long time to convert to ISO. when it did it was unbootable. so any help?


i admire your persistence, DOOM 3 stopped working on my pc so ive bought a copy from play.com for the xbox, and ill get an xbox (original) when it arrives :P

---

### Post by TeamJ on 2009-07-12
> **earthpigg said:**
> it sounds like you have sucessfully created a USB startub disk that is able to save settings and programs and whatnot... can you clarify what you are asking for help with?

well that's the problem. I generally waffle in these posts so I will try to be clear this time
Using the IMG we can make a Live USB that installs the software. however similar to live CDs of other linux, it does not save settings or programs after each session. It also locks off a lot of space on the USB during "burning"
I am looking for a way to make a portable Live USB of netbook remix that is the opposite - doesn't lock off space, etc.

> **earthpigg said:**
> have you tried usb startup disk creator using the regular ubuntu .iso?

I don't know exactly what you mean, but using the Live USB Startup Creator I was able to do the equivalent with other Linux. But it didn't take IMG files and it is impossible to successfully convert it to ISO. it loses all its boot data and the program won't read it.

> **earthpigg said:**
> once you get it up and working, you can install ubuntu-netbook-remix to the usb drive just like any other program in the repos:

you mean install it as if to a harddrive but actually to a USB? I thought that would make it slow, as Harddrives are faster and if an OS is built to boot off a harddrive it will be slow to boot off a USB

---

### Post by TeamJ on 2009-07-12
EDIT: sorry about this post, I had a problem whan going backward and forward about forms and it posted it again

---

### Post by TeamJ on 2009-07-12
has anyone got anymore ideas? I am just waiting for it to install to memory stick

---

### Post by TeamJ on 2009-07-12
ok it runs well off the memory stick. a bit slow but never buggy. it takes up a small portion of it and leaves the rest to me. Our mission is successful, we now have Ubuntu Netbook Remix on a memory stick that boots up anywhere and saves settings, and shares the disk with a U3 Launchpad!

---

### Post by bodyharvester on 2009-07-12
> **TeamJ said:**
> ok it runs well off the memory stick. a bit slow but never buggy. it takes up a small portion of it and leaves the rest to me. Our mission is successful, we now have Ubuntu Netbook Remix on a memory stick that boots up anywhere and saves settings, and shares the disk with a U3 Launchpad!

well done, could you write up a step by step? id be interested in having something like that :)

im sure im not the only one

---

### Post by TeamJ on 2009-07-12
Well it is quite simple

1. Get the Live installation CD or USB of whichever Distro

2. boot it up

3. plug in a 4GB or above Memory Stick

4. Use the install feature

5. tell it to install to the USB

you may find it a bit slow, but it is fine really. it is a bit harder with U3

1. Install the U3 Launchpad as usual on a windows computer

2. open a partitioner

3. make space for a Linux partition

4. install Ubuntu onto that partition

you may wish to backup first, the first time my whole mempory stick corrupted

---

### Post by bodyharvester on 2009-07-12
thanks

---

### Post by TeamJ on 2009-07-12
welcome. although I think it would be good if the creators of the Live USB startup disk creator would inlcude netbook remix. or perhaps canonical could distribute portable Linux, it might make it more popular. have you heard of slax?

---

### Post by bodyharvester on 2009-07-12
> **TeamJ said:**
> welcome. although I think it would be good if the creators of the Live USB startup disk creator would inlcude netbook remix. or perhaps canonical could distribute portable Linux, it might make it more popular. have you heard of slax?

never heard of "slax"

but if a free os was handed out on USB sticks ubuntu netbook remix would control the freakin' world:lolflag: im surprised its not, until i came across your post i had never thought of something like that or that it would be possible

just need something faster than 2.0 USB's now;) ive heard theer is a 1.1 USB, that must be ooooold

---

### Post by TeamJ on 2009-07-12
basically slax is where they give you a compressed 200MB compressed folder, you unzip it and run a bat file, and you now hava a portable OS. simple. unfortunatley it is crap. to install a program you have to download a file, stick it in the right place then restart, insted of the program installer. also they are on KDE 3

anyway. if they distributed ubuntu in this way as well, it would probably get us quite a few more users

also I heard there is a 1.5 Gbps USB 3.0 coming soon.

anyway are you ganna try out NetbkRemx then?

and could you please explain to me the coffee bean system? i don't understand it ;)

---

### Post by bodyharvester on 2009-07-12
> **TeamJ said:**
> also I heard there is a 1.5 Gbps USB 3.0 coming soon.

  sweet  \\:D/  cant wait

> **TeamJ said:**
> anyway are you ganna try out NetbkRemx then?

yeah, the .img file is on my mates computer, the disk imager is on the 1Gb USB i bought for it so ill write the image onto it soon

> **TeamJ said:**
> and could you please explain to me the coffee bean system? i don't understand it ;)

no idea, dont know what the 5 cups/dipped in is either, or the flavours, havent seen anything anywhere that explains it either:roll:

---

### Post by TeamJ on 2009-07-12
> **bodyharvester said:**
> sweet  \\:D/  cant wait

well, I never like new products unless it is nearly christmas ;D

> **bodyharvester said:**
> no idea, dont know what the 5 cups/dipped in is either, or the flavours, havent seen anything anywhere that explains it either:roll:

LOL. I guess the more posts you get, the more beans you get, and the at certain times you get upgrades in your graphic and status (e.g. first cup of ubuntu)

---

### Post by TeamJ on 2009-07-12
Oppsie

I should tell youthis at home
I have failed
I thought it worked
but I gues U3 launchpad and portable UNR will never happen
ohh well
don't try this at home

---

