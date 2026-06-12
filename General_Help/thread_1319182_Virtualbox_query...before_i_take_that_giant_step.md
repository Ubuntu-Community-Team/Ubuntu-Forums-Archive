---
title: "Virtualbox query...before i take that giant step"
date: 2009-11-08
forum: General Help
---

### Post by arnab_das on 2009-11-08
okay. so virtual box has got me hooked. its far more technically sound than running wine (which primarily is for gamers as i have concluded).

but i need some help from the experts here.

1. i have a 2GB ddr2 ram. and amd 64 x2 240 processor. (the rest is on my signature)
are these sufficient to run virtualbox?

2. how much of RAM needs to be allocated to the new OS (say windows xp) i'm gonna setup?

3. how much of hard disk space should i dedicate to it? (considering the fact that currently my entire 160GB is dedicated to ubuntu. i have just a single partition on my hdd)

4. do i need to change the user settings?

plz help me out. thanks in advance.

---

### Post by MelDJ on 2009-11-08
1. Should be able
2. i run it with 128 and it works fine

3. it uses a virtual hard disk

---

### Post by Vaphell on 2009-11-08
try and see for yourself. Depends what you plan to do with it
my xp in vb gets 1GB of RAM and 10GB of hdd space.

---

### Post by arnab_das on 2009-11-08
thanks. one more thing. so when i'm NOT running the virtual OS, will it still consume 1GB of RAM or is it just when i'm running the OS?

in other words will i ALWAYS have 1 GB of RAM "wasted" thanks to the new virtual OS?

---

### Post by arnab_das on 2009-11-08
> **Vaphell said:**
> try and see for yourself. Depends what you plan to do with it
my xp in vb gets 1GB of RAM and 10GB of hdd space.

how much of RAM (in total) do u have?

---

### Post by noelvh on 2009-11-08
I run VB on my laptop its an IBM T43 1.8 processor, 2gb of ram, ati x300 video. I run XP (winflip version) with 356 of ram and 4gb for a hard drive. It runs great for me.

