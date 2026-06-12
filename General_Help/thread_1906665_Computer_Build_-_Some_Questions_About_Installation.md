---
title: "Computer Build - Some Questions About Installation"
date: 2012-01-09
forum: General Help
---

### Post by ClientAlive on 2012-01-09
Hi,

Very soon (as soon as everything arrives through shipping) I'll be putting a desktop together. I had a few questions about certain installation issues. I was hoping I could list them and see if anyone can help.

1) With sata devices you don't have jumpers to worry about? Is that true?

2) If you have a mother board with 6 sata connectors but only 3 sata 6 devices to attach to it - is there some order of the connectors on the board? Is there like a connector 1, 2, 3... etc? And, if so, should you connect your devices in order starting at the first one?

3) If #2 above is right - how do you know which connector is which on the board?

4) If you have 3 sata 6 hard drives and one sata dvd/cd multi drive - is the multi drive sata 3 probably? Should you then connect it to a sata 3 connector and the hard drives to the sata 6 connectors? It's a stupid question, I know, but I have to ask. I'm not sure my optical drive is necessarily sata 6 and want to be sure of the right type of connection to attach it to.

5) Are sata 6 and sata 3 connectors shaped different - to where you can't accidentally connect a sata 3 device to a sata 6 connection? Or are they the same physically and you have to identify which connector to plug which devices into?

6) Is there a possiblity to connect any of the plugs either direction and if you don't put it in the right direction you get a visit from the smoke genie? (I know molex is like that and you can burn something out easy if you screw up - but what about sata?)

7) I know that the connction on memory sticks (on the stick itself) has a notch but it doesn't look like its dead center. I assume there is a "right way up" or a "right direction" to insert them. How do you know what that right direction is? I don't want to be trying to force anything in the wrong way.

8) How do you know what the right direction is for inserting the cpu? I noticed there is a small triangle on one corner of the cpu and one on the socket on the board - is that what you go by? Fine little pins on that cpu, wouldn't want to bend them  :P

9) How do you identify which is the pci x16 slot on the board as opposed to a lesser pci? (Bad terminology, I know). How do you know which pci slot to plug your graphics card into so you get the max performance it's capable of?

10) Is there a typical practice regarding cables being included with devices and/ or the mobo? The monitors? Is there anything in particular I can "expect" regarding this?


Any advice would surely be appreciated. I'm hoping this first build comes off smoothly.

Thanks
Jake

---

### Post by Basher101 on 2012-01-09
okay, first off there is no Sata 6. There is only Sata, Sata 2 (3 GB/s) and Sata 3 (6 GB/s).

I made my first build so hardware wise i can give you alot of details...
you cannot get the cables wrong for the Sata ports, neither on the motherbord nor on the devices themselves (it wont fit if you plug it in wrong, so do not worry about that).

it does not matter at all where you plug your Sata devices. The only important thing is speed - but you will only ever reach the full potential of a Sata 3 port with a SSD. HDDs have too slow read/write speeds.

Otherwise all ports are exactly the same, be it Sata 2 or 3.
Your Ram sticks have a small notch, but it is not exactly on the center, it is offset by a few millimeters, so you will only be able to insert them "the right way".

Knowing where your PCI 16x slot is is very easy. They have a small snatch attached to hold your graphics card and they are always differently colored than the rest of the PCI slots. I included an editied photo of my board, but all boards should have the same PCI slots (number of slots can differ).

You will need some cable management, this is not easy and i had to fiddle around with it most of my time building my PC. It took me a total of 4 Hours to assembly my PC, 1 hour for screwing all the hardware together and 3 for cable management. (i may include a photo of the interior later..)

---

### Post by ClientAlive on 2012-01-09
> **Basher101 said:**
> [deleted until further notice]


You deleted me Basher?  :p

---

### Post by Basher101 on 2012-01-09
> **ClientAlive said:**
> You deleted me Basher?  :p

