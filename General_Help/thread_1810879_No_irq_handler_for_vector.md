---
title: "No irq handler for vector"
date: 2011-07-23
forum: General Help
---

### Post by ClientAlive on 2011-07-23
Hi,

I've been working on getting an older desktop up and running (putting together the hardware).

I'm not quite sure what information might be helpful but I'll take a shot.

It's an HP Pavilion a1253w Media Center (or at least it was). The mobo and CPU are about all that's original now (unless you count the 5 in 1 card reader and media dock that has a couple extra USB ports and audio jacks - those aren't connected to the mobo now though).

~ Mobo: An old amberine board
~ RAM: 2.5 GB PC 3200 ddr sdram (2 X 1 GB + 2 X 256 MB)
~ Hard Drives: Master = WD 80 GB IDE drive; Slave = Maxtor Diamondmax 10, 100 GB IDE.
~ Optical Drives: Master = cd read/ write, IDE; Slave = DVD ROM (Philips brand)

These drives, the RAM, the two fans (CPU fan and the one on the back of the case) are currently the only things plugged into the mobo (plus the power supply to the mobo and this one other, square plug on the mobo).

In bios set up I see that all RAM sticks are recognized, CPU is recognized, and all four drives are recognized. I inserted the Ubuntu 10.04 LTS CD to see if I could run live and I get the following message, at which point the whole system hangs.

```

[     0.080001] do_IRQ: 0.111 No irq handler for vector (irq -1)

```

It also did something weird before giving that output. It began to load and I get the "ISOLINUX . . ." blah blah blah . . .  Then it went down and back up to load a second time. Again I got the "ISOLINUX . . ."; and, after a few more seconds, the output in the Code box above. Both times (beginning to load) I did see the little icon at the bottom of the screen. The one with the little stick person in it.

Does anyone know what's going on? If you need more info just let me know what you need and I'll get it for you.

Thanks.


Oh, by the way, I know for a fact that, that CD is fine. It's the one I used to install 10.04 on this machine (my laptop) that I'm typing to you now. I've also run it live before in other machines. The disc isn't scratched or dirty or anything (I checked).

Any help greatly appreciated. Been wrestling with that machine for a week.
---------------------------

Edit:

To start out I had both hard drives on one channel and both optical drives on the other. On each channel there was a master and a slave. Then I got to wondering if that was the right way to go about it. I tried going down to just one drive and setting it up so there is one hard drive on one channel and a hard drive and an optical drive on the other. Nothing I do seems to work. This second configuration doesn't really make sense because then you have two hard drives both set to master but what alse is there? I'm confused on how to set this up.

I've attached two pictures of the output I get when trying to run Ubuntu 10.04 live in that machine. The first one is from the first configurations and the second is from the second configuration.

Does anyone have any advice on the right way to set this up?

---

### Post by ClientAlive on 2011-07-24
Some added info:

The Western Digital drive is a WD800. It's jumpers have setting for whether a slave is present or whether the drive is by itself. I was careful to pay attention to this.

As far as optical drives go, I have 4 of them stacked up on the table in front of me. I don't really care which one I use as long as it does what what I need it to within the system. One of them is a DVD ROM. Two of them are CD read/ write drives. The last one is a CD drive but I'm not entirely sure it isn't just ROM.

The optical drives I have are:

Philips Model no: CDD4801/81
HP C4465-56000
Toshiba Model no: SD-M1002
Teac CD-524EA
---------------------------

Here is a link to the product specs for that machine.

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00610113&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00610113&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604)

I think I must have been a little tired when I wrote that o/p last night. I should be more specific about what is left that is original and not.

* The Orig equip that's still part of machine:

The mother board:

> Manufacturer: Asus
Motherboard Name: A8AE-LE
HP/Compaq motherboard name: AmberineM-GL6E

The 512 MB of RAM (2 X 256 MB) - but I've also added more that is not original:

> Memory Installed	512 MB (2 x 256)
Maximum allowed	4 GB* (4 x 1 GB) requires the replacement of the installed 256 MB DIMMs
*Actual available memory may be less
Speed supported	PC-3200 MB/sec
Type	184 pin, DDR SDRAM
DIMM slots	Four
Open DIMM slots	Two

The Maxtor HD:

> 100 GB
7200 rpm

It is a Maxtor Diamondmax 10

The CPU:

> Athlon 64 (V) 3400+ 2.2 GHz
1600 MT/s (mega transfers/second)
Socket 939

* Added stuff:

Western Digital 80 GB drive (WD800)
2 GB PC 3200 ddr sdram @400 MHz (2 X 1 GB)

~ It needs to have some optical drive of the ones I have
~ I have a bunch of expansion cards and one of them is a wireless NIC. At the very least I would like to have that wireless NIC in there eventually.

Right now I'm just trying to get a basic setup going. Not worrying about the card reader or media dock or expansion cards of any kind. Just thinking about hard drives and optical drives.
-------------------------

Edit:

The output shown in the code box in the o/p was before I tried 2 other configurations. The two other configs result/ output is what's shown in the pictures.

