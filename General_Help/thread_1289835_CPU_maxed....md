---
title: "CPU maxed..."
date: 2009-10-12
forum: General Help
---

### Post by TheDeathly on 2009-10-12
Okay, well i decided to try linux on a live cd. Was pretty nice, liked it and decided to go ahead and install it. My friend was experienced so i had him help me, eventually we decided to upgrade to the newest version - 9.10 (beta)

All was good, im learning my way through terminal and then all of a sudden everything just gets laggy. and i look at my CPU and its always 50+ and it shows xorg taking up most of it. Since its in beta i thought it was to be expected but its just getting annoying. Is it a bug within xorg? i put a CPU meter on my bar and it shows 87% steady... Im no expert but that just doesnt seem right... Any ideas?

Computer Specs:
3.2 Ghz processor - Sorta duo core... one physical and one threading.
3gigs of ram
nvidia 6200 vid card.

with these specs i dont see why there is a problem with CPU of all things, on XP it was always 10 and under, i put on linux and its like 100%

---

### Post by ApEkV2 on 2009-10-12
Open system monitor and look under processes. Find any that use abnormal amount of cpu % 
(make sure monitor is the only thing running).
Then if you find one, end the process.
Sometimes Firefox does this when I close it (I then have to do manually end the process)

You could also use "top" in the command line to view current processes.

---

### Post by TheDeathly on 2009-10-12
> **ApEkV2 said:**
> Open system monitor and look under processes. Find any that use abnormal amount of cpu % 
(make sure monitor is the only thing running).
Then if you find one, end the process.
Sometimes Firefox does this when I close it (I then have to do manually end the process)

You could also use "top" in the command line to view current processes.

well, this is with pidgin and firefox up

gnome system monitor taking up like 50
and xorg at 20

---

### Post by ApEkV2 on 2009-10-12
Probably wouldn't want to end those.
Does restarting fix the problem?

Try "top" in the terminal and see what the top five entries are.

---

### Post by TheDeathly on 2009-10-12
> **ApEkV2 said:**
> Probably wouldn't want to end those.
Does restarting fix the problem?

Yeah, im a complete noob to linux, so i figured everything has a purpose unlike windows where i could end all of the <user> processes and nothing bad would come to it.

i have restarted and let it sit at login screen because i was eating for about an hour and i logged and within 5 seconds it was back at max.

---

### Post by Giblet5 on 2009-10-12
Are you demanding a lot:

Do you have a half-transparent movie playing on the desktop background?

Are you using a screensaver?

Are you watching flash movies in firefox?

All of these things will make xorg chew CPU, but they'll also chew CPU on Windows. Those things are cool (very) but there is a cost...

A "reasonable" xorg CPU utilization on a quad-core, overclocked, PC running lots of eye-candy is 2%-5% CPU.

---

### Post by TheDeathly on 2009-10-12
> **Giblet5 said:**
> Are you demanding a lot:

Do you have a half-transparent movie playing on the desktop background?

Are you using a screensaver?

Are you watching flash movies in firefox?

All of these things will make xorg chew CPU, but they'll also chew CPU on Windows. Those things are cool (very) but there is a cost...

A "reasonable" xorg CPU utilization on a quad-core, overclocked, PC running lots of eye-candy is 2%-5% CPU.

thats the thing, im not. i have a few effects on for compiz. no music playing, 2 tabs in firefox and pidgin. nothing that should eat my CPU like it is.

---

### Post by Slim Odds on 2009-10-12
> **Giblet5 said:**
> A "reasonable" xorg CPU utilization on a quad-core, overclocked, PC running lots of eye-candy is 2%-5% CPU.

With a good GPU (graphics card).

---

### Post by TheDeathly on 2009-10-12
> **Slim Odds said:**
> With a good GPU (graphics card).

exactly, my GPU sucks pretty bad, an old 6200 geforce

should i tune my effects down? (cries)

---

### Post by Giblet5 on 2009-10-12
What kind of CPU do you have? Single? Dual? Quad? What frequency is it running at?

Do you have errors at the bottom of /var/log/Xorg.0.log?

I get 3% utilization off of a 3.4Ghz quad core.

What GPU are you using and which driver version?

---

### Post by ApEkV2 on 2009-10-12
@ Giblet5, look at his first post.........a little harder




So it still does this even with everything closed or not?
Did you update everything after the installation, plus the graphics driver?

---

### Post by Giblet5 on 2009-10-12
> **TheDeathly said:**
> exactly, my GPU sucks pretty bad, an old 6200 geforce

should i tune my effects down? (cries)

That's one option.

The other is to do a lot of benchmarks and determine what that 6200 is bogging down on and try and address that problem in a way that the 6200 can handle well.

I've seen a determined person triple their apparent graphics performance using just configuration tricks in xorg.conf... They DID have a 6600GT though; a much faster card than the 6200.

---

### Post by TheDeathly on 2009-10-12
> **Giblet5 said:**
> What kind of CPU do you have? Single? Dual? Quad? What frequency is it running at?

Do you have errors at the bottom of /var/log/Xorg.0.log?

I get 3% utilization off of a 3.4Ghz quad core.

What GPU are you using and which driver version?

