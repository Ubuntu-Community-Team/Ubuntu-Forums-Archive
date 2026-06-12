---
title: "Ubuntu 11.10: Intel i7, hybrid graphics, laptop overheating"
date: 2012-03-09
forum: General Help
---

### Post by veroslav on 2012-03-09
Hi,

I have a Dell Inspiron 17r laptop on which I am running Ubuntu 11.10 (64-bit). The laptop has the following specifications:

Intel i7-2670QM (2.20 Ghz, 6 MB, 4 cores)
nVidia GeForce GT 525M (2 GB)
6 GB DDR3 SDRAM

It comes with hybrid graphics, according to the output from lspci:

```
user@user-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev ff) 
```I installed Bumblebee by following the instructions here: 

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Everything installed correctly, however, I am not sure whether the nVidia card was successfully disabled.

Question 1: How can I check whether Bumblebee disabled nVidia card?
Question 2: I think the Intel card is HD 3000, do I need to install any drivers for this card?

My main concern is about the overheating problems, as I have been reading a lot of threads about people having problems with Intel Sandy Bridge and overheating. Also, the fan on my laptop is constantly spinning, even though I am only browsing the Internet for instance. It is not terribly load however.

Question 3: Do I have such a processor (based on Intel Sandy Bridge technology)?

In order to monitor hardware temperature, I installed ls-sensors package. Using only Firefox with three tabs and writing this post in gEdit, I get the following readout:

```
user@user-laptop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +54.0°C  (crit = +100.0°C)
temp2:        +54.0°C  (crit = +100.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +51.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +43.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +44.0°C  (high = +86.0°C, crit = +100.0°C)
Core 2:         +51.0°C  (high = +86.0°C, crit = +100.0°C)
Core 3:         +50.0°C  (high = +86.0°C, crit = +100.0°C)
```Question 4: Would you agree that the temperatures are a bit high? If so, what can I do to lower them? 

I would highly appreciate any input on the issues above, because I am quite happy with this laptop otherwise.

Thank you in advance.

Regards,
Veroslav

---