post edited. this should answer all your questions. feel free to ask me anything else


regards

---

### Post by imachavel on 2012-01-09
Ok I'm going to do you a favor. Instead of telling you exactly how to build the machine, I'm going to tell you exactly how to figure out how to build the machine. Building a pc is a visual concept, so really, it's good to know how to do it from experience. Seems you are still used to IDE drives and jumpers, but main boards require jumpers on pin sets anyway. I don't want to give you the idea that going to a forum will answer every single question, it won't, it will give you a good reference to use however. But some things must be learned the hard way

Here is basically what you need with a pc

>a tower(atx form factor sounds about right)
>a main board(atx form factor sounds about right)
>Now you need a psu, there are two different atx form factors, and I don't have them memorized, but one has a 16 pin connector and the other one has a 20 pin connector. You need to get the one that matches the compatible power controller on your main board.
>YOu need as you said a hard drive, you want a sata hard drive, to fit into an sata slot on the main board, that is very good, all those slots are good to go, but if you want dual boot, raid etc. you are going to have to configure which one is slave or master in the bios. Now if the bios chooses automatically, just remember which hd does where when you chose which one to installl the OS to.
>you need an OS disk, linux is a good OS huh? You got that .iso compressed file or other compressed image installation operating system burnt to an image on a cd or dvd rom? 
>You will need a processor, and your main board will have a socket number, which the processor will fit into. Get a processor that is compatible with your main board socket.
>YOu will need a heat sink, usually the back plate is screwed into the back of the main board. Don't forget also to screw the mainboard to the case with mounting screws.
>YOu need compatible ram, e.g. ddr2 pc5300, ddr3. Whatever the case. Are you getting a main board with a 64 bit bus or a 32 bit bus? A 32 bit OS apparently can't address any more then 3 gigs of ram.
>YOu will need connector cables, and the psu will have seperate cables from each 'rail' that will match up to the main board. It should be easy enough, but don't forget there are usb port in the front that also need to connect to the main board, and the psu rail cable that goes from the power supply to the motherboard expansion slots needs to connect to a 4 pin connector. At least it used to. Now I'm not sure it might be a larger connector. There is going to be a 4 pin slot connector from the psu to the processor controller socket on the main board. The heat sink can sometimes be a bitch to install. And sata cables to connect cd rom and hard drive to motherboard, unless you are getting IDE motherboard.

Did I miss anything? Yes I did:

your audio, video, and network interface adapter in and out ports on the back of your pc. They are usually onboard soldered to the motherboard, if anything isn't onboard when you buy the mobo you are going to need to install whatever it is into an expansion slot, e.g. agp, pci, pcie, pcie 2.0. Get a good processor, consider over clocking it. I wouldn't know how that works with linux btw, with windows there is over clocking and core temperature sensor monitoring software, as the bios lock needs to be over ridden to over clock the processor and to allow more voltage into the processor. Well I hope I didn't miss anything, show your build. And don't forget intel processors usually have a higher l2 cache then amd processors, but both are good quality, however most motherboards these days use a socket that will only allow on processor version(e.g. am3 is amd)

---

### Post by imachavel on 2012-01-09
very nice. yes sata 3 won't reach top interface speed mbps if using hdd, but isn't there a data loss risk from using ssd? Ssd is flash memory right? So it's about as safe as a usb thumb drive. I don't know I shouldn't talk out of my *** hdd's also can lose files if the OS is instantly killed without allowing data to cache out.

---

### Post by Basher101 on 2012-01-09
@ imachavel he already has a thread for all the parts he wants for his PC. Now he is asking some more practical questions about how he is going to proceed once he has them.

---

### Post by imachavel on 2012-01-09
oh where is that other thread? hey nice build i5 solid dependable processor.

---

### Post by ClientAlive on 2012-01-09
yes, sata II and sata III is what I meant. I got the 3.0 Mb/s and 6.0 Mb/s mixed up with that when I wrote it.

