---
title: "need a bit of advice before installing on my laptop"
date: 2012-02-11
forum: General Help
---

### Post by Cha0sBG on 2012-02-11
Hello dear Ubuntu users. Tonight i got the idea that Ubuntu will be quite better on my Lenovo Y570 laptop than windows7. I'm a first year at college studying Informatics and will mostly use it for programming, learning stuff of the internet nothing all that much. I would like to hear your advice in the matter. My general idea was to install it with dualboot so i can switch when ever i like to play some games or stuff like that. So a few concerns popped into my head that i wanted to clear before i jumped into the "Ubuntu lifestyle":

1: Drivers.
I can't shake the feeling that when i install Ubuntu some drivers wont work. For instance my USB 3.0 ports. I have no idea will there be a compatible driver or some other software to make the magic happen. And other similar devices and in general drivers that are ready to use on windows but not Linux.

2: Battery life.
I've looked here and there and i fell under the impression that Ubuntu gives less battery life than Windows 7. If i bring my laptop to college lectures i want it to last for quite some time. Normally with windows if i switch off my nVidia graphics processor off and switch the battery mode to a lower setting it can get me up to 3-4 even 5-6 hours MAX depending on what i'm doing. I would like to hear your thoughts on the matter.

3: x86 or x64.
I'm not quite sure on which to settle. On the one hand there is stability and more applications that are "ready to go" for x86 but does it compensate for the speed that x64 gives ? I've read somewhere that x86 Linux karnel could take advantage of more than 4GBs of ram like the x64. This is another struggle i can't make my mind up about.

