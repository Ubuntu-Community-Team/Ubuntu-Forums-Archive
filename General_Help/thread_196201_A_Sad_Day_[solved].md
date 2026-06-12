---
title: "A Sad Day [solved]"
date: 2006-06-13
forum: General Help
---

### Post by ihavenoname on 2006-06-13
It appears that my time as an Ubuntu user has come to an end. See I have a WUSB54g Linksys wifi card, and as it turns out that one has a particlar problem with it's native linux drivers the rt2570 drives and and the Kernel (which seem to be, if i read the bug report correctly, due to the fact that the kernel has SMP suport (dual core support?) ) the fact that it has smp support causes problems with the rt2570 drivers. At least thats what I have been told the problem is. I thought the problem could be solved by using ndiswrapper. And during the development of Dapper it was fairly stable so long as I stuck to the i386 kernel. However once I updated to Dapper Final another problem presented itself. After being online for a while the Internet would disconnect and would essentially force me to restart in order to get the internet back on. So after a while of contending with this I reinstalled with the Final Disk of Ubuntu. That was about 3 days ago. The problem promptly returned however. I was content to sit there and maybe try to fix it. I posted here and it seems no one knew anything about it.  However the problem strangly took a turn for the worst. It seems to now have the same problem that I had with the Arch Linux kernel. It will freeze. It seems the freeze takes place between 21 and 30 minutes of uptime. I don't know what the problem is or how to fix it. I belive, however that it is related to SMP support in the Ubuntu kernel. Thus it seems that I am off to Fedora Core or Arch Linux (unless someone can suggest a "better" distro)

But I will need some help, here is what I need

1. I would like have my calculator key on my keyboard bring up a calculator, as it does in Ubuntu)
2. I would like my terminal to tab-auto complete for example in Fedora I must type /sbin/modprobe I would like to have it work by simply typing modprobe also in Fedora and most other distros when using sudo I must type out all of the other commands I would like to have it auto complete that as well for example

sudo modp{tab} should result in sudo modprobe. 


If you know about my problem and can help me fix it that would be most appreciated. 

thank you for your time. 

p.s. the reason I opted to leave ubuntu is that I belive that inorder to fix my problem I would have to recompile the kernel with the proper configurations. Which is too much of a hassle IMHO.

---

### Post by kvonb on 2006-06-14
Good luck with Fedora, and get ready for the usual Fedora forum reply which you will hear a lot: RTFM!  

I have had mega arguments with the Fedora morons over the years, they are a bunch of arrogant pig-headed know-it-alls with a god complex who can't abide answering newbie questions! (this is merely MY opinion based on MY experience).

That is one of the reasons I switched to Ubuntu, the fantastic forums and friendly help from REAL people who are willing to help with the newbie of newbie questions.

As for your problem with the network card, have a look at power management settings, it might be an ACPI problem, or look at your interrupt assignments in BIOS (when the computer first starts, keep an eye out for interrupt numbers on the screen and press the PAUSE key if it goes too fast), you might find that the netcard is on the same interrupt as something else like sound or video.  If it is, go into CMOS and try to assign the netcard to it's own IRQ, or disable serial ports and parallel port (if you don't use them), to free up some interrupts.

I believe the stock 386 kernel does NOT have SMP enabled as it is designed to be completely compatible with ALL 386 type machines.

Before you do anything drastic, (warning: the following assumes you have an intel CPU, if you have an AMD you will need to install the K7 kernel et-al), try installing the 686 kernel: synaptic package manager, search for 686 and mark linux-686, linux-headers-686, and linux-image-686 for installation, install, and reboot.

Once it has booted with the 686 kernel you can remove the old 386 kernel in the same way (it saves wasting bandwidth on 386 kernel updates).

Or the easiest way to fix the problem is to buy a supported netcard.  I know that means expense but if it saves you a lot of headaches AND you wish to keep Linux it will be worth it in the end.

