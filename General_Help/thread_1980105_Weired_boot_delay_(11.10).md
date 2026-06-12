---
title: "Weired boot delay (11.10)"
date: 2012-05-14
forum: General Help
---

### Post by roelforg on 2012-05-14
Hey,

I've been working my way through my dmesg trying to find why my laptop boots so slow.
(sidenote: i'll post a bootchart after i finish converting this vid, say another 30 min)
I noticed something odd in dmesg:
```

[    2.388297] firewire_core: created device fw0: GUID 000ae4073960de4b, S400
[    4.962089] EXT3-fs: barriers not enabled
[    4.981592] kjournald starting.  Commit interval 5 seconds
[    4.982280] EXT3-fs (loop0): mounted filesystem with ordered data mode
[   46.826619] udevd[368]: starting version 173
[   46.882113] usbcore: registered new interface driver hdj_mod
[   47.030703] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.

```40+s to load udev*?!

My experience building initrd/-ramfs's from scratch tells me that this is after the initrd.img gets loaded.
```

[    1.038178] Freeing unused kernel memory: 696k freed
[    1.038476] Write protecting the kernel text: 5332k
[    1.038561] Write protecting the kernel read-only data: 2188k
[    1.065067] udevd[87]: starting version 173

```Because that one loads there.

Anyone got a clue? (the clueshop's closed now :p)

PS. Yes, it's a wubi install. Not that i think it matters as i can launch FF with 12+ tabs in <5s it isn't a slow hd.

*= Yes, i know it could be doing other things in that time as well. But it's still very long.

---

### Post by HiImTye on 2012-05-14
> **roelforg said:**
> 
[   46.882113] usbcore: registered new interface driver hdj_mod
[   47.030703] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.

either of these lines might have a hand in it also, try disconnecting all your USB devices and/or using the opensource video drivers and see if anything changes

---

### Post by roelforg on 2012-05-14
Okay, something weired just happened!
I installed bootchart and pybootchartgui
and the laptop rebooted in 20-25s!
Rebooted it again and we're back to 1+min

(note: When i say reboot, i mean shutdown, wait 10s and press the power button)

I attached the bootchart of the second reboot (i didn't keep the one of the first reboot).

---

### Post by roelforg on 2012-05-14
> **HiImTye said:**
> either of these lines might have a hand in it also, try disconnecting all your USB devices and/or using the opensource video drivers and see if anything changes
About those,
my laptop has an ATI card* and i have a hercules RMX but that one's not connected on boot (and not loading the hdj_mod (it's driver) doesn't make a difference)

*=as much as i'd like to use the oss driver, they just won't work right! Neither does the gnome-display-settings, yet the amdcccle works perfectly! So, i'm stuck with the prop. ATI/AMD drivers, but they work just fine.

---

### Post by jadtech on 2012-05-14
first to assume  being a wubi  dont make a difference , I ran wubi 11.10 for several months updated to 12.04 beta and ran that as well.. 

first thing you should know about your wubi install , some of its quirks and problems are related to windows since wubi is  a window program and even though it appears ubuntu boots  before windows, windows boots and is running in the background :) 

what I discovered with wubi is when your not booting windows  updates are falling behind for  virus scan windows updates and anything else scheduled to run like defrag  .. 

I installed my wubi and never checked or booted back in to windows for nearly 6 weeks the wubi install got slower and slower including boot up  other minor issues started popping up ..

I booted windows  windows took 3 or 4 mins to boot and the HD ran on and on as everything fought to  update  and install at the same time once I got things clamed  on my win7 install I did a disk clean up  and I checked and discovered the windows volume was 57% fragmented  I ran defrag several times I even rand a chkdsk for good measure and it actually found several bad sectors.. 

once I was done took me a whole day to recover the unused window OS , I rebooted back to my ubuntu wubi  instal and it flew like a jet again and cleared up   most of the issues I was having  .. 


your milage may vary  but if you are using  Ubuntu wubi install  not booting to windows much or keeping it maintained  it will  bite you  bad  running wubi ..

---

### Post by roelforg on 2012-05-14
> **jadtech said:**
> first to assume  being a wubi  dont make a difference , I ran wubi 11.10 for several months updated to 12.04 beta and ran that as well.. 

first thing you should know about your wubi install , some of its quirks and problems are related to windows since wubi is  a window program and even though it appears ubuntu boots  before windows windows boots and is running in the background :) 

what I discovered with wubi is when your nor booting windows  updates are falling behind for  virus scan windows updates and anything else scheduled to run like defrag  .. 

I installed my wubi and never checked or booted back in to window for nearly 6 weeks the wubi install got slower and slower including boot up  other minor issues started popping up ..

I booted windows  windows took 3 or 4 mins to boot and the HD ran on and on as everything fought to  update  and install at the same time once I got things clamed  on my win7 install I did a disk clean up  and I checked and discovered the windows volume was 57% fragmented  I ran defrag several times I even rand a dskchk for good measure and it actually found several bad sectors.. 

once I was done took me a whole day to recover the unused window OS , I rebooted back to my ubuntu wubi  instal and it flew like a jet again and cleared up   most of the issues I was having  .. 


