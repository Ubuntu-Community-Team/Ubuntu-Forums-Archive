---
title: "Just me or is 10.10 lacking?"
date: 2010-12-29
forum: General Help
---

### Post by Trapper on 2010-12-29
I just did a U 10.10 i386 install and am experiencing many freeze up problems and it doesn't relate to running just any specific application(s). I have nvidia video but _am not_ utilizing nvidia's 3rd party drivers. 

I'll expound:

I already have an install of U 10.04 i386. It works just fine and as expected. I installed U 10.10 to it's own partition. My difficulties started just after the installation and updating. From U 10.10 I browsed to my U 10.04 home in nautilus, selected about 14 GB of files I wanted to transfer to the new install and copied and pasted them to my 10.10 home. After several hundred MB of transfer nautilus and absolutely everything else froze up solid forcing me to make a hard reboot. I tried the copy and paste routine again and got the same results. After a reboot I then tried to just transfer a couple of GB of files. Same results. I tried again. Same results. I then booted up U 10.04 and easily copied all 14 GB to my U10.10 home. No problems. No hassle. No freeze up.

Just for the fun of it I rebooted into 10.10, went to a storage partition through nautilus and attempted to copy several MB of files to my home folder. About half way through I encountered another lock up.

I also note that FireFox has locked up a number of times, as has Gimp, Shotwell, GFTP and Transmission. When the apps lock the entire system freezes up. Absolutely none of this is transpiring in U 10.04. Not even close. For all intent and purposes my 10.10 install is useless.

I'm just curious. Has anyone else been experiencing this lack of reliability in U 10.10?

---

### Post by Mark Phelps on 2010-12-29
> **Trapper said:**
> Has anyone else been experiencing this lack of reliability in U 10.10?

Yes ... I have ... and I made the mistake of daring to report that -- which resulted in so much bashing of me by the community, that I got the thread moved to Testimonials. And, to add insult to injury, someone else started a "counter" thread!

---

### Post by Trapper on 2010-12-29
Thanks for you information Mark. I don't feel alone now.

I, personally, have downloaded the iso again have burned it to cd and will be attempting another fresh install in a few minutes. I've also downloaded the dvd iso and if results from the cd install come up the same as before I will try a dvd install. What I do after that is dependent on the results I get.

One thing is for sure. This _is not_ a testimonial by any means. As of right now I have to consider that something is genuinely amiss in 10.10 that needs resolving on the development end. There are way too many people reporting various freeze issues in 10.10 for this to be an isolated incident.

I'm going to plug along and try to figure out if I can get a reasonable install working. In this case I _am not_ going to try and work around 10.10's issues. That's not what I should be doing. Previous versions of U work very well. I know it's not my machine and I know I have not done any adjustments that would create difficulties, nor have I installed any 3rd party software.

If anyone comes up with anything useful regarding this issue I would like to hear from them. I'll also update any progress I have made and any findings I have

.

---

### Post by requeth on 2010-12-29
I'm quite surprised by this thread. I had your issues with 10.04 and they were fixed in 10.10. I'm using a Gateway NV53 w/ ATI graphics. The only odd issues I have left in 10.10 are the occasional purple screen of death, and my Gnome status bar sometimes goes insane and stops functioning. PSOD's were more common in 10.04 then in 10.10 for me, and I'm fairly sure it's related to my graphics card.

I'd recommend trying the Nvidia proprietary driver, I find the prop's generally work better. Also note that Ubuntu doesn't update the drivers often, you can get much newer ones on the Nvidia website but then you have to manage it which is annoying.

For your file transfer, I've run into your issue a lot, where the application gets overloaded by too much data. I used to work on SAN servers and we'd have to move gigs/tera's of data. Have you tried Rsync? It's about the best app out there for moving data, and if it kills then you just add the sync flag to it and it'll pick up where it left off.

