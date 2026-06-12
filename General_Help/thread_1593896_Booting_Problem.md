---
title: "Booting Problem"
date: 2010-10-11
forum: General Help
---

### Post by mateo124 on 2010-10-11
Okay guys I'm new here so I may not know as much as some of you do. Anyways, I had 10.04 I believe and I really don't use Ubuntu that often and have Windows 7 as my primary OS. I decided to boot into Ubuntu and it checked for updates, I said yes to all and it rebooted. Thats where it messed up. Now when I try to boot, it gives me my options: Windows 7 and Ubuntu as usual but once I select Ubuntu, it flashes a screen (I think it says unknown command, I might be wrong) and restarts again... and it keeps on doing the same thing over and over. Any ideas?? It doesn't even let me get into safe mode. Would I have to do a new install? I really don't want to do this so any help would be appreciated.:confused:

---

### Post by wilee-nilee on 2010-10-11
You need to confirm the type of  Ubuntu install, is this a wubi install?

---

### Post by mateo124 on 2010-10-11
Yes it was wubi, does that affect it any?

---

### Post by wilee-nilee on 2010-10-11
> **mateo124 said:**
> Yes it was wubi, does that affect it any?

Yes, it is important to know what bootloader is in the mbr, yours is MS I assume. Your first post could have had somebody offering fixes for a regular install rather then a wubi excursion. I am just not familiar enough with wubi to be of anymore help.

Not sure if it is helpful for the wubi experts but the bootscript in my signature gives you a lot of information and is worth posting, post in code tags as described.

---

### Post by mateo124 on 2010-10-11
Well I can't even get to the screen to choose what Ubuntu mode I want to load, so you don't have any idea what to do?

---

### Post by wilee-nilee on 2010-10-11
> **mateo124 said:**
> Well I can't even get to the screen to choose what Ubuntu mode I want to load, so you don't have any idea what to do?

Not without the bootscript, even then I can only look to see if the root disc is showing. I would post the script. To make code tags click on the # in the reply and put the text from running the script in between.

If this was a regular install it would be more straightforward. More people on the forum are familiar with standard installs. There are a few though that know wubi well so the wait is just a little longer at times.

---

### Post by mateo124 on 2010-10-11
Eh, thanks anyway. I decided to do a clean install of Ubuntu outside of Windows side by side with it. But now I have two questions. One iis how do I remove the Ubuntu that I installed with wubi and two, if you could point me in the right direction, how do I change grub so Windows boots first? Sorry that I'm like a major noob with this. Thanks

---

### Post by wilee-nilee on 2010-10-11
> **mateo124 said:**
> Eh, thanks anyway. I decided to do a clean install of Ubuntu outside of Windows side by side with it. But now I have two questions. One iis how do I remove the Ubuntu that I installed with wubi and two, if you could point me in the right direction, how do I change grub so Windows boots first? Sorry that I'm like a major noob with this. Thanks

Ubuntu wubi should be in its own folder in Windows and has a un-installer. Add remove is also another way, but look for the first option .

In your new install go to synaptic and in the search look for startup manager. This will allow you to set the default boot and time out.

Good luck you figured out the dual boot it sounds like your on your way.

---

### Post by Kelvin K on 2010-10-11
I too have this problem.

I have an Acer Aspire Laptop which came with Windows Vista Installed. I have been using Ubuntu on desktops and I like it and wanted to use Ubuntu on my laptop. I went to the Ubuntu website and got the then latest release 10.4.

I was unaware that the installer would install Ubuntu INSIDE windows using Wubi. All I knew was that my new laptop now ran both Windows Vista and Ubuntu. I was pretty happy :)

However along comes 10.10 telling me to upgrade and I blissfully follow the upgrade as I have made sure I update Ubuntu each day. O:)

Now I can't boot into Ubuntu (I get a very quick DOS like screen reporting some error or something and then the laptop goes back round to the start asking me which OS to boot up). The Windows boot up works fine but the Ubuntu option just puts me in this loop :( I believe that this is Wubi asking me what I want to boot. Till now I really hadn't any idea what Wubi was and was unaware I had it,:confused: it was just how my laptop booted up I always chose Ubuntu and just got on with replying to emails etc

I need to get my Ubuntu working with the files I have on the machine already. There's lots of data that I really really really do NOT want to lose. How do I get my Ubuntu working again Please help me.

---

### Post by bcbc on 2010-10-11
To get wubi booting again: [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

---

### Post by wilee-nilee on 2010-10-12
> **Kelvin K said:**
> I too have this problem.

I have an Acer Aspire Laptop which came with Windows Vista Installed. I have been using Ubuntu on desktops and I like it and wanted to use Ubuntu on my laptop. I went to the Ubuntu website and got the then latest release 10.4.

I was unaware that the installer would install Ubuntu INSIDE windows using Wubi. All I knew was that my new laptop now ran both Windows Vista and Ubuntu. I was pretty happy :)

However along comes 10.10 telling me to upgrade and I blissfully follow the upgrade as I have made sure I update Ubuntu each day. O:)

Now I can't boot into Ubuntu (I get a very quick DOS like screen reporting some error or something and then the laptop goes back round to the start asking me which OS to boot up). The Windows boot up works fine but the Ubuntu option just puts me in this loop :( I believe that this is Wubi asking me what I want to boot. Till now I really hadn't any idea what Wubi was and was unaware I had it,:confused: it was just how my laptop booted up I always chose Ubuntu and just got on with replying to emails etc

I need to get my Ubuntu working with the files I have on the machine already. There's lots of data that I really really really do NOT want to lose. How do I get my Ubuntu working again Please help me.

I would start your own thread with this information with the bootscript in my signature included. Things will probably happen quicker in that you can post, and have a according header.

If you look at this thread the problem was fixed by doing a regular install, there seemed to be nothing to be saved from the wubi.

bcbc is very good in this area, I would follow their advice.

---

### Post by mateo124 on 2010-10-12
> **Kelvin K said:**
> I too have this problem.

I have an Acer Aspire Laptop which came with Windows Vista Installed. I have been using Ubuntu on desktops and I like it and wanted to use Ubuntu on my laptop. I went to the Ubuntu website and got the then latest release 10.4.

I was unaware that the installer would install Ubuntu INSIDE windows using Wubi. All I knew was that my new laptop now ran both Windows Vista and Ubuntu. I was pretty happy :)

However along comes 10.10 telling me to upgrade and I blissfully follow the upgrade as I have made sure I update Ubuntu each day. O:)

Now I can't boot into Ubuntu (I get a very quick DOS like screen reporting some error or something and then the laptop goes back round to the start asking me which OS to boot up). The Windows boot up works fine but the Ubuntu option just puts me in this loop :( I believe that this is Wubi asking me what I want to boot. Till now I really hadn't any idea what Wubi was and was unaware I had it,:confused: it was just how my laptop booted up I always chose Ubuntu and just got on with replying to emails etc

I need to get my Ubuntu working with the files I have on the machine already. There's lots of data that I really really really do NOT want to lose. How do I get my Ubuntu working again Please help me.

There must be some bug with the updater or something, I didin't interrupt the update at all the it crashes upon reboot. Hopefully this is resolved soon...

---

