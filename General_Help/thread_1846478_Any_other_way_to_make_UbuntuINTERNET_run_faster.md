---
title: "Any other way to make Ubuntu/INTERNET run faster?"
date: 2011-09-19
forum: General Help
---

### Post by RAIDa23 on 2011-09-19
Hey guys,

I just started using Ubuntu 11.04 today, and so far its going pretty well, except that it run a little slow, especially when on the internet. Im even running on Ubuntu Classic (No effects) mode. I have a 2.8ghz processor and I have 512mb of RAM. The internet especially runs slow on websites like Facebook and YouTube, even with the network.http. hack thingy. I also get some visual glitches on websites, so could it be my graphics card? Would I need to upgrade my RAM to make it faster?

Should I downgrade to a lower version of Ubuntu? Is it even possible?

---

### Post by RAIDa23 on 2011-09-19
Bump.

Sorry guys. :(

---

### Post by Basher101 on 2011-09-19
Your RAM looks pretty slim for such a CPU. I suggest getting at least 1, preferably 2 GB of RAM if possible. I had on my browser facebook and 1-2 youtube tabs open and those 3 tabs took 400 MB RAM. Not for me to care as i have 4 GB to spare.

---

### Post by raja.genupula on 2011-09-19
hey man 
You should upgrade your ram Or you have to move to other types of ubuntu . 

now a days xubuntu and lubuntu both are moving very fast. 
xubuntu and lubuntu are good for your system . they also similar to ubuntu but with some low graphics that helps you to run your system with speed even with that ram .so give a try . i am sure you like them . 

all the best

---

### Post by Zephilinox on 2011-09-19
It is almost probably your ram, firefox alone is 400 mb or so, I also have a java game running in a tab which is 300 mb, then everything else adds up to an extra 150 mb, so really you're going to need 1 gb of ram, and all this is on a Xubuntu intallation (which I love, even more than ubuntu/kubuntu, it reminds me of windows XP) so if you don't plan on getting another 512 mb of ram, I'd probably skip right down to Lubuntu, although I've never used it so I can't speak for how memory friendly it is.

There are some things you can do to lower your ram usage, in your internet browser make sure you only have 1 tab open, and only a bare minimum of addons, no custom firefox theme (disable the the ubuntu theme addon) you could use install chromium instead of using firefox, I believe chromium uses just a bit lower memory over time than firefox (due to an intentional "memory leak")

You could also disable startup programs you don't need, and get rid of all your workspaces (apart from 1, obviously), if you use compiz then remove it.

to speed up web page loading, I'd recommend enabling http pipelinning (not sure if that is what you meant by the "hack") to do so type in firefox "about:config" without quotes, then in the search bar on that page type "pipe" you should get 4 results, 3  should be booleans and set to false, double click them to turn them into true, then edit the maxrequests to something like 8 or 16.

---

### Post by ykanello on 2011-09-19
what do you mean the system is slow when its on the internet?
You mean the system is crawling when you watch youtube?
or your network is slow when you wget an ubuntu iso?
yes memory IS important, but honestly nothing to do with netspeed...

---

### Post by raja.genupula on 2011-09-19
> **ykanello said:**
> what do you mean the system is slow when its on the internet?
You mean the system is crawling when you watch youtube?
or your network is slow when you wget an ubuntu iso?
yes memory IS important, but honestly nothing to do with netspeed...

Hi ykanello , 
          if we have a 1 Mbps net connection then its speed gonna be different for a system with 512MB ram and 2GB ram . for better net speed not only High speed connection but also we need High ram too . I have experienced this case.

---

### Post by vasa1 on 2011-09-19
> **Zephilinox said:**
> ... I'd recommend enabling http pipelinning ...

Keep in mind that quite a few "experts" suggest to keep away from changing pipelining defaults in Firefox.

Getting more RAM seems the best bet especially if you want to visit complex sites such as Facebook and YouTube.

---

### Post by ykanello on 2011-09-19
Hi Raja,
I am sorry but I cannot understand pure bandwidth usage, with Ram usage.
Using the pc to watch youtube, or what have you is not about the bandwidth... as the plugin for flash actually caches (copies the flv) locally. Yes to play flash you need ram, but that doesn't make your computer faster (network wise).

You could mention the application that is needed. After all your router could be running 'linux' and still have under 512MB of ram, and handle more speed than your pc does. So yes you need ram to statically trace net packages, in an active firewall lets say, but for home usage hmmm, I would really disagree :)

---

### Post by raja.genupula on 2011-09-19
> **ykanello said:**
> Hi Raja,
I am sorry but I cannot understand pure bandwidth usage, with Ram usage.
Using the pc to watch youtube, or what have you is not about the bandwidth... as the plugin for flash actually caches (copies the flv) locally. Yes to play flash you need ram, but that doesn't make your computer faster (network wise).

