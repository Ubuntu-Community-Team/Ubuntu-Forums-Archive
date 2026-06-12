---
title: "Bad RAM?"
date: 2011-07-28
forum: General Help
---

### Post by ClientAlive on 2011-07-28
Hi,

I'm trying to resurrect this old system (circa 2005); and, one of the things is I bought some extra RAM for it from ebay. It was listed exactly as the type of RAM my mobo supports but I get a different looking ident. from memtest86 v. 4.20.

Here's the link to the listing on ebay (the guy has a bunch of units he's selling of this):

[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=110627476135&ssPageName=STRK:MEWNX:IT](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=110627476135&ssPageName=STRK:MEWNX:IT)

And here's the link to my mobo specs:

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604)

Memtest calls it DDR398 though and spits out errors on the stuff by the thousands. It also says something about 199 MHz but the listing claims (as it ought to be) 400 MHz. I googled "what is ddr398" but only got a couple hits that looked even remotely relevant and they didn't solve anything for me. I'm trying to determine a few things here.

1> Is this the correct type of memory and if so, is it bad, or is it solvable in some way?
2> If it is solvable, how?
3> Should I try and return it? (I want the RAM, if it works, that's why I bought it - just not into getting took for a ride for $25 though).

I've attached a picture of the screen just before I shut memtest down. Does anyone know more about the information it's giving? I'd sure appreciate the help.

Thanks.
----------------------

Oh, by the way, if it helps any here's a link to the specs on the whole machine - except it's not all original now. What is deff. still original is the mobo, the cpu (this one's an AMD 3400 + @ 2.2 GHz, 512 MB cache), 2 X 256 MB RAM (whether it end up in the thing when it's all said and done or not). I have the Maxtor Diamondmax 10, 100 GB IDE drive but it isn't hooked up now (hope to include it later though).

What isn't orig. is the optical drive (a Philips CD Read/ Write drive, circa 2000), a WD800 Caviar, 80 GB IDE drive (which I also hope to include later but isn't hooked up now).

Ok, so here's that link: [http://h10025.www1.hp.com/ewfrf/wc/documentSubCategory?tmp_rule=48080&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604](http://h10025.www1.hp.com/ewfrf/wc/documentSubCategory?tmp_rule=48080&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604)

If you need any other information just let me know.

Thanks

---

### Post by overdrank on 2011-07-28
Hi and the first thing I see is the mother board supports Dual-channel memory architecture. How many channels do you have filled with memory?

[IMG]http://h10025.www1.hp.com/ewfrf-JAVA/Doc/images/c00496046.jpg[/IMG]
They memory you purchased I believe is not dual ram. I would first look at the memory channels on the motherboard and remove the memory and test one channel at a time.
Moved to General Help :)

---

### Post by ClientAlive on 2011-07-28
> **overdrank said:**
> Hi and the first thing I see is the mother board supports Dual-channel memory architecture. How many channels do you have filled with memory?

[IMG]http://h10025.www1.hp.com/ewfrf-JAVA/Doc/images/c00496046.jpg[/IMG]
They memory you purchased I believe is not dual ram. I would first look at the memory channels on the motherboard and remove the memory and test one channel at a time.
Moved to General Help :)


Hi,

Thanks for the reply. I need to look into the meaning of "dual channel" real quick but it's super late here now. I just wanted to respond real quick right now but I'll look at what that means and at the computer tomorrow afternoon after my running is done and make a proper reply.

Some details I might add for right now are:

A> There are a total of 4 memory dimms in my posession. 2 X 256 MB (orig came w/ machine when I bought it used) and 2 X 1 GB (the ebay stuff).
B> That memtest in the picture was done with all 4 dimms in the machine.
C> The machine now consists of a very base unit. The mobo, the CPU, RAM, and the optical drive on the secondary channel as master.
D> This is progress. To begin with I couldn't even get post let alone cmos setup or bios menu.
E> The machine now will run a few live things (Xubuntu, Parted Magic, Ultimate Boot CD) but only with just the 2 X 256.
F> If I can recall correctly, prior to today, I was not able to run anything live even when only having the 2 X 256 in it. I would get various errors depending on what it was I was trying to run.

I just wanted to give as much info as I can to establish some foundation. If any of it is redundant I apologize. If any of it is unnecessary feel free to just ignore it.

