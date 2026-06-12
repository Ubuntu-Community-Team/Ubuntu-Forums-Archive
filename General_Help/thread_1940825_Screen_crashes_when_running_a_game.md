---
title: "Screen crashes when running a game"
date: 2012-03-14
forum: General Help
---

### Post by Psycho Game on 2012-03-14
First I'll explain the hardware I have.
My laptop is a Samsung NP300E7A-S01NL

Specifications                                        Product Description             
                              Samsung 17.3" NP300E7A-S01NL             
         
                                                         Screen              17.3" Widescreen (1600 x 900)             
         
                                                         Processor          Intel Core i5 2430M - 2.4GHz             
         
                                                         RAM                  6GB DDR3 (1x 4GB + 1x 2GB)             
         
                                                         Hard Drive         750GB - 5400 rpm SATA2             
         
                                                         Graphics Card    NVIDIA GeForce GT520MX - 1 GB DDR3             
         
                                                         Optical Drive      Dual Layer DVD-ReWriter             
         
                                                         Card Reader      4 in 1 (SD, SDHC, SDXC, MMC)             
         
                                                         Network            Gigabit Ethernet, 802.11b/g/n wireless, BlueTooth 3.0

The Nvidia card is build into the laptop with Opimus technology in combination with a Intel GMA video card.
To make use of the Nvidia card with games, I installed bumblebee.

Now I've had some strange crashes which I can't solve, and are reproducible.
When executing a program which is graphics demanding, like xonotic, the game starts but then the display crashes.
I get a screen with about 70% which is a black screen and the right side of the screen has strange colours. I'm not exactly sure how to describe it.
The game still runs in background though.
When pushing key combination CTRL - ALT - F1, it goes to terminal, but I can't see anything. Still the black screen with strange colors is visible.
Although I am able to reboot the computer with CTRL - ALT - DEL.
When the computer reboots the screen will flicker for some time, which slowly disappears again after some time. Hopefully somebody can help me with this problem, it's really annoying.
If some more information is needed, feel free to ask. Also if you want a picture of the screen I'll be able to post one.

Greetings Psycho Game

---

### Post by Mark Phelps on 2012-03-14
If you don't get any responses here, I would suggest you go to the Nvidia forums and post this there.  They probably have a LOT more experience with the detauls of using Bumblebee than here.

---

### Post by Psycho Game on 2012-03-14
You would think the problem is NVIDIA related, but I doubt that.
Because also when running the game in normal mode, without optirun that is, the screen crashes.
So what I think is that it's Intel related.
But that's my point of view of course.

Greetings Psycho Game

---

### Post by Psycho Game on 2012-03-15
Hello everybody,

I already solved this strange problem.
If anyone seems to have this problem as well, the solution is to use the xorg-edgers ppa and download the newest video drivers etc.
So I think it had something to do with the older drivers in the xubuntu 11.10 repositories.

Greetings Psycho Game

---

