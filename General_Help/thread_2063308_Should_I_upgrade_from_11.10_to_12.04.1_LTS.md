---
title: "Should I upgrade from 11.10 to 12.04.1 LTS??"
date: 2012-09-26
forum: General Help
---

### Post by Eirreann on 2012-09-26
So I've been running 11.10 comfortably for almost a year.  However, I've had my fill of problems with it (some of which still persist [mainly, an issue with the boot logo, details [here]("http://ubuntuforums.org/showthread.php?t=1956951") )
So, a while back I tried upgrading to 12.04, however I had an issue with there being no available video drivers for my chip (GeForce FX Go5200).  So now, many months later, I've been contemplating giving it another go.  I've given it plenty of time for the support to catch up.  So, should I upgrade now?  I still have my handy install disc, so I can downgrade if necessary...

---

### Post by snowpine on 2012-09-26
Try the Live CD for a few days, see if you like it.

---

### Post by Eirreann on 2012-09-26
> **snowpine said:**
> Try the Live CD for a few days, see if you like it.

With the live CD will I be able to play around with video drivers?  That was my big problem, last time.  But yeah, I'll give that a go!

---

### Post by colin.p on 2012-09-26
I'm kind of in the same boat as you. I have an old Athlon XP 1800+ computer with a GForce 5200 video card that causes ubuntu to choke. I had been running lucid on it since 10.04 came out with no issues, except sometimes I had to fiddle around getting the Nvidia driver re-installed.

I tried to install a fresh xubuntu 12.04, but it kept stopping 2/3 the way through, so I installed xubuntu 10.04 and it has been good. I only use it as a download server, so keep the graphics running on default without installing the Nvidia driver at all. Works great and from what I use it for, I really can't see any difference with or without the official driver installed.

Now I'm waiting until I get adventurous and will try going the upgrade route through the update manager. If that doesn't work, I will stay with xubuntu lucid.

---

### Post by malel on 2012-09-26
I did an upgrade from 11.10 to 12.04 and have nad no problems . Everything is running very smoothly and I am quite happy . Mind you I do not have a video card . Just the onboard video.

---

### Post by Eirreann on 2012-09-27
> **colin.p said:**
> I'm kind of in the same boat as you. I have an old Athlon XP 1800+ computer with a GForce 5200 video card that causes ubuntu to choke. I had been running lucid on it since 10.04 came out with no issues, except sometimes I had to fiddle around getting the Nvidia driver re-installed.

I tried to install a fresh xubuntu 12.04, but it kept stopping 2/3 the way through, so I installed xubuntu 10.04 and it has been good. I only use it as a download server, so keep the graphics running on default without installing the Nvidia driver at all. Works great and from what I use it for, I really can't see any difference with or without the official driver installed.

Now I'm waiting until I get adventurous and will try going the upgrade route through the update manager. If that doesn't work, I will stay with xubuntu lucid.
Funny, I had that problem with Xubuntu 11.10 a while ago, haha!  But yeah, I'll be trying the live CD at some point, I'll let you know how well it works for me!

---

### Post by jingaling on 2012-09-27
I'd create a live USB pen with persistence. This way you can do things like add drivers and applications to see how it all runs.

The persistence will save changes you make to the default live CD. So basically you have a fully working version of Ubuntu that you can write to on a USB pen. I believe the bundled USB creator can allow persistence.

If it doesn't then take a look at pendrivelinux.com - they have plenty of tools for you to download.

Kev

---

### Post by HiImTye on 2012-09-27
the nvidia driver in xorg-edgers supports the go5200
[https://launchpad.net/~xorg-edgers/+archive/ppa/+sourcepub/2683151/+listing-archive-extra](https://launchpad.net/~xorg-edgers/+archive/ppa/+sourcepub/2683151/+listing-archive-extra)
[http://us.download.nvidia.com/XFree86/Linux-x86_64/304.51/README/supportedchips.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/304.51/README/supportedchips.html)

---

