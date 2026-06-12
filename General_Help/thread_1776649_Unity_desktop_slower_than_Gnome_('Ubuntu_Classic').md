---
title: "Unity desktop slower than Gnome ('Ubuntu Classic') - why?"
date: 2011-06-06
forum: General Help
---

### Post by zcacogp on 2011-06-06
Chaps, 

I'm using 11.04, having done a clean install from 10.10. The machine is an AMD dual-core 5600, and I am using 64-bit Natty. There is a reasonable chunk of memory (I think 2Gb) and it ran 10.10 very tidily indeed. 

Since upgrading and getting used to Unity, things aren't so sweet. It's slower; particularly noticeable in trivial things like scrolling around in Firefox, and entering text into gMail (even putting characters in is a little laggy), but opening windows with a bit of Compiz animation is choppy - they don't 'fly' smoothly, and it's not a pretty sight ... 

BUT, if I log in using "Ubuntu Classic" (good 'ol Gnome), all is happiness again. It is crisp and responsive and a pleasure to use. This is a direct comparison - same machine, same settings, same screen driver, same refresh rate (well I assume it's the same as I haven't changed them from one to the other). 

This makes me a bit perplexed; I have also installed 11.04 onto a lightweight laptop, which is also dual-core but rather lesser spec (I can't remember what), and it runs Unity every bit as well as it used to run Gnome in 10.10 (I did a clean update on that as well.) 

So I am doubting that the differences are down to processor grunt either. 

So, what is it? How can I tell? I am assuming that all the settings and configuration files are the same between the two desktops. (It seems identical in many respects; it has even used the custom theme in Ubuntu Classic as I set up in Unity, same screen colours, background, animations and so on - quite impressive!) 

I'm kinda curious to know what is going on and why there is a difference. In truth I'm not *that* bothered as I think I prefer Gnome instead, but I'd like to know why my machine won't do the one as well as the other. 

Thanks, in advance, for any help. All suggestions welcome. 


Oli. 

P.S. FWIW, I have googled around this problem and haven't found much about it - which suggests that either I'm special (:P) or missing the obvious (:(, but more likely.!) 

P.P.S. I installed the sysmonitor, as suggested on webupd8 (here:[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)) in Unity, and it seems to report very high CPU readings and huge memory use - CPU use of above 50% constantly and memory use of never less than 78%. However these aren't borne out when I look at #top, so I am assuming they are anomalous results.

---

### Post by coffeecat on 2011-06-06
> **zcacogp said:**
> So I am doubting that the differences are down to processor grunt either. 

Indeed. I suspect that the difference is down to your graphics card/driver combination. What graphics card do you have in the laptop that runs Unity well and what in the machine that doesn't?

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **coffeecat said:**
> Indeed. I suspect that the difference is down to your graphics card/driver combination. What graphics card do you have in the laptop that runs Unity well and what in the machine that doesn't?

If he switches to classic gnome and it works fine, isn't that a bug in Unity?

---

### Post by zcacogp on 2011-06-07
Coffeecat, 

Good question. 

sudo lshw -C video on the machine which struggles with Unity gives this: 

```
  *-display               
       description: VGA compatible controller
       product: Radeon HD 3300 Graphics
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:ee00(size=256) memory:fdfe0000-fdfeffff memory:fde00000-fdefffff
```

The same command on the machine which runs Unity fine gives this: 

```

  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:f8000000-f80fffff memory:e0000000-efffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f8100000-f81fffff

```
For what it's worth, the first machine is a Gigabyte motherboard with on-board AMD graphics, the second one is an old IBM X61s laptop, with nothing un-standard about it (apart from more memory.) 

Have to say tho', installedlinuxfromhdd is thinking on the same lines as me; surely if one machine can run one desktop fine and the other with problems, the graphics card, driver and configuration remain the same, so surely it is something to do with the difference between Unity and Gnome? 

(This is a question BTW - I could be way wrong!) 


Oli.

---

### Post by coffeecat on 2011-06-07
> **zcacogp said:**
> 
Have to say tho', installedlinuxfromhdd is thinking on the same lines as me; surely if one machine can run one desktop fine and the other with problems, the graphics card, driver and configuration remain the same, so surely it is something to do with the difference between Unity and Gnome? 

It's a good point, but is that gnome with or without compiz, i.e. with or without desktop effects? Unity is simply a compiz plugin. If you are running compiz OK on the gnome desktop, then Unity *ought* to run just as well. If it doesn't, and compiz runs OK on gnome, then something is odd. If you are not running compiz on the gnome desktop then you are not using 3d acceleration in the gnome desktop and that will be the basis for the difference. You need 3d acceleration for compiz = you need 3d accleration for Unity.

Let's deal with the machine that compiz is running OK on. That has Intel graphics. Most Intel graphics that is not too old will cope with 3d/compiz/Unity just fine and that seems to be your experience - end of story.

The machine which is not coping with Unity has an ATI Radeon HD 3300 graphics and I note that you have installed the proprietary fglrx driver. Curiously, the proprietary driver gives inferior performance with some ATI cards than the default open source one. Do you remember what Unity was like with the open source driver before you installed the proprietary one? You may be better with the open source driver.

So - two questions: do you have compiz enabled on the gnome desktop in the machine with the ATI card? Easy and quick way to check - the terminal is transparent if you have compiz enabled. And what was Unity performance like before you installed the proprietary fglrx driver?

I installed the fglrx driver once. I almost lost the will to live. :wink:

---

### Post by zcacogp on 2011-06-07
Coffeecat, 

Thanks for your post. In the light of it, things have become a bit more interesting ... 

I am (was!) using Compiz on both of the desktops on the computer in question. I installed CCSM on the Unity desktop to give me more control over the desktop, and when I switched to Gnome it (Compiz) was there and working apparently as it should. 

The machine that is working as it should (with the Intel graphics) - yes, all is fine, thanks. 

The machine that is struggling; yes, I have the extra driver. I was wondering whether this was the issue, so I removed it and restarted. And it now won't start up! It goes through GRUB fine, shows me the two login accounts on the machine, allows me to put the password in, then plays half the login tune, then goes silent and the screen goes black. And that's it - the only way out (that I can see) is to re-boot. This happens with both the Unity and Gnome interfaces (I've tried them both.) 

Why is this interesting? Because it is* exactly* what happened first time I put 11.04 on the machine; I had put a new HDD in it, and formatted the Ubuntu partition using EXT4, and assumed that was the problem. To get 'round it, I re-formatted using EXT3, and it worked as it should. And the first time I booted it up, I installed the proprietary fglrx driver, so I haven't rebooted without it since. 

(As a point of interest, I posted about this problem, here: 

[http://ubuntuforums.org/showthread.php?t=1776545](http://ubuntuforums.org/showthread.php?t=1776545)

... and the response seemed to be that EXT4 wasn't causing the problems and it must have been something else. I put it down to a bad install.) 
[B]
SO[/B]

It appears that the machine struggles to run without the extra driver. (It clearly will run without it, under some circumstances, as it allowed me to login without the driver in order to install the driver, when I first built it.) So does this mean that the driver is causing the problems with poor running in Gnome? It may, but without it, it doesn't run at all reliably. 

AND

I now have a machine which won't boot - or, more accurately, won't allow me to login, and hence is broken :(. I can get to the recovery console tho' - a plain white  box with a command prompt. Is is possible to install the fglrx driver from here? (Please tell me I won't have to re-build it again! ;) )

All help welcomed, as usual. (Actually, all help welcomed more than usual as my computer is broken!) Thanks. 


Oli.

---

### Post by linuxinstalledfromhdd on 2011-06-07
> **zcacogp said:**
> Coffeecat, 

Thanks for your post. In the light of it, things have become a bit more interesting ... 

I am (was!) using Compiz on both of the desktops on the computer in question. I installed CCSM on the Unity desktop to give me more control over the desktop, and when I switched to Gnome it (Compiz) was there and working apparently as it should. 

The machine that is working as it should (with the Intel graphics) - yes, all is fine, thanks. 

The machine that is struggling; yes, I have the extra driver. I was wondering whether this was the issue, so I removed it and restarted. And it now won't start up! It goes through GRUB fine, shows me the two login accounts on the machine, allows me to put the password in, then plays half the login tune, then goes silent and the screen goes black. And that's it - the only way out (that I can see) is to re-boot. This happens with both the Unity and Gnome interfaces (I've tried them both.) 

Why is this interesting? Because it is* exactly* what happened first time I put 11.04 on the machine; I had put a new HDD in it, and formatted the Ubuntu partition using EXT4, and assumed that was the problem. To get 'round it, I re-formatted using EXT3, and it worked as it should. And the first time I booted it up, I installed the proprietary fglrx driver, so I haven't rebooted without it since. 

(As a point of interest, I posted about this problem, here: 

[http://ubuntuforums.org/showthread.php?t=1776545](http://ubuntuforums.org/showthread.php?t=1776545)

... and the response seemed to be that EXT4 wasn't causing the problems and it must have been something else. I put it down to a bad install.) 
[B]
SO[/B]

It appears that the machine struggles to run without the extra driver. (It clearly will run without it, under some circumstances, as it allowed me to login without the driver in order to install the driver, when I first built it.) So does this mean that the driver is causing the problems with poor running in Gnome? It may, but without it, it doesn't run at all reliably. 

AND

I now have a machine which won't boot - or, more accurately, won't allow me to login, and hence is broken :(. I can get to the recovery console tho' - a plain white  box with a command prompt. Is is possible to install the fglrx driver from here? (Please tell me I won't have to re-build it again! ;) )

All help welcomed, as usual. (Actually, all help welcomed more than usual as my computer is broken!) Thanks. 


Oli.

With your particular problem I would install 10.10, boot from a Live USB stick of Ubuntu 10.10 and install it that way.

Here you go:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

I have a laptop that has the latest chipsets and everything, and I don't have any issues with 10.10.. But I do with 11.04, so that could be why.

---

### Post by coffeecat on 2011-06-07
@zcacogp, sadly I think the problem is the 3300 ATI chipset, or to be fairer to the graphics chipset, the state of Linux drivers for it. I recently purchased a motherboard with the onboard Radeon 3000 ATI graphics. Once I had assembled the machine, booting up with the live Natty CD was - um - unrewarding. That's more a reflection of the onboard graphics because earlier versions of Ubuntu were equally - um - challenging. :) I was relaxed about this because once I had fitted my ATI Radeon HD4350 PCIe card, I was Robert's nephew.

But this is of little help to you. There are two ways to look at this. The fglrx driver notoriously leaves bits of itself behind when you try to uninstall it. I could suggest some commands to run from the root recovery console to get rid of these, but since your experience of the default driver was not good, let's see if we can re-install the fglrx driver, unsatisfactory though it has proven to be. 

I can't guarantee that this will work because I've never found myself in the position of having to do this - reinstall the fglrx driver from a console, that is..

Start Ubuntu, but at the grub menu select the recovery console option. You will see some text scroll by and then you will see a secondary menu. Select "drop to root console with networking" or words to that effect. The networking will only work if you have an ethernet connection.

When you see the '#' prompt, (be careful - you have full root privileges) run these commands:

```
apt-get update
apt-get install fglrx fglrx-amdcccle fglrx-dev
```These command are appropriate for 11.04, not earlier versions. Some of the packages have changed.

I'll keep my fingers crossed for you.

One last thought. Except for Intel graphics, onboard graphics is never really satisfactory. Have you thought of getting a PCIe card (I assume it's a desktop)? It doesn't have to be an expensive one.

---

### Post by zcacogp on 2011-06-07
Coffeecat, 

Hmmm. I had a feeling you would say that. But back to the original question; why does it run one desktop better than the other? 

Actually, a more pressing question; thanks for the commands, but they didn't work! They did something; it downloaded and appeared to install the three packages, but it didn't make any difference when logging in; it has still just failed half-way through the login tune. 

Anymore suggestions? (Anyone else, please do feel free to chip in at this stage ... thanks!) 

Thanks very much for your help BTW. It's appreciated. 

Linuxinstalledfromhdd - I'm hoping not to have to abandon the current install, as it worked pretty well with the Gnome desktop. However, if I do have to go down the reinstall route then I would be tempted to go back to 10.10. I'm  not convinced, but could believe that it ran a smidge better than 11.04 with Gnome ... 


Oli. 

P.S. Thinking about this as I type it, surely I can't be the *only* person to have this problem? Has no-one else tried to put 11.04 on a machine with this particular chipset, anywhere?

ETA: I've started a new thread about reinstalling the driver, here: 

[http://ubuntuforums.org/showthread.php?p=10914129#post10914129](http://ubuntuforums.org/showthread.php?p=10914129#post10914129)

---

### Post by coffeecat on 2011-06-07
I'm sorry that those commands didn't help. I'm out of ideas, I'm afraid.

> **zcacogp said:**
>  But back to the original question; why does it run one desktop better than the other?

I'm speculating here but possibly that the Unity desktop is more demanding of compiz than just the few things you have enabled in gnome. Perhaps if you piled on the special effects in gnome it would start lagging as much as you see Unity lagging, considering that your particular graphics chipset is clearly not that capable. Sorry to be blunt, but there it is! :) The whole of the Unity desktop depends on animations much more than classic gnome = more demand on the GPU which is probably at its limit for you on that machine.

> **zcacogp said:**
>  
P.S. Thinking about this as I type it, surely I can't be the *only* person to have this problem? Has no-one else tried to put 11.04 on a machine with this particular chipset, anywhere?

I've done a search both in the forum and with google. Very unproductive unfortunately. There can't be many people who have tried Natty with this chipset.

---

### Post by gene simmons on 2011-06-07
i recently installed 11.04 on my cheapy acer netbook and my hp dv9000 laptop which is twice the pc the netbook is and 11.04 runs beter on the acer.i had lots of graphic isues on the hp.it works well on the acer out of the box,before 11.04 i used jolicloud on both and it was also faster and smoother on the acer.i also have a older compaq and ive had some probs instaling any version of linux.i got lubuntu to load and its very slow to boot.i guess some pc play well and some dont,the cheapy acer works the best though haha

---

### Post by coffeecat on 2011-06-08
@zcacogp, I've had a further thought. The console commands I gave you would not have reconfigured the xserver. From what I can find you may need to run this command as well after the apt-gets:

```
aticonfig --initial
```

That's from the recovery console, hence no sudo.

If that doesn't help, you could try...

```
dpkg-reconfigure xserver-xorg
```

... also from the recovery console.

---

### Post by zcacogp on 2011-06-08
Coffeecat, 

Thanks again for the suggestions. As is it, they didn't work - the first one gave an error message, the second one seemed to do something but didn't solve the problem; it still wouldn't allow me to login. 

However, I did discover that if you choose "recovery mode" at GRUB, one of the options is to start in low-graphics mode. This did allow me into the system, and from there I could install the graphics driver normally. 

So ... I'm back where I started. AND I have had my question answered! So, many thanks for your help. I guess I could list this question as "Solved", but I'm still quite interested in any more discussion about the differences in performance between Unity and Gnome, and whether things can be improved, so I won't. (I will mark the other thread as "Solved" tho'.)

Thanks again for your help CC. It's appreciated. I feel I have learned something as a result of this thread (which is always good) - even if that was by creating and solving a problem!


Oli.

---

### Post by coffeecat on 2011-06-08
@zcacogp, good luck!

---

### Post by zcacogp on 2011-06-08
Coffeecat, 

Thanks. Snag is, too much seems to come down to luck in this game ... :(

I notice you are in the UK - drop me a line if you are ever in Lahndahn Tahn; I think I owe you a beer!


Oli.

---

