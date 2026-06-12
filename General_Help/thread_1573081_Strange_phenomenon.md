---
title: "Strange phenomenon"
date: 2010-09-12
forum: General Help
---

### Post by DeMus on 2010-09-12
Hi, at the moment I use:
Mint 9 - 64bits (based on Lucid)
VLC 1.1.2 The luggage
Nvidia driver 260.19.04
I have an own picture as background on the desktop

Whenever I move the mouse while watching a movie in VLC, or double-click to exit the full-screen view I see a flash of the desktop background picture. This did not happen until a few days ago. In the mean time I did install some updates, but I have no idea which ones they were.

Two questions:
Is this phenomenon known to others?
Is there a way to find out which updates were installed recently, some log file maybe?

---

### Post by clrg on 2010-09-12
I don't know what causes your phenomenon. I noticed you don't use the most recent version of the nVidia drivers. Maybe an update fixes it? Get the new version here: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Make sure you select the right architecture.

---

### Post by DeMus on 2010-09-12
> **clrg said:**
> I don't know what causes your phenomenon. I noticed you don't use the most recent version of the nVidia drivers. Maybe an update fixes it? Get the new version here: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Make sure you select the right architecture.

Maybe I am blind but the drivers I see on the Nvidia page you mentioned are all older than the one I installed using a ppa. I use the 260.19 driver, while at the webpage it says 256.53 is the latest.

---

### Post by ronnielsen1 on 2010-09-12
The 260.19 is a beta. The 256.53 is a full release

---

### Post by DeMus on 2010-09-12
> **ronnielsen1 said:**
> The 260.19 is a beta. The 256.53 is a full release

So, it could be it is caused by this driver. I installed it not so long ago. I was surprised to see this driver come along so fast after 256.44 was followed by 256.53.
I didn't know it is still a beta. Well, then I believe this could be the reason for the strange behavior I see.
Thank you for your answer. I will install the 256.53 again and see what's happening.

---

### Post by DeMus on 2010-09-12
Well, I uninstalled the 260.44 driver and went back to 195.36. Still the same problems, so it is not the latest non-stable nvidia driver.
What else could it be?

---

### Post by coffeecat on 2010-09-12
> **DeMus said:**
> VLC 1.1.2 The luggage
Nvidia driver 260.19.04

....In the mean time I did install some updates, but I have no idea which ones they were.


Could the updates have included vlc itself? The reason I ask is that the current version in the Ubuntu repository is 1.0.6 Goldeneye, so I guess you might be getting vlc from a PPA. I'm not getting this issue in vlc 1.0.6, so I wonder if the problem is in vlc itself. Did you update from the GUI rather than using apt-get in the terminal? If so, Synaptic > File > History might tell you what the updates included. Or System > Administration > Log File Viewer > dpkg.log might tell you.

I do have one other thought but it's a real long shot and involves nvidia drivers.

I have a machine with onboard nvidia graphics in which I installed a (better) nvidia PCIe card. In Karmic (I think it was) I was getting some odd issues which I temporarily resolved by downgrading the nvidia driver. It was only later I discovered the real reason. The BIOS hadn't autodisabled the onboard nvidia graphics when I plugged in the PCIe card. (Most BIOS's will do this.) When I manually disabled the onboard graphics, the problems melted away and I was able to use the up-to-date nvidia driver.

It seems unlikely that  this is what is happening here, but I offer this in the (faint) possibility it might be helpful.

---

### Post by DeMus on 2010-09-12
> **coffeecat said:**
> Could the updates have included vlc itself? The reason I ask is that the current version in the Ubuntu repository is 1.0.6 Goldeneye, so I guess you might be getting vlc from a PPA. I'm not getting this issue in vlc 1.0.6, so I wonder if the problem is in vlc itself. Did you update from the GUI rather than using apt-get in the terminal? If so, Synaptic > File > History might tell you what the updates included. Or System > Administration > Log File Viewer > dpkg.log might tell you.

I do have one other thought but it's a real long shot and involves nvidia drivers.

I have a machine with onboard nvidia graphics in which I installed a (better) nvidia PCIe card. In Karmic (I think it was) I was getting some odd issues which I temporarily resolved by downgrading the nvidia driver. It was only later I discovered the real reason. The BIOS hadn't autodisabled the onboard nvidia graphics when I plugged in the PCIe card. (Most BIOS's will do this.) When I manually disabled the onboard graphics, the problems melted away and I was able to use the up-to-date nvidia driver.

