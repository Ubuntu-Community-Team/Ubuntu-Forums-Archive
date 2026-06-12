---
title: "Ready to chuck the PC off the balcony"
date: 2010-06-29
forum: General Help
---

### Post by Casper Ghost on 2010-06-29
I have the dreaded blinking cursor.](*,)

But let me give some background info. I have had vista on my rig for about 4 years. Not really impressed but it worked. Finally one of hard drives had an aneurysm, the one that vista was on. So I decided just to get a new drive and start with Ubuntu. I downloaded and burned both the 64 and 32 on separate disks.

I start everything up. Post is fine, Bios is good, goes to a little picture of a keyboard and Encircled Man. I hit a button and it says load Ubuntu which goes to a blinking cursor.

Ok now that being said. I have read a bunch of articles on here. Some say to hit the F6, nomo something or other, key press esc key and do a quiet splash, xforcevesa,... I am sorry but I am a noob and have no clue what any of this means.

Now I hit the esc key and I get "boot:" I type in "quiet splash", and then it comes back with: I have no clue WTF your talking about... I am paraphrasing, I type in xforcevesa and I get the same response. Followed by, your a noob and you need to get some help from more competent authorities... Again I am paraphrasing, but here I am.

If someone could explain this to me in my native language of mentally handicapped I would appreciate it.

Thank ya kindly in advance!

---

### Post by Jakiejake on 2010-06-29
> **Casper Ghost said:**
> I have the dreaded blinking cursor.](*,)

But let me give some background info. I have had vista on my rig for about 4 years. Not really impressed but it worked. Finally one of hard drives had an aneurysm, the one that vista was on. So I decided just to get a new drive and start with Ubuntu. I downloaded and burned both the 64 and 32 on separate disks.

I start everything up. Post is fine, Bios is good, goes to a little picture of a keyboard and Encircled Man. I hit a button and it says load Ubuntu which goes to a blinking cursor.

Ok now that being said. I have read a bunch of articles on here. Some say to hit the F6, nomo something or other, key press esc key and do a quiet splash, xforcevesa,... I am sorry but I am a noob and have no clue what any of this means.

Now I hit the esc key and I get "boot:" I type in "quiet splash", and then it comes back with: I have no clue WTF your talking about... I am paraphrasing, I type in xforcevesa and I get the same response. Followed by, your a noob and you need to get some help from more competent authorities... Again I am paraphrasing, but here I am.

If someone could explain this to me in my native language of mentally handicapped I would appreciate it.

Thank ya kindly in advance!

FIRST OF ALL
Don't kill your computer, it's the software thats the problem not the hardware!
Can I please have the specs of the computer
And are you using a DVI or VGA Cable?

---

### Post by dtfinch on 2010-06-29
Is it accessing the hard disk during the blank screen?

I've had past installs (years ago) where the splash screen didn't work and because it was quiet, it would sit there with a blank screen and a blinking cursor, not saying that it was spending 5-10 minutes checking the disk for errors. I always turn off quiet and splash because of things like that.

---

### Post by Casper Ghost on 2010-06-29
> **Jakiejake said:**
> FIRST OF ALL
Don't kill your computer, it's the software thats the problem not the hardware!
Can I please have the specs of the computer
And are you using a DVI or VGA Cable?

Ok I have a[SIZE=2] 
MSI N8400GS-D512 GeForce 8400 GS 512MB 64-bit DDR2 PCI Express 2.0 x16 HDCP Ready  Low Profile Ready Video Card 					[/SIZE]

I don't remember the exact specs on my motherboard but its got MSI printed all over it. with intel chipset.

and I am using a VGA cable

If you tell me where to look I can get you better info.

---

### Post by Casper Ghost on 2010-06-29
Right now I am digging for my booklets, I got them somewhere around here but with a bunch of kids things get misplaced easily, that and a wife who wants to organize everything contrary to the way you want things organized ... sigh

---