---

### Post by Swagman on 2011-07-24
Is your boot order set to boot from cdrom first as you should be able to boot into the Live cd without ANY hard drives connected.

Try it.. Switch the computer off at the wall and just pull out the *molex's to the hard drives

Boot into BIOS so it auto recognises no drives.. Save out and it'll reboot, hopefully from the cdrom

If that's successful you know you have a hard drive clash

btw. a single beep means a successful POST ( **P**ower **O**n **S**elf **T**est)




*Molex's are the power plugs to the drives. You don't need to pull the IDE leads out to disable the drive, Just the power.
When you re-insert the molex plugs they are keyed but you can still push em in the wrong way.. If you do that then the blue smoke Genie escapes

Red lead on Molex always goes facing IDE lead

---

### Post by ClientAlive on 2011-07-24
> **Swagman said:**
> Is your boot order set to boot from cdrom first as you should be able to boot into the Live cd without ANY hard drives connected.

Try it.. Switch the computer off at the wall and just pull out the *molex's to the hard drives

Boot into BIOS so it auto recognises no drives.. Save out and it'll reboot, hopefully from the cdrom

If that's successful you know you have a hard drive clash

btw. a single beep means a successful POST ( **P**ower **O**n **S**elf **T**est)




*Molex's are the power plugs to the drives. You don't need to pull the IDE leads out to disable the drive, Just the power.
When you re-insert the molex plugs they are keyed but you can still push em in the wrong way.. If you do that then the blue smoke Genie escapes

Red lead on Molex always goes facing IDE lead


Hi Swagman,

Thanks for showing up. The way I've gone about booting from disc is to enter the boot menu using the esc key. After reading your post though I wonder if I haven't created a problem by something(s) I did before in bios setup. When I was adding drives in the beginning I would plug one in, boot up, go into setup then I'd 'save and exit' each time until all drives were added. After that, some changes were made by swapping out drives or the order of drives (master/slave or what channel they were on). I wonder if saving to bios like that messed me up because now it expects a certain thing and it isn't like that any longer.

I want to be sure I understand you instructions right. This is going to sound really stupid but I'm such a newb to this I need to be sure. I don't want to keep fussing with this any more than I have to and I sure as heck don't want a visit from the blue smoke genie :o

In your instructions you go from booting into bios with the power plugs taken out from all drives "so it recognizes no drives" TO "saving out and it'll reboot." Then you say "hopefully from the cd rom." Somewhere in between those things, am I supposed to plug all the drives back in (the power to them)? (I told you this was gonna be super stupid - just that what I've seen with these things it's the little details that do seem to make a diff. Assuming anything seems to be the dumber thing than asking).

Also, somewhere in between there, is bios supposed to automatically boot from cd rom? I thought the default setting was to boot from the HD unless you tell it otherwise in setup or enter the boot menu and select the cd drive to boot from.

Thanks in advance for your help.
---------------------

Edit: 

I have another dumb question too but don't know how else I would find out if I don't ask.

I noticed the power plugs are numbered but have been wondering if it matters which one goes to which drive or what order they are in.

Thanks

---

### Post by Swagman on 2011-07-24
> Somewhere in between those things, am I supposed to plug all the drives back in (the power to them)? (I told you this was gonna be super stupid - just that what I've seen with these things it's the little details that do seem to make a diff. Assuming anything seems to be the dumber thing than asking).

No question is stupid.




No.. Don't plug the drives in yet (after doing all that)

I want to eliminate any possibility of hard drive clash.. so boot without them connected (boot from the live cd)

[Edit]

No it doesn't matter what power plugs (Except for the main Motherboard connector) go where.. If it fits and is the right way round.. It's good to go

Make sure you plug in the "square four" connector near the cpu if it has one too

---

### Post by ClientAlive on 2011-07-24
> **Swagman said:**
> No question is stupid.




No.. Don't plug the drives in yet (after doing all that)

I want to eliminate any possibility of hard drive clash.. so boot without them connected (boot from the live cd)

[Edit]

No it doesn't matter what power plugs (Except for the main Motherboard connector) go where.. If it fits and is the right way round.. It's good to go

Make sure you plug in the "square four" connector near the cpu if it has one too


:confused:

Well, how can it boot from a drive that isn't plugged in?

I wonder if we are on the same page with a certain term "drive". When I say "drive" what I mean is any drive including hard drives and optical drives.

Thanks

---

### Post by Swagman on 2011-07-24
Leave the hard drives unpowered and only connect ONE cdrom

It should boot from optical (cdrom)

I'm trying to test your hardware

---

### Post by ClientAlive on 2011-07-24
Don't want to "edit" while someone may be reading.

And what about this thing of the channels and what drives to include on what channels. I understand this is maybe a later point than what we're talking about but this has been a confusion for me.

Ideally, would want the two hard drives, the DVD ROM drive and a CD read/ write drive (that makes 4). There are 2 channels. That raises the question of whether to combine both hard drives on one channel and both optical drives on one channel or to have it with a hard drive and an optical drive on each channel.

