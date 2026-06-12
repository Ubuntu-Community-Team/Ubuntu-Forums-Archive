---
title: "Computer stopped working"
date: 2010-06-04
forum: General Help
---

### Post by spibou on 2010-06-04
When I tried to turn on my computer yesterday the light went on and the processor fan started working but nothing beyond this. In particular there was no beep. I tried turning it off and on a few times but it was always the same. Another thing was that if I turned the electricity off from the plug and turned it on again the computer came on without pressing the on button. It didn't used to be like this.

I opened the case but didn't remove any components and as far as I can tell nothing  seems out of the ordinary; no loose cables and no leaking capacitors. The power unit fan is also working.

The computer was working fine until the day before yesterday when I turned it off normally. Any suggestions on how to proceed ?

---

### Post by whiskeylover on 2010-06-04
I had the same issue a while back. It turned out to be a bad hard disk. But there could be anything. Try troubleshooting it by disconnecting one component at a time and trying to boot.

---

### Post by spibou on 2010-06-04
> **whiskeylover said:**
> I had the same issue a while back. It turned out to be a bad hard disk. But there could be anything. Try troubleshooting it by disconnecting one component at a time and trying to boot.
But if I disconnect the hard disk it won't boot anyway. How will I know if it's the hard disk causing the problem ?

---

### Post by whiskeylover on 2010-06-04
> **spibou said:**
> But if I disconnect the hard disk it won't boot anyway. How will I know if it's the hard disk causing the problem ?

It will boot to the point where the BIOS would say "No OS found" or something like that. But thats assuming the HDD is the culprit.

---

### Post by sydbat on 2010-06-04
I'd go with whiskeylover's suggestion and unplug the hard drive. If it still doesn't post, I would guess it might be something with the motherboard or processor.

---

### Post by spibou on 2010-06-06
I tried first unplugging the DVD reader/writer and then the hard disk. Symptoms remain exactly the same. The only other things I can possibly unplug are the processor when I assume nothing would work anyway or the graphics card. Should I try unplugging the graphics card ?

---

### Post by SoFl W on 2010-06-06
If you unplug the graphics card you wont be able to see any screen errors... but you should hear everything.  
I would do it just the opposite of what everyone else is saying.  I would removed and unplug everything, including the memory and reboot adding one item at a time starting with the memory.  (boot without the memory first to see if it gives you a series of beeps)

---

### Post by spibou on 2010-06-06
When you say everything you mean even the processor ? So in which order should I add things ? First memory , then processor , then what ? And how will I know when I have reached the guilty component ?

---

### Post by SoFl W on 2010-06-06
Don't remove the processor.  You will know you reached the problem item when the machine no longer boots.  If it boots after installing everying then something came loose or unplugged.  

As a warning/disclaimer, if you are uncomfortable with this, then don't do it, you can't blame me if you ruin your motherboard.

---

### Post by Shakz on 2010-06-06
I have seen this a lot with ram that has gone bad.

---

### Post by LADmaticCA on 2010-06-06
> **Shakz said:**
> I have seen this a lot with ram that has gone bad.

Agreed. I would try re-seating that ram first, or if there is more than one stick swap them out and try one at a time. I also had a similar case like this and it turned out to be my power supply failing.

---

### Post by spibou on 2010-06-06
> **SoFl W said:**
> Don't remove the processor.  You will know you reached the problem item when the machine no longer boots.  If it boots after installing everying then something came loose or unplugged.
But with the hard disk and the memory unplugged it won't boot anyway, will it?
> 
As a warning/disclaimer, if you are uncomfortable with this, then don't do it, you can't blame me if you ruin your motherboard.
Noted.

---

### Post by Swagman on 2010-06-06
> **spibou said:**
> But with the hard disk and the memory unplugged it won't boot anyway, will it?

Noted.

You'll get error beeps for No RAM found.. No hard drive found simply displays on screen "No bootable Disks found"