### Post by Jakiejake on 2010-06-29
> **Casper Ghost said:**
> Ok I have a[SIZE=2] 
MSI N8400GS-D512 GeForce 8400 GS 512MB 64-bit DDR2 PCI Express 2.0 x16 HDCP Ready  Low Profile Ready Video Card 					[/SIZE]

I don't remember the exact specs on my motherboard but its got MSI printed all over it. with intel chipset.

and I am using a VGA cable

If you tell me where to look I can get you better info.

Can you boot to the live desktop by going to "Try Ubuntu Without Installing"?

---

### Post by Jakiejake on 2010-06-29
> **Casper Ghost said:**
> Right now I am digging for my booklets, I got them somewhere around here but with a bunch of kids things get misplaced easily, that and a wife who wants to organize everything contrary to the way you want things organized ... sigh

LOL
Oh and welcome to the Ubuntu Forums!

---

### Post by Casper Ghost on 2010-06-29
> **Jakiejake said:**
> LOL
Oh and welcome to the Ubuntu Forums!

OK I am trying it now.

By the way I have a 945P series (MS-7176) v1.x ATX mainboard

Thanks for the welcome, that and for the intervention of seeing if my PC could fly. Probably saved some passerby's life ; )

---

### Post by Casper Ghost on 2010-06-29
No good, I still get the blinking cursor.

---

### Post by Jakiejake on 2010-06-29
> **Casper Ghost said:**
> No good, I still get the blinking cursor.

Got a bridge near your house?
I'll Keep Looking

---

### Post by dino99 on 2010-06-29
when you boot you should see the grub menu, if not, at end of bios process, hold "shift" key down to see the grub menu

then highlight the line you want to boot on and edit it by pressing E on the keyboard; you will see that line ending with quiet splash: remove them (quiet splash) and boot

if it fail again, redo as above and add nomodeset before booting

---

### Post by Casper Ghost on 2010-06-29
> **Jakiejake said:**
> Got a bridge near your house?
I'll Keep Looking

Yea I got a bridge, but by the time I have lugged this thing down there I don't think I would have the energy to chuck it... Fixing it seems the lesser of two evils at this point... I am lazy like that.

---

### Post by Casper Ghost on 2010-06-29
> **dino99 said:**
> when you boot you should see the grub menu, if not, at end of bios process, hold "shift" key down to see the grub menu

then highlight the line you want to boot on and edit it by pressing E on the keyboard; you will see that line ending with quiet splash: remove them (quiet splash) and boot

if it fail again, redo as above and add nomodeset before booting

Ok holding the shift key down I get the question "Load boot graphics (y/n)? I hit yes

Next "detect display size (y/n)? I hit yes

Then it says "initializing gfx code...

mem area 0: bla bla bla
mem area 1: etc 

If you want me to type this up I will

"press any key to continue" so I do

and it takes me to the menu again.

---

### Post by dino99 on 2010-06-29
what kind of installation have you done ?

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by Casper Ghost on 2010-06-29
> **dino99 said:**
> what kind of installation have you done ?

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

Not sure I understand the link.

This is a brand new hardrive. I just plugged it in and loaded the ubuntu disk into the drive.

---

### Post by Casper Ghost on 2010-06-29
> **dino99 said:**
> what kind of installation have you done ?

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

I guess my question is how can I run partitioning software without an operating system?

---

### Post by dino99 on 2010-06-29
maybe to might listen the wife or read the above link  :lolflag:

---

### Post by Casper Ghost on 2010-06-29
> **dino99 said:**
> maybe to might listen the wife or read the above link  :lolflag:

Listen to the wife?!? Blasphemy!:lolflag:

I guess I am gonna have to try and understand what your link means, I didn't even know what a partition was until you posted that link and even then I had to look into it.

Like I said... I am a noob.

---

### Post by Jakiejake on 2010-06-29
> **Casper Ghost said:**
> Listen to the wife?!? Blasphemy!:lolflag:

