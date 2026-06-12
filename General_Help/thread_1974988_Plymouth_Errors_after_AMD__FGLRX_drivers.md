---
title: "Plymouth Errors after AMD / FGLRX drivers"
date: 2012-05-06
forum: General Help
---

### Post by FishboyFive on 2012-05-06
Hello i just did a clean install of Ubuntu 12.04 and installed the AMD drivers from AMD.com for my 

AMD HD 6870

and the driver installs fine and works but now i get this really UGLY shutdown screen that is Purple with White Text over top 

and the text is all out of place 

whats going on why does it look like i am getting the old Text based shutdown and startup 

overlapped on top of the purple plymouth screen ?

this is so ugly i cant stand to use ubuntu until i can find a fix 

everything worked fine untill i tried to install a simple video driver

---

### Post by FishboyFive on 2012-05-06
anyone have any idea where i can get official support for this problem i have as i need to get this issue fixed

---

### Post by FishboyFive on 2012-05-07
nobody ?

i am the only one with messed up start up and shut down with 

amd drivers ?

---

### Post by georgelappies on 2012-05-07
Hi 

The proprietary drivers have quite a few incompatibilities still. Getting the fugly startup and shutdown screens is one of them. If I am not mistaken it is to do with the inability of the kernel to access the framebuffer before the driver is fully loaded, hence if you "Ctrl + Alt + F1" with the proprietary drivers installed your resolution will be some standard VGA resolution like 800 x 600 which of course doesn't look at all great on a wide screen monitor.

I could still live with that, however the bug that completely breaks the ATI proprietary drivers for me is the one where compiz runs at 100% usage on one of your cores as soon as the display goes into standby mode. My laptop started to run hot and noisy with zero battery life after I installed the drivers. Looking at the system monitor showed that something was maxing a core while the screen went into standby. Logging in remotely via ssh and running htop showed the culprit to be compiz. This breakage however only occurs with the proprietary ATI driver.

As I have a dual boot with win7 I don't use my ubuntu machine for games (well 3d games, I do use it for chess and wesnoth :)) I use win7 for the graphics and sound intensive games. So I can live with using the built in kernel driver for my card (ATI 5470)

Not sure what your needs are or if the current kernel have sufficient support for your card. This is one of the reasons I am happy that steam and ea games are considering linux as a platform. It will be an incentive for nvidia and ati to shape up their linux drivers :)

---

### Post by FishboyFive on 2012-05-07
I play diablo 3 and world of Warcraft and need good drivers for 3d 

I'm sure I could learn to live with it but it really just feels / looks cheap to have such a simple thing as a boot screen and shut down to be so messed up and ugly it makes it look like my OS is broken I drives me nuts.

Why can't we just remove this Plymouth junk if it doesn't work with official drivers for Amd

---

### Post by QIII on 2012-05-07
This is not a problem with the driver, per se.  It is a condition that occurs with the frame buffer, as above.  It is a result of the installation, but not a bug in the driver.

Which would you rather have:  5 seconds of pretty Plymouth at startup and shutdown, or fully functional graphics while using the machine?

FWIW, the only effect I get is minor distortion of the Plymouth image coming and going.

If you have trouble with Compiz killing your CPU, there are posts addressing the issue.  Do you have an APU or xxxxM GPU or hybrid graphics?

If you are intrpid and you absolutely must fix it, you can do some things to you grub cofig, such as changing the resolution, I think webupd8.com has some ideas.

This is really a matter for the Plymouth devs, and how the should deal with a kernel with a proprietary driver -- either ATI, NVIDIA or Joe's Magical Graphics.

---

### Post by FishboyFive on 2012-05-08
> **QIII said:**
> This is not a problem with the driver, per se.  It is a condition that occurs with the frame buffer, as above.  It is a result of the installation, but not a bug in the driver.

Which would you rather have:  5 seconds of pretty Plymouth at startup and shutdown, or fully functional graphics while using the machine?

FWIW, the only effect I get is minor distortion of the Plymouth image coming and going.