Regards,

Kev :)

---

### Post by ihavenoname on 2006-06-14
Haha yes, you are right, the Fedora Forums is not ALWAYS the nicest place. I have had more problems with the 686 kernel then the 386 kernel. I must admit your ACPI theory is very intresting as some people have told me about this before. I do not fully understand the issue though, I will look into it as soon as I can restart. If you could point me to a good place to learn about IRQs it would be great. I am googling IRQ as I type this to see if there are any cases similar to mine. (Would this affect USB wifi cards?)

---

### Post by zxee on 2006-06-14
And even if you leave the people here will welcome you back when you return. I've used fedora since FC3-it keeps getting worst with each release, and as kvonb mentions the forums there will set your teeth on edge. I do think dapper has some rough edges. Maybe you can go back ( none of us like those words) to breezy for awhile? Or try foresight, frugalware or slack with dropline-gnome(my 2nd favorite after ubuntu) Good luck.

---

### Post by ihavenoname on 2006-06-14
[QUOTE=zxee]And even if you leave the people here will welcome you back when you return. I've used fedora since FC3-it keeps getting worst with each release, and as kvonb mentions the forums there will set your teeth on edge. I do think dapper has some rough edges. Maybe you can go back ( none of us like those words) to breezy for awhile? Or try foresight, frugalware or slack with dropline-gnome(my 2nd favorite after ubuntu) Good luck.[/QUOTE]
Thank you very much! It is this friendliness that draws me to Ubuntu (as well as other things). I am going to give it one more go before leaving. I must say though that I think Fedora 4's theme was in some ways better the FC5 but all in all it is a sturdy distro. However it has a small repo and some packages (due to being so bleeding edge) are very glitchy. (OpenOffice to name one.) Also it's a weird feeling being Red Hat's test rat. (haha red hat => rat get it? Oh my it's late)

---

### Post by kvonb on 2006-06-14
Hi,

To get into your CMOS or BIOS try holding down the DEL key when you first turn the computer on (above left of the arrow keys).  It might also be the ESC key, or F1 or F1 to 12 key, or CTRL ESC, if you have a manual that came with your computer it might tell you in there, or search on-line for your computer/mainboard model; usually the boot screen has some hint on the key combination to press to get into your BIOS/CMOS.

Being a USB card I would be toggling the USB interrupt (in BIOS/CMOS), ie if it is on - turn it off.  I usually find that the USB interrupt is annoyingly the same as the VGA interrupt!

You can always disable the VGA interrupt, it doesn't seem to do much as far as I have seen.

Look through the menus in your BIOS/CMOS (same thing) for PCI or Plug & Play options, somewhere in there should be the interrupt settings, like I said earlier if you aren't using serial ports, disable them, that could solve your problems in a flash!

Regards,

Kev :)

---

### Post by ihavenoname on 2006-06-14
[QUOTE=kvonb]Hi,

To get into your CMOS or BIOS try holding down the DEL key when you first turn the computer on (above left of the arrow keys).  It might also be the ESC key, or F1 or F1 to 12 key, or CTRL ESC, if you have a manual that came with your computer it might tell you in there, or search on-line for your computer/mainboard model; usually the boot screen has some hint on the key combination to press to get into your BIOS/CMOS.

Being a USB card I would be toggling the USB interrupt (in BIOS/CMOS), ie if it is on - turn it off.  I usually find that the USB interrupt is annoyingly the same as the VGA interrupt!

You can always disable the VGA interrupt, it doesn't seem to do much as far as I have seen.

Look through the menus in your BIOS/CMOS (same thing) for PCI or Plug & Play options, somewhere in there should be the interrupt settings, like I said earlier if you aren't using serial ports, disable them, that could solve your problems in a flash!

Regards,

