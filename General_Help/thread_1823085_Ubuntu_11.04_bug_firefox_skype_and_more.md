---
title: "Ubuntu 11.04 bug firefox skype and more"
date: 2011-08-11
forum: General Help
---

### Post by AgentZ86 on 2011-08-11
I posted the bug but no response yet

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/818595](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/818595)

I already posted this under another title but no effect.

Can anyone please confirm that their install of 11.04 does NOT have this problem ?

Otherwise back to 10.10 I guess on this computer

---

### Post by mcduck on 2011-08-11
No, I definitely don't have such problem on 11.04. And to tell you the truth, if there was such bug I'm pretty sure people would be jumping all around because of it, so it definitely sounds like the problem is related to your system only.

Have you tried switching to another theme? That looks more like a theme-related problem than any actual bug in those programs...

(by the way, it's rather unlikely you'd even have a Shockwave plugin, considering that one has never been released for Linux. Shockwave Flash, perhaps? ;))

---

### Post by AgentZ86 on 2011-08-12
> **mcduck said:**
> No, I definitely don't have such problem on 11.04. And to tell you the truth, if there was such bug I'm pretty sure people would be jumping all around because of it, so it definitely sounds like the problem is related to your system only.

Have you tried switching to another theme? That looks more like a theme-related problem than any actual bug in those programs...

(by the way, it's rather unlikely you'd even have a Shockwave plugin, considering that one has never been released for Linux. Shockwave Flash, perhaps? ;))

Thanks for letting me know that your not seeing this topic at least I can move to trying 10.10 on that system to see if it creates the same problem and if so I would say there something going on with the machine itself.

Check your firefox addons, there is clearly a shockwave plugin installed by default on 10.10 and 11.04

Shockwave Flash - version 10.3.r181 or r183 depending on latest updates

But this is the second fresh install of 11.04 and disabling the shockwave plugin corrects the problem of the file browsing, however you can no longer see video or any streaming media on yahoo or other sites.

So to toggle this on/off does at least allow the (browse to file) features to work but I posted in the launchpad with NO responses at all.

I certainly hate to simply get another computers just because ubuntu cannot run on it and it's working perfectly with Windows XP dual booting no problem at all.

Also the live Ubuntu CD does not have this problem likely because the live CD is not running flash by default, but the fresh install creates this issue instantly on boot of the new system.

I did change and actually turned off any of the visual features and boot to the default ubuntu (no effects) and this did not change anything.

The only thing that changes it, is to disable the shockwave plugin, but then I love video capability.

And if I do not have to upload or download any files I would never had known there is ANY problem at all because other then this the system appears to work perfectly.

Thanks again, let me know if you happen to see any others who may have reported anything similar.

---

### Post by mcduck on 2011-08-12
> **AgentZ86 said:**
> Thanks for letting me know that your not seeing this topic at least I can move to trying 10.10 on that system to see if it creates the same problem and if so I would say there something going on with the machine itself.

Check your firefox addons, there is clearly a shockwave plugin installed by default on 10.10 and 11.04

Shockwave Flash - version 10.3.r181 or r183 depending on latest updates

But this is the second fresh install of 11.04 and disabling the shockwave plugin corrects the problem of the file browsing, however you can no longer see video or any streaming media on yahoo or other sites.

So to toggle this on/off does at least allow the (browse to file) features to work but I posted in the launchpad with NO responses at all.

I certainly hate to simply get another computers just because ubuntu cannot run on it and it's working perfectly with Windows XP dual booting no problem at all.

Also the live Ubuntu CD does not have this problem likely because the live CD is not running flash by default, but the fresh install creates this issue instantly on boot of the new system.

I did change and actually turned off any of the visual features and boot to the default ubuntu (no effects) and this did not change anything.

The only thing that changes it, is to disable the shockwave plugin, but then I love video capability.

And if I do not have to upload or download any files I would never had known there is ANY problem at all because other then this the system appears to work perfectly.

Thanks again, let me know if you happen to see any others who may have reported anything similar.
It's not Shockwave plugin, it's *Shockwave Flash*, also more commonly known as the Flash plugin. Shockwave is a completely different thing.

At some point i the history, After Shockwave's popularity, Macromedia started adding the "Shockwave" to all it's product names. Flash became Shockwave Flash, Fireworks was changed to Shockwave Fireworks etc... The names were changed back at some point, and Macromedia is now history, but the old naming still appears every now and then.

You'll find Adobe's web page for the Shockwave plugin here: [http://get.adobe.com/shockwave/]("http://get.adobe.com/shockwave/"), although there is nothing to download for Linux. 

(The download page for Flash plugin is here: [http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/"))

Fine by me, if I must say, since Flash now hanldes pretty much everything Shockwave does. Things were a bit different ten years ago when Flash only did simple vector graphics and you had to use Shockwave if you wanted to add video or bitmap graphics.

Anyway, if the Flash plugin is clearly causing your problems, you could try reinstalling it. Also it might be worth trying a fresh Firefox profile or testing if another user on the same machine has the same issue.

---

### Post by AgentZ86 on 2011-08-12
Thanks,

I did post that it's shockwave-flash in my last post

But also it's firefox plugin so it's pretty clear that it's the shockwave plugin or flash or whatever people want to call it.

I have always typically called it flash, but it's now called shockwave in the addon section of firefox so I referenced whatever it's staying.

But what happened to lead up to the launchpad etc. was that at first I thought it was my actual video card which was older and actually not supported by the new x.org included with ubuntu 11.04

So I certainly could install the driver support but for some reason there was no way to turn off the x.server from running the driver continued to say that x.server is running and needed to be turned off in order to run the program.

Anyhow after a zillion different methods found all over the net, forums and more I never could turn off the x.server to satisfy the driver install program.

I had similar problems that others also had where the x.server shutdown script would freeze at [OK] on one of the script lines and could not complete.

Anyhow during this time I also did not have 3D support so I used the experimental drivers and which were working with GL testing etc and still had this problem as described in the launchpad now.

But after considering it that it still may be video related I purchased a nvidia GS 8400 PCI cheap vid card, and it worked fine no need for extra drivers.

But the problem persists.

I also had already removed java-icetea and installed sun-java and flash and other variants.

Since the LIVE CD did not produce this problem I figured I still believe it must be related to plugins.

So I disabled one at a time and restarted firefox to confirm where the problem was.


And it was disabling of shockwave-flash that finally allowed me to use the browse to file location features for uploading a file to ebay etc.

So it seems very strange and likely just a compatibility problem, but really wish I could fix this.

I'm already on the lookout for another computer but it seems silly to get another computer for an otherwise perfectly working machine.

Sorry for the long response, this is just bugging me a little

Oh well, back to the drawingboard

;)

---