The XP winflp
[http://en.wikipedia.org/wiki/Windows_Fundamentals_for_Legacy_PCs]("http://en.wikipedia.org/wiki/Windows_Fundamentals_for_Legacy_PCs") 
This is a great version of windows XP that has very low over head, and dose every thing I need XP to do.

But I have run the full version of XP with out issue I just give it a bit more ram and hard drive space.

Noel

---

### Post by Vadi on 2009-11-08
Don't use VB for gaming. It has worse perf than wine, and it's directx -> opengl transformation is based on wine anyway.

---

### Post by muteXe on 2009-11-08
> **arnab_das said:**
> thanks. one more thing. so when i'm NOT running the virtual OS, will it still consume 1GB of RAM or is it just when i'm running the OS?

in other words will i ALWAYS have 1 GB of RAM "wasted" thanks to the new virtual OS?

No. When you "switch off" your VM you'll get your 1Gb back.

---

### Post by arnab_das on 2009-11-08
thanks again. last question.

heard rumours about virtualbox slowing the host OS to unusable extents. true?

---

### Post by The Real Dave on 2009-11-08
> **arnab_das said:**
> thanks again. last question.

heard rumours about virtualbox slowing the host OS to unusable extents. true?

It'll only slow it if you don't have enough power. You have plenty. I have 1.4Gb of Ram with a 3Ghz PIV, and I can easily run Ubuntu and an XP VM at once. With regard to your previous questions, XP will run fine with 192Mb of RAM. It won't take 192Mb of your RAM the moment it boots, only as much as it needs, maybe 100Mb. It can take up to 192Mb of your RAM, no more. If you set it to a higher figure, it will be able to take up to that amount of RAM. It won't use it all at once, unless the guest OS needs all of it, same as if it was a native install. 

You don't need to partition your harddrive. Virtualbox uses VDIs, virtual disk images, a single file, which your guest OS sees as a harddrive. If you select it to be a dynamic VDI, the VDI file will only be as big as is necessary, eg, a clean install of XP takes 2GB, so the file will be 2Gb. XP however will see it as a 10Gb or whatever harddrive. 10Gb is plenty, but, like with RAM, the file will only be 10GB in size, if the guest fills its harddrive. 

User settings and that don't need to be touched. XP won't realise that its in a VM, it'll think its a native install. 


BTW - XP's support is gone, so you won't be able to get updates for it. That could give you some problems in running certain programs

---

### Post by arnab_das on 2009-11-08
a huge thank you for all the help. i'm running XP perfectly on virtualbox! :)

however there's one more question. do i install the nvidia graphics drivers on this virtual OS? or do i keep it as it is?

---

### Post by Monotoko on 2009-11-08
XP support isnt gone, it is just in extended life period, updates are still available.

No you dont install the nvidia drivers, as it is using a virtual graphics driver.

In order to get your graphics and sound working as they should be, install Virtualbox Guest Additions

---

### Post by snowpine on 2009-11-08
> **arnab_das said:**
> a huge thank you for all the help. i'm running XP perfectly on virtualbox! :)

however there's one more question. do i install the nvidia graphics drivers on this virtual OS? or do i keep it as it is?

The "guest" OS (Windows) can't "see" your actual hardware. You don't need to install the nvidia drivers in Windows, but you also will not be able to take advantage of your graphic card's acceleration. As mentioned earlier, don't use Virtualbox for gaming or multimedia.

---

### Post by MelDJ on 2009-11-08
> **arnab_das said:**
> a huge thank you for all the help. i'm running XP perfectly on virtualbox! :)

however there's one more question. do i install the nvidia graphics drivers on this virtual OS? or do i keep it as it is?

when you install the guest additions, you will be able to choose whether you want 3d accelaration. install it that time.

---

### Post by arnab_das on 2009-11-08
> **snowpine said:**
> The "guest" OS (Windows) can't "see" your actual hardware. You don't need to install the nvidia drivers in Windows, but you also will not be able to take advantage of your graphic card's acceleration. As mentioned earlier, don't use Virtualbox for gaming or multimedia.

okay. but can i use it for converting say video formats etc? i dont want to "play" anything, but just conversion. can i do that?

also, is there any way to get the virtualbox OS to access my main hard drive?

---

### Post by snowpine on 2009-11-08
Sounds like MelDJ has more experience than me with this question, I'd listen to him instead. :)

---

### Post by fisheater on 2009-11-08
Dont worry about performance, my old slow laptop can handle running a virtual copy of winxp - you will find it works well. On my partner's computer, virtual winxp runs better than how it once ran when it was the only os.

Related question: I have botched my current version of ubuntu 9.04 and will need to reinstall. Can I copy my current virtual HD (where my virtualbox winxp is setup on), reinstall ubuntu and vbox, then reload my virtual harddrive with winxp and my program unchanged?

Thx!

---

### Post by P4man on 2009-11-08
> **arnab_das said:**
> okay. but can i use it for converting say video formats etc?

Sure that doesnt rely on the videocard.

Then again why not use something like [handbrake]("http://handbrake.fr/") natively on linux?

---

### Post by MelDJ on 2009-11-08
> **arnab_das said:**
> okay. but can i use it for converting say video formats etc? i dont want to "play" anything, but just conversion. can i do that?

also, is there any way to get the virtualbox OS to access my main hard drive?

you can install converters in it. no problem

to share files with your host drive, try this: [http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12](http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12)

---

### Post by arnab_das on 2009-11-08
> **P4man said:**
> Sure that doesnt rely on the videocard.

Then again why not use something like [handbrake]("http://handbrake.fr/") natively on linux?

handbrake cant change resolutions. :( :( :( thats the huge problem of that otherwise wonderful program.

also, sometimes i find convertx doing a better job at conversion that winff or devede (although it has the same dependencies)

---

### Post by P4man on 2009-11-08
> **fisheater said:**
> 
Related question: I have botched my current version of ubuntu 9.04 and will need to reinstall. Can I copy my current virtual HD (where my virtualbox winxp is setup on), reinstall ubuntu and vbox, then reload my virtual harddrive with winxp and my program unchanged?


Yep no problem. Just make sure you set roughly equal settings for the VM for things like acpi and IO APIC or windows may not like it and bluescreen.

---

### Post by arnab_das on 2009-11-08
> **MelDJ said:**
> you can install converters in it. no problem

to share files with your host drive, try this: [http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12](http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12)

dunno why, but the page isnt opening. :(

---

### Post by arnab_das on 2009-11-08
question: how do i get the virtual OS to access my main drive (on which ubuntu is installed)? oh btw, its ext4, so will win xp recognise it?

---

### Post by snowpine on 2009-11-08
> **fisheater said:**
> Related question: I have botched my current version of ubuntu 9.04 and will need to reinstall. Can I copy my current virtual HD (where my virtualbox winxp is setup on), reinstall ubuntu and vbox, then reload my virtual harddrive with winxp and my program unchanged?


Yes, when I got a new computer, I copied my entire .Virtualbox folder over no problem. (Of course, legally you need a new Windows license activation to use it on another computer.)

---

### Post by MelDJ on 2009-11-08
> **arnab_das said:**
> question: how do i get the virtual OS to access my main drive (on which ubuntu is installed)? oh btw, its ext4, so will win xp recognise it?

i will go to the points then:
open virtualbox
click your xp machine 
click on the *Settings* icon at the top.
left, click on the *Shared Folders*. Then, click on the [IMG]http://images.maketecheasier.com/2008/11/virtualbox-add-folder.jpg[/IMG] icon on the far right. 
Select the folder that you want to use as a share point. Give it a name.
Click *OK* to close the Settings window.
boot up

---

### Post by P4man on 2009-11-08
> **MelDJ said:**
> i will go to the points then:
open virtualbox
click your xp machine 
click on the *Settings* icon at the top.
left, click on the *Shared Folders*. Then, click on the [IMG]http://images.maketecheasier.com/2008/11/virtualbox-add-folder.jpg[/IMG] icon on the far right. 
Select the folder that you want to use as a share point. Give it a name.
Click *OK* to close the Settings window.
boot up

Then you still need to find the share in windows. Easiest is mapping a network share. In windows open a terminal (dont laugh)
start > run > cmd.exe
```

net use x: \\vboxsvr\nameofyourshare 
```

that will map the X: drive to one share.

---

### Post by MelDJ on 2009-11-08
> **P4man said:**
> Then you still need to find the share in windows. Easiest is mapping a network share. In windows open a terminal (dont laugh)
start > run > cmd.exe
```

net use x: \\vboxsvr\nameofyourshare 
```that will map the X: drive to one share.

forgot to add that ;)

---

### Post by fisheater on 2009-11-08
> **snowpine said:**
> Yes, when I got a new computer, I copied my entire .Virtualbox folder over no problem. (Of course, legally you need a new Windows license activation to use it on another computer.)

Thanks for the reply...

When you set up your new computer - did you install virtualbox, then copy your .virtualbox folder over what had been installed?

TY

---

### Post by arnab_das on 2009-11-08
> **P4man said:**
> Then you still need to find the share in windows. Easiest is mapping a network share. In windows open a terminal (dont laugh)
start > run > cmd.exe
```

net use x: \\vboxsvr\nameofyourshare 
```that will map the X: drive to one share.


 :lolflag:    thanks again.

okay so if i want to share a folder called /home/username/Pictures then i'll have to type:
net use x: \\vboxsvr\home\username\Pictures or net use x: \\vboxsvr\Pictures?

---

### Post by P4man on 2009-11-08
> **arnab_das said:**
> :lolflag:    thanks again.

okay so if i want to share a folder called /home/username/Pictures then i'll have to type:
net use x: \\vboxsvr\home\username\Pictures or net use x: \\vboxsvr\Pictures?

No.
First you have to do the steps MelDJ gave you to create a share called "[COLOR="DarkRed"]pictures[/COLOR]" which shares /home/yourname/Pictures with virtualbox.

then in windows you type

net use x: \\vboxsvr\[COLOR="DarkRed"]pictures[/COLOR]

---

### Post by snowpine on 2009-11-08
> **fisheater said:**
> Thanks for the reply...

When you set up your new computer - did you install virtualbox, then copy your .virtualbox folder over what had been installed?

TY

Correct; then the first time I used virtualbox, all of my virtual machines and settings were there. It is a cool technology for sure. :)

---

### Post by arnab_das on 2009-11-08
> **P4man said:**
> No.
First you have to do the steps MelDJ gave you to create a share called "[COLOR=DarkRed]pictures[/COLOR]" which shares /home/yourname/Pictures with virtualbox.

then in windows you type

net use x: \\vboxsvr\[COLOR=DarkRed]pictures[/COLOR]

it says system error 53.

network path not found. :(

---

### Post by P4man on 2009-11-08
> **arnab_das said:**
> it says system error 53.

network path not found. :(

You did install the virtualbox guest additions did you?

---

### Post by arnab_das on 2009-11-08
> **P4man said:**
> You did install the virtualbox guest additions did you?

erm...i did install the virtualbox package. was guest additions included in that?

---

### Post by arnab_das on 2009-11-08
okay i installed guest additions and its simply brilliant! period.

i'll tell u what i did. i "booted" xp, clicked on the "Devices" option and then on Install Guest Additions. installed perfectly and now there's integrated mouse control and also I can access the pictures folder! woo hoo! :)

huge thank u to all! :)

---

### Post by noelvh on 2009-11-08
One cool thing I do once you have you share folder is creat folder links to other folder and place them in the share folder. Then you have access to what ever you have a link for.

Noel

---

### Post by The Real Dave on 2009-11-09
> **Monotoko said:**
> XP support isnt gone, it is just in extended life period, updates are still available.


Not for a fresh install....

---

