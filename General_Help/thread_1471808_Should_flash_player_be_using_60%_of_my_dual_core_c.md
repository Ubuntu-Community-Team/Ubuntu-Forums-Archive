---
title: "Should flash player be using 60% of my dual core cpu? ati drivers, pics inside"
date: 2010-05-03
forum: General Help
---

### Post by ram130 on 2010-05-03
Now this is a fresh install of Ubuntu 10.04. I have done nothing but follow the steps on installing flash and ati driver from the main site. I have this problem on my desktop too which also has ATI graphics but with a AMD cpu. The desktop was upgraded from Ubuntu 9.10 and the driver installed from ATI site like my laptop. This is really troubling because while the video is in full screen its using over 90% of my cpu?? Then my laptop gets really hot so I just switch back to Windows 7(which only uses 15%). Can anyone help me out here?? Last time I had this problem was with the FGLRX proprietary drivers on Ubuntu 9.10 with the desktop. So please someone help me out here.

Ubuntu 10.04
Intel Core 2 Duo 2.1GHz
4GB
ATI HD 4650 1GB

video I'm trying watch: [http://www.hulu.com/watch/146253/the-white-house-correspondents%E2%80%99-association-dinner-president-obama-and-jay-leno-at-white-house-correspondents-dinner](http://www.hulu.com/watch/146253/the-white-house-correspondents%E2%80%99-association-dinner-president-obama-and-jay-leno-at-white-house-correspondents-dinner)

Pictures Attached.

--
Ramon

---

### Post by WorMzy on 2010-05-03
Flash is pretty notorious for being a CPU hogger, but still, I'd say it's uncommon for it to use 90%. Try reinstalling ubuntu-restricted-extras.

---

### Post by Sam on 2010-05-03
Also ~60% CPU here (even if it says that it cannot streams outside USA). I think their flash player is buggy.

CPU: AMD Athlon(TM) XP 2000+

---

### Post by ram130 on 2010-05-03
Just uninstalled the ATI driver. Same results, I thought it would be higher? Its not even using the hardware acceleration any more, why?

---

### Post by clhsharky on 2010-05-03
Adobe flash player for Linux doesn't have hardware acceleration.
Complain to Adobe, they say there working on it.

Sharky

Adobe requirements
[http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)

---

### Post by ram130 on 2010-05-03
> **clhsharky said:**
> Adobe flash player for Linux doesn't have hardware acceleration.
Complain to Adobe, they say there working on it.

Sharky

Adobe requirements
[http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)

oh come on now. It worked perfectly fine in 9.10...watching a youtube video in HD in full screen takes up 100%!! ...:confused::confused: I NEVER HAD THIS PROBLEM with 9.10 or Windows. So strange, if they didn't support it then why is it a option under settings when you right click a flash video?:confused: Also I don't see no where on the page that Adobe Flash Player does not support it under Ubuntu 10.04 and my system more than blows those specs away.

---

### Post by Dilutu on 2010-05-04
lucky you if you can watch youtube HD full screen. 480p takes above 80% cpu (P4 2.8ghz) not even full screen .Its better if I use fglrx driver ,but still nothing compared to my old winxp which has no trouble full screen. Even Hardy plays flash better than Lucid here. I wish I could find the magic tweek if there was one....

---

### Post by ram130 on 2010-05-07
I guess this is normal since no one has a solution. Anyway I tested the same video in Windows and it was considerably lower. About 28%-40% on avg in Chrome..

On YouTube I was getting around 15% for 360p and 60-70% for 1080p.

**pictures attached..**

So again, why is flash in linux so high?

---

### Post by Ad@m on 2010-05-07
ram130, out of interest what does firefox + flash in windows report its cpu usage at?

---

### Post by ram130 on 2010-05-07
> **Ad@m said:**
> ram130, out of interest what does firefox + flash in windows report its cpu usage at?

Same amount Adam..picture attached.

---

### Post by P4man on 2010-05-07
Try downloading flash player from adobe's website. I got the same cpu, I dont get nowhere near that high (although i am using an nvidia card and proprietary drivers)

---

### Post by ram130 on 2010-05-07
> **P4man said:**
> Try downloading flash player from adobe's website. I got the same cpu, I dont get nowhere near that high (although i am using an nvidia card and proprietary drivers)

tried already..same results. Possible bug in ATi drivers for 10.04?

---

### Post by Ad@m on 2010-05-07
Perhaps this will work,