I guess I am gonna have to try and understand what your link means, I didn't even know what a partition was until you posted that link and even then I had to look into it.

Like I said... I am a noob.

BRAIN WAVE!
I guess that you have another computer since you are posting on the forums!
PLEASE PUT THE DISK IN THAT!
See if you can boot the CD and go to "Try Ubuntu Without Installing" If it doesn't boot there burn your disk again because it is corrupted!

---

### Post by Casper Ghost on 2010-06-29
> **Jakiejake said:**
> BRAIN WAVE!
I guess that you have another computer since you are posting on the forums!
PLEASE PUT THE DISK IN THAT!
See if you can boot the CD and go to "Try Ubuntu Without Installing" If it doesn't boot there burn your disk again because it is corrupted!

OK It works. I don't understand what its trying to tell me because I borrowed my buddies laptop and its a japanese computer. Ubuntu is automatically detecting it and the script is all in japanese. Sooooooo anyways... It does work. I can make out something like full install, install in a separate window... I think. I can speak it I just can't read that stuff.

---

### Post by cebudr88 on 2010-06-29
Hey Casper,
Firstly I am not trying to imply in any way, shape or form that I am well versed with Ububtu, but have installed a few laptops with Ubuntu.
Also have had the same frustrating problems - managed to solve it though by installing Ubuntu 9.10 Netbook Remix.
Just a thought - maybe it may help.
All the best - cheers
James Roa

---

