---
title: "Issues That Have Come Up Already in Oneiric Ocelot"
date: 2011-10-23
forum: General Help
---

### Post by Jaybyrrd on 2011-10-23
Ok so I have two of, what I hope are, simple issues. Before starting here are my system specs which should prove to be more than adequate:

AMD Phenom II AM2+ Quad Core Processor 3.0 GHz
4 GB DDR2 Kingston RAM (2 * 2GB)
Asus M3N78 Pro Motherboard
nVidia 9800 GTX+ Video Card by EVGA
2 Hard Drives, 1 320 GB, 1 1 TB
CD Drive (of Course)


First when I click and drag a window there is a major lag type issue where the window kind of skips around and the movement is extremely jittery. The windows simply skip around like mad men and the mouse never stays in line with the bar that I click to start dragging. I don't think this is an issue with needing better hardware.

Second alt-tab does not work at all. It is almost as if the computer does not recognize the alt buttons at all. When I was running 11.04, it recognized them as "Mod5" and so instead of fixing it, I simply changed all my hotkeys to for example Mod5+Tab, but now I don't know what to do. 

Thanks.

---

### Post by westie457 on 2011-10-23
Hello.

The first issue is one or both of two things. Graphics card drivers are not installed properly. I am no expert on these, take a look at this thread [http://ubuntuforums.org/showthread.php?t=1743535&highlight=nvidia+drivers](http://ubuntuforums.org/showthread.php?t=1743535&highlight=nvidia+drivers) for some ideas. It is a long one so will take some time to check. Or if your mouse is not an optical mouse the ball needs cleaning. On the other hand the mouse could be dying.

Absolutely no help from me with the second issue.

---

### Post by Jaybyrrd on 2011-10-23
Thanks for the reply Westie. I did some digging, messed with xmodmapping.. Really it messed with me, and have fixed my alt issue. However the graphics card issue still stands, I am about to visit the thread you gave me and I will edit this post with any updates.


Ok so I have tried to follow the instructions to the best of my abilities and I am left rather confused and I think it functions worse... :( Any other suggestions?

---

### Post by zero2xiii on 2011-10-23
> **Jaybyrrd said:**
> Thanks for the reply Westie. I did some digging, messed with xmodmapping.. Really it messed with me, and have fixed my alt issue. However the graphics card issue still stands, I am about to visit the thread you gave me and I will edit this post with any updates.


Ok so I have tried to follow the instructions to the best of my abilities and I am left rather confused and I think it functions worse... :( Any other suggestions?

If it is a nvidia driver issue, sit tight for a while. The newest drivers is not functioning properly. I had them on 10.04 and 11.04 and they gave me more headaches than running without them. If you cannot turn of the effects (trough compiz or another method perhaps) try installing the older 270.41.06 drivers manualy (aka download them from nvidia and install via rescue mode)

Good luck with this. PM me for more detailed instructions on doing this manualy, I am not sure if forum code allows me to post that "advance" things in normal posts, if I am allowed, I will post it here :)

Cherz

---

### Post by Jaybyrrd on 2011-10-23
I wish I had received that earlier. I followed the instructions on installing the newest driver from nVidia's site and all the occurred was that the boot would hang at Stopping Userspace bootsplash. So I went to a friend's house burnt a livecd and did some working on moving personal files from my hard drive with the install on it to my secondary terabyte drive. After doing so, went through a clean install of Oneiric Ocelot and now with the Propriety drivers all is well. 

Moral of the story: Back up all personal files so that you can start over anyways, at least this way you won't spend all day trying to figure out how to not start over and you go ahead and get it over with. (Moments like this kind of make me miss Windows)

Haha, all is good though, I am learning a ton everyday. ;):D:p:p

---

