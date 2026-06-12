---
title: "Big showstopper bug, screen freezes after login"
date: 2009-10-30
forum: General Help
---

### Post by Rackstar on 2009-10-30
Hello,

I did a fresh install of 9.10 as the upgrade failed.. I actually did it twice trying to fix the current problem.

I will describe my problem the best I can, if somebody could help pointing me towards the right direction, so I can file a decent bug report that has chance of being fixed.

Sometimes (70% of the time) when I boot, everything is quite normal when I reach the login screen. But I can notice that I can't switch terminals anymore by pressing ctrl-alt-fX.

I still can enter my password, the animations are all ok. The login box disappears, but then the Ubuntu logo + throbber don't appear. I can still move my mouse. The only button responding is the power button, but shutting down also fails. I can do ctrl-alt-prt scr-reisub. Even if I try to shutdown before I log in, it fails.

Other thing I sometimes experience is, when I click on "edit connections" on the network-applet, the dialog box shows up, but I can't do anything in it. I don't know if it has something to do with it, but then I can't shutdown properly also. And almost guaranteed to have a problem while booting.

Which logs should I consult? This is the first time I experience such a big problem, I would like to fix it, but maybe I should go back to 9.04.

Help would very much be appreciated, if I should provide more information, please do ask.

Best regards.

---

### Post by Rackstar on 2009-10-31
Bump..

If somebody would be kind enough to help me out here. Please do.

---

### Post by Rackstar on 2009-11-02
Bump

---

### Post by P4man on 2009-11-02
you could check in /var/log/messages
Perhaps also post your dmesg output (as attachement pls)

The fact you cant edit network connections could be a result of whatever root problem you're having, but it might be interesting to disable any network cards you have (if its onboard, disable it in the bios if you can) and see if it changes anything.

---

### Post by Rackstar on 2009-11-02
Hi!

Thanks for taking time to help me on this.

