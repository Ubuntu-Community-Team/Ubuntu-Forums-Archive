---
title: "Ubuntu 11.04 not using all my ram or any swap"
date: 2012-01-15
forum: General Help
---

### Post by RabidFangs on 2012-01-15
Hello everyone, 

Im not one to ask for help, When I have a problem I use google or I come to the forums 
and I can find the answers I need here but this one has got me stumped for the past few 
weeks.

I have 16gb or ram and 16gb swap partition, In the image i am using handbrake to convert a video as you can see the CPU usage is at 100%, no swap is being used and the availiable ram is not being used. I cant get ubuntu to utilize no more than about 1.2gb or ram.


I have googled and read and read various sources tried different edits and I just cant seem to get this working. 

Does anyone have any ideas as to why this is happening.

Thanks

[IMG]http://img687.imageshack.us/img687/6082/screenshot1xw.jpg[/IMG]

---

### Post by elliotbeken on 2012-01-15
I think the answer is simple, ubuntu does not need to use any more RAM that what it is currently using.

In most cases Linux is good at handling resources !

for what you are using it for at the moment (handbrake) Ubuntu does not need that amout of RAM

---

### Post by bluexrider on 2012-01-15
Ubuntu does not require the use of that RAM installed. IMHO 16Gb is an overkill by 4X the amount you have installed. And same goes for the swap file.

Installation requirements are low compared to other operating systems. 

**Ubuntu Desktop Edition**

 
[LIST]
[*]1 GHz CPU (x86 processor (Pentium 4 or better))
[*]1 GiB RAM (system memory)
[*]15 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach)
[*]800 by 600 screen resolution
[*]Either a CD/DVD drive or a USB port for the installer media
[/LIST]

---

### Post by Buntumatic on 2012-01-15
Let me put it this way.

Do you think your car will run better if you install additional 8 wheels? No? Same with RAM, you need some but adding excess RAM will just waste energy. I used to have 2 **GiB** (not **gb**) of RAM for long time on my quad-core without any need for swap. Then I added 2 more GiB because it was so cheap. Now, looking at free output I see less than 400 MiB used, uptime is over 8 days, lots of apps running.

---

### Post by grahammechanical on 2012-01-15
At least it does recognise all that RAM. Try running some more programs. I have found that PDF documents of scanned images of each page use up a lot of memory, especially if the document is a PDF of a large book such as a dictionary. You will see RAM usage go up then.

Regards.

---

### Post by RabidFangs on 2012-01-16
> **elliotbeken said:**
> 

In most cases Linux is good at handling resources !

for what you are using it for at the moment (handbrake) Ubuntu does not need that amout of RAM

Thanks, I would have thought ubuntu wouldnt use so much cpu just converting a video.
considering there was so much ram installed.

> **bluexrider said:**
> Ubuntu does not require the use of that RAM installed. IMHO 16Gb is an overkill by 4X the amount you have installed. And same goes for the swap file.

Installation requirements are low compared to other operating systems. 

**Ubuntu Desktop Edition**

 

I can aggree its overkill and that much ram isn't required, but who wants to run their OS with minimum specs anyway. The reason why we do it is to let us run more than just the bare operating system and a couple of programs.

I raised the swap file from 4 to 16 gigs in 2gig increments while troubleshoot and get Ubuntu to use it or RAM, but none was used during my research.

> **Buntumatic said:**
> Let me put it this way.

Do you think your car will run better if you install additional 8 wheels? No? Same with RAM, you need some but adding excess RAM will just waste energy.

This is a great analogy thank you, but I look at it this way...adding those 8 extra tires will/should allow you to carry a more/bigger/heavier loads in your car (or tank if you have 12 tires)


> **grahammechanical said:**
> At least it does recognise all that RAM. Try running some more programs. I have found that PDF documents of scanned images of each page use up a lot of memory, especially if the document is a PDF of a large book such as a dictionary. You will see RAM usage go up then.

Regards.

Thank you for the suggestion, I did run sorta unscientific stress test to determine if 
ram is being used over the 1.5gigs, I opened some pdf files a couple of movies using 
vlc and movie player at the same time ran an encode and the ram did shoot up to 2.6gigs being used, but still the cpu was at 99-100% utilization, which is what im 
trying to avoid, I guess Ill be upgrading my CPU next.

Thanks for the suggestions everyone.

---

### Post by amauk on 2012-01-16
Processing power and RAM are two very different things
Tasks that max out one will probably not make a dent in the other

Video processing can very processor intensive, but generally doesn't use much memory

On the flip side, editing a high resolution image in an image editor can be very RAM intensive, but generally don't use much processing power

---

### Post by xyzzyman on 2012-01-16
If you upgrade your CPU, you will still use 100% of your CPU. The only difference will be your video will be done encoding quicker. Encoding is CPU intensive but not necessarily RAM intensive. It's like doing a large puzzle. While you could do it on an end table (Minimum requirements for RAM), having a kitchen table is easier (More RAM), doing it on a basketball court is a waste (16GB of RAM).

---

