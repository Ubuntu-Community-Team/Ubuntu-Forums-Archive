---
title: "Utterly new to linux systems."
date: 2009-11-11
forum: General Help
---

### Post by ShiftSide on 2009-11-11
So my journey starts with the want for a low end gaming PC, primarily to play World of Warcraft and to surf the Internet. I'm a college student about to graduate in a few weeks, and I'm on a pretty strict budget. I set up a 400 dollar system (no monitor or operating system) and I'm trying to find a way to squeeze every last ounce of power with what little money I have.  I would consider myself someone computer competent, but I have zero experience with Linux operating systems. Let me also say that I've scoured these forums and google searches looking for answers before embarrassing myself in front of all of you, but many of the topics and results were unrelated or over my level of understanding. Now that you know some general information, here's the fun part- my plethora of nooby questions that everyone's sick of seeing.

First and foremost- Can Ubuntu be installed onto a completely blank hard drive? 

I've seen posts about partitioning hard drives of windows systems so that Ubuntu can be ran, but I was considering installing and running only Ubuntu as it would save me $100 by not purchasing Windows. Not only was I interested in saving money, I've heard tons of great things about Linux OS's and have seen that people run World of Warcraft better on Linux.

Second: Can CPU's be over-clocked on Ubuntu? I guess I know the answer is yes, but is it as simple as on a windows system? I guess I just need to read up on over-clocking and get an understanding of it's basics. 

I guess those are my questions as of now. I really should get back to studying for my final exams. I would like to say thank you in advance for everyone's time and patience. If someone could link me to any information a newcomer would find useful that would be great! Thanks and good day.

---

### Post by Neezer on 2009-11-11
CPU's are overclocked from the BIOS, not the operating system, So yes you can OC a CPU that runs Ubuntu. The problem you are going to run into is the to OC a system, it helps a lot to start out with high quality RAM and Motherboard. for the type of budget you are on, I would doubt that you OC much and still be stable. You also need to spend extra on aftermarket cooling for your CPU. When you OC the CPU it puts out more heat than the stock heat sink/fan are designed to deal with. This adds ~50 bucks to the operation as well.

I also want to be clear that Ubuntu won't run most windows games. You are going to have to use WINE or some other option to run windows games in Ubuntu.

---

### Post by Veovis Muad'dib on 2009-11-11
To answer your first question:  Yes.  In fact, the reason you never see tutorials on how to do it is because it's amazingly easy.  There's an option when you get to the partitioning stage where you can choose to "Automatically use entire disk" or something like that, I forget the exact wording.  I would suggest that if you're new to Linux.  There is also a manual method if you'd like to play with things, but again, I recommend the automatic method.

As for games, be careful.  Very few Windows games run well on Linux.  I know WoW used to run perfectly without any workarounds (Platinum rating in WINE), but last I saw the WINE (Windows emulator) compatibility list; WoW was moved to the gold list from the platinum list, which means that it works if you follow some workarounds.  I have never played WoW, so I don't know how hard it is, but just know that you could run into some problems there.  I recommend you install [Play On Linux]("http://www.playonlinux.com/en/") to help walk you through it.  Play on Linux is optional, but helpful, it is a frontend to [WINE]("http://www.winehq.org/"), which, to play WoW, is not optional.

EDIT: Apparently I took way too long, someone already hit this ^ point.  Oh well, it deserves to be emphasized.

For your second question:  Yes, they can, but you'll have to ask someone who actually does.  With my only machine being a laptop, I don't think I'll ever overclock it lol.

I don't really know any links for new users, but someone who frequents the forum more surely does, since it's a common request.

Good luck, and please post any questions you have either here, or on [IRC]("https://help.ubuntu.com/community/InternetRelayChat").  We'll be happy to help you out, if you aren't a [help vampire]("http://slash7.com/pages/vampires").

---

### Post by ShiftSide on 2009-11-11
Thanks for the help everyone! I can assure you that I'm not a help vampire :)

---

### Post by Swagman on 2009-11-11
re: overclocking

The old statement... ***"There is no replacement for displacement"*** always springs to mind

Meaning.. If you want to go faster... Buy a better engine !!

---

### Post by eriktheblu on 2009-11-11
What video card does your system have?

WoW these days can be a bit taxing on your system; I recommend a decent Nvidia card. ATI cards have notoriously bad Linux support. When I was using an ATI card, the game was barely playable (worked fine in XP, same machine). Switching to a not spectacular Nvida card produced dramatic improvement.

I too have seen some reports of 'better' WoW performance in Linux vs MS, but I suspect this is not truly the case. System resources aside, they *perform* about equally in my experience. In Windows however, the game is more stable (at least the game crashes in Linux are more predictable than the OS crashes in Windows). A machine running Linux *can* use less system resources than a Windows machine, so if you have limited system resources, it might work better. 

If you have such limitations, you might try a lighter weight distro than the regular Ubuntu (try Ubuntu first, and adjust if you get too much lag)

If you like the maximum graphics settings, you will find the shadow rendering is not the same. Windows can employ DirectX which can render shadows at the highest setting. Mac and Linux users have to use OpenGL which currently does not.

---

### Post by XCan on 2009-11-11
Overclocking is fine as long as you use common sense. As long as you don't increase any voltages, you would have to have seriously bad karma if you break something. Actually, the stock coolers on the "modern" CPUs (prescott not included of course) do just fine for moderate overclocking with no voltage bumps.

---