@basher - I see what you're talking about with the pci slot. It almost looks like the little clip on either end of the slot for memory sticks. I'm sure I'll see it better when I have the board in my hands tho. Also, I hadn't noticed it before but I see that there is a smooth part on the face of the slot for memory that shows where the notch goes. If you look really close you can see which end it is closer to and I should be able to tell before sticking the dimm in.

What about the cpu alignment. You know, the first time I ever inserted a cpu was with that older machine I fixed up. I didn't know how to align the cpu and bent the pins. I spent most of the next day straighening them out. It was greivous but that was just an old cpu that I didn't even pay anything for. If that happened to this brand new chip I'd jump out the second story window or something.  :P

In case anyone else wonders what the build consists of I'll paste the link to the other post. I thought I should start a different one about these questions because that one is in community cafe and you aren't supposed to ask technical questions there.

Post #37 modifies 4 items from post #33 so if you replace those with the updated choices from #37 you'll have the final list I ordered.

Also note: 3 x on hard drives, 2 x on memory, 2 x on monitor.

---

### Post by Basher101 on 2012-01-09
well i dunno what socket you will get, but in general CPUs have small notches that you CANNOT get wrong when inserting...it wont fit otherwise

---

### Post by ClientAlive on 2012-01-09
> **Basher101 said:**
> well i dunno what socket you will get, but in general CPUs have small notches that you CANNOT get wrong when inserting...it wont fit otherwise


Ok. Right on. I didn't know that. I'd seen the little triangle in the corner (seen in the lower left hand corner of that pic) but wasn't sure that's a very good indicator.

---

### Post by Basher101 on 2012-01-09
> **ClientAlive said:**
> Ok. Right on. I didn't know that. I'd seen the little triangle in the corner (seen in the lower left hand corner of that pic) but wasn't sure that's a very good indicator.

well take the triangle and the notches and you wont mess up..

p.s. dont forget to apply thermal paste on the cpu before mounting the cooler (it was hella hard to hold a giant 1 kg coolergrill still enough to place it perfectly :< still managed tho^^) but i doubt you will get such a cooler like me^^

---

### Post by topsites on 2012-01-09
You speak of jumpers, it has been a while, has it?

Here is what I know.


1) With sata devices you don't have jumpers to worry about? Is that true?
- Yes that is true, it's all plug and play.

2) If you have a mother board with 6 sata connectors but only 3 sata 6 devices to attach to it - is there some order of the connectors on the board? Is there like a connector 1, 2, 3... etc? And, if so, should you connect your devices in order starting at the first one?
- It does not matter because the power is off, but I would start using slot 0 for the HDD, 1 for the CD-Rom, and so on.

3) If #2 above is right - how do you know which connector is which on the board?
- It will be labeled (0,1,2) and also the MB user's / owner's manual should list them.

4) If you have 3 sata 6 hard drives and one sata dvd/cd multi drive - is the multi drive sata 3 probably? 
- I don't know, but the HDD goes to the first connector.

5) Are sata 6 and sata 3 connectors shaped different - to where you can't accidentally connect a sata 3 device to a sata 6 connection? Or are they the same physically and you have to identify which connector to plug which devices into?
- Remember your hardware comes with User's manuals, read them!

6) Is there a possiblity to connect any of the plugs either direction and if you don't put it in the right direction you get a visit from the smoke genie? 
- No, to my understanding they're all one way Conways.

7) I know that the connction on memory sticks (on the stick itself) has a notch but it doesn't look like its dead center. I assume there is a "right way up" or a "right direction" to insert them. How do you know what that right direction is? I don't want to be trying to force anything in the wrong way.
- It's another one way Conway, plug everything in carefully and if it resists try the other way.
Remember your hardware comes with User's manuals, read them!