It does sound like a RAM issue though.

---

### Post by bondo101 on 2010-06-06
Does the power supply fan spin?, do the case fans spin? It could be the mobo
 hows the battery on the mobo ? if its dead no bios. How old is the machine? do you keep it on all the time? did you up grade hardware lately . ask your self these Questions. Un plug the power supply see if it still works . does  the fan spin? Memory yes sometimes goes bad . you should have beep codes on mobo and memory .keep posting so someone can help. :confused:

---

### Post by Sef on 2010-06-06
Moved to General Help.  OP asking for support.

---

### Post by spibou on 2010-06-06
> **bondo101 said:**
> Does the power supply fan spin?,

Yes, I said so in my opening post.
> do the case fans spin?
There aren't any, just the processor fan and the power unit fan.
> It could be the mobo
 hows the battery on the mobo ? if its dead no bios.
How can I tell if the battery is alive?
> How old is the machine?
3 years old.
> do you keep it on all the time?
Yes.
> did you up grade hardware lately . ask your self these Questions.

No.
> Un plug the power supply see if it still works .
How could it possibly work if I disconnect power :confused:

---

### Post by spibou on 2010-06-07
I tried disconnecting the RAM and now I get beeeeeeep-beep-beep. No messages on the screen with the graphics card still connected. So I guess it's the RAM and I need to buy a new RAM chip. Problem is I don't know what type. I know it's 1 gigabyte but I don't remember the specification and nothing on the chip itself or the motherboard gives any useful info. Any ideas ?

Also I would like recommendations for shops in the U.K. which sell this sort of thing through mail.

Thanks everyone for all the help so far , I'm making progress.

---

### Post by Dimarchi on 2010-06-07
First and foremost, the beeps you get are what Swagman mentioned about. It does *not* mean that they are bad. That beeping should happen if there are no RAM seated in the motherboard. For you to determine whether the RAM is bad you need to run memtest that is selectable as one option in the grub menu (if you can get that far) with the RAM sticks seated in their proper slots. Run it in a loop a few times (which it should do automatically until you stop it).

LADmaticCA had a good description of how to go about it for each individual RAM stick if you wish to see which one has gone bad. memtest will report errors if it is not a good RAM stick.

Unplug the power supply can be interepreted in the following manner (as I see it...no need to fiddle with the insides of the computer, although you may have to resort to that, too): remove the power cable to you computer for some minutes and replug it again. Turn on the power and check whether the computer starts as it should. The purpose of this routine is to drain the residual electricity in the computer...it is a sort of reset for the computer.

Some computers do not start if the battery is dead. Some merely report the date as 1 / 1 / 1970 - usually, or some other date that is not the current date but will start anyway. This can be seen either in bios (if the bios reports it) or in OS when it has booted. To test it, set the date, do the unplug thingie above, and then check if the date sticks...if it does, battery is not dead. If it does not and it reverts to that other date, battery is dead.

Patience...do not rush yet to the store. Yes, I admit it is easy for me to say...on the other hand, this will allow you to test your computer more thoroughly and perhaps save some money.

---

### Post by spibou on 2010-06-07
> **Dimarchi said:**
> First and foremost, the beeps you get are what Swagman mentioned about. It does *not* mean that they are bad. That beeping should happen if there are no RAM seated in the motherboard. For you to determine whether the RAM is bad you need to run memtest that is selectable as one option in the grub menu (if you can get that far) with the RAM sticks seated in their proper slots. Run it in a loop a few times (which it should do automatically until you stop it).
I can't get to the grub menu. With the memory connected the symptoms are as I described them in my opening post. With the memory not connected I only get beeeeeeep-beep-beep and nothing on the screen.
> 
LADmaticCA had a good description of how to go about it for each individual RAM stick if you wish to see which one has gone bad. memtest will report errors if it is not a good RAM stick.
There's only 1 stick.
> 
Unplug the power supply can be interepreted in the following manner (as I see it...no need to fiddle with the insides of the computer, although you may have to resort to that, too): remove the power cable to you computer for some minutes and replug it again. Turn on the power and check whether the computer starts as it should. The purpose of this routine is to drain the residual electricity in the computer...it is a sort of reset for the computer.
The computer has been unplugged for hours between successive tests.
> 
Some computers do not start if the battery is dead. Some merely report the date as 1 / 1 / 1970 - usually, or some other date that is not the current date but will start anyway. This can be seen either in bios (if the bios reports it) or in OS when it has booted. To test it, set the date, do the unplug thingie above, and then check if the date sticks...if it does, battery is not dead. If it does not and it reverts to that other date, battery is dead.
Since I don't get anything on the screen I can't check this.