### Post by oldos2er on 2012-01-16
> **RabidFangs said:**
> I raised the swap file from 4 to 16 gigs in 2gig increments while troubleshoot and get Ubuntu to use it or RAM, but none was used during my research.

Why would you want to use swap?

---

### Post by xyzzyman on 2012-01-16
> **oldos2er said:**
> Why would you want to use swap?

16GB's of RAM on eBay is more expensive than a 16GB hard drive, so which would you rather wear out first? **rimshot**

---

### Post by bluexrider on 2012-01-17
OMG! I don't think the OS know how to handle that much RAM. DOES IT REALLY. 

As far as the SWAP file... well any ones guess. Personally I don't even have one installed. The zRam handles that for me due to the virtual ram that exists within the filesystem.

I suppose if my computer was NORAD compliant I would be concerned.     Best of luck [B]RabidFangs  
[/B]

---

### Post by xyzzyman on 2012-01-17
In a way it is kind of weird, that 4GB has been a level that's actually way more than enough for most people even though the cost has come down so much. How long did most of us wish we had more RAM but it was cost prohibitive? $300 laptops have 4GB's, 320GB HDD's, media readers, dvd burners, webcams, wifi/ethernet. Running Pentiums and not celerons?. Granted most of us would want more HDD and CPU, but for most of our family members the hardware has actually moved past their demands. Probably the same as how well XBox 360 and PS3 are still doing in sales, even though 360 came out over 6 years ago). I've only recently retrained myself to stop closing everything, and enjoy having different applets running, etc... OMG I'm using 800MB's of RAM now with all my extensions loaded and applets in the tray!!!! That's like 20% of my 4GB's, even though I'm not doing anything important!! (In Windows I would be at 1.4-1.5GB's probably but that still holds.)

---

### Post by bircoe on 2012-03-28
Hold up a second... your worried because your Ubuntu installation is not consuming all of your available memory?

I'd be worried if it did... this would mean that your PC has not got enough memory, the fact that it's not utilising swap means that you have enough physical memory for the tasks you are running and it does not need to utilise swap.

You really should go away and learn about how Operating Systems use memory if you're seriously worried about an OS not using all of your RAM.

It is really quite simple, the OS will use as much RAM as it needs to support the running processes, open up the system monitor app and go to the processes tab, add up the memory column and I'll bet it equals your current memory usage.

Here's a test for you, open a terminal window and type 'free -m', this will show you the current memory usage, of particular interest to you should be the buffers/cache line.

The Linux kernel will fill your memory with cache (from hard disk) of commonly accessed files, however it doesn't report this as utilised memory as it will drop cache as new programs are opened and extra memory is required. As an example my 16gb RAM machine is using 1.9gb of RAM and has used 13gb for cache according to free.

Now CPU and RAM usage are not linked in any way, your processor can be at 100% usage while your RAM may only be at 10% and vice versa your RAM could be 100% while the processor is at very low usage.

Various tasks use system resources differently:
Video Encoding especially in h264 (h264 is a multi threaded encoder) uses lots of processor and very little RAM.
Processing large images will use very little processor but lots of RAM.
Editing a document or spreadsheet will neither use large amounts of memory or processor, unless the files are excessively large.

Using Handbrake to test memory is a bad idea, video encoding apps read from the input file and write to the output file at the same time, they don't store the entire video in RAM (only enough to process the current frames) and most of the time use very little RAM. Just to get some numbers I've kicked off an encode of a 3.8gb 720p AVI and Handbrake is currently using only 315mb of RAM.

Here's another test... download this 13.7mb Panorama photo:
[http://upload.wikimedia.org/wikipedia/commons/4/41/Hong_Kong_Skyline_Panorama_-_Dec_2008.jpg]("http://upload.wikimedia.org/wikipedia/commons/4/41/Hong_Kong_Skyline_Panorama_-_Dec_2008.jpg")
Open it in an image viewer and then check that applications memory usage, Eye of Gnome uses 100% CPU and up to 1.2gb of RAM to open the image, once it's open it uses just under 425mb to display the image on screen.

---

### Post by Paqman on 2012-03-28
Have a look at what's in your /tmp when you're doing tasks like this. Some things like authoring DVDs will create massive temp files. If you find that's the case, then putting /tmp into a ramdisk might be a good idea. It'll certainly gobble up a lot of RAM on those rare occasions when you need it.

I agree with the above posters btw, the reason you're struggling to use 16GB of memory is because it's incredibly hard to make a desktop do that. 16GB of swap is also a bit pointless, even for hibernation.

---

### Post by bircoe on 2012-03-28
> **Paqman said:**
> Have a look at what's in your /tmp when you're doing tasks like this. Some things like authoring DVDs will create massive temp files. If you find that's the case, then putting /tmp into a ramdisk might be a good idea. It'll certainly gobble up a lot of RAM on those rare occasions when you need it.

I agree with the above posters btw, the reason you're struggling to use 16GB of memory is because it's incredibly hard to make a desktop do that. 16GB of swap is also a bit pointless, even for hibernation.

Just a tip, if you mount /tmp as a ramdisk and the files being written to /tmp exceed the amount of RAM space available then the OS will start to page to the swap partition... making the system slow.

---

