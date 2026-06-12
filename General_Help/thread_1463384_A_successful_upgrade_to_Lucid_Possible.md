---
title: "A successful upgrade to Lucid Possible?"
date: 2010-04-26
forum: General Help
---

### Post by Spiritof76 on 2010-04-26
Has anyone successfully upgraded to 10.04 successfully? I am running 09.10 and am reading about all the horror stories of folks upgrading and systems not working.  The experts seem to be telling people that upgrading is an exercise in futility an a stupid thing to do.  Has anyone ever upgraded to Lucid successfully without starting from scratch? Has anyone heard of anyone doing this successfully?  I wouldn't attempt it unhtil it is fully released on the 29th. But I'm starting to believe that it might just be impossible because  I've never heard anyone having success with Upgrading Lucid. 

Maybe those having good luck aren't writiting about it much.

---

### Post by Zintha on 2010-04-26
9.10 Karmic to Beta2 Lucid.

Not a single issue.
If anything some things worked better than before.

Only problem i've got is a slightly bleh splash screen, but i've fixed it by using a custom one which looks great :D

There, success story. Enjoy :D
:guitar:

p.s You're probably only hearing about the problems people are having because this is a support forum, there isn't a success story sub-section. Even if there was there wouldn't be 100% of people posting.
It happens!

---

### Post by JOHNNYG713 on 2010-04-26
Yup !

---

### Post by 3rdalbum on 2010-04-26
> **Zintha said:**
> 
Only problem i've got is a slightly bleh splash screen, but i've fixed it by using a custom one which looks great :D

Drivers that support Kernel Mode Setting will get a nice splash screen, others will get a "bleh" splash screen. Hey, it's better than the text one from the alpha versions of Lucid :-)

Conventional wisdom says "Don't upgrade to a development version", which is why probably many people don't attempt it until the release date. In fact, I've never had a dist-upgrade go badly except when going to a development version.

So, it's your choice.

---

### Post by kostkon on 2010-04-26
> **Spiritof76 said:**
> The experts seem to be telling people that upgrading is an exercise in futility an a stupid thing to do.
Then, they aren't experts. Total BS.

I have already upgraded from 7.04 to 8.04 and now I'm planning to upgrade to 10.04.

That would be 7.04 &#8594; 7.10 &#8594; 8.04 &#8594; 10.04

---

### Post by llamabr on 2010-04-26
If your upgrade isn't working, you could try a fresh install.  dload the live cd, and see if there's any trouble before you go.

---

### Post by kaibob on 2010-04-27
I also upgraded without issue. However, just to be safe, I highly recommend that you create an image of your existing install just in case things go wrong or if you simply dislike lucid and want to go back. Clonezilla is great for this purpose.

---

### Post by WinterRain on 2010-04-27
Just don't be surprised if something *does* go wrong after the upgrade. Many people do not have issues, but there are those that do experience problems. If you are one of the latter, just make sure everything is backed up and fresh install.

Personally, I prefer a clean, fresh install of ubuntu every 6 months. Only takes me a couple hours to get back to where I was, so I see no reason to *not* clean install. But whatever you do, good luck and enjoy.

---

### Post by Krayona on 2010-04-27
There are hardware incompatibility issues with 10.04
I boot to white screens about 75% of time on my desktop (I upgraded, then when the white screens started, I did clean install, but it did not help). I then used same CD on my laptop...and it installed without issue. So, it depends on your hardware. I tried in vane to get help, but sadly, none was offered. 
I rolled my desktop back and will wait till at least someone acknowledges a problem. As you can see from some of the replies to your post, getting folks to accept there is ANY problem with Ubuntu is not easy.

---

### Post by WinterRain on 2010-04-27
> **Krayona said:**
> There are hardware incompatibility issues with 10.04
I boot to white screens about 75% of time on my desktop (I upgraded, then when the white screens started, I did clean install, but it did not help).

To be fair, hardware incompatibilities have been around since linux first started. It is impossible for any distro to work on every computer in the world. You just happen to be one of the unlucky few. I accept that fact and use the best tool for the job, no matter which OS that turns out to be.

Until recently, I could not run ubuntu (or most distros) on my older Thinkpad for one reason or another, and had to use Puppy Linux. (which is good btw) But the latest version of Lubuntu runs great on it. That's just the way it is. No reason to get upset over it, just use what works best on it.

---

### Post by carlexpc on 2010-04-27
I upgraded from Karmic to Lucid Beta 1. The only problem I have encountered was the splash screen. Overall, the upgrade is ok.

---

### Post by wilee-nilee on 2010-04-27
> **kaibob said:**
> I also upgraded without issue. However, just to be safe, I highly recommend that you create an image of your existing install just in case things go wrong or if you simply dislike lucid and want to go back. Clonezilla is great for this purpose.

Back it up is good advice, before doing anything. I just use a external HD for all the stuff I want to keep and generally fresh install, it is much faster, but I know what I need to install on a fresh install. In the past I have never really had a problem with doing a web upgrade. I just prefer a usb install takes about 20 min, every web upgrade was like 4 hours.

---

### Post by garvinrick4 on 2010-04-27
All has gone well for me 2 installs with  intel drivers for graphics took one little work around to get my graphic drivers to start plymouth before getting system mounted. Been here since the get-go and all is well in 10.04.
Below is graphics driver fix for my Intel.

sudo su
# type your password here, then:
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
update-initramfs -u
# exit root-mode:
exit
By Scott James Remnant:

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)

Copy and Paste below to terminal and jump in:

sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list &&  sudo aptitude update && sudo aptitude dist-upgrade 

Have a nice day.

---

### Post by Spiritof76 on 2010-04-27
I am glad to see that at least 2 people have succeeded. I did a ressh install of netbooks and that went real well and uneventful. I have a karmic desktop and server that I would like to release, but I am a little nervous about. I had a hard time setting things up so that my desktop properly talks to me server, and I would hate to screw it up.

---