### Post by veroslav on 2012-03-09
I've tried applying the patch I've found here but to no avail (the temperatures even increased): [www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html")

I also installed the Jupiter applet, which is a power management application but not even letting Jupiter run in the "Power Saver"-mode had any positive effect on the temperature.
With laptop running in this mode, the temperature averages 55 C while idle.

Further suggestions are highly appreciated.

---

### Post by Mark Phelps on 2012-03-11
> **veroslav said:**
> Further suggestions are highly appreciated.

You've done a good job of trying what's currently available.  There are no other current solutions.

It's rumoured that Ubuntu 12.04 has fixed the kernel problem, even though in another thread, someone tried that and found out it hadn't -- at least, for them.

It's worth trying if you want to burn a bootable USB of 12.04 and see if it works.  However, if it doesn't, then since it's still Beta, you need to post those questions in the Precise Development forum, not here.

---

### Post by veroslav on 2012-03-12
Thank you for you reply, Mark Phelps.

It feels good to know that I did all that I could even though it didn't resolved my issues, yet.

After posting my last post here, I tried booting 12.04 Live USB, however, the temperatures stayed pretty much the same as in 11.10.

MODS: is there any way for my original question to be moved to the Precise Development forum, as it appears that it might be more beneficial to ask there, because the problem still seems to exist in the latest daily iso I tried two days ago?

Thank you in advance and thanks again Mark Phelps.

Regards,
Veroslav

---

### Post by dave2001 on 2012-03-12
Have you tried Ubuntu 10.04 LTS? It runs much cooler than Oneiric on most laptops.

I tried a fresh install of 11.10 on my laptop and it ran very hot, even after all the tweaking I could manage.

---

### Post by Mark Phelps on 2012-03-12
> **veroslav said:**
> ... After posting my last post here, I tried booting 12.04 Live USB, however, the temperatures stayed pretty much the same as in 11.10.

Sorry to hear that, but that only serves to confirm what others have already posted -- that 12.04 does NOT fix the overheating problem, at least, when that is related to the kernel bug.

---

### Post by idoitprone on 2012-03-12
bumblebee does not shutdown the graphic card by itself

[https://github.com/Bumblebee-Project/bbswitch](https://github.com/Bumblebee-Project/bbswitch)

install a bbswitch
here is a ppa package
```
sudo apt-add-repository **ppa:bumblebee/stable**
sudo apt-get install bbswitch
```i hope tat command is right. I left ubuntu since they break too many things 2 years ago

add some parameters to /etc/default/grub
[B]```
i915.i915_enable_rc6=1

```[/B]```
[B]i915.i915_enable_fbc=1
[/B]**i915.lvds_downclock=1**
```look at link for more details.
[http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)

doing these things will extend ur batt life by 2x and over.

I always do these things when i install a new distro on acer 4830tg timelinx

One more thing, when the new kernel 3.3 comes out install it cuz it fix some batt issues

---

### Post by veroslav on 2012-03-13
Hi all,

Mark Phelps,

unfortunately, after having read a lot of other reports where people mention the same problem, and
also having read comments on the launchpad's bug report, I can only confirm what you already said.
That the kernel fix in 12.04 does not fix this issue.

I have also found out that it looks as though there are two different issues that cause the overheating,
one of these being specific to the Intel's Sandy Bridge architecture and which seems to affect me.
This one is supposably being fixed by the Intel engineers and already in the lates kernel in 12.04,
but does not fix my problem as it looks.

idoitprone,

I though the latest version (3.0) of Bumblebee automatically disables the discrete (nVidia) card,
according to this:

[https://github.com/Bumblebee-Project/Bumblebee/wiki/Power-Management](https://github.com/Bumblebee-Project/Bumblebee/wiki/Power-Management)

Also, I have tried i915.i915_enable_rc6=1 without any luck, should I try all the three kernel
parameters you posted at the same time? What do the last two parameters do?

Those are my observations, I feel I have simply run out of luck, at this point in time. I will be watching the
kernel development closely in the future and hope for a fix that really fixes the problem. Also, I will
still be very thankful for all the findings posted here or elsewhere on the forum.

Thank you both of you.

Regards,
Veroslav

---

### Post by idoitprone on 2012-03-13
> **veroslav said:**
> Hi all,

Mark Phelps,

unfortunately, after having read a lot of other reports where people mention the same problem, and
also having read comments on the launchpad's bug report, I can only confirm what you already said.
That the kernel fix in 12.04 does not fix this issue.



I have also found out that it looks as though there are two different issues that cause the overheating,
one of these being specific to the Intel's Sandy Bridge architecture and which seems to affect me.
This one is supposably being fixed by the Intel engineers and already in the lates kernel in 12.04,
but does not fix my problem as it looks.

idoitprone,

I though the latest version (3.0) of Bumblebee automatically disables the discrete (nVidia) card,
according to this:

[https://github.com/Bumblebee-Project/Bumblebee/wiki/Power-Management](https://github.com/Bumblebee-Project/Bumblebee/wiki/Power-Management)

Also, I have tried i915.i915_enable_rc6=1 without any luck, should I try all the three kernel
parameters you posted at the same time? What do the last two parameters do?

Those are my observations, I feel I have simply run out of luck, at this point in time. I will be watching the
kernel development closely in the future and hope for a fix that really fixes the problem. Also, I will
still be very thankful for all the findings posted here or elsewhere on the forum.

Thank you both of you.

Regards,
Veroslav

wrong wrong. You have to put all three parameters to your grub default. Intel disable alot of power saving features because of regressions. RANT: I starting to think AMD should make all the hardware standards not Intel.
add these two
**```
i915.i915_enable_fbc=1 
```**```
**i915.lvds_downclock=1**
``` all kernel parameter do different things. If you experience graphic problems. Isolate the kernel parameter that cause it and remove. Congrats, you found a kernel regression on your hardware.
btw lvds_downclock will definately reduce lots of your power usage

There is an explanation of those kernel parameters in the link I provided on my previous post
Here is the link if you are lazy to scroll up [http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)

 In order to turn off the nvdia card** YOU HAVE TO INSTALL BBSWITCH** I cannot empasize this enough. Hardware has to be manage by the kernel, if it is not mange by the kernel, the os cannot it turn off or turn on. Bumblebee does not do it. It kidda like a daemon such as upower that call the kernel acpi driver. bbswitch is the acpi driver and bumblebee is the daemon.

Your link say use bbswitch [https://github.com/Bumblebee-Project/Bumblebee/wiki/Power-Management](https://github.com/Bumblebee-Project/Bumblebee/wiki/Power-Management)
> f Power Management doesn't work (please check the [FAQ]("https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ") to be sure of this first) on your model **using [bbswitch]("https://github.com/Bumblebee-Project/Bumblebee/wiki/bbswitch")**, follow the *Reporting bugs* instructions on **[https://github.com/Bumblebee-Project/bbswitch](https://github.com/Bumblebee-Project/bbswitch)**. On Ubuntu, the installation of the mentioned tools can be done with:

One more thing, if bbswitch is not needed, since bumblebee exist, then why is it part of the bumblebeeproject? It is little bit of dilution resources.

[https://github.com/Bumblebee-Project/bbswitch](https://github.com/Bumblebee-Project/bbswitch) here the link read it


Rant: sometimes I wonder if I should either copy paste or post links. I realize most of the time op do not read my links

---

### Post by veroslav on 2012-03-14
idoitprone,

thank you for your reply. I apologize if my lack of knowledge offended you (judging from your rant at the end of your last post). I am very new to the whole hybrid graphics / Bumblebee thing and I am trying really hard to learn. One of the ways I try to do this is by reading the supplied information.

In your post, you are mentioning that "In order to turn off the nvdia card YOU HAVE TO INSTALL BBSWITCH". I understand this, as that is exatcly what they mention on the Bumblebee's GitHub page, BUT what still confuses me is this (from the Bumblebee FAQ at [https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ):](https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ):)

How can I disable my card?
Bumblebee 3.0 automatically disables your card if it's unused. There is no need for additional configuration.

My understanding was that bbswitch was automatically installed and configured correctly when installing Bumblebee. I haven't been able to find any info about how to use bbswitch manually (I followed the guide here when installing [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee))

You also mention that "Your link say use bbswitch https://github.com/Bumblebee-Project...wer-Management". It does, but previously they mention that this is done automatically in Bumblebee 3.0, that is what I dont understand and what confuses me. I've never said that "bbswitch is not needed, since bumblebee exist"; what I thought and still think, is that according to my understanding, it is automatically installed when installing Bumblebee 3.0. That might not have been the case before, again, this is what I get from reading the FAQ over at Bumblebee GitHub.

I've checked the FAQ before asking the question here, in order to find out whether my card is supported ([https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ](https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ)) under "How to know if my graphics card is supported?" section. I followed the [http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606) link from there (because I installed using the propriatery driver, according to the instructions here: [https://wiki.ubuntu.com/Bumblebee):](https://wiki.ubuntu.com/Bumblebee):)

3. Install Bumblebee using the proprietary nvidia driver:
```
sudo apt-get install bumblebee bumblebee-nvidia
```

There, it appears that my card should be supported (5-series). Please do correct me if (probably) I am wrong.

Also, I did read through all of the links you've posted, and I really appreciate them. However, I did read throgh most of them before asking the question, and I think that the reason I am still confused is simply because I lack knowledge and not the ignorance. I am very thankful for your help so far.

If you could just clear my last doubt, I would be very thankful:

1. How can I check if my discrete card is disabled/ bbswitch is correctly installed? Should I run the commands here:
[https://github.com/Bumblebee-Project/Bumblebee/wiki/Power-Management](https://github.com/Bumblebee-Project/Bumblebee/wiki/Power-Management)
I really have hard time understanding what they mean there.

I will have a go at playing with the kernel parameters you posted later today when I am at home, and report back the results. Thank you very much for these!

Again, I am very sorry if I offended you in any way, that wasn't the intention. I am neither lazy nor ignorant, but sometimes, people miss clues and tips, not because they do it on purpose but because they lack knowledge but are eager to learn.

Regards,
Veroslav

---

### Post by spynappels on 2012-03-14
> **idoitprone said:**
> wrong wrong. You have to put all three parameters to your grub default. 
> Rant: sometimes I wonder if I should either copy paste or post links. I realize most of the time op do not read my links

Perhaps a little harsh, the OP has demonstrated that he is willing to do some digging and has tried a lot of different solutions. Explaining rather than copying and pasting links might be more helpful.

---

### Post by veroslav on 2012-03-14
Hi again,

I think I finally managed to find what you was talking about, idoitprone! :)

[https://github.com/Bumblebee-Project/bbswitch#readme](https://github.com/Bumblebee-Project/bbswitch#readme)

I will have a go as soon as I am home! The reason I didn't find this before is because I thought the bbswitch module was automatically installed and configured when Bumblebee was installed, so I never gave the link above the attention it clearly deserves.

Thanks again, I will come back if I need more help, but right now I feel that I just make manage to get it working! So happy right now

/Veroslav

---

### Post by veroslav on 2012-03-14
Sorry for spamming my own thread, but I now have solid evidence that bbswitch IS included in Bumblebee 3.0 (current version, the one I installed), AND that Bumblebee should manage the power automatically without any user input, please have a look here:

[http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work/36936#36936](http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work/36936#36936)

and search for the following reply/quote:

"Bumblebee 2.2 or 2.3 did not have power saving, but the new 3.0 version has power saving features available that are automatically applied. Thus, the discrete video card will always be turned off unless a program is requested to be run with Bumblebee." 

It can be found at the end of the first zero vote reply.

The comment was written by Lekensteyn, one of the guys behind the bbswitch project (as can be seen here [https://github.com/Bumblebee-Project/bbswitch#readme](https://github.com/Bumblebee-Project/bbswitch#readme), watch for his name among the bbswitch commits).

This leads me to believe that something went wrong after installation on my system (bug perhaps?) and I will have a look at how I can report it to the relevant people.

/Veroslav

---

### Post by idoitprone on 2012-03-14
> **veroslav said:**
> idoitprone,

thank you for your reply. I apologize if my lack of knowledge offended you


Again, I am very sorry if I offended you in any way, that wasn't the intention. I am neither lazy nor ignorant, but sometimes,** people miss clues and tips**, not because they do it on purpose but because they lack knowledge but are eager to learn.

Regards,
Veroslav

It is not about the lack of knowledge that urks me, but people skiming over clues and tips.

spynappels
I usually do not this, but this is faster to get the op attention. If you want me to explain, then I will, but I kidda think it will be better if he read the wiki and not skim over important details which it too much to write on a single post

Those kernel parameters than I post in the link on phoronix, is power saving features of intel sandy bridge chipsets. There are discussion amound intel driver engineers of possible kernel regression in which the screen does not refresh proper on special hardware configurations. They disable three things. An experimental powersaving feature introducted on 6th release; hence, i915.i915_enable_**rc6**=1 rc = release candidate. lvds downcloak, it is a power saving feature that allow integrate processor power consumption to go down on idle and i915.i915_enable_fbc=1 fb = framebuffer. it does sometype of compression to the data so the gpu does less work.
It is standard knowledge that the kernel must manage all hardware. In order for the hardware to talk to the kernel, there must be drivers. Bbswitch is a kernel module that is an acpi - something i wish was simpler- driver that controls on and off switch of optimus card. The bumblebee just remove the kernel module of the nvidia driver and call the bbswitch. This is how you get your power saving features. If there isnt any kernel module to mange the on and off switch, bumblebee cannot turn off the card. It is that simple. Btw, i am sure how the binary work on your computer, but it fails on mine. I am using the open source nouveau driver

---

### Post by veroslav on 2012-03-15
idoitprone,

points taken. I actually managed to verify that bumblebee indeed has disabled my nVidia card, when not needed, so that is a good thing.

Also, I've applied all of the three kernel parameters above without any graphical glitches that some people experience.

I consider my original issue as solved for now.

Thank you.

Regards,
Veroslav

---