[http://blogs.adobe.com/penguin.swf/2008/08/secrets_of_the_mmscfg_file_1.html](http://blogs.adobe.com/penguin.swf/2008/08/secrets_of_the_mmscfg_file_1.html)

sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" > mms.cfg
sudo mv mms.cfg /etc/adobe

---

### Post by ram130 on 2010-05-08
> **Ad@m said:**
> Perhaps this will work,

[http://blogs.adobe.com/penguin.swf/2008/08/secrets_of_the_mmscfg_file_1.html](http://blogs.adobe.com/penguin.swf/2008/08/secrets_of_the_mmscfg_file_1.html)

sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" > mms.cfg
sudo mv mms.cfg /etc/adobe

Tried. Didn't make a difference. If you read the comments on the link you provided, people are actually saying it has NO EFFECT with 10.04 and that this problem seems to be with Adobe.

  Here are some new pictures. Notice that in one of them, when firefox is "minimised" xorg usage is near 0% and my cpu is around 18% for flash. Xorg bug anyone? can anyone with nvidia drivers confirm if Xorg is using the cpu like mine is? Lets see if this is really a  ATi issue.

---

### Post by WorMzy on 2010-05-08
I have Ubuntu Lucid x64 running on a dual-core Intel E8500, overclocked to 4GHz, with a single nVidia 8800GTX. Current drivers enabled.

[[img]http://www.ubuntu-pics.de/thumb/58904/desk_1_100_87L5Xa.png[/img]](http://www.ubuntu-pics.de/bild/58904/desk_1_100_87L5Xa.png)

As you can see, I don't have this problem. I have the 64-bit flash plugin installed.

---

### Post by ram130 on 2010-05-08
> **WorMzy said:**
> I have Ubuntu Lucid x64 running on a dual-core Intel E8500, overclocked to 4GHz, with a single nVidia 8800GTX. Current drivers enabled.

[[img]http://www.ubuntu-pics.de/thumb/58904/desk_1_100_87L5Xa.png[/img]](http://www.ubuntu-pics.de/bild/58904/desk_1_100_87L5Xa.png)

As you can see, I don't have this problem. I have the 64-bit flash plugin installed.

Wow. Thats what I want. What is your xorg percentage like though? also what side bar is that.:p

---

### Post by WorMzy on 2010-05-08
Sorry, here's a shot with all processes visible. [[img]http://www.ubuntu-pics.de/thumb/58913/desk_1_102_jIQg2f.png[/img]](http://www.ubuntu-pics.de/bild/58913/desk_1_102_jIQg2f.png)

Using about 8% average, occasionally jumps to 50% for a split second, then drops back down. Not sure why it's doing that, but System Monitor keeps doing the same, so I think it's probably something to do with my system monitor histograms rather than flash.

The sidebar's Conky. :)

---

### Post by dtfinch on 2010-05-08
This says Flash doesn't use hardware acceleration if Compiz is enabled, though it's from 2008:
[http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html)

---

### Post by ram130 on 2010-05-08
> **WorMzy said:**
> Sorry, here's a shot with all processes visible. [[img]http://www.ubuntu-pics.de/thumb/58913/desk_1_102_jIQg2f.png[/img]](http://www.ubuntu-pics.de/bild/58913/desk_1_102_jIQg2f.png)

Using about 8% average, occasionally jumps to 50% for a split second, then drops back down. Not sure why it's doing that, but System Monitor keeps doing the same, so I think it's probably something to do with my system monitor histograms rather than flash.

The sidebar's Conky. :)

Could you click on the hulu click in my first post and do another screenshot of that. Looks like I'm stuck with this problem. I guess back to windows for a few months, especially since I need Pro Tools. 

 Also look at it way, your running more things than I am, I just have a clean install so far. My xorg is taking up more memory than yours and more cpu. I can bet you also have compiz enabled. So I'm confused as to what the problem could be. I say its the drivers and not flash...what do you think.

---

### Post by WorMzy on 2010-05-08
Sorry for the late reply.

Hulu doesn't work outside of the US, so I can't watch that video, so I couldn't say whether it's flash or your drivers. If you're not getting a high cpu usage while watching Youtube, then it's possible that there's a problem with Hulu's flash client, rather than your machine.

You're right though, I do have Compiz enabled.

---

### Post by ram130 on 2010-05-08
> **WorMzy said:**
> Sorry for the late reply.

Hulu doesn't work outside of the US, so I can't watch that video, so I couldn't say whether it's flash or your drivers. If you're not getting a high cpu usage while watching Youtube, then it's possible that there's a problem with Hulu's flash client, rather than your machine.

You're right though, I do have Compiz enabled.

Youtube is like 10% lower so its not so bad. I'm just worried I won't be able to watch online video anymore without my laptop heating up first.:mad:

---