It seems unlikely that  this is what is happening here, but I offer this in the (faint) possibility it might be helpful.

Thanks for your answer. I have been looking through the log files and couldn't find an entry for VLC. I did however find it in Synaptic itself, as you suggested. I installed it directly after installing the OS. It comes from:
[_http://ppa.launchpad.net/onestone/vlc/ubuntu_]("/vlc/ubuntu")
The strange thing is I did not have that at first.
The update for the nvidia driver came on the 9th of September, but as said in an earlier post, even with an older driver I have the same phenomenon.
Do you have anymore ideas, cause I have not.

---

### Post by coffeecat on 2010-09-12
> **DeMus said:**
> I installed it directly after installing the OS. It comes from:
[_http://ppa.launchpad.net/onestone/vlc/ubuntu_]("http:///vlc/ubuntu")
The strange thing is I did not have that at first.

The strange thing for me is that your link looks right but if I click on it, it tries to open up [http://vlc/ubuntu](http://vlc/ubuntu) which, of course, gives me a 'server not found' in Firefox.

Anyway, I notice that the latest VLC is 1.1.4 - available at other PPAs. The onestone PPA has the 1.1.2 version, which is what you have. It may be that there's a problem with 1.1.2.

The VLC website  tells me that Lucid's official repository version (1.0.6) is out-of-date, so I'll do a bit of experimenting. I won't be able to get back for a few hours, but I might try both the 1.1.2 and 1.1.4 versions out myself and see what happens.

In the meantime you might want to investigate alternative PPAs and see if you can get 1.1.4 from one of them. Offhand I don't know which one is best, because you get several listed at:

[https://launchpad.net/ubuntu/+ppas?name_filter=vlc](https://launchpad.net/ubuntu/+ppas?name_filter=vlc)

---

### Post by mc4man on 2010-09-12
never seen this with vlc, maybe once with totem-xine which I've kept going thru 10.10

Anyway a bit of a longshot  - 
If you have compiz enabled (and ccsm installed), then open CompizConfig Settings Manager - in System/Preferences, and at the very bottom in the 'Utility' section enable Video Playback, then see (maybe also a restart

(there is also the Workarounds - maybe disable or enable - the only one inside workarounds of interest would be 'force snyc.. between X and GLX

Edit:
you probably should look to upgrade to 1.1.4 - beware of any ppa's that replace your shared ffmpeg libs - it can work but several ppa's do it quite poorly

here's on that offers 1.1.4 - uses existing ffmpeg libs, I'd only enable to install/upgrade what you want, then disable the ppa or watch carefully when running update manager for what is being replaced
[https://launchpad.net/~ferramroberto/+archive/linuxfreedomlucid](https://launchpad.net/~ferramroberto/+archive/linuxfreedomlucid)

---

### Post by DeMus on 2010-09-12
Weel, I have VLC 1.1.4, I enabled Video Playback in Compiz, did a reboot but still the same.
When I stop Compiz the strange effect is gone so it is caused by the combination of VLC and Compiz.
Which parameter could it be? Any idea, besides Video Playback?

---

### Post by coffeecat on 2010-09-12
@DeMus, I've installed vlc 1.1.2 from the onestone PPA and I still don't see this phenomenon. I've got compiz enabled with a nvidia card in Lucid and with the 195.36.24 driver, but my settings in ccsm are fairly conservative. I think mc4man is right to bring up compiz. There might be a setting in there that's causing this.

---

### Post by DeMus on 2010-09-12
> **coffeecat said:**
> @DeMus, I've installed vlc 1.1.2 from the onestone PPA and I still don't see this phenomenon. I've got compiz enabled with a nvidia card in Lucid and with the 195.36.24 driver, but my settings in ccsm are fairly conservative. I think mc4man is right to bring up compiz. There might be a setting in there that's causing this.

I think so to, I will try to find out which one(s).
Thanks for your help.

---

### Post by DeMus on 2010-09-25
Anyone an idea about how to get rid of the desktop background flashing through a movie in VLC? It must be a combination of VLC and Compiz but I have no idea which item in Compiz is responsible for this. Who can help?

---

### Post by philinux on 2010-09-25
Try resetting compiz to it's default settings. Bottom left on ccsm preferences.

---

### Post by DeMus on 2010-09-25
> **philinux said:**
> Try resetting compiz to it's default settings. Bottom left on ccsm preferences.

I just did that and the effect was gone. Than one by one I enabled the ones I used and the effect is still gone. Any idea how that is possible? Anyway thanks a lot for your help.

---

