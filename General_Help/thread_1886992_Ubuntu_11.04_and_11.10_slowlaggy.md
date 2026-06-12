---
title: "Ubuntu 11.04 and 11.10 slow/laggy"
date: 2011-11-26
forum: General Help
---

### Post by sd0070 on 2011-11-26
Hey guys, sorry for posting this topic again (I've seen several posts regarding slow performance issues here and elsewhere on the web). But everything I found so far was no help to my specific situation. Hopefully someone here can help me get this running properly because I am excited to be making the switch from windows to Ubuntu! As I said I'm new to Ubuntu but I should be able to follow some basic Terminal commands and whatnot.

Sorry for the long post! I want to give as much info in the first post as possible. Let me know what else you need to know (and where to find it if it's advanced stuff). 

I first installed 11.04 and it was really slow and using close to 100% CPU just opening new windows. Everything was choppy, from the wheel showing a web page was loading, to moving windows around the screen. I eventually realized that 11.10 was the newest version available and thought upgrading might fix the problem, but it didn't. Right now with just google chrome open gkrellm is idling around 20% and jumps to 99% just by opening the software center (which takes a good 10 seconds to open). 

Also, maybe related or not, I am having an issue with my graphics card driver. I go to settings > additional drivers and it shows I have 2 not activated. 1 - ATI/AMD proprietary FGLRX graphics driver, and 2 - ATI/AMD proprietary FGLRX graphics driver (post-release updates). I can install/activate the first one, but the "post-release updates" one always fails. Then after that one fails it says the first one isnt activated again! Watching videos on youtube or hulu are pretty choppy. I'm guessing that has something to do with the chopiness of my whole OS but not with taking so long for an app to load and using so much CPU.

_Specs_
Laptop: Toshiba Satellite L555D
Processor: AMD Turion II Dual Core Mobile M500x2
Memory: 2.7 GiB
Graphics: VESA RS880M (experience:standard)
Ubuntu 11.10 32 bit 
500GB hard drive (system info says 483)


I'm very close to just trying to install 10.04 (but coming from windows 7 I really want Unity) and if that doesnt work just give up! I hate giving up on technology though so PLEASE HELP!!! 

Thanks in advance and again I apologize for the lengthy post.

---

### Post by esky64 on 2011-11-26
> **sd0070 said:**
> Hey guys, sorry for posting this topic again (I've seen several posts regarding slow performance issues here and elsewhere on the web). But everything I found so far was no help to my specific situation. Hopefully someone here can help me get this running properly because I am excited to be making the switch from windows to Ubuntu! As I said I'm new to Ubuntu but I should be able to follow some basic Terminal commands and whatnot.

Sorry for the long post! I want to give as much info in the first post as possible. Let me know what else you need to know (and where to find it if it's advanced stuff). 

I first installed 11.04 and it was really slow and using close to 100% CPU just opening new windows. Everything was choppy, from the wheel showing a web page was loading, to moving windows around the screen. I eventually realized that 11.10 was the newest version available and thought upgrading might fix the problem, but it didn't. Right now with just google chrome open gkrellm is idling around 20% and jumps to 99% just by opening the software center (which takes a good 10 seconds to open). 

Also, maybe related or not, I am having an issue with my graphics card driver. I go to settings > additional drivers and it shows I have 2 not activated. 1 - ATI/AMD proprietary FGLRX graphics driver, and 2 - ATI/AMD proprietary FGLRX graphics driver (post-release updates). I can install/activate the first one, but the "post-release updates" one always fails. Then after that one fails it says the first one isnt activated again! Watching videos on youtube or hulu are pretty choppy. I'm guessing that has something to do with the chopiness of my whole OS but not with taking so long for an app to load and using so much CPU.

_Specs_
Laptop: Toshiba Satellite L555D
Processor: AMD Turion II Dual Core Mobile M500x2
Memory: 2.7 GiB
Graphics: VESA RS880M (experience:standard)
Ubuntu 11.10 32 bit 
500GB hard drive (system info says 483)


I'm very close to just trying to install 10.04 (but coming from windows 7 I really want Unity) and if that doesnt work just give up! I hate giving up on technology though so PLEASE HELP!!! 

Thanks in advance and again I apologize for the lengthy post.

I've just updated to 10.04 and finding it really slllowwww everthing was working fine till now I'm also using Gnome not Unity

---

### Post by sd0070 on 2011-11-26
So i just read somewhere to type "top" in terminal and it shows whats eating your CPU. My top 3 are compiz, xorg, and java...

---

### Post by insomniaccanuck on 2011-11-26
With the video drivers you can only use one at a time and need to restart X (the user environment) each time you change them.


Do you reboot after installing/activating the first one?
If so how does it work afterwards? Does it lag?

If you haven't yet used the one that does install after a reboot and install it and reboot and see how things are.
Hopefully that will clear up all the video issues.

Also the software center takes a while to load.  Its probing your system to see what's installed (and probably checking the installed versions against the newest available online etc).

Stick with it, things get better
Hope this helps.

---

### Post by sd0070 on 2011-11-26
> **insomniaccanuck said:**
> With the video drivers you can only use one at a time and need to restart X (the user environment) each time you change them.


Do you reboot after installing/activating the first one?
If so how does it work afterwards? Does it lag?

If you haven't yet used the one that does install after a reboot and install it and reboot and see how things are.
Hopefully that will clear up all the video issues.

Also the software center takes a while to load.  Its probing your system to see what's installed (and probably checking the installed versions against the newest available online etc).

Stick with it, things get better
Hope this helps.

Restarted after first install and it says the driver is activated but video is still choppy. 

Also, I was just using the software center as an example. Every mouse click has a delay before it actually does anything on the screen. ex: it takes over a full second to open a new tab in chrome.

ps. are you from montreal? go sabres! ;)

---

### Post by dudinatrix on 2011-12-02
Unfortunately I have no solution to add, but I am experiencing the exact same problem. I first started on 11.04 a few months back. Since I couldn't work like that, I did a clean install to 10.04 figuring it was an LTS version and was hopefully more stable. It was a little better, but it still eventually would get slow and unresponsive. Sometimes rebooting would fix it, but it would get slow again soon enough.

Today I did another clean install to 11.10, and noticed the issues right away again. I get the same 10+ second load for the Ubuntu Software Center. Nothing really loads quickly, there's always some sort of delay that seems too long (even if just a second or two). It just doesn't feel right. I don't have the hardware specs right now (it's my work system and I'm at home), but it is Dell system that is a couple years old.

Ubuntu works fine on my ~3 year old laptop.

---

### Post by oldtimer7777 on 2011-12-03
I'm running almost the same make/model but it is from last year, and the exception is that it is running Pentium dual core with Intel Graphics.  If you are going to use a Toshiba laptop, stick with Intel all the way.  None of that AMD or ATI stuff. 

> **dudinatrix said:**
> Unfortunately I have no solution to add, but I am experiencing the exact same problem. I first started on 11.04 a few months back. Since I couldn't work like that, I did a clean install to 10.04 figuring it was an LTS version and was hopefully more stable. It was a little better, but it still eventually would get slow and unresponsive. Sometimes rebooting would fix it, but it would get slow again soon enough.

Today I did another clean install to 11.10, and noticed the issues right away again. I get the same 10+ second load for the Ubuntu Software Center. Nothing really loads quickly, there's always some sort of delay that seems too long (even if just a second or two). It just doesn't feel right. I don't have the hardware specs right now (it's my work system and I'm at home), but it is Dell system that is a couple years old.

Ubuntu works fine on my ~3 year old laptop.

---

### Post by cmb271 on 2011-12-07
I had the same problem my computer is well not old but has age under it. When i run ubuntu 11.04 it worked fine but my hard drive is tiny so i was drinking up storage fast with my files. I don't like getting my HDD under 20 GB then i get uncomfortable. I used Live usb with 11.10 and it was so laggy it kept freezing i didn't install. After downgrading to 10.04 due to it being a Long Term Release it works fine. 

Specs below
release:10.04 (lucid)
Kernel Linux 2.6.32-36-generic
gnome:2.30.2

Memory:1.9 GiB
Single processor: e1200@1.60 GHZ
40GB hard drive with 24.0 GiB Available

maybe ubuntu teams should design a nice unity system like 11.10 but with lighter impact to a computer.:popcorn:

---

### Post by Themotorman on 2011-12-17
mine is slow too.. everything was fine with 9.04 I wish i hadn't upgraded!!
More or less the same problems as the rest of the posts here.

---

### Post by MM7 on 2011-12-25
Same here.

I'm running 1.5 Gb Pentium 4 and 1 Gb of ram on an old pc but finding Ubuntu just gobbles up my processing power.  Even the system monitor eats up 30-97% of my processing power.  That's pants!!!

I'm not impressed with Ubuntu so far.  It's the slowest operating system I've ever witnessed. :(

---

### Post by wildmanne39 on 2011-12-25
@MM7
Hi, I recommend you try Lubuntu or xubuntu they are both lighter distributions.
Thanks

---

### Post by MM7 on 2011-12-26
@wildmanne39

I installed Lubuntu 11.10 and I'm impressed so far.  Audio is good.  Video is good.  Everything seems quick and snappy. 

Thank you very much for pointing me in the right direction. :cool:

---

### Post by West201 on 2011-12-26
Welcome to Unity ;)

---

### Post by wildmanne39 on 2011-12-26
Hi, your welcome! I am glad to help, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