Kev :)[/QUOTE]
Hmm weird. Today it froze after one hour. Then I was up for 7 hours 30 minutes with no freeze. I restarted to look at the bios and now I am back. The problem is that it is random and there is no way to check. I turned of a setting that said IRQ to PCI VGA. I also change the default video settings from PCI to AGP as my video card is agp. Let's see what happed. If this doesnt work then I will try the i386 kernel and see what happens. For now it has stablized.  I could not find anything about the interrup settings just a place where I could set the irq number. I have an American Megatrends BIOS I belive. I am not sure thou, when it comes to BIOS issues, I know very little. Thanx for all the help!

---

### Post by ihavenoname on 2006-06-25
Ok, so as it turns out I was using the 686 kernel which caused alot of problems. So now, ubuntu does not freeze. However, there is another problem. After an unspecified time my network goes down and the only way to restart it is to unload the ndiswrapper module and then reload it. This gives me anywhere between a few minutes and a few hours before the internet goes down again. It's very strange. I haven't heard of anything like this, but I will keep looking. Anyone know what it maybe???

Also it does not look like I will be going to Fedora. I first used FC4 then I went to FC5, it was intresting to see how fast things have been improving in the linux world. How ever fedora's package management frustrates me. So now it's either Ubuntu or Arch Linux (pacman is amazing! If you haven't tried it you should. it's missing some features (wildcards mostly) but it makes up for it. Arch also has some other package management tools that are very good.) For some reason however, I have become quite attached to Ubuntu (probably has something to do with the enoumous repo and the way most things are already setup. Anyways we shall see. If you could help me I would be very grateful.

---

### Post by joshrobinson on 2006-06-25
[QUOTE=ihavenoname]Ok, so as it turns out I was using the 686 kernel which caused alot of problems. So now, ubuntu does not freeze. However, there is another problem. After an unspecified time my network goes down and the only way to restart it is to unload the ndiswrapper module and then reload it. This gives me anywhere between a few minutes and a few hours before the internet goes down again. It's very strange. I haven't heard of anything like this, but I will keep looking. Anyone know what it maybe???

Also it does not look like I will be going to Fedora. I first used FC4 then I went to FC5, it was intresting to see how fast things have been improving in the linux world. How ever fedora's package management frustrates me. So now it's either Ubuntu or Arch Linux (pacman is amazing! If you haven't tried it you should. it's missing some features (wildcards mostly) but it makes up for it. Arch also has some other package management tools that are very good.) For some reason however, I have become quite attached to Ubuntu (probably has something to do with the enoumous repo and the way most things are already setup. Anyways we shall see. If you could help me I would be very grateful.[/QUOTE]


are you using the ndiswrapper in the repos? or did you manually compile the newest from the ndiswrapper website

---

### Post by joshrobinson on 2006-06-25
oh yeah, also, are you using a broadcom chipset? bcm43xx? are you removing the native bcm43xx module before using modprobe ndiswrapper

---

### Post by patrickfromspain on 2006-06-25
Do you have the same problem with i386 kernel and the native rt2570 drivers??

---

### Post by ihavenoname on 2006-06-25
**joshrobinson:** I belive my ndiswrapper is from the repos. I have a wusb54gv4 using the rt2500usb chipset. I have the rt2570 drivers blacklisted because they do not work correctly on Ubuntu.

**patrickfromspain:** I am not sure, those drivers tend to freeze Ubuntu when you attempt to connect from the "Networking" tool. They only work if you connect using dhclient rausb0. And sometimes Ubuntu freezes after a while if you do that (at least with the livecd, I never spent too much time on them once I installed.)

---

### Post by Who on 2006-06-26
You may find some light here
[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=10847&sid=3c1a949915743ffaae80bba7ec31f0b2](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=10847&sid=3c1a949915743ffaae80bba7ec31f0b2)

The discussion there seems to suggest compiling the rt2x00 driver, which will not conflict with SMP and is being more actively developed than the others, and _not_ the legacy rt2570 one. I will be doing this tomorrow for a friend (I hope!) so I can keep a log of what I do and post it here, or even do it on IRC...

Good luck if you get around to trying it before me!

Who

---

### Post by chestnut1969 on 2006-06-26
For my 10 cents worth, good luck with Fedora if your a newcomer to Linux!!

Fedora forums, ha!

I really went through the trial-by-fire 10 years ago when I started on Red Hat, things don't seem to have improved much in the Fedora camp aka 'RTFM'

Yes, I did end up reading all TFM's!!

---

### Post by patrickfromspain on 2006-06-26
Could someone explain what RTFM is? In the english academy I went to they didn't teach me that :D And IMHO??

Many thanks :)

---

### Post by patrickfromspain on 2006-06-26
Oh, also.. I'm using the rt2500 modules with no problems at all. As said, you could try compiling a kernel without SMP support and with the latest rt2x00 drivers, it's very easy.

Search for Kernel compilation for newbies, it is an Ubuntu 5.10 thread. There, it explains how to compile the kernel, it should help you.

---

### Post by joshrobinson on 2006-06-26
[QUOTE=patrickfromspain]Could someone explain what RTFM is? In the english academy I went to they didn't teach me that :D And IMHO??

Many thanks :)[/QUOTE]