CPU is 3.2ghz - I have yet to figure out if its single or duo, all i know is theres a physical and threading processor and the system monitor shows 2 cpus.

for the log.. leme check - logs are empty

GPU - nvidia 6200 geforce, drivers im not sure 180 i think. im about to update to 185 from update manager theres about 100 updates, so im going to go ahead and do them and see if that happens to fix this problem.

---

### Post by Giblet5 on 2009-10-12
You say it was fine for awhile, then the CPU usage on xorg went up and stayed up. Is that correct?

Adding cpu/network/disk meter applets will dramatically increase the CPU utilization of xorg, but not THAT much.

Do you have xhost authentication wide open? Are you on a LAN where others might be screen-scraping your display?

---

### Post by TheDeathly on 2009-10-12
> **Giblet5 said:**
> You say it was fine for awhile, then the CPU usage on xorg went up and stayed up. Is that correct?

Adding cpu/network/disk meter applets will dramatically increase the CPU utilization of xorg, but not THAT much.

Do you have xhost authentication wide open? Are you on a LAN where others might be screen-scraping your display?
im pretty sure thats how it went, i never payed alot of attention to the CPU seeing as i wasnt lagging, im just assuming its low.

well, my friend helped me through getting setup, all i know is he installed ssh and a different vnc.

i dont know what xhost is and what is screen-scraping... sorry for the newbish questions >.>

-- just finished the 91 updates. lol

---

### Post by mick55 on 2009-10-12
In all honesty a linux noob shouldn't be using a beta version 
of anything.As you all know linux can kick you in the teeth at
any time regardless of your expertise.

Troubleshooting a beta may be pointless because the problem could
disappear completely with the next update, or it could get worse.

Since you just installed this, you might want to consider moving 
to something more stable, Like Ubuntu 9.04 or Linux Mint,
or waiting for the official release of Ubuntu 9.10.

Linux Mint is probably the perfect distro for noobs, it's Ubuntu
with all the multimedia codecs built in, and it updates a lot less
often, thereby eliminating a lot of woes.

I'm not trying to upset anyone with my comments, but by 
definition a beta is not ready for release and should only be
used for testing, not on a production machine.

Cheers and good luck
mick

---

### Post by TheDeathly on 2009-10-12
> **mick55 said:**
> In all honesty a linux noob shouldn't be using a beta version 
of anything.As you all know linux can kick you in the teeth at
any time regardless of your expertise.

Troubleshooting a beta may be pointless because the problem could
disappear completely with the next update, or it could get worse.

Since you just installed this, you might want to consider moving 
to something more stable, Like Ubuntu 9.04 or Linux Mint,
or waiting for the official release of Ubuntu 9.10.

Linux Mint is probably the perfect distro for noobs, it's Ubuntu
with all the multimedia codecs built in, and it updates a lot less
often, thereby eliminating a lot of woes.

I'm not trying to upset anyone with my comments, but by 
definition a beta is not ready for release and should only be
used for testing, not on a production machine.

Cheers and good luck
mick

well tbh the main reason i upgraded to 9.10 was so i could connect to my network drive, 9.04 wasnt working correctly with it. i dont mind using a beta release or 9.04 but then i have to re-do everything, and ive done this like 3 times by now.. ill look into mint though, thanks for the suggestion

---

### Post by Giblet5 on 2009-10-12
> **TheDeathly said:**
> well tbh the main reason i upgraded to 9.10 was so i could connect to my network drive, 9.04 wasnt working correctly with it. i dont mind using a beta release or 9.04 but then i have to re-do everything, and ive done this like 3 times by now.. ill look into mint though, thanks for the suggestion


Yeah... It's a lot easier and safer to troubleshoot a stable release problem than a beta release of anything.

Go with Mint or 9.04 and ask about the network drive problem, if you still have one.

---

### Post by TheDeathly on 2009-10-12
> **Giblet5 said:**
> Yeah... It's a lot easier and safer to troubleshoot a stable release problem than a beta release of anything.

Go with Mint or 9.04 and ask about the network drive problem, if you still have one.

with 9.10 its fixed. connected i 5 seconds. i guess ill bare through it, seeing as a stable release is being released this month correct?


anyways, i have  to go for now, so i wont be responding, anybody can feel free to suggest something though. =D ill check this in the morning.

---

### Post by TheDeathly on 2009-10-13
well, its sorta averaging about 50% and under... my computer was off for the entire night... i suppose ill bear through it and wait for a fix if there will be any... it doesnt really affect my performace, well sometimes. but in the end everything runs fine.

---

### Post by mick55 on 2009-10-13
I just saw this thread, it should be mandatory reading.

[html]http://ubuntuforums.org/showthread.php?t=1286309[/html]I buggered up my install of Jaunty a while back when i 
did an uprade-dist to Karmic Alpha 5.
I was eager to try the new features and threw caution to the wind.

I ended up with no xwindows and 2 days later running an
update installed the KDE desktop, which wasn't really helpful
because i was running gnome, and the CPU was at 100% use.

I was able to get everything working again but i learned my lesson.

Now if i get an urge to try a new distro, i do it on one of my old 
computers.


Good Luck
mick

---