I'll look at what you mentioned and get back with proper response tomorrow. Thanks again.

Jake
---------------------

Oh, by the way, before posting this I just re-read the end or your response. What I think you are suggesting is to test each slot for memory that is on the mobo itself? And, if I'm not mistaken, I can think of one way of doing that that makes sense - to take a single dimm of memory that I know is good (one of the 256 MB dimms, for instance) and move it from one slot to the next, testing each time, until I run through all the slots? Is that what you meant?

---

### Post by ClientAlive on 2011-07-28
Ok, I couldn't help myself. I googled about this a little bit. It looks like they're saying dual channel or not is a "mode" as in something you set in the bios? So maybe, hoo! hoo!, as I was hoping, this RAM I bought might just not be "set" in the right "mode"?? Oh that I could be so lucky?
-------------------

Edit:

The 2 links I looked at -

[http://forums.techguy.org/hardware/539792-what-does-dual-channel-supported.html](http://forums.techguy.org/hardware/539792-what-does-dual-channel-supported.html)
[http://www.google.com/search?client=opera&rls=en&q=what+does+Dual-channel+memory+architecture+mean&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest](http://www.google.com/search?client=opera&rls=en&q=what+does+Dual-channel+memory+architecture+mean&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest)

(at that second one I was just browsing the captions)

---

### Post by mcduck on 2011-07-28
The frequency (~200MHz) is correct for the RAM, it's DDR RAM which means input/output happens on both the beginning and the end of a clock cycle, so DDR RAM running at 200MHz transfers data at 400MHz. (I wouldn't worry about the missing 1Mhz)

I would be more worried about the errors in memtest. Even a single error there is a sign of broken memory (or motherboard, or compatibility issue between the two). Thousands of errors and you can be pretty sure the RAM modules are broken, especially if everything works fine when only using the old modules you had.

(dual channel mode isn't usually something you'd turn on or off from BIOS, it's just a question of placing RAM modules in appropriate memory slots. And even if you had such option disabling it wouldn't give you errors in memtest.)

---

### Post by CatKiller on 2011-07-28
> **ClientAlive said:**
> 
Memtest calls it DDR398 though and spits out errors on the stuff by the thousands. It also says something about 199 MHz but the listing claims (as it ought to be) 400 MHz.

That's kind of a con, and kind of not, by the memory manufacturers. The actual clock of the bus will be 200 MHz, but because you get signalling on the rise and fall of the cycle ("[Double Data Rate]("http://en.wikipedia.org/wiki/Double_data_rate")") they call it 400 MHz. The later bandwidth-based nomenclature is more immediately accurate.

Running it at 199 rather than 200 is still in spec, so I don't think that's causing your problem.

> 
1> Is this the correct type of memory and if so, is it bad, or is it solvable in some way?
2> If it is solvable, how?
3> Should I try and return it? (I want the RAM, if it works, that's why I bought it - just not into getting took for a ride for $25 though).

The only difference I can see between the specs listed by the seller and what Crucial say are the [right modules]("http://www.crucial.com/store/listparts.aspx?model=Pavilion%20a1253w&Cat=RAM") for that motherboard is that the voltage is listed as 2.5V rather than 2.6V. Assuming no typos, there may be a setting in your BIOS to control the voltage, although that type of thing is usually handled automatically by [SPD]("http://en.wikipedia.org/wiki/Serial_Presence_Detect").

Best to try it one stick at a time as overdrank says. The seller says that they'll take it back if it doesn't work.

---

### Post by overdrank on 2011-07-28
> **ClientAlive said:**
> Hi,

Thanks for the reply. I need to look into the meaning of "dual channel" real quick but it's super late here now. I just wanted to respond real quick right now but I'll look at what that means and at the computer tomorrow afternoon after my running is done and make a proper reply.



From HP site
> If RIMMs are being used, keep the following items in mind when purchasing and installing modules:
The memory configuration of channel A (the first two sockets) and channel B (the second two sockets) must be identical.


---

### Post by ClientAlive on 2011-07-29
Ok. So I came home tonight and I ran a number of memory test (same test, different sticks/ combinations). Now I understand what overdrank was saying about testing those 1 GB sticks one at a time. I took it different at first, and I did to those tests also, but now I get it. So here's a list of the tests I ran followed by results, pics, and a couple things I notice that I don't quite understand but that may be telling.

1> 2 X 1 GB but in the other pair of slots (the two slots that are left most on the board). Failed.
2> 1 X 256 MB beginning with the left most slot and moving over one slot after each test until all 4 slots had been tried. All 4 tests passed.
3> 1 X 1 GB. That stick passed (left most slot; but, by this point, don't think what slot mattered for this test).
4> 1 X 1 GB (the other stick). Failed miserably.
5> 2 X 256 MB + 1 X 1 GB (with the 1 GB stick that did pass). Test is still running and is at about 15 min now. No problems so far and I think all three together (1.5 GB total) is going to pass. It's nearing the end of the test but we'll see.

One of the things I noticed was a difference in a couple places on the memory test output. On the line titled, "Memory" the entry to the far right of that line is a reading for MB/s. If you notice in the first pic I posted (in the op) it reads "1782 MB/s". This is a different reading than in all the other tests of all the other sticks. Another place there is a difference is the line titled, "Settings". In that line, to the far right of the line, there is a reading in parenthesis. I don't know what it refers to but in all the other tests it says "64 bits". In the first pic it says "128 bits". Everything else in those three lines (Memory, Chipset, and Settings) seems to match, just not those two things.

Unfortunately, I forgot to get a picture of the screen on a couple of the tests. I would have liked to use comparisons to see when it is that this "128 bits" reading comes up. One of the pictures I attached is the screen for that one bad stick of RAM - entitled, "TheOtherStick". Notice that it's reading says "64 bits". Based on what I have seen, I believe this "128 bits" reading comes into play when both the 1 GB stick are in the board together. Don't really understand it though and I don't understand the MB/s reading and why there is a difference there.

So, I guess I'm finding out that one of the two stick I bought on ebay is good and one is not? What I'm still wondering though is whether the problem is some physical failure or is due to something that can be changed. In other words, is there still something that could be done that would solve the problem or am I at the point where you just say, "that memory is bad." If I do contact the seller about it I wonder two things. (1) What is the best way to describe the problem so I get my point across and get what is fair? And (2) if I were to ever but RAM in this way again, or if the seller volunteered to send me a replacement, is there anything in particular I should make sure of so I get the right stuff?

I attached a couple more pics for your viewing pleasure  :D Thanks for helping me out on this guys.
-----------------------

Edit:

That test just passed (the one with both the 256ers and the 1 GB).

Sorry about that first pic. Real blurry but it was the one where I had both 1 GB sticks together and that's all. Notice that you can make out 3 digits in the field for "bits". I'm assuming what it said was "128 bits".

Edit 2:

So if I compare the first pic (test with 2 X 1 GB) and the last pic (test with 1 X 1 GB - the bad one) I see that this reading for bits is 64 even with the bad one but only if it is alone in the board. So I guess good or bad makes no difference on that reading. It is when those two stick are together that you get the different reading. I'd bet that also the condition for the different reading for MB/s as well.

---

### Post by mcduck on 2011-07-29
Based on those test it's safe to say that indeed one of the 1GB sticks is broken. And no, there's nothing you can do to fix it, especially when the other 1GB stick is working just fine with the settings you have. Simply a fail in memtest should be enough information for the seller to replace the stick.

What comes to the 64bit/128 bit thing, that's the dual-channel mode in action. If you have identical amounts of memory connected to both channels, the systems is able to use two memory channels instead of just one, thus doubling the bandwidth from 64 bits to 128 bits (and of course improving the transfer rate at the same time). But as long as you don't have suitable (and working!) memory sticks for that, I'd say you get a lot more benefits from using all 1,5GB of RAM you have than you'd get from only using the two 256MB sticks in dual-channel mode.

---

### Post by anewguy on 2011-07-29
I believe one of the things the Overdrank was quoting about your motherboard is important here as well:

memory must be installed in matched pairs.  If not, you won't get DDR, you'll just get single transfer on the cycle, or perhaps other problems.

So, 2 - 256 matched sticks would run in DDR.  1 - 1gb stick will not run in DDR mode.  At least, what I remember about DDR and motherboard requirements are compared with what you have and what Overdrank is quoting this should hold true.

So......yes, you a faulty stick of memory.  You should replace it with one whose specs match the working one you have, then be sure to install them both in a single bank.  Don't mix the 256mb and the 1gb sticks in the same bank, and be sure you install all memory in pairs or your performance will suffer.

Hummm....goes back to the beginning and starts with 1 thing at a time.  Don't know where that idea came from.

---

### Post by ClientAlive on 2011-07-29
> **anewguy said:**
> I believe one of the things the Overdrank was quoting about your motherboard is important here as well:

memory must be installed in matched pairs.  If not, you won't get DDR, you'll just get single transfer on the cycle, or perhaps other problems.

So, 2 - 256 matched sticks would run in DDR.  1 - 1gb stick will not run in DDR mode.  At least, what I remember about DDR and motherboard requirements are compared with what you have and what Overdrank is quoting this should hold true.

So......yes, you a faulty stick of memory.  You should replace it with one whose specs match the working one you have, then be sure to install them both in a single bank.  Don't mix the 256mb and the 1gb sticks in the same bank, and be sure you install all memory in pairs or your performance will suffer.

Hummm....goes back to the beginning and starts with 1 thing at a time.  Don't know where that idea came from.


Ok. I was wondering about that. I noticed that, out of 4 slots for memory, two are colored blue and two colored black. I'm guessing this is what is meant by a "bank." That a pair of slots is 1 bank? So that, for my machine, I have two banks - represented by the pair or blue slots (1 bank) and the pair of black slots (the other bank)?

I wanted to google it to make sure I'm not just making up something stupid. Wikipedia's article was pretty slim but I did find the following. Not sure if it really confirms my above assumption or not though. Maybe I carried that idea into the faq with me and didn't read it right.

> Each bank of RAM can deliver data the full width of the data bus, so a bank on a 486 would be 32-bits wide, whereas a bank on a Pentium 2 would be 64-bits wide. to fill a bank sometimes it takes more than a single stick of RAM depending on the width of both the bus and the RAm stick. . . .

Source: [http://www.overclock.net/faqs/125216-info-what-memory-bank.html](http://www.overclock.net/faqs/125216-info-what-memory-bank.html)

Ultimately though. I'd love to make sure I understand this just right. Then I can run with it. So what I think I'm hearing is that, in my machine, with 4 slots and dual channel capability, I can mix quantities as long as those quantities are paired and the pairs are identical.

> **anewguy said:**
> matched pairs.

So, for me it would work to have two 256 MB sticks and two 1 GB sticks as long as I keep the 256 sticks in the adjacent slots (either both blue or both black) and the 1 GB sticks in the other slots. Is that right?? Or does really ALL sticks have to be the same regardless of their placement?

Could I end up with 2.5 GB of ram using all 4 slots somehow? Or would I have to make a choice between 2 GB using 2 slots or 512 MB using 2 slots? (I mean, we know what the choice would be, I'm just using that for an illustration).

Lastly, I wonder what exactly is meant when they say the memory has to be the same. Is that with regard to size, or maybe to other, additional, factors besides? Maybe not even just one factor but several?

I tried to to look around for whatever info I can find on the net. Just not always sure what I run into is accurate or not.

> **mcduck said:**
> Based on those test it's safe to say that indeed one of the 1GB sticks is broken. And no, there's nothing you can do to fix it, especially when the other 1GB stick is working just fine with the settings you have. Simply a fail in memtest should be enough information for the seller to replace the stick.

What comes to the 64bit/128 bit thing, that's the dual-channel mode in action. If you have identical amounts of memory connected to both channels, the systems is able to use two memory channels instead of just one, thus doubling the bandwidth from 64 bits to 128 bits (and of course improving the transfer rate at the same time). But as long as you don't have suitable (and working!) memory sticks for that, I'd say you get a lot more benefits from using all 1,5GB of RAM you have than you'd get from only using the two 256MB sticks in dual-channel mode.

> **mcduck said:**
> What comes to the 64bit/128 bit thing, that's the dual-channel mode in action. If you have identical amounts of memory connected to both channels, the systems is able to use two memory channels instead of just one

Could it be that the type of memory is not dual channel type and it wouldn't matter if the guy sent me another good 1 GB stick anyway because there's an incompatibility between the mobo and the memory? Specifically, that the mobo is made for dual channel memory and if you put memory in it that isn't you get an incompatibility? If that were the case then it wouldn't matter if I got another good stick.

Yes. This figure of "two" channels contributes to my thinking that the channels are made up of a pair of slots. That's because 4 divided by 2 is 2. 4 slots on the mobo, 2 channels, must be looking for a "pair" of slots?

You said, " . . . you get a lot more benefits from using all 1,5GB of RAM you have than you'd get from only using the two 256MB sticks in 'dual-channel' mode."

But right now, out of 3 sticks total, I only have two that are paired and one is on it's own or 'different'. As the machine is now, can the entire 3 be operating in dual channel mode then?

I guess it goes back to my confusion about seeing this word "pair" and knowing there are actually 4 slots on my machine.

Then though, there's still that odd ball 1 stick on it's own there (as things are now). Can it be that the two 256 sticks are operating in dual channel mode but he 1 GB stick is not?

I'm trying to get a grasp on this thing. I keep running various questions through my mind to try and do that. Saying, "what if you do this or you do that?" What would happen then?

By chance does anyone know of a good reference that explains these things in more detail? I'll be looking around too.

Thanks.

---

### Post by ClientAlive on 2011-07-29
Wow. That guy was not easy to contact. I sure hope I don't have problems with him. When you click on "contact seller" you get some kind of help faq type thing. Even if you select that it didn't answer your question (which is supposed to let you send a message to the guy) it says some bs like he could not be contacted and sorry your question was not answered. Thinin' I got screwed on this one guys. We'll see.


:(

---

### Post by mcduck on 2011-07-30
Don't mix up dual data rate and dual channel, they are two different things. You have DDR (dual data rate) RAM, and nothing is going to change that. You wouldn't even be able to physically fit a SDR RAM module into your motherboard.

Dual channel mode, on the other hand, simply depends on having equal amount of RAM on each memory channel. you'll have to see your motherboards manual to see which RAM slots on the motherboard belong to which channel. And no, there's no way you'd be able to use dual channels with three RAM modules. Also it's dual channel mode for all memory, or single channel mode for all. (it's not that the RAM module would somehow switch to dual channel mode, it's your motherboards memory controller that switches into different mode when there are suitable amounts of memory in each memory channel)

And yes, not all RAM modules need to be same, you simply need same amount in each memory channel. So 2X 1GB + 2X 256MB would work in dual channel mode if you put 1GB stick and a 256MB stick in each channel.

Other features of RAM than just the size don't make a difference for dual-channel mode. All RAM installed in a computer will use the settings and speeds fit for the slowest installed module, so they will all run at the same speed anyway.

---

### Post by ClientAlive on 2011-07-30
> **mcduck said:**
> Don't mix up dual data rate and dual channel, they are two different things. You have DDR (dual data rate) RAM, and nothing is going to change that. You wouldn't even be able to physically fit a SDR RAM module into your motherboard.

Dual channel mode, on the other hand, simply depends on having equal amount of RAM on each memory channel. you'll have to see your motherboards manual to see which RAM slots on the motherboard belong to which channel. And no, there's no way you'd be able to use dual channels with three RAM modules. Also it's dual channel mode for all memory, or single channel mode for all. (it's not that the RAM module would somehow switch to dual channel mode, it's your motherboards memory controller that switches into different mode when there are suitable amounts of memory in each memory channel)

And yes, not all RAM modules need to be same, you simply need same amount in each memory channel. So 2X 1GB + 2X 256MB would work in dual channel mode if you put 1GB stick and a 256MB stick in each channel.

Other features of RAM than just the size don't make a difference for dual-channel mode. All RAM installed in a computer will use the settings and speeds fit for the slowest installed module, so they will all run at the same speed anyway.


I see. Thanks.

I contacted the seller and got a reply from him. He had some questions and requests for things I think I've already done and written about in this thread - so I just gave him a link to this thread with a brief explanation. I invited him to participate in the thread so maybe we'll see a comment from him here, maybe not. That'd be kinda cool though.

Thanks again for explaining. I'm going to close this one out (solved) since I think I'm at a point where I understand what's going on and know what needs to happen. Have a great weekend - all you all.


Jake

---