ill post you a link to that, besides if i type what RTFM means it will get bleeped.. so heres a link

[http://en.wikipedia.org/wiki/RTFM]("http://en.wikipedia.org/wiki/RTFM")

yes it has bad language.. just a warning

and IMHO is short for in my humble opinion.. you will also see IMO, which is just in my opinion.. its just lazy internet type we use to shorten things up
:-p

---

### Post by ihavenoname on 2006-06-26
Yes, Fedora Forums can definatly be a harsh place, quite frankly though many forums are harsh compared to Ubuntu Forums. I love it when they say RTFM when they don't even know what your talking about, and as it turns out your actually not asking for help your just suggesting something. But it's all good I am no longer using Fedora, it's a well made distro but it's repos are a joke.

Now back on topic.

I am not sure if I said this before or not, I have in fact ditched the linux based drivers and I am using ndiswrapper because ndiswrapper works with Network Manager. However  as soon as I can I will try the newest Linux drivers to see what happens, I also will try the newest ndiswrapper. I will updated this as I test things out. The thing is that sometimes it works flawlessly and other time it messes up. There seems to be no set time period and no certain action that triggers the problem. I am having a hard time beliving that the network goes down randomly. What are your thoughts on this?

Ps. Patrickfromspain your english is excellent! I am amazed whenever I meet someone who (I am guessing here) does not live in an English speaking country and yet can speak/type flawless english. Hats off to you!

---

### Post by ihavenoname on 2006-06-28
Hmm, I have been using Debain the past few days ( the original debian). I must say, it has been very enlighting seeing where Ubuntu came from.  It's a bit difficult, especailly compared to Ubuntu. The Ubuntu devs really are spoiling us. But thats ok. Do you think I could use the Debain kernel with Ubuntu??? Hmm I am not sure it would be worth it, oh well. We shall see what happens. Back to Ubuntu ( I think) to find that solution (Now I am sure I can find it!)

---

### Post by ihavenoname on 2006-07-03
ok, so debian works rather well, and it seems that it has many if not all of the same things that exsist in Ubuntu. However it takes some configuration to start with. I wanted to install the Debain Kernel in Ubuntu but that was a no go due to what seems to be a diffrence in the naming scheme. I would like to compile the kernel my self without the patches for the rtx00 wifi drivers and w/o smp support if anyone can help or has any advice it would be great.

---

### Post by H.E. Pennypacker on 2006-07-04
[QUOTE=ihavenoname]ok, so debian works rather well, and it seems that it has many if not all of the same things that exsist in Ubuntu. However it takes some configuration to start with. I wanted to install the Debain Kernel in Ubuntu but that was a no go due to what seems to be a diffrence in the naming scheme. I would like to compile the kernel my self without the patches for the rtx00 wifi drivers and w/o smp support if anyone can help or has any advice it would be great.[/QUOTE]

Compiling kernel......whaaaaaoooo.  That sounds like a scary thing to do.  Whenever I hear "compiling kernel," I get scared of what it may entail.  I fear that it requires so much knowledge and it is so difficult, only a few can master it.

What's even worse?  Creating a custom kernel (never done it, and I don't even know what it means).  God protect us from that, please! :oops:

---

### Post by insyzygy on 2006-07-06
Two things. One, have you tried compiling separately the ralinktech drivers.
[http://www.ralinktech.com/supp-1.htm]("http://www.ralinktech.com/supp-1.htm")
They have linux drivers (different from the rt2x00 drivers).
I have a usb wifi card that uses their chipset and I compiled their drivers and it worked fine. You could try compiling these drivers and replacing the current one with them. This would avoid recompiling the kernel and would probably recompile the only piece of the kernel you really need to. 

If your thinking of custom compiling the kernel I would recommend it.
I recently  (this weekend) had to compile a custom kernel to get a wifi card working (Belkin F5D6020)  ver 2 does not work with the dapper kernel but does with newer kernels (its a known bug). So I followed this guide

[http://www.ubuntuforum.org/showthread.php?t=157560&highlight=custom+kernel]("http://www.ubuntuforum.org/showthread.php?t=157560&highlight=custom+kernel")

Ignoring step 10. (Note the current kernel is 2.6.17.3 available from 
[www.kernel.org]("http://www.kernel.org"))

If you do this you can keep using the ubuntu packages, but you strictly speaking won't be running the ubuntu kernel ( it has various additional patches). This worked absolutely fine for me and fixed my problem.  The only difference I noticed is there is no pretty ubuntu splash screen when you boot up, but once you get to the login screen everything is the same.

If you want to actually compile a special version of dapper you can get the dapper source with these instructions 
[https://wiki.ubuntu.com/KernelCustomBuild?highlight=%28kernel%29%7C%28custom%29]("https://wiki.ubuntu.com/KernelCustomBuild?highlight=%28kernel%29%7C%28custom%29")

I had never done it before but I did it a couple of times over the weekend to tweak things. If it doesn't work you can always go back to the previous version.

Basically you just download the source to /usr/src,  untar it, make a sym link to it
ln -s /usr/src/<your new src > linux

Then you go into /usr/src/linux  and run make xconfig. It will give you a gui with a huge list of kernel options. You can choose to have them be part of kernel ( a check) a module which can be loaded later  (a dot) or completely disabled (empty).

Go through it carefully turn off everything you don't need or want. Actually most things are on by default. If your unsure just turn off what your sure you don't want, the additional stuff just makes it take longer to compile ( and maybe makes the kernel slightly slower, but the normal ubuntu kernel that your running is designed to run on any machine so has all this stuff in it anyway so you can only speed things up).  Some of the stuff you probably obviously won't need, other stuff might be more obscure if you dont' really know whats in your computer.

There are only two places you can really mess up. One is make sure you have included the drivers for whatever type of hard drive you use (this is the section on scsi or atapi devices)i. These will be included by default so just don't uncheck them if you don't know. (You probably just need the atapi stuff).

The other thing to be careful of is that one the the things you have to choose is whether to compile file systems as modules or part of your kernel. Whatever partition your file system uses,  you must have that be part of the kernel (checked) or your new kernel will hang on boot. That cannot be loaded as a module. (Thats what happened the first time I compiled it). In gnome in the systems menu there is a disks option it will tell you your partition type (probably ext3).  I would just check all the file system (especially ext2 and ext3) to make sure.

Once your happy with your options you save it and run the make-kpkg -initrd kernel_image  and it will compile for a while (perhaps hours depending on your machine). When its done you will have a linux-<new kernel>.deb file.

Then you do dpkg -i linux-<new kernel>.deb and when you reboot you are in your new kernel. 

If it doesn't work you can go back to your old one and startover (press esc at boot and choose the old one). 

Of course I would back things up in case something somehow did go wrong. If you are considering installing a different distro you might consider trying it. After all if it doesn't work you can always install the new distro on top of whatever happened.

The guide I linked to is pretty good, let me know if you have questions.

---

### Post by 3rdalbum on 2006-07-06
Yay, i'm the first person with a solution to your less serious problem.

If you install and run Fish ([http://sourceforge.net/projects/fish/)](http://sourceforge.net/projects/fish/)), you will find that typing "sudo modp [TAB]" will auto-complete to "sudo modprobe".

If 1000 monkeys typed into Fish for an unlimited amount of time, eventually one would push the tab key and Fish would auto-complete the rest of the complete works of Shakespeare.

---

### Post by ihavenoname on 2006-07-09
> **insyzygy said:**
> Two things. One, have you tried compiling separately the ralinktech drivers.
[http://www.ralinktech.com/supp-1.htm]("http://www.ralinktech.com/supp-1.htm")
They have linux drivers (different from the rt2x00 drivers).
I have a usb wifi card that uses their chipset and I compiled their drivers and it worked fine. You could try compiling these drivers and replacing the current one with them. This would avoid recompiling the kernel and would probably recompile the only piece of the kernel you really need to. 

If your thinking of custom compiling the kernel I would recommend it.
I recently  (this weekend) had to compile a custom kernel to get a wifi card working (Belkin F5D6020)  ver 2 does not work with the dapper kernel but does with newer kernels (its a known bug). So I followed this guide

[http://www.ubuntuforum.org/showthread.php?t=157560&highlight=custom+kernel]("http://www.ubuntuforum.org/showthread.php?t=157560&highlight=custom+kernel")

Ignoring step 10. (Note the current kernel is 2.6.17.3 available from 
[www.kernel.org]("http://www.kernel.org"))

If you do this you can keep using the ubuntu packages, but you strictly speaking won't be running the ubuntu kernel ( it has various additional patches). This worked absolutely fine for me and fixed my problem.  The only difference I noticed is there is no pretty ubuntu splash screen when you boot up, but once you get to the login screen everything is the same.

If you want to actually compile a special version of dapper you can get the dapper source with these instructions 
[https://wiki.ubuntu.com/KernelCustomBuild?highlight=%28kernel%29%7C%28custom%29]("https://wiki.ubuntu.com/KernelCustomBuild?highlight=%28kernel%29%7C%28custom%29")

I had never done it before but I did it a couple of times over the weekend to tweak things. If it doesn't work you can always go back to the previous version.

Basically you just download the source to /usr/src,  untar it, make a sym link to it
ln -s /usr/src/<your new src > linux

Then you go into /usr/src/linux  and run make xconfig. It will give you a gui with a huge list of kernel options. You can choose to have them be part of kernel ( a check) a module which can be loaded later  (a dot) or completely disabled (empty).

Go through it carefully turn off everything you don't need or want. Actually most things are on by default. If your unsure just turn off what your sure you don't want, the additional stuff just makes it take longer to compile ( and maybe makes the kernel slightly slower, but the normal ubuntu kernel that your running is designed to run on any machine so has all this stuff in it anyway so you can only speed things up).  Some of the stuff you probably obviously won't need, other stuff might be more obscure if you dont' really know whats in your computer.

There are only two places you can really mess up. One is make sure you have included the drivers for whatever type of hard drive you use (this is the section on scsi or atapi devices)i. These will be included by default so just don't uncheck them if you don't know. (You probably just need the atapi stuff).

The other thing to be careful of is that one the the things you have to choose is whether to compile file systems as modules or part of your kernel. Whatever partition your file system uses,  you must have that be part of the kernel (checked) or your new kernel will hang on boot. That cannot be loaded as a module. (Thats what happened the first time I compiled it). In gnome in the systems menu there is a disks option it will tell you your partition type (probably ext3).  I would just check all the file system (especially ext2 and ext3) to make sure.

Once your happy with your options you save it and run the make-kpkg -initrd kernel_image  and it will compile for a while (perhaps hours depending on your machine). When its done you will have a linux-<new kernel>.deb file.

Then you do dpkg -i linux-<new kernel>.deb and when you reboot you are in your new kernel. 

If it doesn't work you can go back to your old one and startover (press esc at boot and choose the old one). 

Of course I would back things up in case something somehow did go wrong. If you are considering installing a different distro you might consider trying it. After all if it doesn't work you can always install the new distro on top of whatever happened.

The guide I linked to is pretty good, let me know if you have questions.


Thanx for all the info! I did try to compile the drivers seperatly, but it messed things up kinda bad...I am kinda busy now so I will get to this a.s.a.p. Thanx to all who have tried to help so far.

---

### Post by ihavenoname on 2006-07-13
I am getting ready to recompile the kernel.(this weekend) However a thought just occured to me. I have been in the habit of compiling ndiswrapper and installing it using make and make install. However it seems the the Ubuntu kernel comes with ndiswrapper. so perhaps there has been a conflict in between the two. So on one of my partions I have installed Ubuntu and used the ubuntu versions of ndiswrapper. What do you think?

---

### Post by ihavenoname on 2006-07-19
AHA!!! I found the problem. No need to recompile the kernel. In fact my problem was that I wanted to compile too much. In most distros that I have used you have to compile ndiswrapper yourself or at least install it yourself from the repos. Ubuntu's kernel comes with the ndiswrapper module built it. ( I found this while looking through the kernel source). To make it worse the version in the the kernel is 1.8 I belive, the one I compiled was 1.10. This seemed to cause some kind of glitch. Although it seems to me like it shouldn't have cause a problem, it did (The way the issue manifested it's self was rather strange as well). I also got problems when I recompiled the rt2570 drivers and installed them (which is what tiped me off to the issue) I am not 100% sure this is the reason but all indicators have led me to this conclusion. Right now however, my main distro is arch linux. I am not sure if I will go back to Ubuntu as after I was fairly certain I had pinpointed the problem, I torched apt-get. ( I ran apt-get install  "several-pacakges" && init 0 (as root) then in a separte terminal I ran (as root) sleep 5h && init 0 (because I wanted to have my comp. off by then. This some how messed up my apt-cache.I am not sure why, but what can you do. Anyways thanx for bearing with me. My return to Ubuntu is on hold for now, but I don't doubt that I will be back at most by edgy as I have become a chronic distro hopper (there is soo much that is good about some many diffrent distros!) Thanx for you patience and adieu!

p.s. SMP was also causing a problem but it is disabled in the i386 kernel as was mentioned at b4.

p.p.s How can I change the title to say that the issue is solved?

---

### Post by matthew on 2006-07-19
> **ihavenoname said:**
> p.p.s How can I change the title to say that the issue is solved?I'll do it for you. Congratulations!!

---

### Post by ihavenoname on 2006-07-19
> **matthew said:**
> I'll do it for you. Congratulations!!

Thanx! I could be back very soon actually, arch is starting to act weird again. God, I love the Ubuntu forums/community. Most friendly people ever, and although it doesn't directly affect the distro it does make for a much more enjoyable experience. (Esp. in terms of finding help with something or trying to get people to work with you on project etc. 

It feels so good to finally fix a problem that has plagued you for so long.:) 

ps. sorry for the "emotional" moment. I am not normally an emotional person. It's just that after getting the support from the various people on this board I felt it was necessary. Besides I am sure that on certain forums the people would have simply said goodbye if you want to leave we don't care to solve your problems. Sorry for being so long winded...it's a bad habit I am working on.

---