The logs were to big to be attachments, so I uploaded them on my server:
[http://ninetynine.be/rfiles/messages.txt](http://ninetynine.be/rfiles/messages.txt)
[http://ninetynine.be/rfiles/dmesg.txt](http://ninetynine.be/rfiles/dmesg.txt)

But I have to tell I got these logs while having a successful boot (otherwise I wouldn't be able to post this...), I don't know how long back in time this goes.

I tried disabling the network card on my laptop, but I couldn't find much in the bios. I diabled "network boot" but that seems to be something different, (disabling network card as boot device)

EDIT: The hardware I'm running on is a Acer Aspire 9420 laptop.

Thanks!

---

### Post by P4man on 2009-11-02
the messages logfile contains messages from previous boots as well. And plenty of errors. I dont have time to investigate it properly now, Ill see if I can make sense from it tonight, but you may already want to check if there is  a newer bios  for your laptop and I would also run the memory test from the livecd as the errors you get there seem somewhat random on first sight.

---

### Post by Rackstar on 2009-11-02
I will do that, I'll post the outcome later. I do have the latest bios for my laptop.

Thanks a lot!

---

### Post by P4man on 2009-11-02
I see a lot of errors and warning all somehow relating to acpi, but im not knowledgeable enough to judge how serious they are and google searches dont provide definite answers. I would suggest opening a bug report so devs can have a look at it.

In the meanwhile you could try a few often used kernel boot options and see if it helps.

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

Id experiment with *napic* *nolapic* and *irqpoll*

---

### Post by Rackstar on 2009-11-02
Thanks for all your time and effort!

I ran the memtest for three hours. And this is the result: 2 errors were found, rather in the beginning of the test.

I do remember I did this test before installing karmic, and no errors showed then. Two errors on memtest, is this fatal? Or can this be explained?

After this test I was successful to boot 5 times, 6th time failed, 7th time is now. Which seems to be an improvement, and maybe this shows that it is memory related. (As the test does a lot of writes, which maybe sort of "reset" the memory, don't know)

But memory-related fault would explain why I had so much trouble installing karmic in the first place. (update failed, 64bit iso failed, first 32bit iso failed, installing through usb-key failed, only second download of 32bit version burned onto a cd worked)

But it does not explain why I had a rock-solid Jaunty. Although I upgraded one memory after installing Jaunty.

What do you think? Should I blame it on the memory and just get new ones, or should I still file a bugreport? I wouldn't like to waste precious dev-time :)

Thanks!

---

### Post by P4man on 2009-11-02
that definitely sounds like the problem.

---

### Post by Rackstar on 2009-11-02
> **P4man said:**
> that definitely sounds like the problem.

Is it smart to open up my laptop, get out the new memory, and running only 1gb ram now? Or would that violate garanty?

The hardware-guy, just opened it up at my place, and changed the memory, so I guess I can do the same thing? (I have experience with setting up desktops, but no experience with laptops)

---

### Post by P4man on 2009-11-02
> **Rackstar said:**
> Is it smart to open up my laptop, get out the new memory, and running only 1gb ram now? Or would that violate garanty?

The hardware-guy, just opened it up at my place, and changed the memory, so I guess I can do the same thing? (I have experience with setting up desktops, but no experience with laptops)

I cant see it violate you warranty. At least not in Belgium. As long as you do it properly and dont force the module out with a crowbar. If you want to play ultra safe, ground yourself or discharge yourself before touching anything inside the laptop (touch water tubes or something) to avoid damage due to static electricity. At the very  least dont do it on a carpet or something that could generate tons of static electricity. I never take any such precautions myself and in 20 years I dont think I ever damaged a ram module, but it can be done. Then again, yours is already toast...

---

### Post by Rackstar on 2009-11-02
Thanks!

I tried several boots with once the original ram (1gb) and the other time the new ram (2gb), both gave me freezes..

Is it possible that this comes from an error during the installation, caused by faulty ram? Or does an install checks whether the outcome is correct? (with checksums and such)

Your help is really appreciated, thanks!

---

### Post by P4man on 2009-11-02
> **Rackstar said:**
> Thanks!

I tried several boots with once the original ram (1gb) and the other time the new ram (2gb), both gave me freezes..


If I remember your logs correctly, didnt you have 3gb? So maybe 1 Gb elsewhere or soldered to the mb? Can you boot with neither modules?

> 
Is it possible that this comes from an error during the installation, caused by faulty ram?


I guess thats possible but it doesnt seem all too likely to me. Try a live cd perhaps?

---

### Post by Rackstar on 2009-11-02
Well, the 3gb was the 2gb and 1gb modules combined, I was using two modules.

---

### Post by P4man on 2009-11-02
> **Rackstar said:**
> Well, the 3gb was the 2gb and 1gb modules combined, I was using two modules.

ok. Well, test with a live cd and/or rerun memtest. Keep in mind its not necessarely the modules themselves that are too blame, it could be the ram socket (did you use the same for each module?) or the memory controller.

---

### Post by Rackstar on 2009-11-02
Yes, I used the same socket for testing. I will first test the other socket, then I will rerun the memtests for each module.

I'll get back to you as soon as I get results, thanks!

---

### Post by Rackstar on 2009-11-02
Wow,

Maybe we you got it! Memtests of both the modules passed when they were in the second socket.

I tried 13 boots (yea, supersticious :) ) and all worked without any problems.

I will try doing multiple boots a day, just to be sure. And because suspend/resume causes kernel oops since karmic (maybe this will be fixed also).

One little thing though: should I return my laptop back to Acer? (I did so a couple of months ago, and needed to wait a month as UPS lost my laptop first). And if so, how should I describe the problem?

"One of the memory-sockets sometimes fail during memtests"?

Or should I better invest in a 4GB module and let it be?

Thanks a lot man! I would never have thought it was the socket. Great diagnostics department here at UF ;) (Yea, watching House MD right now)

---

### Post by P4man on 2009-11-02
I guess we got lucky finding that. I hadnt really considered it myself until you mentioned both dims produced errors separately; bad slots arent nearly as common as faulty ram modules.

Now perhaps its just a problem of oxidation and cleaning the contacts with a rubber "gum" (=nederlands, dont know english word. eraser?) can fix it. But I wouldnt count on it.

as for the warranty; thats your call of course. I would send it back, because if the problem is in the memory controller or the motherboard, and not just the module holder then God knows what else will start failing later on when your warranty expired.

As for explaining it, sure just tell m like it is. Memtest fails with any module in dim slot A while it passes in dim slot B. It wont take them their top engineers to figure out they have to replace the mb. I would also lean on them and explain its the second time and this time you want to be sent a replacement laptop before you ship yours.

BTW, it seems as if you're not using windows. Did you apply for a refund? I got an acer laptop myself and was told to get a refund Id have to ship it at my expense, wait 2 weeks and then get it back with the sticker removed and a €60 refund (guessing UPS would cost about the same).

---

### Post by Rackstar on 2009-11-02
Haha, geen probleem met dat nederlands, belg of nederlander? :)

I didn't get a refund, I used the license for a desktop computer. I didn't know Acer gave refunds.

As for the warranty, I will first check if it isn't the new BIOS version that's giving me the errors, maybe I can change versions back or something. (I got the new version when I returned my laptop last time), hmm and as I come to think of it. Acer probably has only a standard warranty of 2 years, and I bought my laptop like 2 years and a month ago...

Thanks!

---

### Post by Rackstar on 2009-11-04
Hmmm, bad news,

I had the freeze again this morning. Didn't had any trouble this evening. Maybe it's not my ram?

---

### Post by P4man on 2009-11-04
Meh, what can i say? Maybe not, but you had memory errors before so that would still be the first think to check. Have it run memtest over night. Even if its not the dimms or socket it could still be any other hardware failure (memory controller, cpu, voltage regulators, whatever). Unlike a complex OS memtest is not very prone to bugs or compatibility issues. On proper working hardware is shouldnt generate errors - ever. Have it run for 12 hours.

---

### Post by Rackstar on 2009-11-04
Thanks for the fast response.

I will run the memtest tonight. But I'm thinking of reverting back to Jaunty, if it's the hardware, then problems should show up also. If not, I'm better of with Jaunty. But I would've liked to know what the problem was, to get it fixed by Karmic+1.

I'll post when I get more info.

Thanks!

---

### Post by Rackstar on 2009-11-07
Maybe this will help.

I was happily running Karmic, only Empathy, Firefox and Thunderbird were running. Then the freeze happened also. (I only had this a couple of times).

Symptoms:
- nm-applet showed icon of no connection, when I click it, nothing happens
- not able to switch terminals with ctrl-alt-f...
- able to use gnome, but with hick-ups. (When I open Terminal, it opens, but it doesn't respond)

As this happened somewhat isolated from the boot, maybe you can see what went wrong here. In the attachment are the messages, only the messages around the time it happened. (I also put last dmesg lines as attachment, but don't think there is something interesting in it)

Can you see what causes the breakage?

Thanks!

---

### Post by P4man on 2009-11-07
Im assuming you have currently no errors running memtest right?

 Id put it on launchpad so more knowledgeable people can check it out. I see errors which appear related to acpi still, but when I google them I get precious little, only this in fact:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1767713.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1767713.html)

which relates to standby/resume problems, but contains the same acpi error messages and interestingly on a similar machine (acer aspire 9300)

Aside from filing this on launchpad, perhaps you could test if you can boot with acpi disabled (acpi=off as kernel option). That will disable a lot of functionality related to powermanagement, it may even not boot, but could help narrow this down if it does work.

Another VERY long shot is trying this: edit
etc/modprobe.d/alsa-base.conf 
Comment out the last line which reads something like
options snd-hda-intel power_save=10 

Im suggesting this because thats a new option that enables the soundsystem to go in sleep mode if not used for some time and is known to cause problems on some systems, and because I see a few weird things in your logs related to the onboard sound. But like I said, its a long shot. Launchpad is your best bet I think.

---

### Post by Rackstar on 2009-11-07
> **P4man said:**
> 
 Id put it on launchpad so more knowledgeable people can check it out. I see errors which appear related to acpi still, but when I google them I get precious little, only this in fact:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1767713.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1767713.html)

which relates to standby/resume problems, but contains the same acpi error messages and interestingly on a similar machine (acer aspire 9300)


I also have that problem on suspend/resume. I get kernel oops when I resume. I already filed that on launchpad.. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417842](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417842)

I will investigate further, thanks for the tip for alsa, whenever it wakes up from sleep I hear a pop.

---

### Post by Rackstar on 2009-11-07
I posted my information on this bug report, it seems they are having the same troubles like I do:

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/344428](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/344428)

Thanks for all your time p4man!

---