8) How do you know what the right direction is for inserting the cpu? I noticed there is a small triangle on one corner of the cpu and one on the socket on the board - is that what you go by? Fine little pins on that cpu, wouldn't want to bend them  :P
- Again careful does it and almost always everything is one way conway.
Remember your hardware comes with User's manuals, read them!

- With the CPU I do want to add my own tidbit of experience is because of those fine little pins...
Technically a CPU should seat under its own weight, literally you just place it over the square and let it slide down on its own.
Do NOT push it!
If it won't seat, you may have to try another angle, very carefully, merely setting it down should be sufficient.
Most have a dot / triangle marking to help guide.
Once it is seated, use the lever to lock it down.
Don't forget the heatsink and FAN!

9) How do you identify which is the pci x16 slot on the board as opposed to a lesser pci? (Bad terminology, I know). How do you know which pci slot to plug your graphics card into so you get the max performance it's capable of?
Your graphics card should be PCI-E, of which there exists only one slot, another method I use is closest to CPU.

10) Is there a typical practice regarding cables being included with devices and/ or the mobo? The monitors? Is there anything in particular I can "expect" regarding this?
- Take your time and be ready to take a break, also it would likely help greatly if you have a second, Internet-enabled PC somewhere around so you can look things up should you get stuck.

Any advice would surely be appreciated. I'm hoping this first build comes off smoothly.
- Take your time, likely take you the whole afternoon and maybe longer, just take as long as it takes.

---

### Post by ClientAlive on 2012-01-09
> **Basher101 said:**
> well take the triangle and the notches and you wont mess up..

p.s. dont forget to apply thermal paste on the cpu before mounting the cooler (it was hella hard to hold a giant 1 kg coolergrill still enough to place it perfectly :< still managed tho^^) but i doubt you will get such a cooler like me^^


I'm thinkin' the order to do it in is the paste after the cpu is inserted and locked down - right? Nothing else really makes sense (and I know that paste is a mess when it gets on your skin).

---

### Post by Basher101 on 2012-01-09
> **ClientAlive said:**
> I'm thinkin' the order to do it in is the paste after the cpu is inserted and locked down - right? Nothing else really makes sense (and I know that paste is a mess when it gets on your skin).

thats how you proceed. But holding a 16x14x5 CM coolgrill with a weight of 1 KG and mounting it to the millimeter exact was quite the challange.

---

### Post by topsites on 2012-01-09
> **ClientAlive said:**
> I'm thinkin' the order to do it in is the paste after the cpu is inserted and locked down - right? Nothing else really makes sense (and I know that paste is a mess when it gets on your skin).

The paste binds the CPU to the heatsink and fan so yes, the CPU has to be locked down first.
Usually I do first boot with the cover off to make SURE that fan is spinning.
More than anything the smoke genie tends to visit me when a fan isn't working.
And by the way it all happens rather quickly and unceremoniously, you almost don't even get a satisfactory Poof.
So while it's booting check the P/S and GPU and any and all other fans visually as well.
You'd be surprised how easy it is to overlook a cable connection, yet another reason to do first boot with the cover off, at least for myself it almost never works first boot lol but eventually it all gets set straight.
First (few) boots is also a good time to visit the BIOS.

One other thing I just remembered, on brand new cases be DANG careful a LOT of the edges are pretty sharp, they are made of unfinished steel and can cut the hell out of you so just be careful, then in back you may have to break out slot covers, sometimes screw holes have to be tapped first, and every so often something isn't a perfect fit and has to be "persuaded" to fit, lets hope all goes well but be prepared to have tools bigger than watch repair screwdrivers handy... Further, you may have to run off to a local computer store to pick up some part either you or they "forgot." 
Granted you could also order what it is online but then you won't have it for another week or two.

Long story short it could take more than an afternoon before it's up and running, remember easy does it, you will get her done so don't let it get to you.
Yeah... :p


Twist / cable ties can be awful handy for keeping the wires tidy, most important is they don't get caught in a fan.