You could mention the application that is needed. After all your router could be running 'linux' and still have under 512MB of ram, and handle more speed than your pc does. So yes you need ram to statically trace net packages, in an active firewall lets say, but for home usage hmmm, I would really disagree :)
hey man , its nice to see you . 
hmm i have a example man , its big to write .what ever lemme try to make it short . 
you're a big river and i am a small stream . at a time both of us getting same heavy water flow . then who gonna handle it , me or you ?

---

### Post by JKyleOKC on 2011-09-19
> **RAIDa23 said:**
> I have a 2.8ghz processor and I have 512mb of RAM. The internet especially runs slow on websites like Facebook and YouTube, even with the network.http. hack thingy. I also get some visual glitches on websites, so could it be my graphics card? Would I need to upgrade my RAM to make it faster?As others have said, Firefox itself is going to use around 4/5 of your RAM, and the Kernel will need most if not all of what's left over. Thus there's little or no room left for the images, which have to be copied down into RAM before they can appear on your screen!

The only reason things work at all with such a small amount of RAM is that the kernel will swap pages of memory back and forth between RAM and the swap file, as necessary to keep everything going. However this swapping takes lots of time, and during that time nothing else is going to be happening. Bottom line: things get slow. It has nothing to do with speed of your internet connection, or http-pipelining, and everything to do with whether there's enough physical RAM in the system to do the job.

I have a couple of very old boxes here, one with 256 MB of RAM and the other with 512 MB. Both are usable, thanks to the swapping action, but slow. Due to their age, RAM sticks for them are now too costly to afford, so I put up with it when using them -- but most of the time they stay powered down. I have two others with RAM measured in GB (one has 2 and this one has 3) and both are much snappier.

Increasing your RAM to a full gigabyte will probably solve your speed problem; going to 2 or even 3 almost certainly will. Going past 3 GB with a 32-bit CPU is hardly worthwhile however, since these chips are limited to 4-GB addresses and most kernels don't even go that high...

---

### Post by ykanello on 2011-09-21
> **raja.genupula said:**
> hey man , its nice to see you . 
hmm i have a example man , its big to write .what ever lemme try to make it short . 
you're a big river and i am a small stream . at a time both of us getting same heavy water flow . then who gonna handle it , me or you ?

Its a nice example (put a little nature in our lives) but i think the result is the same. The traveling speed of the water in both cases is the same. In the case of the river true all the water will stay inside the banks, in the small stream it will overflow and create a nice lake by it :) 
the fact is though that the water travels at the same speed :)

---

### Post by raja.genupula on 2011-09-21
> **ykanello said:**
> Its a nice example (put a little nature in our lives) but i think the result is the same. The traveling speed of the water in both cases is the same. In the case of the river true all the water will stay inside the banks, in the small stream it will overflow and create a nice lake by it :) 
the fact is though that the water travels at the same speed :)

But we never want overflow of data , right ?

---

### Post by ofnuts on 2011-09-21
> **JKyleOKC said:**
> As others have said, Firefox itself is going to use around 4/5 of your RAM, and the Kernel will need most if not all of what's left over. Thus there's little or no room left for the images, which have to be copied down into RAM before they can appear on your screen!.
I have Firefox open with 2 windows and 15 tabs over various sites and it takes 180MB (plus 27MB shared). (I did put a cap of 50MB on its cache...).

---

### Post by raja.genupula on 2011-09-21
> **RAIDa23 said:**
> Hey guys,

I just started using Ubuntu 11.04 today, and so far its going pretty well, except that it run a little slow, especially when on the internet. Im even running on Ubuntu Classic (No effects) mode. I have a 2.8ghz processor and I have 512mb of RAM. The internet especially runs slow on websites like Facebook and YouTube, even with the network.http. hack thingy. I also get some visual glitches on websites, so could it be my graphics card? Would I need to upgrade my RAM to make it faster?

Should I downgrade to a lower version of Ubuntu? Is it even possible?

Hey man , The best thing i can suggest you is please move to lubuntu or xubuntu . because you have a low RAM .so now you have a problem with firefox and later with some other application  . we cant predict what you will going to DO in next minute . so please move xubuntu or lubuntu . 

all the best .

---

### Post by ykanello on 2011-09-21
> **raja.genupula said:**
> But we never want overflow of data , right ?

Raja I really dont get your point mate.
Your router and your pc, have the same 'internet' speed. 
I mean you download the latest iso from ubuntu, the data first pass the router, then your pc. The router has 1/10 at best the ram of your pc.
Why the router doesn't suffer?
Its the application running that starve the ram on the pc. not the network.

---

### Post by mahmoodkamal on 2011-09-21
If only the internet speed is a problem, check whether IPV6 is enabled or diabled?

---