---

### Post by whiskeylover on 2010-06-07
> **spibou said:**
> I tried disconnecting the RAM and now I get beeeeeeep-beep-beep. No messages on the screen with the graphics card still connected. 

I think its the video card. See this link for beep codes.

[http://www.pcstats.com/articleview.cfm?articleID=1223](http://www.pcstats.com/articleview.cfm?articleID=1223)
> [SIZE=2]One Long  Beep, Two Short Beeps[/SIZE]     [SIZE=2]Video Problem[/SIZE]

Also, this website has additional beep codes. -> [http://www.computerhope.com/beep.htm](http://www.computerhope.com/beep.htm)

And it also says its a video problem.

---

### Post by spibou on 2010-06-09
> **whiskeylover said:**
> I think its the video card. See this link for beep codes.

[http://www.pcstats.com/articleview.cfm?articleID=1223](http://www.pcstats.com/articleview.cfm?articleID=1223)


Also, this website has additional beep codes. -> [http://www.computerhope.com/beep.htm](http://www.computerhope.com/beep.htm)

And it also says its a video problem.
My motherboard is Asus Pundit P1-AH2. Does anyone know the beep codes specifically for this one ? The first 2 pages of a Google search did not reveal anything and annoyingly the motherboard manual doesn't say either or at least I didn't see it with a quick look.

If it is the video card I need to buy a new one , yes ? Ok , this may be a silly question but why does the computer need a video card to display some characters on the screen ? Why can't the processor do it on its own ?

---

### Post by spibou on 2010-06-09
> **whiskeylover said:**
> I think its the video card. See this link for beep codes.

[http://www.pcstats.com/articleview.cfm?articleID=1223](http://www.pcstats.com/articleview.cfm?articleID=1223)


Also, this website has additional beep codes. -> [http://www.computerhope.com/beep.htm](http://www.computerhope.com/beep.htm)

And it also says its a video problem.
Just to be clear, if I disconnect the memory chip then I get the beeps, if I connect it I don't get anything. If the problem is the video card why would I get this sort of behaviour ?

---

### Post by Dimarchi on 2010-06-10
Because memory is required for computer to operate - video card, however, is not. This is normal is server farms which are made of several computers...there usually is one terminal (computer with a display and hence a video card) that is used to monitor the rest of the interconnected computers and their status (oversimplification perhaps, but that's one option).

In the early days of computing the video capabilities were inside CPUs. At the time if you needed more powerful display capabilities, you had to make do with whatever the processor allowed you to do. This lead to the birth of integrated and discrete video cards, eventually. And nowadays the video card capabilities are going back to CPUs (I believe Intel has such at the moment, AMD to follow soon). This does not kill video cards...CPU bound video is still restricted in power by whatever CPU you have, while video processing power can be upgraded to a more powerful one by swapping a new video card in place of the old card - to get the same for CPU you would need to replace the CPU with a more powerful one. Which one of these you would prefer, is up to you.

Anyway...back to the topic: if you can get a video card from somewhere for testing (old computer you had, friends, some surplus computer store, or some such), that would help. The important thing to know now is this:

The motherboard info that you gave us implies that there is an integrated video card present on the board (NVIDIA GeForce 6150 Shared Video Memory (UMA)). You are using the integrated video card? It has two PCI slots so another possibility would be that you use a video card that is in one of these slots?

---

### Post by spibou on 2010-06-17
> **Dimarchi said:**
> Because memory is required for computer to operate - video card, however, is not.

Still , it sounds strange that with memory I would get no beeps and without memory I would get beeps not for the memory but for the video card. By the way , I tried a new memory chip and when it's connected I get the same symptoms as in my opening post. So I guess this rules out a memory problem , right ?

> This is normal is server farms which are made of several computers...there usually is one terminal (computer with a display and hence a video card) that is used to monitor the rest of the interconnected computers and their status (oversimplification perhaps, but that's one option).
So how do the computers without the graphics card communicate with the world ? Because one of the problems in my case is that the computer isn't really giving me much information as to what's wrong. 
> 
In the early days of computing the video capabilities were inside CPUs. At the time if you needed more powerful display capabilities, you had to make do with whatever the processor allowed you to do.
I wasn't thinking about powerful display capabilities but that it would be convenient if the computer would still be able to display some error message on the screen even if the graphics card is broken.
> 
Anyway...back to the topic: if you can get a video card from somewhere for testing (old computer you had, friends, some surplus computer store, or some such), that would help. The important thing to know now is this:

The motherboard info that you gave us implies that there is an integrated video card present on the board (NVIDIA GeForce 6150 Shared Video Memory (UMA)). You are using the integrated video card? It has two PCI slots so another possibility would be that you use a video card that is in one of these slots?
Both slots are empty so I guess this means I'm using the integrated card , yes ? So what kind of card should I get for testing ?

---

### Post by Dimarchi on 2010-06-18
> **spibou said:**
> Still , it sounds strange that with memory I would get no beeps and without memory I would get beeps not for the memory but for the video card. By the way , I tried a new memory chip and when it's connected I get the same symptoms as in my opening post. So I guess this rules out a memory problem , right ?


So how do the computers without the graphics card communicate with the world ? Because one of the problems in my case is that the computer isn't really giving me much information as to what's wrong. 

I wasn't thinking about powerful display capabilities but that it would be convenient if the computer would still be able to display some error message on the screen even if the graphics card is broken.

Both slots are empty so I guess this means I'm using the integrated card , yes ? So what kind of card should I get for testing ?

I would say it rules out the memory problem. Computers without graphics cards communicate with the world by whatever means that are available to them - usually this means a network...it could be other things, too...or not at all: they are there just to store data to be retrieved later by some means built to them. Computers may have other ways to display error data, or not at all - it depends on the manufacturer, among other things.

Yes, you are using the integrated video card. The slots in that particular motherboard are PCI slots. Not AGP, nor more modern PCI-E. Therefore you should look for a PCI video card, if such a beast even exists today somewhere. PCI slots are found even today in motherboards, though...AGP was meant to be a dedicated video card slot (old standard), and PCI-E (newer standard) seems to have taken AGP's place. Very few manufacturers make AGP cards nowadays. More knowledgeable people can chime in on this one if they wish to. So...look for a PCI video card.

I would strongly recommend a visit to a computer repair shop with that thing if you can afford it and are able to do so. For all our so-called knowledge and the best of intents we could be giving you totally wrong information.

---

### Post by spibou on 2010-06-19
> **Dimarchi said:**
> So...look for a PCI video card.

I would strongly recommend a visit to a computer repair shop with that thing if you can afford it and are able to do so. For all our so-called knowledge and the best of intents we could be giving you totally wrong information.
I will look into the possibility of going to a repair shop but I have another question: will *any* PCI video card do ? I mean does the motherboard know how to use any PCI card to display information on the screen ? Is it not an issue of having the right drivers or something ?

---

### Post by Dimarchi on 2010-06-20
As far as I know, any PCI video card will do. There is a basic VESA driver in Ubuntu (and other distributions) that video cards have access to when they don't have any other driver. It should be installed by default. All video cards follow certain standards, and VESA is one of them. You should see *something* displayed on the screen, therefore.

This is one reason why some of us in the thread have been suspecting the fault is in the video part of your computer, along with the beeps: you don't see stuff on the screen.

A Google search with "pci video card uk" should provide some advice, and perhaps pointers to where to obtain one. The cheapest possible will do for testing purposes.

---

### Post by cuberts on 2010-06-20
> **spibou said:**
> When I tried to turn on my computer yesterday the light went on and the processor fan started working but nothing beyond this. In particular there was no beep. I tried turning it off and on a few times but it was always the same. Another thing was that if I turned the electricity off from the plug and turned it on again the computer came on without pressing the on button. It didn't used to be like this.

I opened the case but didn't remove any components and as far as I can tell nothing  seems out of the ordinary; no loose cables and no leaking capacitors. The power unit fan is also working.

The computer was working fine until the day before yesterday when I turned it off normally. Any suggestions on how to proceed ?I'm affraid that your hard drive or even your computers mother board might have been damaged somehow. Also I heard that there is a computer virus which when you try to turn on your computer, it automatically shuts down. First things first just disconnect it from the network, and get a new computer. I'm sorry but if you cant turn on your computer there will be no way of restoring the lost files.

---

### Post by Chocrates on 2010-06-20
> **Dimarchi said:**
> And nowadays the video card capabilities are going back to CPUs (I believe Intel has such at the moment, AMD to follow soon).  
Not entirely true.  Video cards are moving towards being on the same die as cpu's therefore elimnating the bus and allowing video cards and processors to talk to each other a lot faster.

[QUOTE=cuberts]I'm affraid that your hard drive or even your computers mother board  might have been damaged somehow. Also I heard that there is a computer  virus which when you try to turn on your computer, it automatically  shuts down. First things first just disconnect it from the network, and  get a new computer. I'm sorry but if you cant turn on your computer  there will be no way of restoring the lost files.[/QUOTE]
i've heard of rare bios virus's but i assume that your bios would still display something.  This doesnt sound like a virus, but even if it was, he could recover his data with an external drive and a live cd, or plugging the drive into another computer.

I would suggest doing what has been said already, buy a really cheap pci graphics card, or even going to a repair shop and asking if you can borrow one.

---

### Post by spibou on 2010-06-21
> **Dimarchi said:**
> As far as I know, any PCI video card will do. There is a basic VESA driver in Ubuntu (and other distributions) that video cards have access to when they don't have any other driver. It should be installed by default. All video cards follow certain standards, and VESA is one of them. You should see *something* displayed on the screen, therefore.
Thank you , you are a source of very useful information.
> 
This is one reason why some of us in the thread have been suspecting the fault is in the video part of your computer, along with the beeps: you don't see stuff on the screen.
In a situation where the processor is damaged but everything else, including the video card, is working would one expect to see something on the screen ?

---

### Post by spibou on 2010-06-21
> **Dimarchi said:**
> As far as I know, any PCI video card will do. There is a basic VESA driver in Ubuntu (and other distributions) that video cards have access to when they don't have any other driver. It should be installed by default. All video cards follow certain standards, and VESA is one of them. You should see *something* displayed on the screen, therefore.
But the hard disk is not connected so whether Ubuntu has a driver is not relevant. I was asking whether the motherboard knows how to use any PCI video card to display "No operating system found" or something to that effect.

---

### Post by Dimarchi on 2010-06-22
> **spibou said:**
> Thank you , you are a source of very useful information.

In a situation where the processor is damaged but everything else, including the video card, is working would one expect to see something on the screen ?


Offhand, that I do not know. I would suspect that there would be. Error codes or such.

---

### Post by Dimarchi on 2010-06-22
> **spibou said:**
> But the hard disk is not connected so whether Ubuntu has a driver is not relevant. I was asking whether the motherboard knows how to use any PCI video card to display "No operating system found" or something to that effect.

Yes. Or to be more specific, certain values of affirmative. ;)

I have been in that situation myself, and seen it happen (the price you pay for tinkering too much, sometimes :P). However, whether it works that way in every computer setup in the world, that I can not say. It would stand to reason that it does, but who knows what manufacturers are up to when it does not.

---

### Post by jwbrase on 2010-06-22
> **spibou said:**
>  Another thing was that if I turned the electricity off from the plug and turned it on again the computer came on without pressing the on button. It didn't used to be like this.

If the way the computer behaves when you connect/disconnect the plug has changed, this would suggest a power-supply problem to me. But one generally does not turn a working machine on/off by manipulating the plug, so it may be correct behavior that just seems strange because you don't trigger it in normal operation. Also, if it correctly detects and beep-codes the presence/absence of RAM, this would suggest that it's getting far enough in the boot process to do so, which would say that it's probably not a power supply problem.

---

### Post by spibou on 2010-06-28
> **Dimarchi said:**
> 
[quote=spibou;9490249]In a situation where the processor is damaged but everything else, including the video card, is working would one expect to see something on the screen ?
Offhand, that I do not know. I would suspect that there would be. Error codes or such.[/QUOTE]
So I take it the motherboard does not use the processor to execute the motherboard's firmware?

---

### Post by spibou on 2010-06-28
> **jwbrase said:**
> 
[QUOTE=spibou;9409764]Another thing was that if I turned the electricity off from the plug and turned it on again the computer came on without pressing the on button. It didn't used to be like this.
If the way the computer behaves when you connect/disconnect the plug has changed, this would suggest a power-supply problem to me. But one generally does not turn a working machine on/off by manipulating the plug, so it may be correct behavior that just seems strange because you don't trigger it in normal operation. Also, if it correctly detects and beep-codes the presence/absence of RAM, this would suggest that it's getting far enough in the boot process to do so, which would say that it's probably not a power supply problem.[/QUOTE]
I need to clarify some things. First, in the U.K. power plugs (on the walls) come with a switch so if you want to turn off the power supply to a device you don't have to actually unplug it , you just turn off the plug switch. For a photo see [here](http://files.turbosquid.com/Preview/Content_2009_09_28__09_40_49/Uk%20Wall%20Plug%20twin.jpg4a0e7cca-21ac-41fb-b7ca-895df171d486Large.jpg). Whether the earthing also gets disconnected when the switch is in the off position I don't know. 

When I want to turn off the computer I first press the computer's off button (I would never just turn off the electricity to an electronic device if I can avoid it) and when it goes off then I also turn off the plug switch. I haven't actually unplugged the computer at all. Turning off the computer works as it used to. When time comes to turn it on I turn on the plug switch. Before the computer stopped working the next step would be to press the computer's on button. But now when I turn the power on from the plug then the computer automatically goes on without pressing the computer's on button.

---

### Post by spibou on 2010-08-17
In the end I took the computer to a repair shop. They told me it was the motherboard. I guess that explains the strange behaviour with regards to the beeps. I bought a new motherboard and now I have a working computer again.

There was a slight twist though : a few days after I got the computer back from the repair shop I saw that the processor was an Athlon whereas when I had taken the computer to them it had a Sempron ! I had to go back and they found my Sempron. It might have been a honest mistake or they might have replaced a Sempron which was working with an Athlon which wasn't working. At the time I noticed I was waiting for a new CPU fan so I couldn't test it. The moral of the story is if you take your computer to a shop for repair make a note of the codes on the various components so that you can verify that what you get back is what you took to them.

It's also worth knowing that the Asus M2NC61P motherboard does not produce any beeps and does not show anything on the screen if a processor isn't connected.

---