Good luck!

---

### Post by Basher101 on 2012-01-09
> **topsites said:**
> 
Long story short it could take more than an afternoon before it's up and running, remember easy does it, you will get her done so don't let it get to you.
Yeah... :p


Twist / cable ties can be awful handy for keeping the wires tidy.

Good luck!

my case would be a mess without ties...also that the paste "binds" the heatsink is false. It only helps to conduct more heat away from the CPU and to the heatsink for better cooling.

---

### Post by imachavel on 2012-01-09
> **ClientAlive said:**
> yes, sata II and sata III is what I meant. I got the 3.0 Mb/s and 6.0 Mb/s mixed up with that when I wrote it.

@basher - I see what you're talking about with the pci slot. It almost looks like the little clip on either end of the slot for memory sticks. I'm sure I'll see it better when I have the board in my hands tho. Also, I hadn't noticed it before but I see that there is a smooth part on the face of the slot for memory that shows where the notch goes. If you look really close you can see which end it is closer to and I should be able to tell before sticking the dimm in.

What about the cpu alignment. You know, the first time I ever inserted a cpu was with that older machine I fixed up. I didn't know how to align the cpu and bent the pins. I spent most of the next day straighening them out. It was greivous but that was just an old cpu that I didn't even pay anything for. If that happened to this brand new chip I'd jump out the second story window or something.  :P

In case anyone else wonders what the build consists of I'll paste the link to the other post. I thought I should start a different one about these questions because that one is in community cafe and you aren't supposed to ask technical questions there.

Post #37 modifies 4 items from post #33 so if you replace those with the updated choices from #37 you'll have the final list I ordered.

Also note: 3 x on hard drives, 2 x on memory, 2 x on monitor.

don't forget the thermal paste. little tiny bit. don't forget to be very specific with what heat sink you buy. that can be a bitch. btw if sata 2 and sata 3 had 3 mbps and 6 mbps transfer interface speed, they would be pretty slow ;)

most i.s.p. modem routers today can do over 25 mbps transfer speed, and they are slow by todays standards. most modern mobos have onboard 1000 mbps network adapter interface chip set, and I'm not even sure the processor/ram/hard drive speed can handle the top transfer rate, 7200 rpm for hdd? well I guess I shouldn't throw out ssd, but even the i7 over clocked to 4 ghz at whatever processing speed the l1 and l2 cache process at, I'm not sure they would ever fully utilize the full capability.

---

### Post by imachavel on 2012-01-09
> **Basher101 said:**
> my case would be a mess without ties...also that the paste "binds" the heatsink is false. It only helps to conduct more heat away from the CPU and to the heatsink for better cooling.

true. I wonder how long the processor could handle running without the heat sink fan cooling it, perhaps days, perhaps only minutes? I'll never know because I wouldn't ruin a system just to test it out

---

### Post by Basher101 on 2012-01-09
Full capacity won't be reached beacuse of voltage. The maximum you can overlcock stable to is 5,5 GHz with good watercooling. Everything else is voltage limited, beacuse you need more voltage for higher clock speeds, which would fry the CPU regardless of cooling if increased too much. And the current overclock cap is at 5,5 GHz without frying CPUs with the Voltage.

---

### Post by eddier on 2012-01-09
Just want to point out something regarding heatsink compound,try not to use those nasty pads that are sometimes supplied with cpu's. They DO bond Heatsink and CPU,such that if you have remove heatsink perhaps to upgrade etc. then your gonna have fun because you wont be able to lift the haetsink cause its stuck and neither can you then get at the realease arm for the CPU!
(I got the 'T' shirt)

Personally i use simple Silicon grease-the same stuff I use on car brakes-just a smear not a blob.Works a treat.

eddier

---