### Post by Duncan Williams on 2011-09-21
get a slight speed advantage on the net by using opendns:
[http://www.afasterinternet.com/](http://www.afasterinternet.com/)

---

### Post by JKyleOKC on 2011-09-21
> **ykanello said:**
> The router has 1/10 at best the ram of your pc.
Why the router doesn't suffer?The router only has to pass one packet at a time to the PC, and the maximum size of a packet is usually 1500 bytes or less. It's up to the PC to stitch all the packets together and re-create the original file, image, or stream, and that takes much more space.

To continue the water analogy, think of a dripping faucet. The drops are the packets; if you put a bowl beneath they will eventually fill it. If the bowl is not big enough, it then overflows -- but the swapping mechanism catches the overflow.

---

### Post by ykanello on 2011-09-21
maybe in plumbing the water analogy it works, but in computing sorry it doesn't.
Try this: 
open a terminal , and wget the latest ubuntu iso:
```
wget "http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=latest"
```

on a seperate window run multiple times:
```
ps aux -www  |grep wget 
```

According to the theory of the 'running water' the memory footprint of wget should increase each tcp packet it receives right?

Well it doesn't :(
from the beginning till the end of the download, the memory used is the same:
> ykanello  8828  1.7  0.3   5624  1788 pts/5    S+   16:31   0:02 wget [http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=latest](http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=latest)


---

### Post by JKyleOKC on 2011-09-21
Most programs establish their memory footprint when first loaded, to avoid the delays when allocating additional memory later. In addition, the packet-assembly process is done by the TCP drivers rather than by the top-level program making use of them. The necessary large RAM buffers to hold the image will most likely be associated with the file-storage process rather than with wget, which simply calls the TCP interface and stuffs the received data into a file (or pipe) as it arrives. Thus wget itself needs to buffer no more than a single 4K storage page. Attempting to track exact RAM usage requires a detailed understanding of how the entire system fits together, and the kernel does an excellent job of hiding this from most users!

It's theoretically possible to replace hardware with software, and vice versa, so long as you have at least an absolute minimum of one and an unlimited maximum of the other. However the cost of such a tradeoff is speed. Years ago I actually programmed a demonstration of a simple computer using just one flip-flop for storage, one NAND gate as the CPU, a tape read-write device, and an unlimited amount of tape. However it would have taken almost a week of uninterrupted operation to add two single-digit numbers -- not at all practical. In practice, hardware is always faster than the equivalent software, and some hardware is faster than others. RAM is faster than SSD, SSD is faster than disk drives, and disks are faster than tape...

---

### Post by ykanello on 2011-09-21
I agree completely. This is why I detest on the idea that the initial user question why his internet is so slow, has to buy more ram.
We simply don't know where the problem is.

---

### Post by JKyleOKC on 2011-09-21
My experience, and that of many of the others in this thread, is that 512 MB is simply not enough to provide acceptable viewing of video over the Internet. While the OP might be able to store the streamed images to a file on his disk drive with no problem, viewing them later would still be unacceptably slow.

A few months ago, a TV commercial touting somebody's cell phone service showed the problem clearly: at the critical point in a sports contest, the action froze and the message "Buffering..." appeared on the screen.

Consider that a normal color display on a 15-inch screen (which is actually about 9x12 inches of image space) at the standard VGA resolution of 72 dots per inch requires 9x12x72x72 or 559872 dots; each dot (or if you prefer pixel) requires three bytes to represent it in RAM, so you need 1,679,616 bytes of RAM for each frame of the stream. Movies usually run at 24 or 30 frames per second, so for each second of the stream you need 40,310,784 bytes of storage -- which is approximately 40 MB of buffer space just for a single second of viewing time.

The OP said that Firefox was occupying 400 MB, which would leave him only 112 MB for all other program and buffer space. That's not enough to hold three seconds of movie, even if the kernel and display code took no space at all.

Of course, the system's code does take up space, and most of that code can be swapped out until it's needed. There's no need to buffer the entire stream, either; assuming that the code left in RAM can deal with the situation, you can get by with just two buffers: one for the frame being displayed and another for the frame that will follow it. That cuts the buffer space down to just 80 MB, leaving 32 MB for the code to handle the stream and do the swapping. It's usable, but not fast.

The result of all this is that with so little physical RAM, his system is forced into swapping -- and while the swap file does solve the space problem, it also takes time to accomplish this feat and thus slows down the display. You can test this if you like, by loading up a dozen or so instances of a text editor and opening the largest document you have into each, so that you have less than a gigabyte of RAM still available. Then log onto the Internet and try to view a video stream...

Lack of RAM may not be his **only** problem, but it's the most likely cause of unacceptable slowness. A number of web sites offer free speed tests to verify net transfer rates; using several of them can quickly show whether the data is coming in rapidly enough to be useful. If it's not, the stream can be buffered to disk and viewed later, when internet speed won't be a factor. But with so little RAM, it will probably still be too slow for comfortable viewing.

---

### Post by Duncan Williams on 2011-09-22
don't forget the `vram' that can be a huge factor.
How much, is it being used, does `hardware acceleration' occur, etc...

---

