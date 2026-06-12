---
title: "hplip printer driver in meerkat ?"
date: 2010-10-27
forum: General Help
---

### Post by grey1beard on 2010-10-27
I found a post on the open printer forum that suggested that the hplip driver would work with my GX3000 gel printer.
On the HPlip page, the latest version shown is for 10.04.
I'd be very grateful if anyone could advise if this version will also install in 10.10, especially from their own experience ;)

I'm not seeking confirmation of it successfully driving the printer, only this first step ! 
Thanks
John

---

### Post by bertmung on 2010-10-27
I switched to UBUNTU 10.10 from openSUSE. After the switch I found that duplex printing was disabled. I considering trying 10.4. Does duplex printing work in 10.4?

---

### Post by grey1beard on 2010-10-28
Can't help you there, bertmung, as I've not yet tried printing in any earlier release.
This is a fresh start for my graphics setup, coming from win xp into meerkat !

Perhaps someone else could come in on that one.
John

---

### Post by grey1beard on 2010-10-29
I've decided to go ahead and see how far I could get.
The answer was not very far :(

I'm following HP's web page for installing the driver, and told it to "Automatic install", confirmed 10.10 was my correct version, entered my password, and it ran the pre-install commands ok. 
It then threw up the following "missing dependency" lines - 

INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 7 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: This installer cannot install 'gcc' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.

Knowing next to nothing, I'm asking for a little light to be shone in my direction. 
I tried repeating the process, making sure that Firefox was running, but the end warning lines were the same,
I note that it mentions 7 dependencies are missing, but goes on to name only one specific one - gcc, so am I right in thinking that this must be got first, and do I use system manager to get it ?
(See, I told you I knew just about zero ;) )

Many thanks,
John

---

### Post by grey1beard on 2010-10-29
The story so far, and perhaps I should have waited for help !
I used sudo apt-get install gcc, and the terminal ran, and finished by telling me that there were 9 files that were automatically installed that I could remove with autoremove, which I did.
I then ran the hplip installer again in terminal, and got exactly the same result.
I've saved the terminal insructions that I followed and will post them if it's a help in seeing what I did wrong, or haven't done yet.
John

---

### Post by grey1beard on 2010-10-29
OK sorted that by reading further down the hp page :rolleyes: and using sudo dpkg --configure -a, and there it was !

I'll add more until the next sticking point.
John

---

### Post by 73ckn797 on 2010-10-29
Isn't hplip available in Synaptic in 10.10? I loaded it and it worked. I now am not using 10.10 due to other issues.

---

### Post by grey1beard on 2010-10-29
I now think that I am stuck because following the hplip install pages has got me to the point of having the hp installer installed, but I have yet to jump the hurdle of /configure and make, etc.
Not quite sure what my terminal instructions should be, so I'm going to sleep on it and have another go tomorrow.
John

---

### Post by grey1beard on 2010-10-29
> **73ckn797 said:**
> Isn't hplip available in Synaptic in 10.10? I loaded it and it worked. I now am not using 10.10 due to other issues.

Pity I didn't find that before.
I've just looked, and yes it is installed, so I only hope I haven't done anything yet to mess it up !

Ill start fresh tomorrow, and see if I can get my gel printer to work with it.
Many thanks,
John

---

### Post by grey1beard on 2010-10-30
So far I've had no luck in trying the different installed drivers, but that may be because I don't know what I'm doing.
I know that in windows, having loaded non-working drivers can interfere with subsequent drivers, and that removing them is necessary, I presume the same is true for ubuntu.
So my next problem is to find out if this is the case, where such drivers are to be found, and how to remove them correctly.
I didn't expect it to be easy, but I find most sources of help written in such a way that if you could understand the answer, you wouldn't have needed to ask the question.
Although this seems to be getting me nowhere, and it maybe the case that I'm banging my head on a brick wall anyway, I'm creeping up the learning curve, so I would still apreciate any input that readers might care to contribute.
Happy Halloween,
Old and Grumpy John

---

### Post by mailprashant07 on 2010-11-19
Same problem with me.......any one help please:)

---

### Post by victorhugo289 on 2011-01-14
Alright, it's now been more than 2 months since the OP first started the thread and I see no asnwer yet. I have the exact same problem trying to install my HP printer.

The HPLIP driver worked perfectly for me in Ubuntu 10.04. I installed it using the terminal and the downloaded file from the website. Great.
But when I moved to Ubuntu 10.10 I found that HPLIP was in the Ubuntu Software Center,  I installed it from there and I could see again the HP icon on the top panel, just like in 10.04, but the printer doesn't work, or it works parcially, it can run self-tests and align the cartridges but I doesn't print anything.
So I went to the HPLIP website and downloaded the file and did the exact same procedure that the OP mentioned and I got the "7 dependencies" and "GCC" missing....
I'm stuck. I didn't go any further as the OP went, i.e. I didn't installed GCC via terminal. I'm waiting for some help as to what to do here.

Anyone??

Thanks.

---

