---
title: "NEED HELP! critical temp prob."
date: 2006-04-19
forum: General Help
---

### Post by Blacktalon on 2006-04-19
Hello,

I just got a Compaq v2000 and loaded ubuntu breezy bager on it, and it starts up fine.  But it seems I am having a problem with it, every once in a while when I freshly start it up after it has even set for an hour or more I get an error like message saying "Critical Tempature (144 C)".....I know that can't be correct cause I had just started it, can anyone please shed some light on my problem.


Thanks,
Blacktalon 8)

---

### Post by jazzmuzik on 2006-04-19
Compaq v2000 is a laptop. I don't know laptops, but on a desktop if your cpu fan is not working or even if the heat sink is not FULLY touching the CPU you can get overheating in about 1 second after bootup. I just fixed a computer with that problem. I'd turn it on and immediately it would start beeping the overheating code. Here's what I did to fix it, and again, I'm not sure if this applies to a laptop:

1. Remove the CPU fan and heat sink and clean them thoroughly. I use a cheap 4" paint brush for dusting.

2. Remove the old silicone gel from underneath the fan and from the top of the cpu. That old stuff gets hard, so don't put your heat sink back on top of the CPU without a good cleaning.

3. Apply new CPU silicone gel (~$2 at Radio Shack) to the top of the CPU and reinstall the fan. Make sure the heat sink is fully seated on the CPU. 

I understand using a laptop on a bed can cause more heat than on a hard surface.

Also, make sure the fan is working properly. Those bearings go bad after a while. If you spin the fan with your finger it should move SUPER EASILY. Any binding indicates it's bad. Dust buildup can also block air flow.

---

### Post by amosbatto on 2006-05-10
Blacktalon,
I'm having the same problem.  I installed Ubuntu Breezy Badger for i386 on a Compaq Presario v2410.  The v2410 uses a Turion (AMD64) chip, but I decided to install 32bit on my laptop, because the AMD64 version of Ubuntu has a bug which makes it impossible to cut and paste plain text into an OpenOffice document.  On the 64 bit version of Ubuntu Breezy, I never had a problem with overheating, but with the 32bit version running on 64 bit laptop, I regularly have overheating problems.  It is really annoying.  Anyone have any suggestions?

---

### Post by amosbatto on 2006-05-10
Oh, I see the problem. I need to load the powernow module into the kernel.  Here are instructions:
[http://www.ubuntuforums.org/archive/index.php/t-3267.html](http://www.ubuntuforums.org/archive/index.php/t-3267.html)

---

