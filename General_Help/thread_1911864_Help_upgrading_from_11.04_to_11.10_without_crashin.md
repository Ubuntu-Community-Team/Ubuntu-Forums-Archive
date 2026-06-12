---
title: "Help upgrading from 11.04 to 11.10 without crashing"
date: 2012-01-19
forum: General Help
---

### Post by tim_norman2003 on 2012-01-19
hi guys.
im not a new ubuntu user, its been my only OS for 2 years now, however i dont know much about the details of it.

yesturday i decided to upgrade my system from 10.10 to 11.10.
going to 11.04 was fine, and I went to bed leaving the system updating from 11.04 to 11.10. when I woke up, I restarted my machine, and then booted up. (I had dual boot, as I had an old windows OS on my computer too) when I selected to choose Ubuntu, as I have been doing for 2 years it didn’t let me, instead it came up with a black screen and a flashing '_' in white, in the top left. I restarted, after 10 or so minutes of flashing, and tried to log on with the recovery mode, the same thing happened. the only way I could log on was to select 'previous versions' I did this, and logged. I was using my computer fine for around half an hour (it was the 11.10 OS) I was installing some software, nothing major, just little widgets etc., like docky, and all was fine, however for one bit I needed to log out then back in. when I hit log out, the screen froze, it was black, with some bios looking green / blue horizontal stripes along the width.

after that I had to restart my machine again, and I could then no longer log on to any of the versions of Ubuntu I had on the system, just got the flashing '_'

I went to my library and downloaded  10.04 and 11.10 onto separate DVD-Rs so I could do a clean install on my machine. it wasn’t a big deal to me, just annoying and time consuming, as I don’t keep much data on my computer.

I first tried to install 11.10. it didn’t work, the first purple screen, with a small graphic at the bottom came up but then the next screen was just a big lot of bios, none of it making any sence. this screen didn’t go away by its self (I left it for 40 minutes) I tried again, but nothing.

to round the story off, I successfully installed 10.04 from the DVD, and since then I have manually upgraded to 11.04.

I do however want to get back to 11.10. I no longer have a partition, its only Ubuntu now on my computer.
my computer isn’t excellent, however it should be good enough to run it hardware wise its got:
2.56gb RAM
3ghz processor
nVidia GeForce 6200 graphics card.

like I said, my whole computer is much cleaner now, so that may help. (ive been wanting to get rid of windows for a while, I never use it)

do you think it was just a freak one off, or if I try and upgrade to 11.10 will it happen again? have you ever heard of this happening to anyone else ? any ideas what caused it, ad how to prevent it happening again ?

please help me !!
I’m happy to answer any further questions, and give more details (thought I would try and keep this short...ish though)

all advice is much appreciated !

Tim

---

### Post by Fernhill Linux Project on 2012-01-19
We have not experienced the problems you described.
A clean install would be a better option than upgrading. 
Upgrading 11.04 to 11.10 is not recommended as many people have had problems.
Will 11.10 boot, run or install from the live disc now?
I would not try upgrading or installing until you know that 11.10 works from the live disc, and you might want to try downloading the iso again and checking the md5 sum if it fails.

---

### Post by tim_norman2003 on 2012-01-19
hi, thanks for your quick reply.

i tried using the 11.10 disk again, i can get as far as the menu, however from there, either selecting run via cd, or installing will give me the same bios screen, and ill have to restart.
i tried re downloading and burning 11.10 to a DVD, but i have the same result.

i took a pic of the BIOS screen, (i cant upload it unfortunately cause my phone is very old.) the last line of the bios is:

kernel_thread_helper+0x6/0x10

there are some other bits about kernels, acpi processors, devices and bus registers and a load of other stuff if any of that helps.

how do i check the md5 sum ?

Tim

---

### Post by tim_norman2003 on 2012-01-19
-                               bump                              -

---

### Post by DevinMcElheran on 2012-01-19
I would say to give the alternative installation a shot. It's very old looking, but it's very reliable. It's purely text, but you don't need to know any commands. I feel like you might be having an nVidia problem. It seems like your x server is crashing. I don't know what to suggest other than that and to boot into CLI the first time to update/upgrade all your packages. That usually solves the small things. Maybe there's something in the nouveau package that's preventing your x from running properly. So I would suggest the alternative installer because it doesn't rely on x, and then update/upgrade everything from CLI on first boot. Then try to boot up normally. If that doesn't work, remove the nouveau kernel module or blacklist it until you find another fix, possibly the actual nVidia driver from the website. I hope that helps.

---

### Post by tim_norman2003 on 2012-01-20
okay, thanks. could you tell me how to do that in layman's terms please, and ill give it a try ?

Tim

---

