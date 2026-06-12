---
title: "CTRL-ALT[LEFT] &amp; [RIGHT] not working to change workspace"
date: 2009-10-23
forum: General Help
---

### Post by pokeyoats on 2009-10-23
Hi all,

I have just installed Ubuntu 9.04 under VMWare Workstation 6 and everything is going well, even the installation of VMWare Tools (after I alien'ed the .rpm package).

My only problem is that CTRL-ALT Left and Right is not changing my workspace and I am unsure how to fix it (I have only used Ubuntu on a straight system where Compiz worked and under VMWare it's not giving me my usual options.

CTRL-ALT-UP and then ALT Left and Right IS allowing me to change desktop, but I'd really like to be able to use CTRL-ALT Left and Right again to jump between them.

Any help would be greatly appreciated.

Thank you kindly.

---

### Post by Cuddles McKitten on 2009-10-23
System -> Preferences -> Keyboard shortcuts

Switch to workspace on the left/right/above/below of current workspace
They're under "Window management."

---

### Post by pokeyoats on 2009-10-25
Thank you so much for your kind reply, it was wonderfully helpful and spot on.

I noticed, in looking at the keyboard preferences that it is now ctrl-alt-shift left and right etc. I wonder why the change.

Now I am not sure whether I want to leave it at that and learn the new methodology or change it back to the way I was used to before.

Irrespective of my indecisiveness I am very grateful for your answer!

---

### Post by P4man on 2009-10-25
ctrl alt left/right is still the default and should still work unless you changed it, with or without compiz. 

That said, i do vaguely recall reading something about it and VMware. Is it possible VMware uses those keys?

---

### Post by pokeyoats on 2009-10-25
Oops, I was wrong.

Because I'm using VMWare it seems I have to use ctrl-alt-space and then left or right.

A tad inconvenient, but oh well, I'll survive.

Again, thanks for all the help!!

---

### Post by pokeyoats on 2009-10-27
Yupppers,

In the end it was indeed VmWare.

Even though I have VMTools running and don't NEED to use the ctrl-alt key to get the mouse out of the window, Workstation was still checking for it.

I changed the VMWare focus keys to ctrl-shift and now I can change between desktops easily the way I remember!: )

Thank you everyone for your help, it is really appreciated!

Now if only I could get the same level of help with this tooth that just fractured, is hurting like a ... and is going to cost me a fortune to get fixed :(

---

### Post by P4man on 2009-10-28
Cant help with the tooth im afriad.. but is there any reason you're using VMware instead of VirtualBox ?

---

### Post by theozzlives on 2009-10-28
Is your mouth running Windows or Ubuntu? haha... But seriously, I can't speak for VMWare but VirtualBox uses the right ctrl key as the home key. I changed mine to the left Super Button and everything runs just just fine.

---

### Post by pokeyoats on 2009-10-28
> **P4man said:**
> Cant help with the tooth im afriad.. but is there any reason you're using VMware instead of VirtualBox ?

Eek, I am so petrified about the upcoming Dental appointment :(

Predominantly I am using VMWare because of the extremely frustrating job market. In the world of keyword search Resume's keeping up with VMWare and being able to answer an HR persons rapid fired acronym test is the predominant reason.

Is it true that Virtual Box does 3D emulation now, so you can have the cube working under emulation? If so, that's ever so very tempting!!

---

### Post by P4man on 2009-10-28
> **pokeyoats said:**
> Eek, I am so petrified about the upcoming Dental appointment :(

Predominantly I am using VMWare because of the extremely frustrating job market. In the world of keyword search Resume's keeping up with VMWare and being able to answer an HR persons rapid fired acronym test is the predominant reason.

Is it true that Virtual Box does 3D emulation now, so you can have the cube working under emulation? If so, that's ever so very tempting!!

Virtualbox has experimental support for 3d acceleration, but Im not sure if it works in "either direction". I run windows as a guest OS under Ubuntu, not the other way around. That said, its not very good or stable the way I use it. I have no idea if its good enough the other way around to enable compiz. Find out :) Or better yet, install ubuntu natively and spin your (virtualized) windows on your cube. That works very well ;)

---

### Post by pokeyoats on 2009-10-29
I'm sure you will all hate me saying this but running Ubuntu, or any Linux alone, absolutely not; quite frankly it just has too many problems.

For example, Ubuntu 9.04 appears to be the FIRST Ubuntu that doesn't cause my Logitech MX3200 mouse to lock up. I begged and pleaded on these very Forums for help on the matter and the FINAL response I was left with was "Buy a compatible mouse and keyboard".

And then I said, what about Video chat, so I can talk with my wife whilst she's away - answer, nope, not supported yet; neither was my USB webcam.

I do however have an Ubuntu partition and use grub to multi-boot, and I had my desktop configured just right with all my screenlets and configs the way I wanted, then I did the "unthinkable".

I had one nVIDIA card (my motherboard supports SLI) and when I got the cash together, I added a second identical card for SLI, booted into Ubuntu and KAPOW, BAM, no more GDE.

I've been using Linux for a log time, since the days you had to recompile the kernel with a series of yes/no answers and when it was required for IP Masqing as home routers weren't readily available and I've got to say, running it virtualized is the safest most painless option I have found.

---