### Post by Basher101 on 2012-01-09
> **eddier said:**
> Just want to point out something regarding heatsink compound,try not to use those nasty pads that are sometimes supplied with cpu's. They DO bond Heatsink and CPU,such that if you have remove heatsink perhaps to upgrade etc. then your gonna have fun because you wont be able to lift the haetsink cause its stuck and neither can you then get at the realease arm for the CPU!
(I got the 'T' shirt)

Personally i use simple Silicon grease-the same stuff I use on car brakes-just a smear not a blob.Works a treat.

eddier

interesting...if you do it the wrong way. How i did it:

step 1: open thermal paste
step 2: just apply a small amount on the CPU chip
step 3: get an old credit card and smear it like butter on bread, nice and evenly, yet thin but not too thin
step 4: put the friggin huge heatsink on it....

this way it wont get stuck anywhere..

---

### Post by ClientAlive on 2012-01-09
Yeah, I went out this morning and had Ace hardware order me some yellow zip ties. I wanted yellow and had called around all over town. They just didn't stock them. Even called auto parts stores and everything.

I remember when I applied cpu past to that older machine's cpu it seemed clumpy and didn't want to spread very well. in the end I had a few globs and streaks on the surface of the cpu. That really didn't seem right so I called a couple local shops and asked about it. They told me it would spread when you press the heat sink down against it and lock it in. Honestly, I could let it go on an old junker made from used parts, but I'm not so comfortable with that picture on a new cpu/ computer. I wonder if I should warm the paste a little to help it spread? It has some kind of metal salt in it or something. Idk...

---

### Post by Basher101 on 2012-01-09
it should not be clumpy...well thats quality for you...mine was just a bit sticky, but still fluid.

---

### Post by ClientAlive on 2012-01-09
> **Basher101 said:**
> it should not be clumpy...well thats quality for you...mine was just a bit sticky, but still fluid.


Right on. Well, I think it's all gonna work out in the end. Mainly I just wanted to have some answers to a few things I wasn't sure about. Now at least I can get this thread up in front of me and have it to look at as I go.

I can't think of a way to safely shut down the computer w/o an operating system installed so I figure I'll be sure and have some live cd in the drive for those first few boots. I really really don't want to hard boot the thing - At All - EVER - neVer eVer.  :(

But then you think, "what if the something (the optical drive or something) isn't connected right and you can't access that live cd anyhow." They ought to make a feature in the bios or something to shutdown - ya' know?
---------------

Edit:

Better yet, wouldn't it be cool if someone created an uber tiny distro that all it does is shutdown? It would have like the tiniest, bare minimal in the kernel and be created for just the one single purpose - to shutdown safely. The whole thing would be like 1 Mb or something and you could install it in seconds on a new build. When the build was done and you had a working machine you could take it off and put whatever you want on there. Somebody needs to make that if it doesn't already exist.

---

### Post by Basher101 on 2012-01-09
if you have no OS, a hard boot is just about as "dangerous" as pressing the ON switch...nothing more.
If you knew how computer work, or lets say think about how they work, you would know a hard reset is just cutting the power. A normal shutdown simply writes some OS files to the HDD before it cuts the power. And here is what is considered the "danger" in a hard reset, you can loose some data. I must admit, if you do this TOO frequently, you will break something sooner or later...but come on, no one hard resets all the time <.<

---