The reason I think of this now, at this stage is that to boot from cd rom that drive is gonna have to be plugged into one or the other channels right? And it's going to have to have some jumper setting as well. Should this not be on my mind from the beginning?

---

### Post by ClientAlive on 2011-07-24
Swagman,

Brother. I'm not trying to test your patience. I get what we're trying to do here. It's me. It's that there are like 4 things in play when it comes to this stuff. Which are important at this stage (testing the hardware) and which aren't I don't know. You have: channels (two of them) you have jumpers, with 4 drives and 2 channels you have to make jumper decisions. Even if I am only plugging in the one, cd rom, drive right now, does it matter to make a decision on where to set the jumper and what channel for it to be on based on where you want it to end up in the end (when all drives are connected in the end). I don't understand if this is important right now or not. What I'm really trying to get my mind around is what I would 'physically' be doing. I think I understand clearly but I've seen this computer (and I think it safe to say all computers) be very finicky about stupid little details like this. If I think I understand but don't and I end up doing it differently in some way, the result may not be positive and then your time get's wasted and we go through all kinds of talking back and forth and end up finding out there was some stupid mistake I made because I didn't understand correctly to begin with. It isn't the result or what we're trying to do that I'm questioning, it's the 'precise' way to achieve that result.

What I think you mean, what I think needs to happen (If I'm understanding correctly) is this:

> 1 unplug ALL drives (hard drives and disc drives) from the power plug but not the ide, flat, cable.
> 2 power up the machine and enter bios setup
> 3 check to see that there are no drives being recognized; and, if so, "save and exit"
> 4 power off the machine
> 5 plug the power plug only into the cd rom drive and no other drives
> 6 power up the machine

Problem: at this point there will be no cd in the drive. Either I will need to have inserted the cd at some point before beginning all the above or I will need to hit the pause button (something that, for all I know, interrupts what we're trying to do somehow).

Assumption: I have to 'assume' that, that cd rom drive should be jumpered as master??? or that it just doesn't matter - but I don't know. I wouldn't know unless I read it somewhere or someone told me. Not sure how much computer's get along with assumptions so that's why feel concerned that I understand these things.

I have to assume that it doesn't matter what channel that cd rom drive is on. After all the plugs on the mobo are colored differently and intuition would say that any difference is supposed to mean there is a difference. I wouldn't know though.

This is the newbie experience. In a way, we are like a computer. If the knowledge isn't there, since we are humans and not computers, we can make and assumption rather than just and error output. The computer won't do that though. It'll take my assumption; at best, give me an error output, at worst, wreck a drive or two.

Please Swagman, please understand me. This would be easy for you because you've already dealt with these petty little questions and know the answers. I only need to learn them once, then I'll remember forever.

I'm going forward with:

Insert the cd first, then power off, then the steps I listed out above. I hope that's right and doesn't make needless effort or confusion.

---

### Post by ClientAlive on 2011-07-24
Ok,

I was just really confused about the sequence of events that were supposed to happen. I stood there staring at the thing for a couple minutes just thinking trying to figure out what is important and what isn't for achieving the right outcome. Whether something I do would interrupt getting that outcome. Don't know if I did it right or not but what I did was:

I left the drives jumpered as they would be in the end. As it was set up it was that the WD hard drive and the cd rom are on one channel with the hd as master and the cd rom as slave. The other, maxtor drive, is on the other channel by itself as master. That maxtor drive is using a different cable that only has two plugs (one for the mobo and one at the other end for the drive).

I unplugged all drives from the power supply. Fired up the machine and went into setup with F1. I saw that there were "no drives recognized". I saved and exited. I powered down and plugged in only the cd rom drive (I chose the Philps brand drive out of the 4 I have). I powered on, hit pause, put the cd in the drive, and hit the space bar to resume. It began to boot the live cd. It gave me the line talking about "ISOLINUX . . ."; and, for a minute, I saw the little person icon at the bottom of the screen. Then it gave me the ". . . No irq handler for vector . . ." thing. That's where I'm at at this moment. I haven't touched anything. The computer is still powered on and is at that ". . . No irq . . ." screen just sitting like that.

Pictures attached.

---

### Post by ClientAlive on 2011-07-24
awe fk it!

I'm not trying to be difficult. I'm confused.

---

### Post by egalvan on 2011-07-24
Patience is a virtue when working with computers.  :P

Now, lets clear some air concerning your concerns about which drive to plug into which cable..

with modern drives, this is really a function of ease-of-connection...
in general, hard drives are mounted close to each other,
 and opticals are also mounted close together.
so typically one connects both hd's to one cable (as a rule, use the primary channel)
 and both opticals are connected to the second cable (this will be the secondary channel)

(with older drives, master/slave relationships and transfer speeds were a different matter...
 but except for that CD-ROM optical, I don't think your drives are that old)

On the cable side of things, if you look at the IDE cables, they should have three connectors...
one at each end, and a third in the middle (closer to one of the ends, actually).
the end with the two connectors closer together is the drive end,
the other is the mobo end.
(sometimes they have printing on the cable, or the connector, or their is a tag, to indicate there function.
 and sometimes they are color-coded.)

on the mobo, there are two IDE connectors... sometimes color-coded, sometimes not... 
but there SHOULD be printing on the board next to each connector...


eye-balling a few older mobos here in my shop, i see the following
variations in names...

IDE-0 IDE-1
channel0 channel1
PRI_IDE0 SEC_IDE1

they all mean the same thing.. and they are all colored **BLUE** for channel 0 (primary) and **BLACK** for channel 1 (secondary)

YOUR MILEAGE MAY VARY... 

In your case, I am guessing you want the 80g drive for the OS, and the 100g drive for data/storage, right?
if so, then jumper the 80g to be MASTER, and jumper the 100g to be SLAVE.

same for the opticals, although you may want to make the DVD the MASTER and the CD the slave.

questions?

(N.B. there are **NO** stupid questions
we were **ALL** born ignorant.
i started computers back in Nineteen Sixty and Nine
with IBM Big Irons... :guitar:

We'll see how well we can get that machine of yours running...
(and i know a thing or two about old machines :P )

---

### Post by Swagman on 2011-07-24
Sorry.. Been away.. Missus is decorating the room and I get collared now and then to do "Man stuff"

I also got ordered to dip into Fat wallet and go buy us all a KFC (KFC is the other side of town, so I had to drive there as they don't do home delivery here in UK)

So my wallets not so fat anymore

:( 

Now.. back to you...

irq means interrupt requester and as you are running a board with bare minimals this should not be an issue.

What board is it ?

---

### Post by ClientAlive on 2011-07-24
> **egalvan said:**
> Patience is a virtue when working with computers.  :P

Now, lets clear some air concerning your concerns about which drive to plug into which cable..

with modern drives, this is really a function of ease-of-connection...
in general, hard drives are mounted close to each other,
 and opticals are also mounted close together.
so typically one connects both hd's to one cable (as a rule, use the primary channel)
 and both opticals are connected to the second cable (this will be the secondary channel)

(with older drives, master/slave relationships and transfer speeds were a different matter...
 but except for that CD-ROM optical, I don't think your drives are that old)

On the cable side of things, if you look at the IDE cables, they should have three connectors...
one at each end, and a third in the middle (closer to one of the ends, actually).
the end with the two connectors closer together is the drive end,
the other is the mobo end.
(sometimes they have printing on the cable, or the connector, or their is a tag, to indicate there function.
 and sometimes they are color-coded.)

on the mobo, there are two IDE connectors... sometimes color-coded, sometimes not... 
but there SHOULD be printing on the board next to each connector...


eye-balling a few older mobos here in my shop, i see the following
variations in names...

IDE-0 IDE-1
channel0 channel1
PRI_IDE0 SEC_IDE1

they all mean the same thing.. and they are all colored **BLUE** for channel 0 (primary) and **BLACK** for channel 1 (secondary)

YOUR MILEAGE MAY VARY... 

In your case, I am guessing you want the 80g drive for the OS, and the 100g drive for data/storage, right?
if so, then jumper the 80g to be MASTER, and jumper the 100g to be SLAVE.

same for the opticals, although you may want to make the DVD the MASTER and the CD the slave.

questions?

(N.B. there are **NO** stupid questions
we were **ALL** born ignorant.
i started computers back in Nineteen Sixty and Nine
with IBM Big Irons... :guitar:

We'll see how well we can get that machine of yours running...
(and i know a thing or two about old machines :P )

<sigh>

Ok.

Sorry for my little tantrum there. :P  It's frustrating.

Yes, I wanted the 80 to have the o/s (actually, it won't be a standard install but that's another story). So yeah, the 80 GB for boot and the 100 GB for storage.

And thank you for clearing those things up for me. I was doing some googling on it before but hadn't gotten the right info yet. I also googled a few things just now to try and understand this output I'm seeing on my computer right now:

```
[     .0884001] do_IRQ: 0.111 No irq handler for vector (irq -1)
```

These are the tabs I have open:

[http://en.wikipedia.org/wiki/Interrupt_handler](http://en.wikipedia.org/wiki/Interrupt_handler)
[http://en.wikipedia.org/wiki/Interrupt_vector](http://en.wikipedia.org/wiki/Interrupt_vector)
[http://en.wikipedia.org/wiki/Mutual_exclusion](http://en.wikipedia.org/wiki/Mutual_exclusion)
[http://www.webopedia.com/TERM/I/IRQ.html](http://www.webopedia.com/TERM/I/IRQ.html)
[http://www.webopedia.com/TERM/D/DIP_switch.html](http://www.webopedia.com/TERM/D/DIP_switch.html)

Trying to figure out where to go from here.

Ultimately, my guess is that Ubuntu 10.04 does not have a driver for that optical drive. Except that I have some problem or other no matter which of those drives I try. Total guessing here though. No idea what's really up.

As a side note, I think I should set up the drives like you describe (hard drives on one channel, disc drives on another). That's how I set it up to begin with because that's what made sense to me. When I started having problems I started trying different ways to set it up. I didn't know, still don't know, what the source of the problem is.

Regarding setting the drives up on their own channels like that, I've run into yet another thing I'm unsure of. Here's what that is . . .

I have two pairs of cables. One pair are the ones that came out of the machine/ came with it when I bought it used. The other pair are from a different machine.

2 things:

I noticed that the plugs on one pair are different than the plugs on the other (the pair that came from the other machine). The pair that came with the machine has one less pin about in the middle of the plug. This corresponds with the pins in the socket on the mobo. The other pair (the ones that came from the other machine) have the additional pin.

Here's what ties that together. The pair that has one less pin - one of those cables is not the type with 3 plugs on it. It is the type with only 2 plugs on it. If I want to end up with a grand total of 4 drives I would have to use a different cable in place of that one with only 2 plugs on it.

From some of what I've read, I believe this difference of one pin has to do with whether my mobo supports cable select or not. Still guessing though. If that is the correct assumption, I'm not sure which way it goes. In other words - extra pin = cable select ability or vice versa??

Regardless of cable select functionality or not, I had chosen to go with setting the jumpers like one would do in the old days anyhow. This seems like having more control and I had read you can still do that even if your equipment does support cable select. That it isn't a problem and you can do it that way if you want to.

So, with the cables thing, in the end I'm not sure if using those other cables with the extra hole for a pin is ok or not. I do have a whole box full of all kinds of cables (not just those flat type) that I inherited but I don't know their condition. I do know the condition of that pair from the other machine (the ones with the extra hole). Those came out of a working machine. The difference is having a second cable with 3 plugs on it or a second cable with 2 plugs on it. The difference of 4 drives total or 3 drives total.

Well, I have some ideas that I would normally just go over there and try but I think it best I wait for a response before I do anything more. I hope just leaving that machine sitting there like it is (powered on and the output tells the state) is not going to hurt anything.

---

### Post by egalvan on 2011-07-24
quick reply because i have a date to get to...

regarding the optical drive... linux has drivers for it...
unless its a **REALLY** old pre-ata type...

if  you want four drives attached, you need sufficient connectors...

it seems your machine may have more than two channels.. 
check the mobo to see how many IDE connectors there are.
and check if it has a SATA connector.

as for the missing pin, its not really a problem...
and i would not use Cable Select on your machine,
 I would use hard-wired MASTER/SLAVE options via the jumpers on the drives.

i'll be back in a few hours...
and no, it won't hurt the machine to just sit there,
unless it's dirty and prone to overheat...

---

### Post by ClientAlive on 2011-07-24
> **Swagman said:**
> Sorry.. Been away.. Missus is decorating the room and I get collared now and then to do "Man stuff"

I also got ordered to dip into Fat wallet and go buy us all a KFC (KFC is the other side of town, so I had to drive there as they don't do home delivery here in UK)

So my wallets not so fat anymore

:( 

Now.. back to you...

irq means interrupt requester and as you are running a board with bare minimals this should not be an issue.

What board is it ?


ok. Sorry for my little fit there. :(  I've been fussing with this thing for over a week and the orig goal wasn't messing with hardware. What can you do though?

Thanks for understanding my frustrations.

Here are the exact specs of that board:

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604)

---

### Post by ClientAlive on 2011-07-24
Talking about KFC made me hungry. I got some curry beef stew on a bed of rice that the Somalian lady down the hall makes. It's awesome!
-------------------

Edit:

I found this link. The guy is talking about installing Macintosh and his system is a diff model but he has the same board with the same chipset. One person in post #44 calls it an "obscure chipset".

FWIW, this system has never worked with Linux. Just a little while after I bought it, around the time I switched to Linux, I first tried to install Linux on that machine (I'm on my laptop typing to you now). I went through 3 different distros and a few releases of one of them. The system would get somewhere into the install and then hang or I would get all kinds of output and it would hang there.

Based on some input from someone else I came to believe the mobo was bad or burnt out. (Although it had been running Windows XP prior to that and doing fine with it). This was all around 4 or so mos ago. At that time I took it apart partially, with the intention of finding another, good mobo to replace this one with. It sat in a box all this time - up to about 2 weeks ago or so.

Recently I had got to thinking that maybe the input I had gotten was either incorrect or incomplete. I pulled the box back out and went to work trying to get the thing up and running. Since bringing it back out successfully run several distros live on that machine (before right now). I've run Ubuntu 10.04, Xubuntu and Knoppix on it successfully (not installed but live).

Now, here we are at this point. Along the way there have been hardware additions and changes which bring us to the current setup. Maybe, just maybe, the issue I was having with installing those 4 mos ago, and the issues I'm having now, are somehow related. Maybe, if I'm real lucky, we get those issues worked out somehow and my troubles with that machine are over.

I can only hope.

---

### Post by Swagman on 2011-07-24
Ok .. Lets start at the beginning.

The board you linked to looks ok to me. I ran an Msi socket 939 for years.

So.. Clear CMOS (BIOS) following the destructions on your board link.

Lets make it bog standard.

Just for now...

Use.. ONE stick of RAM

ONE Optical drive

ONE hard drive

---

### Post by ClientAlive on 2011-07-24
> **Swagman said:**
> Ok .. Lets start at the beginning.

The board you linked to looks ok to me. I ran an Msi socket 939 for years.

So.. Clear CMOS (BIOS) following the destructions on your board link.

Lets make it bog standard.

Just for now...

Use.. ONE stick of RAM

ONE Optical drive

ONE hard drive


Ok.

Gotcha. I'd done that before so I know how.

Just a min. Lemme do that.
----------------------------

If it matters let me know. Otherwise I figure.

Both drives on primary channel

Hard Drive = Master
CD ROM = Slave

---

### Post by Swagman on 2011-07-24
That'll do for now (process of elimination)

Ideally I'd have put hard drive on blue (Primary)

Cdrom on other connector on motherboard

That way if this works we can add the other hard drive on primary as slave

---

### Post by ClientAlive on 2011-07-24
Ok.

I cleared both jumpers, moving the jumper over and then back for one and then doing the same for the other after that. I counted off the 6 seconds very slowly so it was over 6 sec.

I put both drives on the primary channel. I used the WD hard drive which has 3 jumper setting (master with slave, master by itself, and slave). I chose the first thing, master with slave. 1 stick 256 MB RAM. One optical drive.

Picture shows bios setup.

Should I set up the date and time or does it matter for now?

Hang on. Why does it show the current date and time? Did it not clear as it should have? Look at the RTC too. That doesn't look right for a cmos that's supposed to be cleared. I did exactly according to instructions though.

---

### Post by ClientAlive on 2011-07-24
> **Swagman said:**
> That'll do for now (process of elimination)

Ideally I'd have put hard drive on blue (Primary)

Cdrom on other connector on motherboard

That way if this works we can add the other hard drive on primary as slave

Perhaps I ought to start over from the beginning, make sure cmos clears this time, and set it up one for each channel as you say?

---

### Post by ClientAlive on 2011-07-24
Set it up just as you said. One drive per channel. Hard drive on primary channel and set to master alone. CD ROM on other channel and set to master.

Before that I moved the jumper again (with power cord unplugged as per instruction) and went out for a smoke. About 5 min passed before I came back in, moved the jumper back over, and set up the drives as described.

Notice what the RTC and date reads in the attached picture. Sorry it's a little blurry.

---

### Post by ClientAlive on 2011-07-24
I'm tempted to just throw the towel in on this whole thing. This is ludicrous.

I get the thing set up (as described last), cmos apparently won't clear, but I move forward. I put Ubuntu 10.04 CD in with just the 256 MB of RAM and it starts to load. It gets to a point and I get a black screen with just the pointer and the pointer won't move (prob because 256 MB isn't enough to load the gui, I guess).

So I put the other 256 stick in and try again, all along it's recognizing everything in bios. Ubuntu starts to load sits there with the Ubuntu logo w/ the status indicator forever, then the Ubuntu logo w/ the status indicator somehow moves over from the center of the screen to the far left and there's a white line across the bottom of the screen. Everything freezes.

Now I take both 256 sticks out and I replace them with the two 1 GB sticks I have. I try again. Ubuntu starts to load, I see a line of output talking about "missing parameter" something and then I get a different looking screen than I've seen before. This one is a text menu with the selections to try Ubuntu or Install it and a couple other options. I let it time out on the selection for Try Ubuntu and it starts to load. Then I get what's in the attached pic.

---

### Post by egalvan on 2011-07-24
to completely clear the cmos, un-plug from the mains,
then remove the cmos battery... it's the quarter-sized thingy near the cmos chip

while you are at it, COMPLETELY disconnect all drives... remove them if easy to do so.
if this was my machine, i would remove EVERYthing not needed to boot the machine,,,
you need cpu, ram and video... NOTHING ELSE.
what you need to do is reduce the machine to its BASIC configuration, 
the less installed, the less to go wrong.

install at least 512M ram (but not less than 256m)

wait AT LEAST 15 minutes after you removed the battery,
preferably 30 minutes.


while waiting, you can
download tinyme, a *very* small distro.
[http://tinymelinux.com/doku.php/home](http://tinymelinux.com/doku.php/home)

or PartedMagic, a slightly larger distro (*very* useful for hard drive partitioning and stuff.)
[http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start)

after the wait time,,, re-install the battery...
btw, unless YOU KNOW FOR SURE that the battery is good, you should replace it... its a standard 2032 button cell.

re-connect the mains...
boot.
the machine should start up, and the bios should natter about needing configuring... some do, some don't.

go into bios and set the time and date.

re-boot... (power-down optional, not really needed)

the machine should complain about "no operating system found"
or "no boot drive found"

power down, dis-connect the mains...

grab the newest optical you have (they should all have a manufacturing date on them)

set it for MASTER

connect it to the mobo, using the outer-most connectors on the cable.

re-connect mains.

boot.

if it nattered before about no op-sys or no boot drive, it must do  so again.

go to bios to VERIFY that the optical is found, and on 
device 0 of the first channel. VERIFY THIS.

if all copacetic up to this point, open the optical drive,
insert tinyme or PartedMagic and re-boot.

IF THIS DOES NOT WORK, you have other problems...
I would try each RAM, one by one.
then each cable, one by one.
then each optical, one by one.

N.B. modern mobos will keep 5v on the bus when powered down...
this can kill stuff that is plugged/un-plugged...
MAKE SURE you pull the mains between each test above. EVERY TIME.
use a power strip with switch,
 its what I do...makes it easy to dis-connect mains.

---

### Post by egalvan on 2011-07-24
> **ClientAlive said:**
> I'm tempted to just throw the towel in on this whole thing. This is ludicrous.

In the end, only you can decide what amount of time is "ludicrous".

I've resurrected many an old machine...
and I've got to say, it feels good when Linux boots and runs like a top on those "old, obsolete" machines that Microsoft scoffs at :P

Most of my machines are Windows XP era, some go back to Vista.
I have two that harken to the 98SE era.
some were fished out of trash cans, some given to me (while the owner snickered about "finally getting rid of that old dinosaur").
some cost bucks, but the most expensive i've got I spent $100 on.

You WILL learn about hardware and software.
you MAY feel satisfaction at the results.
only you can decide.

but you will find some of us willing to share our knowledge and experiences...

---

### Post by egalvan on 2011-07-24
BTW, that last screen shot show a kernel panic.

I would try like crazy to run a memory tester to check that RAM.

PartedMagic has a memory test option on the boot menu.

The Ubuntu LiveCD should have a memory test option on the boot menu.

or using a dependable computer, download the memtest+ iso, burn it, CHECK IT,
 then boot the oldster and run the memtest overnight.

[http://www.memtest.org/](http://www.memtest.org/)

---

### Post by egalvan on 2011-07-24
> **ClientAlive said:**
> 

 This one is a text menu with the selections to try Ubuntu or Install it and a **couple other options**. 

What are the "couple other options" ?

is one "check media"  ?
is one "check memory" ?

I would run the "check media" first.
if ok,
then run the "check memory" overnight.

---

### Post by ClientAlive on 2011-07-25
Right on. I guess I don't really mean it (about throwing in the towel). I just get fed up and I have very little patience. I should, I know. It does feel good. I know because I couldn't even get post, let alone bios a couple days ago. I just worry about things not working out with this thing. Sad to say but It's the only hope I've got right now.

I've got to hit the sack and stuff to do in the morning but I'll try to do some work on it tomorrow eve.

Thanks again for the encouragement and for sharing your knowledge.

---

### Post by Swagman on 2011-07-25
WAKEY WAKEY

/Bangs dustbin lids together.

How are things progressing ?

---

### Post by ClientAlive on 2011-07-25
> **Swagman said:**
> WAKEY WAKEY

/Bangs dustbin lids together.

How are things progressing ?

:D


I rode my bike to get places I needed to go today and it ended up being 22 miles I rode (I just looked it up on mapquest). A marathon is 26 miles. I guess I almost rode a marathon today. I started out around 11 am this morning and didn't get home until just after 4 pm (but I had a couple stops along the way).

I downloaded Parted Magic 6.3 and burned it to disc. I wanted to check memory with it. I wanted to check the memory I got from ebay recently so I just had those 2 sticks in there (2 X 1 GB). I removed the hard drive and it's cable leaving only the disc drive (CD read/write drive) on the secondary channel and set as master, of course.

I made sure I had the newest disc drive (manufactured in 2000). I went into setup to see that the drive is recognized, it was. While in setup I inserted the Parted Magic CD into the drive and pressed esc to exit setup and resume boot. I let it boot and the menu for Parted Magic came up. First, I selected the first option in the menu (to run from ram - the default). It started to load then spit out a bunch of gobeldy gook I don't understand and at the bottom there were about half a dozen lines all saying the same thing. Something about "bad swap" file (unfortunately I didn't get a picture of that screen).

Next I power cycled the machine and let it boot again with the disc still in the drive. This time I selected the second option in the Parted Magic menu - the option to run live. Again, it began to load, spit out a bunch of junk, and is hanging on that screen. I did get a picture of that screen and it is attached.

There is one line from that output that stood out to me as possibly being useful. It is about in the middle of the screen. It says:

```
. . . error_code+0x67/0x6c
```

Don't kill me guys. I didn't clear the cmos before doing all this. I'm concerned about that button battery being bad and I don't have any way to get another right now. I thought if I remove it, it might kill the thing. I want to do that but I want to look into this "error code" first to see if it just tells me what the problem is.

Also, for what it's worth, I had successfully cleared cmos just not that long ago. That's why the rtc is such a small figure.

Do you guys know what its complaining about with either the "bad swap" thing or the ". . . error_code . . ." thing or both??

I'm gonna google that error code right now and see what I come up with. I just keep having the same thought pop into my mind. 'I fried something on the mobo.' I sure hope not. Not that PC 3200 ddr sdram is that great but it's still better than ddr which runs at anly 100 mhz rather than 400. Not only that but those other mother boards I have also don't support very much RAM total. This mobo supports up to 4 GB and of better RAM.

Anyhoo . . .  I'll let you know what I find out from googling. Please let me know if there's anything you know about it.

Thanks
--------------------

Edit:

First pic was too blurry to see. I got another one and exchanged for it.

---

### Post by ClientAlive on 2011-07-27
Well I managed to get Parted Magic to run and to get Xubuntu to run (both live). I was suspecting that memory I bought off ebay so this was all with just the 512 of original memory installed and the optical drive - that's it.

I wanted to be more certain so I powered down, added that other memory, and tried to run Xubuntu live again (it had just been running with the 512 only). Booted back up and sure enough, no go.

I remembered being told that Xubuntu has a memory test so I power cycled; and, when it booted back into the Xubuntu menu, chose that memory test (with all the RAM in the machine, including the ebay Ram). The test ran ok for a minute, then it must have gotten around to those other dimms and started spitting out errors by the thousands.

What I don't understand though is that I had tried to run several live cds with only the 512 MB RAM before this (like in the last couple days) and it didn't work then. Now it works. These are the kind of symptoms you hear about when the mobo is bad. Things acting strangely and working intermittently.

When I had Parted Magic running earlier I saw something in there that looked to test the mobo and I ran it. I don't recall the exact name now, maybe something like 'system stability', but it came back fine. From what I saw of it though it looked like all it does is give basic information about the mobo (like the name). That might be a file somewhere on a chip on the mobo though and has nothing to do with any actual test being run on it. I'm not really sure. I do wish there is something I can run that actually tests the mobo and does so thoroughly.

I have an appointment coming up soon here but I hope to get back to that computer this evening some time. Best case scenario? That ebay memory is bad and that's all the problem is. Even if that is the case though I'm still back to square one - with only 512 MB RAM and dreaming of a project where that simply isn't going to cut it.

Ahh well, what can one do?

I've attached a pic of that output from that memory test. I was trying to look at that information in the top half of the screen on the left. It seemed to identify the type of RAM that is and I was hoping it tells me exactly what type that ebay RAM is - some details on it. I have a hunch they sent me the wrong type of RAM. To the best of my knowledge this mobo only supports a single type or RAM. There's information about people getting the wrong kind, thinking it's gonna work, and it doesn't. Then they're standing there scratching their head wondering what's going on. The mobo supports ddr sdram pc 3200 @ 400 MHz, 185 pin. If I recall correctly, it does not support ddr2 @ 800 MHz. People think it will because that's what is common with everything else but it doesn't.

Anyhooo . . .  I'm done with my little rant. I could be wrong about all that. I'm just going off memory from reading I'd done on it before. If there is detailed info on that memory in that memory test output, and it's the wrong kind of RAM, maybe I have some ground to stand on trying to get my $ back. Otherwise they're probably going to just tell me it's my problem and that I did something to it after I got it.
------------------------------

Oh, I think I forgot to mention - earlier, I was also able to get Ultimate Boot CD running (with only the 512 in the machine) and it has a memtest 86 v. 4.20 in it. I ran that and it the 512 passed with flying colors. I let it run for over 4 hrs while I went out an ran errands - no problems at all. (So I know that 512 is good, even if the mobo isn't and is just happen to work right then).

---

### Post by waveOSBeta on 2011-07-28
So, this is solved, then?

---

### Post by ClientAlive on 2011-07-29
> **waveOSBeta said:**
> So, this is solved, then?


Oh. Well, what was happening is there are so many things I don't understand. As of this point I've started a total of 3 threads to do with this resurrection  :p  in general. I was learning what was going on as I encountered it and as you guys gave me information. I was also, and more importantly, learning what is important to focus on in order to make progress with this.

I had found a way to test the RAM sticks; and, tonight, I have run a number of tests. Currently it appears that one of those 1 GB sticks is bad and the other is good (or something else I wonder about). The computer currently has 1 X 1 GB + 2 X 256 MB for 1.5 GB total and passes the memory test as well as runs Xubuntu live (including the **good** 1 GB stick). There are oddities though that I can't explain and it makes me wonder if there is not still some solution to getting that other GB in there and working. So I'm ahead, RAM wise, but still a huge chunk of the total behind. I paid for 2 GB.

I apologize if starting a different thread was the wrong thing to do. It seemed the topic truly was different even if the project and the ultimate goal was the same. If it interests anyone, here's a link to that other thread - it brings you up to speed to the current time. I just didn't think it was good to run all over the place in one thread as I learned more and made progress - things I was having to do to get where I am did change.

Thanks a whole bunch for all your help. Maybe I'll see you over there.  :D

[http://ubuntuforums.org/showthread.php?t=1813583](http://ubuntuforums.org/showthread.php?t=1813583)

---

