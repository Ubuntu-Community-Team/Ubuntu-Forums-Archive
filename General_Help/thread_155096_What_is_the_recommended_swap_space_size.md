---
title: "What is the recommended swap space size??"
date: 2006-04-04
forum: General Help
---

### Post by sands on 2006-04-04
I'm having 

intel P3
256mb ram
80gb hdd

What is the recommended swap space..
Presently im having 5gb swap..Is it ok??
Or shud I reduce tat??

---

### Post by ndhskp on 2006-04-04
[quote=sands]I'm having 

intel P3
256mb ram
80gb hdd

What is the recommended swap space..
Presently im having 5gb swap..Is it ok??
Or shud I reduce tat??[/quote]Way too much!  32 bit operating systems can only support a swap size of 2GB or 4GB I can't remeber which.  Set your swap size at most too 1GB.  If you do work with large files all the time, like many hundreds of megabytes in size then set your swap size to 2GB.  If you only work with files that are genrally small only a few dozen megabytes then you could set it too 500MB to 700MB.  Okay, 5GB is way excessive.

Larger files many hundreds of megabytes 2GB

few and or small files few dozen megabytes 500MB to 700MB

Also do not set your swap space smaller than 500MB as your memory is only 256MB.  500MB is about 1 half more than your memory and you need at least that much swap space in your case.

---

### Post by theycallmemorty on 2006-04-04
I think someone told me swap size should be 1.5 times the amount of RAM.  I could be wrong though.

---

### Post by sands on 2006-04-04
Thnx for tat...
So now I should shrink tat one..

---

### Post by ndhskp on 2006-04-04
[quote=sands]Thnx for tat...
So now I should shrink tat one..[/quote]Your welcome

---

### Post by johnnymac on 2006-04-04
I can echo.....swap space should be 1.5 to 2x your physical RAM up to 2GB of ram

---

### Post by John.Michael.Kane on 2006-04-04
Just add if you have 2gig of mem or more in your machine you can go swapless.

---

### Post by ndhskp on 2006-04-04
[quote=SD-Plissken]Just add if you have 2gig of mem or more in your machine you can go swapless.[/quote]Bad idea!  Never go without swap.  For example some of the full resolution photos taken by the Hubble telescope can easily consume 2GB of ram and 2GB of swap.  Always! Always! have at least some swap space set up on a computer.  Also the idea of swap being 1.5 to 2 times ram is a bit outdated.  Consider that if you have 2GB of ram that gives you way too much swap.  Always determine how much swap you need by how you will be using your computer or how you think you will be using your computer in the future.

I myself have 2GB of system memory and 2GB of swap as I like to work with full resolution photo's from the Hubble telescope.  And it's still not enough for some photo's.  Someday I plan on upping my system memory to the max which is 4GB.  If you have a 64 bit system and enough memory slots then you can go well beyond 4GB, lucky bastards.

---

### Post by John.Michael.Kane on 2006-04-04
ndhskp It's a bad idea for you. however it can be done, and i have done it. just cause you dont like it does not give you cause to call it a bad idea for everyone. going with out swap did not work for you to bad does not mean it would not work for others, and as i said before users can go swapless if they want to, and have enough memory.

---

### Post by ndhskp on 2006-04-04
[quote=SD-Plissken]ndhskp It's a bad idea for you. however it can be done, and i have done it. just cause you dont like it does not give you cause to call it a bad idea for everyone. going with out swap did not work for you to bad does not mean it would not work for others, and as i said before users can go swapless if they want to, and have enough memory.[/quote]Okay but your just asking for trouble.  Of course if your running a cluster machine a mainframe a super computer a distributed server system or other such special machines then swap space is another whole universe.  Those machines don't have an swap space in a conventional sense.  However last time I checked most home computers are desktop and laptops and for them to go without swap can literally cause the computer to grind to a halt or a program will simply terminate due to lack of memory.  Like I said your asking for trouble unless your a big iron operation.

Edit: Think of it this way, swap is insurance against the unknown future.

---

### Post by MetalMusicAddict on 2006-04-04
I have a gig in most of my machines. I have always set my swap to half my RAM with this setup and never had a problem. Even running games or large GIMP projects. Its what worked for me.

---

### Post by ndhskp on 2006-04-04
Okay I have thought about this some more and about what SD-Plissken said.  I have slightly revamped my point of view on this.

Swap is fundamentally insurance against an unknown future but if thats the case then why doesn't everybody max out their swap potential.  Managing swap size originally came about because of limited hard drive space.  Todays hard drive space is not the premium that it once was although in older computers thats still the case.  I think that managing ones swap size in this day and age is about human perception, meaning how much hard drive space are you willing to devote to laying down idle 99% of the time.  Swap most likely is unused in my guess about 99% or better of the time.  But it only takes a single desired action on the part of the user to bring the swap space to life.  

Most likely the computer system itself will dictate the limits of what the user is willing to push however many people from time to time will go slightly beyond if not more than what the computer is capable.  Also we have to consider misbehaving kernels and programs.  All kernels and programs in all os's will at one time or another misbehave and generate excessive ram output and so swap may be the saving grace for an user in the race to kill or terminate a misbehaving kernel or program.  Keep in mind that swap space on a hard drive grows in size much more slowly than ram chips.

Ultimately I think in todays computer landscape it comes down to human perceptions, emotions and gut feelings and the willingness or not to decide how much idle hard drive space to devote to insurance against the unknown future.

So in answer to user "sands" I would recomend you look at your computer and decide if hard drive space is at an premium and if it is manage it the best you can.  On the other hand if your like my mom's 80GB hard drive then only a small fraction is ever used and in this case hard drive space is not at a premium and hence a 2GB swap.

---

### Post by dcstar on 2006-04-04
[QUOTE=johnnymac]I can echo.....swap space should be 1.5 to 2x your physical RAM up to 2GB of ram[/QUOTE]
That is a now essentially obsolete canard that dates back from when RAM was an expensive commodity and it was found that the best compromise was to use an amount of (cheaper) slow disk based VM to get acceptable performance in most non-desktop Unix environments.

The amount - and type - of Virtual Memory that a Linux/Unix system requires is set by the actual tasks the machine should perform.

For an environment that runs mainly real time tasks - like a desktop environment where people require a fast responsive system - then you need as much fast VM as possible (and that means RAM).

For an environment where there are many processes loaded that are not real time (like a system running a mail server or other batch mode apps) then these will perform quite adequately in an environment with a lot of slow VM (not much RAM, lots of Swap space).

There is no set "rule" for Swap space in regard to RAM any more, you need as much RAM as you can to run all the real time applications you need adequately and then you need as much Swap to comfortably meet all of your total VM requirements.

If you have 2G of RAM your system will be as reliable as one with 1G of RAM and 1G of Swap, but it may work a bit quicker - but it also may not if you never get close to using 1G of VM anyway!

If you run high resource and memory hungry applications (like Graphic manipulation) that gobble up all of you available RAM, then all the slow Swap you add isn't going to make much difference into improving performance (once the kernel swaps out all the other processes anyway).

If there is any "Rule" for the average Ubuntu environment - one where most people run a browser, mail app and one or two other things simultaneously, it would be something along the lines of you probably need a minimum of 1G of VM, but you should probably also have at least 256K of RAM as with any less the swap will be hammered and the system will run slowly not matter how big the swap partition is.

---