### Post by rg4w on 2012-01-10
I find the NewEgg videos helpful - here's one on assembling a custom build:
[http://www.youtube.com/watch?v=d_56kyib-Ls](http://www.youtube.com/watch?v=d_56kyib-Ls)

---

### Post by Basher101 on 2012-01-10
okay as promised here are some photos of my setup:

on the first photo you can see my system while it is turned off (you can see the case fan and blue CPU fan through the window).

[[img]http://ompldr.org/tYzY5MQ[/img]](http://ompldr.org/vYzY5MQ)

on the next one i opened the side panel so you can see the interior. There you can see the RAM, gigantic CPU cooler, the giant GTX 570, my tiny TV card at the bottom and the holy mess of remaining cables (my Power supply has still alooooot of options for me to upgrade my system with a second GTX 570 and a few HDDs^^)

[[img]http://ompldr.org/tYzY5OA[/img]](http://ompldr.org/vYzY5OA)

here i took out the graphics card and put a 30 cm ruler next to it, just for size comparison...

[[img]http://ompldr.org/tYzY5OQ[/img]](http://ompldr.org/vYzY5OQ)

here i took the other sidepanel off where you can see my cable management. My Sata cables are not single ones, but a smaller "bundle" with 4 cables at each end (saving alot of room when you want multiple HDDs..). This is why there are two sata power connectors at the back, i just had to place them like this for one end to reach my Blu-ray drive and the other my HDD...i then tied all the Fan controller cables together with those. The really big cable you can see is the 24-pin connector for the motherboard. On the right you can see the backplate for the CPU cooler mount (no way would a 1 KG heavy cooler stay properly if just screwed in ._.)

[[img]http://ompldr.org/tYzY5Yw[/img]](http://ompldr.org/vYzY5Yw)

and on the last one we have my system up and running (the mess of files on the desktop is a school project...). The side-panel fan has LEDs (looks much better when spinning, you can also see more light than on the photo) and the front of my case has 3 LED "bars" which you can only see one clearly..

[[img]http://ompldr.org/tYzY5aQ[/img]](http://ompldr.org/vYzY5aQ)

regards^^

edit: the second and third photo do not display in the thumbnails... :( if anyone knows what i have to do to make them display, please share)

---

### Post by Frogs Hair on 2012-01-10
Most of the installation questions regarding connections were answered in the mother board manual . This included , hard-drive , fans , power supply , power button , memory , and led indicators for the tower. Bios installation and updating are also covered.

---

### Post by Basher101 on 2012-01-10
+1 in any case of doubt, RTFM (read the friggin manual)^^ The only thing that was not mentioned though, were what the M connectors are for (they look like big jumpers). They are for the headers from your front panel, like power button, reset button, and others. Since the actual header cables are really small, you can just plug them onto the M connector, which has the same names as where you would have to plug the headers on the motherboard. This way you can comfortably put them all on the M connector, which you can then plug to the motherboard, having all headers connected without much trouble. Otherwise you would have to fiddle around with 4-5 tiny cables in a rather inaccessible area...

---

### Post by ClientAlive on 2012-01-11
Well that's good to know. I'll be sure to read those carefully, of course. Wasn't sure what they cover though - never saw one before.  :P

@Basher

Nice setup you got there. Something seems odd (or different) about the main board. What appears to be the cpu coller is not where I would expect to see it or sitting in a diretion I would expect. Interesting. Thx for those btw.

A chunk of the stuff is supposedly coming in tomorrow. I still haven't heard word when my hard drives will come. I ordered them through this weird company I had never heard of before (sparco.com). They seem pretty legit. Supposedly been in business 20 yrs. Just that the drives are on back order and they tell me they haven't received word from the manufacturer when they will send them (when Seagate will send them to sparco I guess). I hope they don't screw around too long.

---

### Post by ClientAlive on 2012-01-12
Well the first wave of stuff came in and the way the CPU was packaged is not what I expected. I thought it would be in a box, like the rest of the stuff. I had to go back and check my emailed invoice and the paper invoice to see if they'd sent me some 'refurbished' component or something. And the return policy seems like some kind of rapo deal. 30 days exchange only. I don't get it.

I attached a picture of it in the packaging. Does anyone have some experience with this? Is that the the normal way to package it? And most importantly - what does the packaging say about the kind of component I received. Is it "OEM" or "refurbished"? Should I be concerned?

Thanks
-------------------------

Edit:

@Basher - Now that I saw what my cpu cooler looks like I get what I was seeing inside your case there. I thought it was designed at a different angle than that - guess I was wrong.  ;)

---

### Post by Basher101 on 2012-01-13
looks like the OEM...Was it in a box witht he brand on it? If not you might have bought the tray version (like i did since its 20 bucks cheaper) which is the CPU only, no pretty box, no manual, no nothing. The tray is for manufacturers of computers as they do not really need those :D (note: tray version has only 2 years of warranty, but as long as you dont overclock too much it will run for 5 years+ stable..)

---

### Post by ClientAlive on 2012-01-14
> **Basher101 said:**
> looks like the OEM...Was it in a box witht he brand on it? If not you might have bought the tray version (like i did since its 20 bucks cheaper) which is the CPU only, no pretty box, no manual, no nothing. The tray is for manufacturers of computers as they do not really need those :D (note: tray version has only 2 years of warranty, but as long as you dont overclock too much it will run for 5 years+ stable..)


Ok. Wasn't sure about that. Thx.


Now I really have a quandry. I've made a couple calls this morn and been looking around at products but there's these differences between them I don't get.

I'm trying to order a couple dvi cables to connect those monitors with. Problem is, the plugs on the graphics card look slightly different than the one on the monitor. Then, when I look at products, I see there are dvi - d and dvi - i and the plug in the picture (of the product) looks different between them.

I just need to figure out what I need to buy. I never even saw a dvi plug before this.

I attached 2 pics - one of the plug on my graphics card and one of the plug on the monitor. See how there are 4 little holes around the little flat hole on the graphics card but not on the monitor plug?

---

### Post by oldfred on 2012-01-14
The one without the extra holes is digital only. The other is digital or analog.

[http://www.datapro.net/techinfo/dvi_info.html](http://www.datapro.net/techinfo/dvi_info.html)

---

### Post by ClientAlive on 2012-01-14
> **oldfred said:**
> The one without the extra holes is digital only. The other is digital or analog.

[http://www.datapro.net/techinfo/dvi_info.html](http://www.datapro.net/techinfo/dvi_info.html)


Thanks oldfred. I think I need dvi-d. That's what someone told me anyhow, and it looks right. I mean, the plug end looks right.

---

### Post by ClientAlive on 2012-01-25
Ok, so I got all the stuff in and started building the thing. As I started into it though, I'm a little confused about a couple things.

1) The power supply was listed as being a 585 watt power supply.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16811121002](http://www.newegg.com/Product/Product.aspx?Item=N82E16811121002)

And this here at the manufacturers website seems to confirm that

[http://hecgroupusa.com/products/pc-cases/mid-tower/6c28bb8Sx585/](http://hecgroupusa.com/products/pc-cases/mid-tower/6c28bb8Sx585/)

Except that on the label on the power supply itself it has a line that reads:

"Combined Power 195W"  The model name is "X-Power 585" and if you look close at the info at the bottom of that manufacturers link it says "Peak Output 585W" (Peak Output).

What's this??


2) Regarding power to the mobo:

The psu has a rectangular 20 pin plug, a 4 pin plug that's bound together with it at the wires (a twist tie or something like that/ plastic tie); and, in another lead of wires there's another 4 pin plug.

The mobo has an eatx plug that has 8 pins and an eatx plug that has 24 pins.

Regarding the 24 pin plug on the mobo - I'm guessing I plug both the 20 pin and the 4 pin plugs from the psu into that 24 pin deal on the mobo??

Regarding the other 8 pin deal on the mobo...  err...  What? Plug the 4 pin plug from the psu into it?? If so, which half of the 8 ping thingy on the mobo?

I don't get it and the manual for the mobo is really not very explanitory. it's one page with a couple drawings and very little to say about it. Really all it's doing is describing it's existence, not how to connect anything.

Are these things incompatible or somethting?

---

### Post by ClientAlive on 2012-01-26
I think I got it. I'll post some pics sometime in the very near future. Thanks for all your help guys.

---