### Post by robert shearer on 2010-06-29
Put the Ubuntu cd into the drive of the computer you are trying to install to.
Start up and when you see the first screen hit enter and you should see an option to "try ubuntu"
Before doing anything else hit F6 and you should see some options such as "nodmraid" "nomodeset" et al.(or try F7 if they don't show)
Put a check in the boxes for the two named above then press esc.
Hit enter and the "try Ubuntu" from the live cd should boot up.

It takes a while but will get to a live desktop and you can then try out things for a day or two and when you are happy that all your hardware works and you have done some research on simple Ubuntu install steps then install.

Post if any step above fails with any info you think may help such as error messages.

Good Luck and Happy Experiments....

---

### Post by Casper Ghost on 2010-06-29
> **robert shearer said:**
> Put the Ubuntu cd into the drive of the computer you are trying to install to.
Start up and when you see the first screen hit enter and you should see an option to "try ubuntu"
Before doing anything else hit F6 and you should see some options such as "nodmraid" "nomodeset" et al.(or try F7 if they don't show)
Put a check in the boxes for the two named above then press esc.
Hit enter and the "try Ubuntu" from the live cd should boot up.

It takes a while but will get to a live desktop and you can then try out things for a day or two and when you are happy that all your hardware works and you have done some research on simple Ubuntu install steps then install.

Post if any step above fails with any info you think may help such as error messages.

Good Luck and Happy Experiments....

Nope, I got the blinking cursor of death....

Actually the last thing I did yesterday was burn a copy of parted magic so I am gonna try and partition my drive like dino said.... 

I just hope I don't kill anything.

---

### Post by Casper Ghost on 2010-06-30
> **dino99 said:**
> what kind of installation have you done ?

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

Alright, I created the partitions using parted magic, using ext 3. 

12000 MiB for the root
2000 MiB for the swap
and the remainder for the data



I rebooted the computer with the Ubuntu live disk and tried "install ubuntu" to go to the blinking cursor of death

I tried again hitting the F6 key and checking the nodmraid and nomodeset, again blinking cursor.

I tried rebooting holding the shift key and I still have no GRUB menu...

:confused:

---

### Post by ToxicBurn on 2010-06-30
sorry to hear your troubles but what cpu do you have ( core 2 duo ect..)

---

### Post by Casper Ghost on 2010-06-30
[SIZE=2][SIZE=3]MSI N8400GS-D512 GeForce 8400 GS 512MB 64-bit DDR2 PCI Express 2.0 x16 HDCP Ready  Low Profile Ready Video Card[/SIZE]
[SIZE=3]
945P series (MS-7176) v1.x ATX mainboard[/SIZE][/SIZE]

I have a brand new 1.5 TB hard drive. I just partitioned it as stated above.

Anything I am missing?

---

### Post by Casper Ghost on 2010-06-30
Nothing?

---

### Post by Casper Ghost on 2010-06-30
OK I got it folks. I went in the F6 menu and just Xed a bunch of random items in the menu out of frustration and.... It worked?!?! 

I appreciate everyone's input!

and I didn't even have to listen to the wife :grin:

---

### Post by Casper Ghost on 2010-06-30
Ok so now that it has installed and the system has rebooted I am once again getting the blinking cursor of great frustration

The good news is that now I actually have a GRUB menu YAY.

Any ideas?

---

### Post by robert shearer on 2010-06-30
Well, if we knew what you 'x-ed' out at F6 then we would know what it was that prevented it booting in the first instance and could offer some advice.

So, how about putting in the live cd, experiment with some of the F6 options and combos and try to boot the live cd(no install). ie the 'try without changing anything' option.

Once you have the option combo that boots then post back with it.
Note, do write it down and quote it accurately cause something like 'the no mode whatsit' won't mean anything to anyone coming in on this late. ):P

---

### Post by Casper Ghost on 2010-07-01
OK I am past the blinking cursor of death. I went into the GRUB menu and hit E. From there I erased "quiet splash" and replaced it with noapic and noacpi. This has brought me into ubuntu. 

OK so now I have no internet connections. I went into the network connections under the wired tab (I have a little red exclamation point in my network connections image) Ok so I am in the tab and filled out the IPv4 tab with my address netmask gateway info... no problem.

Still no conncetion. I am plugged in via LAN by the way.

I read somewhere on here to go into the terminal and type in sudo client eth0 and I get something like this...

siocsifadder: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

So anyways when I was trying to search out what the hell that meant, someone said something about drivers.

Well this is a blank hard drive with no previous operating system so I was like "yea maybe my prob is I havn't installed any drivers" so I checked  under system/administration/hardware drivers and sure enough its an empty cubbord.

When I try to put in say my graphics driver disk I get this...

Error autorunning software
cannot find the autorun program

OK so this is just me flying blind and trying to figure this stuff out on my own. How can I download drivers without a connection? and how can I load them from a disk if it won't let me?

So I leave it once again on the alter of you experts and ubuntu gurus

---

### Post by Casper Ghost on 2010-07-01
Shameless bump

---

### Post by robert shearer on 2010-07-01
][QUOTE=Casper Ghost
So anyways when I was trying to search out what the hell that meant, someone said something about drivers.

Well this is a blank hard drive with no previous operating system so I was like "yea maybe my prob is I havn't installed any drivers" so I checked  under system/administration/hardware drivers and sure enough its an empty cubbord.[/QUOTE]

Ubuntu is not Windows, your Windows driver disc will not work and is not needed.
Those 'drivers' that are required are mostly present already. Notice how you didn't need any drivers for the board ?

The system/administration/hardware drivers option is for Hardware that doesn't have native open source software such as some Graphics cards, wireless etc.

If you have such hardware then usually the option will report that and offer to install downloadable alternatives.
Look in system/administration/hardware drivers and if it is empty then thats ok.

Now, for your connection, usually the card is automatically found and configured and all that is needed is to right click on the icon choose edit connection then on the window that opens select the card- usually something like 'Auto eth0' or 'Auto Ethernet' and it will attempt to connect.

Can you boot back up to the live cd and see if that connects, remember earlier I said that the live cd was useful for testing your hardware for compatibility before installing ?

If it can then post from the running cd and we can do some testing of your system to ascertain the network hardware etc.
If it won't connect then you will have to do some good old manual copying and typing.

Look also at the beginners section to learn more about Ubuntu..
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

and this free book has lots of useful stuff

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