So i would be very grateful if someone could explain some of the stuff and aid me in the matters. I just love the overall Ubuntu experience ever since i installed in for the first time on my Desktop. Anyway time for me top stop writing , this text is way to long anyway. I leave u with the " Sorry if this post is in the wrong section, didn't know if i should post it here or in the laptops and hardware section. " And last but not least my pc specs: [http://valid.canardpc.com/show_oc.php?id=2244686](http://valid.canardpc.com/show_oc.php?id=2244686) 
I'm only not sure why doesn't it show up my second video card there ( nVidia Geforce GT 555m 1GB video memory ).

---

### Post by Rodney9 on 2012-02-11
Try the **[Live CD/DVD]("https://help.ubuntu.com/community/LiveCD")** first you will  then know if all your hardware will work.

64 bit is the standard now, it will see all your ram, 32 bit wont see more than 4GB.

Rodney

---

### Post by wolfen69 on 2012-02-11
> **Cha0sBG said:**
> 
1: Drivers.
I can't shake the feeling that when i install Ubuntu some drivers wont work. For instance my USB 3.0 ports. I have no idea will there be a compatible driver or some other software to make the magic happen. And other similar devices and in general drivers that are ready to use on windows but not Linux.
USB 3.0 is well supported in linux.

> 2: Battery life.
It just depends on the computer. There's only one way to find out. You can always install the Jupiter applet to help with battery life.

> 3: x86 or x64.
64bit has been ready for prime time for a while now. The default ubuntu download will be 64bit starting with 12.04. I've been using 64bit for over 2 years now with no issues, and would never go back to 32.

> I'm only not sure why doesn't it show up my second video card there ( nVidia Geforce GT 555m 1GB video memory ).
Are running Optimus? If so, it could be a problem.

Edit: I see you *are* running Optimus. You could try the Bumblebee drivers, but it only works for *some* people.

---

### Post by 3Miro on 2012-02-11
> **Cha0sBG said:**
> 
1: Drivers.
I can't shake the feeling that when i install Ubuntu some drivers wont work. For instance my USB 3.0 ports. I have no idea will there be a compatible driver or some other software to make the magic happen. And other similar devices and in general drivers that are ready to use on windows but not Linux.

As Wolfen69 said, USB 3.0 works fine under Linux. However!!!

> 
2: Battery life.
I've looked here and there and i fell under the impression that Ubuntu gives less battery life than Windows 7. If i bring my laptop to college lectures i want it to last for quite some time. Normally with windows if i **switch off my nVidia graphics** processor off and switch the battery mode to a lower setting it can get me up to 3-4 even 5-6 hours MAX depending on what i'm doing. I would like to hear your thoughts on the matter.

Are you using Nvidia Optimus Hybrid graphics. This has barely any support and it is bound to cause a lot of trouble. If you have Optimu, there is a good chance that Linux will not work properly at all.

Normally, if enough tweaks, Linux can last for quite some time. This is hardware dependent and the tweaks are sometimes tricky. Other than the Optimus thing, there should be no issues.

> 
3: x86 or x64.
I'm not quite sure on which to settle. On the one hand there is stability and more applications that are "ready to go" for x86 but does it compensate for the speed that x64 gives ? I've read somewhere that x86 Linux karnel could take advantage of more than 4GBs of ram like the x64. This is another struggle i can't make my mind up about.

64-bit is becoming the default now. Unless your machine has very low RAM (i.e. 2GB or less), there is no reason to stay with the x86.

> 
So i would be very grateful if someone could explain some of the stuff and aid me in the matters. I just love the overall Ubuntu experience ever since i installed in for the first time on my Desktop. Anyway time for me top stop writing , this text is way to long anyway. I leave u with the " Sorry if this post is in the wrong section, didn't know if i should post it here or in the laptops and hardware section. " And last but not least my pc specs: [http://valid.canardpc.com/show_oc.php?id=2244686](http://valid.canardpc.com/show_oc.php?id=2244686) 
I'm only not sure why doesn't it show up my second video card there **( nVidia Geforce GT 555m 1GB video memory )**.

Yep, Nvidia below 560 is Optimus. Make sure to do **a lot** of reading before you install anything.

---

### Post by Cha0sBG on 2012-02-11
Any suggestions on what i must read to make sure everything works smoothly with my nVidia ?

---

### Post by 3Miro on 2012-02-11
> **Cha0sBG said:**
> Any suggestions on what i must read to make sure everything works smoothly with my nVidia ?

Smoothly will not happen, with Optimus you will have problems.

I would start by searching the forum for Optimus and then looking at more recent threads. A few months ago, Optimus simply meant "doesn't work", then last I know was that some people had managed to disable Nvidia altogether from the BIOS and just run on Intel. Search the forum for newer posts on what people have done with Optimus and Hybrid graphics.

---

### Post by jerrrys on 2012-02-11
> **Cha0sBG said:**
> Any suggestions on what i must read to make sure everything works smoothly with my nVidia ?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=nVidia+Geforce+GT+555m+oneiric+11.10&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=nVidia+Geforce+GT+555m+oneiric+11.10&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Optimus&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Optimus&sa=Search&cof=FORID:9)

---

### Post by Cha0sBG on 2012-02-11
Well at the moment i'm reading that a app called  bumblebee is a nice solution and can manage the cards for you or something like that. Anyone used  bumblebee and can give some more inside info on it? From they're own tests i mean.


Edit: hmm seems that the bumblebee project is abandoned and transfered to ironhide or am i wrong

---

### Post by hawthornso23 on 2012-02-12
Not all optimus laptops need ironhide. On mine linux runs fine on the nvidia card ignoring the intel i5 GPU. The drawback to that should theoretically be higher battery use, but it honestly hasn't been too bad. I tried ironhide a while back but it doesn't seem to work on my machine. I might try it again in future, but I get 5 to 7 hours at the moment so I'm not hurting.

There is a power regression that is easily fixed with a kernel option and a few other known kernel bugs that cause higher power use in laptops. The fix for most of these is supposed to arrive in kernel 3.3, but they will be backported into 3.2 for the ubuntu 12.04 release. If you can't wait you could compile your own kernel. 

My advice would be not to spend too much time worrying about it. Just try the live CD and if it seems to work OK then install it. Then work on any issues that arise. In linux problems are often fixable. You'll learn a lot. And since you plan a career in IT, the experience will be valuable.

---

### Post by Cha0sBG on 2012-02-12
I've messed with ubuntu in like 9.04 and above and the experience i got from it i don't wanna give back :). It's fun to mess around with settings, codes etc so i'll give it a shot, but there's  still something i don't get. If i don't install ironhide will it use my Intel card or my nVidia card, and there is another thing, since i got a Lenovo Y570 there is a switch on the laptop to switch off the nvidia card, will that work on linux or not. If the switch works and if when ever i switch the nVidia on and it handles everything when i need the fast GPU processing power i will be very happy with it.

Edit: Will a 12.04 be a good choice aswell

---

