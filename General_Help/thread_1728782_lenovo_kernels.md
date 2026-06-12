---
title: "lenovo kernels?"
date: 2011-04-14
forum: General Help
---

### Post by frogotronic on 2011-04-14
Where can I find the download?: [http://www.ubuntu.com/certification/hardware/201102-7229](http://www.ubuntu.com/certification/hardware/201102-7229) 

Thanks,
Ch

---

### Post by Ad@m on 2011-04-14
**The [B]       Lenovo       Thinkpad T520     **     laptop     has been awarded the status of     **Certified**     on Ubuntu     PC (x86).[/B]

         **[B]Please note that for pre-installed systems:**[/B]

   **1) A special image of Ubuntu is available via the computer  manufacturer designed for this specific computer. **It takes advantage of  hardware features for these systems and may include proprietary software  and codecs. _**Please contact the computer manufacturer for access to that  specific Ubuntu operating system version.**_


   

:popcorn:

---

### Post by frogotronic on 2011-04-14
I was hoping not to have to go through that, and just find a link - thanks

---

### Post by tursiops on 2011-04-14
Perhaps I can rephrase cement_head's question in order to avoid someone cutting and pasting the very link that was provided as if it should be a painfully obvious answer to the question.  Does anyone think contacting the manufacturer directly about  a Linux distribution sound like anything that's not akin to sticking sharp things in your eye?

Try this:
Has anyone contacted Lenovo/Thinkpad and been referred to the exact instructions or link to obtain the Ubuntu version cited in the link concerning a unique build for the T520?  If so, please let others know what it actually entailed and what your experiences were/are.

Thank you.
***rolling eyes***

---

### Post by frogotronic on 2011-04-14
@tursiops

Thanks, that's a better re-phrase of what I was after...

OR...Anyone have experience on installing Ubuntu 10.04 or greater on a T520?  How does it work?

Thanks

---

### Post by coober85 on 2011-05-03
hey I have a basic t520 (intel 2520 / Intel HD Graphics)

tried installing the AMD64 DVD version of 11.04(64 bit version) - it didn't work (as a live disk). I tested my 10.04 CD and the live disk worked fine. Using the 11.04 Wubi didn't work either, I got an error half way through 210 rev error I think.

anyone else care to share their experiences.

---

### Post by o1e9 on 2011-05-03
> **cement_head said:**
> @tursiops
OR...Anyone have experience on installing Ubuntu 10.04 or greater on a T520?  How does it work?


Works for me on 11.04 amd64, tried 10.10 and 11.04 i686 version, work as well however 10.10 and 11.04 have different list of unsupported hardware.  On 10.10 Bluetooth did not work because no device has been found and 11.04 may not detect ThinkFinger.  I have not tried card reader, firewire and other extension slots yet, I have disabled WAN/WiMAX and modem because no use for me.

---

### Post by thaibuntu on 2011-05-19
I just ordered a t520 from Lenovo, but it hasn't arrived yet. I did contact Lenovo via their website support chat and inquired about the special image as well as not paying for Windows 7 (as I won't be using it).

I was informed that they do not sell any computers without Windows 7 and that they do not have any special image of Ubuntu. I was instructed to get Ubuntu from the Ubuntu site.

---

### Post by frogotronic on 2011-05-19
> **thaibuntu said:**
> I just ordered a t520 from Lenovo, but it hasn't arrived yet. I did contact Lenovo via their website support chat and inquired about the special image as well as not paying for Windows 7 (as I won't be using it).

I was informed that they do not sell any computers without Windows 7 and that they do not have any special image of Ubuntu. I was instructed to get Ubuntu from the Ubuntu site.

Please let us know how Ubuntu installs, especially with the GPU switching.

- CH

---

### Post by thaibuntu on 2011-05-22
My new T520 has been shipped, so here's to hoping I can report back on comparability by the end of the coming week.

[EDIT] In regards to GPU switching: I have been doing to preparatory research and it would appear that Optimus does not work out of the box with Ubuntu. nVidia doesn't have/won't have a solution because its not a hardware problem, but rather a software problem (drivers excluded). But there is hope on the horizon.

Check this out, if you would:[https://github.com/MrMEEE/bumblebee]("https://github.com/MrMEEE/bumblebee"). It's called the BumbleBee project and is supposed to enable Optimus on Linux and has a numbered of tested and working laptop models (unfortunately, Lenovo Thinkpad t520 is not one of those).

Hope this helps you ('cause it'll help me).

---

### Post by thaibuntu on 2011-05-26
Okay, just got my T520 this morning. Promptly installed 11.04 alongside W7. First and foremost, there was an error during installation regarding the nVidia card. Still, it completed installation and when I started up I was informed that my hardware was too old to run the unity desktop and I would use the classic desktop (so, the intel card is not 3D enabled, but working). I haven't tried the BumbleBee workaround yet, but I will do that today and report back.

---

### Post by frogotronic on 2011-05-26
> **thaibuntu said:**
> Okay, just got my T520 this morning. Promptly installed 11.04 alongside W7. First and foremost, there was an error during installation regarding the nVidia card. Still, it completed installation and when I started up I was informed that my hardware was too old to run the unity desktop and I would use the classic desktop (so, the intel card is not 3D enabled, but working). I haven't tried the BumbleBee workaround yet, but I will do that today and report back.

Can you try enabling/permanently activating the nVIDIA card in the BIOS and then booting UBUNTU?

- CH

---

### Post by thaibuntu on 2011-05-26
The first install of bumblebee went well enough. It even enabled 3d on the intel card so I could use the unity interface. It didn't quite get the desired effect with the McLeod chip. After un and reinstalling, it failed to build on the latest bumblebee source, but the dev was still changing things so I decided to put it off a week or so.

The good news is that you can go into the BIOS and set it to multiple options. Integrated only, discrete, and optimus. Plus you can set it to optimus* (meaning that it will enable optimus mode if and only if the is supports it). Which is probably better if you plan on gaming in windows. For now, I have mine set to discrete. Which allows me to play Vendetta online at the expense of battery life. If I decide to go on battery power, I can go into the BIOS and set it to integrated only.

---

### Post by frogotronic on 2011-05-27
@thaiubuntu

That's great news.  Can you test and see how long your battery life is with the discrete on all the time?  Do you have the standard 6 cell battery (the small one) or a larger one?

Thanks,
CH

---

### Post by thaibuntu on 2011-06-02
I would say about 5.5 hours with the larger 9-cell battery (which is what i got because it was only 50 USD more, but it does stick out past the back edge of the laptop).

---

### Post by brMichal on 2011-06-07
> **thaibuntu said:**
> I just ordered a t520 from Lenovo, but it hasn't arrived yet. I did contact Lenovo via their website support chat and inquired about the special image as well as not paying for Windows 7 (as I won't be using it).

I was informed that they do not sell any computers without Windows 7 and that they do not have any special image of Ubuntu. I was instructed to get Ubuntu from the Ubuntu site.

Apparently, you can buy T520 without Windows from Lenovo web site: 
[http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/special-offers.workflow:ShowPromo?LandingPage=/All/US/Landing_pages/Promos/thinkpad/ThinkPad_DOS]("http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/special-offers.workflow:ShowPromo?LandingPage=/All/US/Landing_pages/Promos/thinkpad/ThinkPad_DOS")

---