your milage may vary  but if you are using  Ubuntu wubi install  not booting to windows much or keeping it maintained  it will  bite you  bad  running wubi ..


Wrong!
The only windows things wubi uses are the fs (ntfs) and bootloader, the rest is all linux.

The only valid point you made is that i may need to defrag, that's all (and i did that 2 weeks ago, big stuff loads in a splitsecond on ubuntu so i don't think that's the problem).


I mean, when i read your post, i thought you were jerryleecooper for a moment!

EDIT:
[http://rixstep.com/1/1/20070724,00.shtml](http://rixstep.com/1/1/20070724,00.shtml)
There! Read it. The first paragraph of the first quote is basically what you wrote.

---

### Post by jadtech on 2012-05-14
i ran wubi I am giving you  facts of   what I know for a fact happens :) 

if you want to  think that  your wubi install is not a windows program fine with me go back to window delete the ubuntu fold and all the files in it including the root.disk let me know how your next ubuntu boot goes :)

---

### Post by roelforg on 2012-05-14
> **jadtech said:**
> i ran wubi I am giving you  facts of   what I know for a fact happens :) 

if you want to  think that  your wubi install is not a windows program fine with me go back to window delete the ubuntu fold and all the files in it including the root.disk let me know how your next ubuntu boot goes :)

Never said it isn't a win prog.
I said you don't have your facts straight on how wubi works.
EDIT:
I'll explain.
While installing, wubi creates a raw disk image and stores it on the win partition.
This image is then used to store ubuntu as if it was a normal partition.
On boot, you select the wubi entry in winbcd and wubldr.mbr gets booted instead of windows.
wubldr.mbr will access the ntfs on your partition and chainload to a grub-like bootloader,
this one will launch the linux kernel that resides in the disk image.
The lupin initrd that'll be loaded as well will mount the image on /dev/loop0 and boot from that as if it were from a normal partition.
Nowhere does the windowskernel even touch the ram in that process, wubi basically creates a full ubuntu install in a file.

Maybe i should've warned you about that i'm a geek that knows the linux boot process by heart.

---

### Post by jadtech on 2012-05-14
oh no I do understand it :) 

just believe me when I tell you anything that happens to window will effect ubuntu sessions when its a wubi install ..

when you run window you get use to it being self maintained , even though wubi is on window none of the auto stuff is running none of it and over weeks it start to take it toll..

like said  my post was about what I found your mileage may vary some might concider me a geek of sorts too  What ever happen to the good ole days when you never had to worry about bad video drivers  your big concern was getting the printer rethreaded before you missed much and after you dailed the server getting the hand set in the modem cradle before there screeching stopped so you could loggin ..

also ran BBS on ham radio a bit back in the days when mac looked more like a tube type radio and used cassette player as hard drive or if you were poor and real clever   8track  recorder player would  do  to  a small degree ..

---

### Post by roelforg on 2012-05-14
> **jadtech said:**
> oh no I do understand it :) 

just believe me when I tell you anything that happens to window will effect ubuntu sessions when its a wubi install ..

when you run window you get use to it being self maintained , even though wubi is on window none of the auto stuff is running none of it and over weeks it start to take it toll..

like said  my post was about what I found your mileage may vary some might concider me a geek of sorts too  What ever happen to the good ole days when you never had to worry about bad video drivers  your big concern was getting the printer rethreaded before you missed much and after you dailed the server getting the hand set in the modem cradle before there screeching stopped so you could loggin ..

also ran BBS on ham radio a bit back in the days when mac looked more like a tube type radio and used casset player as hard drive or if you were poor and real clever  *track  recorder player would  do  to  a small degree ..

True

I never experienced any of the "self-maintenence" you're talking about, i always get frustrated with windows when using it for anything but my school work (and even then...). But thats my experience, yours may differ.
(i'm much more productive on linux then on windows)

Fine, fine! i believe you! But clarify what you said: "windows boots and is running in the background" because i dare to bet all 8 of my computers on that not being true. If you meant the windows boot loader, then that would still only make half sense as control is transferred to the kernel by the bootldr and, by definition, the bootloader isn't running anymore at that point.
Having written a toy os kernel, i actually studied the subject of bootloaders. And having build linux distros from scratch taught me the internals of linux boot procedures quite well i think.

---

### Post by jadtech on 2012-05-14
checked out the link you posted here this is funny reality is xp was good Vista was ok  neither was great they were just such a breath of fresh air from the failure that was windows ME the edsel of the computer world at that time but it was the huge gap of time between the two that was really the nail in Microsoft coffin, they may  some day catch up with everyone else but I don't think windows will have the popularity it had in the begining ..

win7 in my thinking is very good  how ever it was  to little to late and win 8 is a step away from the traditional PC a lot of people are gonna have a tough time accepting they will all be in there android and Iphones bitching about it to each other for years ..

---

### Post by roelforg on 2012-05-15
Anybody any fresh ideas on speeding up boot?
I noticed my server has this as well as my laptop.
My server runs ubuntu server as sole os.

@jadtech Sorry, i enjoyed the discussion but i really want to get back on topic.

---