One thing that I think Linux in general is very lacking in is use able logfiles for crashes. Logs are great for stable systems, but like my purple screen of death? Not a single log to show that any problem occured. Annoying as hell. Microsoft always has one, though out of necessity(and I'm a bit spiteful having been a windows admin).

---

### Post by Cheetah1933 on 2010-12-29
> **requeth said:**
> I'm quite surprised by this thread. I had your issues with 10.04 and they were fixed in 10.10. I'm using a Gateway NV53 w/ ATI graphics. The only odd issues I have left in 10.10 are the occasional purple screen of death, and my Gnome status bar sometimes goes insane and stops functioning. PSOD's were more common in 10.04 then in 10.10 for me, and I'm fairly sure it's related to my graphics card.

I'd recommend trying the Nvidia proprietary driver, I find the prop's generally work better. Also note that Ubuntu doesn't update the drivers often, you can get much newer ones on the Nvidia website but then you have to manage it which is annoying.

For your file transfer, I've run into your issue a lot, where the application gets overloaded by too much data. I used to work on SAN servers and we'd have to move gigs/tera's of data. Have you tried Rsync? It's about the best app out there for moving data, and if it kills then you just add the sync flag to it and it'll pick up where it left off.

One thing that I think Linux in general is very lacking in is use able logfiles for crashes. Logs are great for stable systems, but like my purple screen of death? Not a single log to show that any problem occured. Annoying as hell. Microsoft always has one, though out of necessity(and I'm a bit spiteful having been a windows admin).

What ATI card do you have specifically? and how well does your computer run games? I am exeriencing the same problems as the original post, on an HP Envy 14, and on top of that, I can barely run games on my computer through WINE, and I have found no solution.

---

### Post by Frogs Hair on 2010-12-29
I think it is important to find out why 10.10 works great for some and not for others. If there is a real problem I would not want it to carry over to 11.04. 

I am using Nvidia recommended drivers , third party software and ppa software. So far 10.10 is the best of the three Ubuntu releases I've tried starting with 9.10.

---

### Post by coldraven on 2010-12-29
I was dual booting 10.04 and 10,10 64bit but found 10.10 so much better that I removed 10.04 completely.
The only problems I have is with Adobe Flash which will freeze up (grey screen) or with the newest version totally crash.
This is on a Compaq 6715b laptop, 2xTurion 2GHz, 4GB memory and the dreaded ATI X1250 video card.
I wish you luck, it seems that not all releases will work on all computers.

---

### Post by Trapper on 2010-12-29
Well, this is where I sit right now. I have both positives and negatives to report.

The negative:

I downloaded the CD iso again, it checked out okay, I burned it to disc and the burn verified okay. Then I did an install and then updates. After that I tried to transfer my 14 + GB of personal files from my u 10.04 install. I experienced the same freeze I experienced with the first install.

The positive:

I downloaded the DVD iso, it checked out okay, I burned it to disk and verified the burn. I then did a fresh install from the dvd and then updated. Next, with nautilus, I went to my U 10.04 and copied all 14+ GB of personal files to 10.10 easily and successfully. I've done test runs of FireFox and then test runs with FireFox and the flash plugin. I've experienced no lockups at all. The same holds true for other apps that were having difficulty. It's still early but I can already tell things are working normally now.

Now I am perplexed. My understanding is that the cd and dvd install are actually the same. There's more available on the dvd disk but the install routine is the same. That's my assumption but maybe that's not completely so. Whatever, if someone's having the difficulties I've experienced with a cd install perhaps they should try a dvd and see what happens. I'm surely not saying this is a fix or even what's actually being fixed. I'm just saying it's working for me.

I'm going to leave this thread unresolved until I am satisfied that my problems are resolved. Comments have been and are appreciated. Thank you all.

---

### Post by Trapper on 2010-12-31
Well, I have done some pretty heavy testing of this 10.10 install off of the dvd and everything works like a charm. I have experienced absolutely no freezes or anything else abnormal, for that matter.

I still have absolutely no idea why the cd installs were not working for me. All I know is that all is okay now and I am going to mark this thread as resolved.

---

### Post by Trapper on 2011-01-10
I am reopening this thread because my system has started to completely freeze again any time I copy and paste or cut and pasted anything over approx. 300 MB to a mounted partition other than the partition my home is mounted on. USB drives, my storage partition on the hard drive, etc.

As previously, I can go into 10.04 and copy everything easily but in 10.10 my system freezes at about 200-300 mb of transfer.

 ?????????????????????????????????????????????????????????????????????

We move a lot of information here through nautilus. U 10.10 has not been up to the task so I guess we will be forced to go back to 10.04. Going back with anything always sucks.

---