If you have trouble with Compiz killing your CPU, there are posts addressing the issue.  Do you have an APU or xxxxM GPU or hybrid graphics?

If you are intrpid and you absolutely must fix it, you can do some things to you grub cofig, such as changing the resolution, I think webupd8.com has some ideas.

This is really a matter for the Plymouth devs, and how the should deal with a kernel with a proprietary driver -- either ATI, NVIDIA or Joe's Magical Graphics.

Do you know how I can talk with these Plymouth people / dev 

I want to know how to fix it 

Ubuntu in my eyes is broken until it can boot up with official drivers without graphical glitches and errors 

Does Plymouth have a support fourm ?

---

### Post by collisionystm on 2012-05-08
here, try this

[http://www.omgubuntu.co.uk/2010/11/plymouth-manager-lets-you-change-boot-theme-resolution-in-ubuntu/](http://www.omgubuntu.co.uk/2010/11/plymouth-manager-lets-you-change-boot-theme-resolution-in-ubuntu/)

---

### Post by FishboyFive on 2012-05-08
thanks im going to do a fresh install with wubi to see if i can get this fixed

---

### Post by FishboyFive on 2012-05-09
Well it's a no go for anyone with the Amd drivers in Ubuntu 12.04 

Ubuntu 12.04 does not support Fglrx AMD Drivers.

Only thing that is supported is the hacked open source drivers 

You can not release an OS when you know if the end user installs the Official drivers it breaks the boot process . 

This is absurd .

If I install drivers in windows I don't get a hideous boot up or shut down . 

Ununtu you are never going to make it like this 
You need to make sure hardware is fully supported with official drivers not 3rd party hacked drivers. 

If Plymouth does not work then fix it before release . 

Back to windows 8 until you can fix this broken mess you call an OS.

For all you fan boys 
People need fully working 3d even in Linux  don't offer the drivers if your OS can't handle them .

---

### Post by QIII on 2012-05-09
> **FishboyFive said:**
> Ubuntu 12.04 does not support Fglrx AMD Drivers.
 
 They work for me, 3d and hardware acceleration.  The boot process still works fine.

Windows doesn't support AMD/ATI drivers, by the way.  Microsoft doesn't support anything but Microsoft.  It's the AMD/ATI folks that make sure their drivers work with Windows, not the other way around.  Common misconception, though.
 
 Again, it's Plymouth, not Ubuntu.  The Plymouth devs need to get it straight.  And if you think this single thing is a commentary on an OS in its entirety, you've missed the mark.
 
 Good luck with Win8.

---

### Post by FishboyFive on 2012-05-09
If its Plymouth then Ubuntu needs to fix it because Plymouth is part of the total package . 

Don't release Ubuntu when you know for a fact your boot manager is broken and does not support official drivers from Amd.com

It's not ok to just say things work it's just a boot screen . It should work 

And thanks my windows 8 preview is working 100% with official drivers  it's really nice 

Good luck getting that 1% desktop market without full 3d support in official drivers

---

### Post by QIII on 2012-05-09
Once more from the top:

Ubuntu offers only the open source drivers.  AMD/ATI produces the proprietary drivers for both Windows and Linux.  Neither Windows nor Linux supports the drivers.

The boot process is not broken.  If it's not pretty enough for you, then you and I have a somewhat different notion about what computers are.

The proprietary fglrx drivers provide 3D.

Again, good luck.

---

### Post by FishboyFive on 2012-05-10
> **QIII said:**
> 

  AMD/ATI produces the proprietary drivers for both Windows and Linux. 



 ( 1 ) AMD Makes Video Card called HD 6870 
 ( 2 ) AMD/ATI produces the proprietary drivers for both Windows and Linux

( 3 ) Its up to Windows and Linux to make sure the Operating System can use the drivers without Breakage

AMD clearly Shows on there blog that the day Windows 8 Consumer preview was launched that they launched a Version of a Driver for Windows 8 .

Downloaded and installed 


UBUNTU launches 12.04 

amd website has Drivers for Ubuntu 12.04 for download

I download and install drivers 

I then Reboot the PC and

.....................................

BROKEN BOOT SCREEN
BROKEN SHUTDOWN SCREEN
.....................................

Do not blame AMD / ATI they mad the drivers they work
its UBUNTU that does not work 

if the drivers were made to work with Linux then what did linux do or break that they dont work.

this is ridiculous in the year 2012 that Linux is still pointing fingers at AMD / nvidia because they can not get there act together.

---

### Post by QIII on 2012-05-10
Let me say this again:  it is *NOT* incumbent on OS purveyors to make sure someone else's product works with their OS.  That is a common misconception and expectation.  Perhaps I am ignorant because I am a Microsoft Certified developer, but I  am under the impression that it is my responsibility to make sure my  products work with Windows, not the other way around.  Microsoft has no  obligation to make sure their OS works with my products.  In fact, Microsoft has a very stringent approval process for OEMs to have their drivers included in the Microsoft driverbase.  Microsoft makes the OEMs do it.  Microsoft does not make their own developers do it.  Many people simply do not understand the industry.  Microsoft *does not support your hardware or its driver.*  Microsoft is under no moral, ethical, legal or market-driven obligation to do so.  The OEMs are under a market obligation to make their products work with Windows or they go out of business.  It is a simple and wise business decision to spend the lion's share of their effort on Windows compatibility and only a small effort for Linux compatibility.  I don't know how to be more clear.

Canonical did nothing to change or break the driver.  It's the one they were given.  It's closed source so Canonical *can't* change it even if they wanted to. Canonical put it in the repo as is and the MOTU responsible included in the package what was necessary to install it.  That is all. * The driver is AMD/ATI's, unchanged*.  If you read the description of the driver in Synaptic, you will see that Canonical states clearly that they *cannot provide support or modify the code.  *It's not a matter of blame.  It's a matter of fact.  What is also a matter of fact is that AMD/ATI and Canonical have such a good relationship that every fourth and tenth month, Canonical gets the x.4 and x.10 versions of ATI/AMD's drivers before they are even released to the public *or any other distro*.  Phoronix complains about that every time.

The driver does work, in fact, as demonstrated by the fact that so many people use it.  It provides full 3D and can even be made to use hardware acceleration with a few additions that AMD/ATI does not itself include in the Linux package because they are open standard and available to all.  The driver is not broken and it does not interfere with the boot process.  A consequence of its installation, which Canonical has no control over in any way, is that the Plymouth image is distorted.  We know this.  Canonical knows this.  It has been known for a long time.  You were even given a link to a way to resolve this behavior somewhat.  Someone spent the time to make that available -- for free.

What the open source community can do is produce an open source driver, which they have done.  However, since the hardware is proprietary the best they can do is program against a black box (there is some light at the very edge because AMD/ATI makes some things available) and try to make it work.  It would be illegal, unethical and cost-prohibitive for the developers to attempt to fully reverse engineer the hardware in order to sort it out.  That driver does not cause the Plymouth issue, because the open source developers have control over that. Someone* is* producing a driver that works well with Plymouth.  It's just not ATI.  It's the very people who you say can't get their acts together.  Open source developers even make a number of drivers for hardware where the OEM provides no Linux driver *at all*.  Ironic, no?  

However, the open source developers have not gotten to the point where they have full 3D or hardware acceleration because they cannot see into the black box.

Your only possible legitimate complaint in all of this can only be with the open source driver.  Even then, that would be blaming people who work very hard to produce something under very difficult circumstances -- and they don't deserve that.

I think you have convinced yourself of what you need to think, so Win8 is probably your best bet for continued happiness and joy.  There is nothing wrong with that and there is nothing wrong with Windows.  I use it.  I even have Win8 installed.  I am aware that is current lack of polish (to be honest, it looks like sticky notes on a white board right now) is due to the fact that it is an advanced proof-of-concept provided for users to give feedback.  It does not yet reflect its ultimate final form.  The fact that Windows has made it available as they have is highly unusual -- and very welcome.  I used to get pre-release versions as a Beta tester.

Be intellectually honest.  You have taken an insignificant thing and blown it entirely out of proportion in order to justify using Windows.  That is unnecessary.  Just use Windows.  Nobody here can fault you for using what works for you.

---

### Post by georgelappies on 2012-05-12
> **QIII said:**
> Let me say this again:  it is *NOT* incumbent on OS purveyors to make sure someone else's product works with their OS.  That is a common misconception and expectation.  Perhaps I am ignorant because I am a Microsoft Certified developer, but I  am under the impression that it is my responsibility to make sure my  products work with Windows, not the other way around.  Microsoft has no  obligation to make sure their OS works with my products.  In fact, Microsoft has a very stringent approval process for OEMs to have their drivers included in the Microsoft driverbase.  Microsoft makes the OEMs do it.  Microsoft does not make their own developers do it.  Many people simply do not understand the industry.  Microsoft *does not support your hardware or its driver.*  Microsoft is under no moral, ethical, legal or market-driven obligation to do so.  The OEMs are under a market obligation to make their products work with Windows or they go out of business.  It is a simple and wise business decision to spend the lion's share of their effort on Windows compatibility and only a small effort for Linux compatibility.  I don't know how to be more clear.

Canonical did nothing to change or break the driver.  It's the one they were given.  It's closed source so Canonical *can't* change it even if they wanted to. Canonical put it in the repo as is and the MOTU responsible included in the package what was necessary to install it.  That is all. * The driver is AMD/ATI's, unchanged*.  If you read the description of the driver in Synaptic, you will see that Canonical states clearly that they *cannot provide support or modify the code.  *It's not a matter of blame.  It's a matter of fact.  What is also a matter of fact is that AMD/ATI and Canonical have such a good relationship that every fourth and tenth month, Canonical gets the x.4 and x.10 versions of ATI/AMD's drivers before they are even released to the public *or any other distro*.  Phoronix complains about that every time.

The driver does work, in fact, as demonstrated by the fact that so many people use it.  It provides full 3D and can even be made to use hardware acceleration with a few additions that AMD/ATI does not itself include in the Linux package because they are open standard and available to all.  The driver is not broken and it does not interfere with the boot process.  A consequence of its installation, which Canonical has no control over in any way, is that the Plymouth image is distorted.  We know this.  Canonical knows this.  It has been known for a long time.  You were even given a link to a way to resolve this behavior somewhat.  Someone spent the time to make that available -- for free.

What the open source community can do is produce an open source driver, which they have done.  However, since the hardware is proprietary the best they can do is program against a black box (there is some light at the very edge because AMD/ATI makes some things available) and try to make it work.  It would be illegal, unethical and cost-prohibitive for the developers to attempt to fully reverse engineer the hardware in order to sort it out.  That driver does not cause the Plymouth issue, because the open source developers have control over that. Someone* is* producing a driver that works well with Plymouth.  It's just not ATI.  It's the very people who you say can't get their acts together.  Open source developers even make a number of drivers for hardware where the OEM provides no Linux driver *at all*.  Ironic, no?  

However, the open source developers have not gotten to the point where they have full 3D or hardware acceleration because they cannot see into the black box.

Your only possible legitimate complaint in all of this can only be with the open source driver.  Even then, that would be blaming people who work very hard to produce something under very difficult circumstances -- and they don't deserve that.

I think you have convinced yourself of what you need to think, so Win8 is probably your best bet for continued happiness and joy.  There is nothing wrong with that and there is nothing wrong with Windows.  I use it.  I even have Win8 installed.  I am aware that is current lack of polish (to be honest, it looks like sticky notes on a white board right now) is due to the fact that it is an advanced proof-of-concept provided for users to give feedback.  It does not yet reflect its ultimate final form.  The fact that Windows has made it available as they have is highly unusual -- and very welcome.  I used to get pre-release versions as a Beta tester.

Be intellectually honest.  You have taken an insignificant thing and blown it entirely out of proportion in order to justify using Windows.  That is unnecessary.  Just use Windows.  Nobody here can fault you for using what works for you.

+1 Most excellent reply full of truth.

---

