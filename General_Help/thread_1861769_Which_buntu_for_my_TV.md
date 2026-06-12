---
title: "Which *buntu for my TV?"
date: 2011-10-16
forum: General Help
---

### Post by BuddyThirteen on 2011-10-16
We have an older desktop computer that we use primarily as a TV. I recently upgraded the Ubuntu on it to Oneiric, and I'm finding video, especially that of Hulu, to be jittery/laggy.

It seems this new Ubuntu is a bit too resource-hoggy for my older machine, though Natty seemed to do just fine.

So I thought I'd ask your opinions on what flavor of Ubuntu I should maybe switch to in order to optimize the video watching experience.

It's got a 1.8MhZ processor and 2GB of RAM. I'm on my laptop right now, but I can get the video card specs or anything else if necessary.

Basically, here's what we use it for (and would like it to do smoothly)
Watch fullscreen flash videos, mainly on Hulu
Watch video files (usually in the default Movie Player (totem?))
Watch ISO files (in VLC, don't even have to mount 'em, how nice is that?)
Watch DVD's, usually in VLC
Play music, probably in Banshee
And of course rip DVD's. Used to use k9, but I'm finding it unreliable these days. I'm now using AcidRip (or trying to, it's suddenly not working).

I was thinking Lubuntu might relieve the resource stress. But I was also thinking that MythBuntu might be interesting. But we have no TV tuner, so if it's resource intensive, it's probably not worth the trouble.

Oh, and it also has to be able to network with this Ubuntu laptop, mainly for the purposes of sharing wirelessly the external hard drive where all the media is stored.

[edit]: And looks don't really matter, mainly functionality. I'd like as much resources cleared up as possible for video without having to manually renice the video every time I wanna watch something (which as of now barely works anyway)

---

### Post by gsmanners on 2011-10-16
Since it's just for watching TV, probably what would be best is to stick with 10.04. I mean, why bother upgrading the whole distro just for a few apps that you can probably find ppas for?

---

### Post by BuddyThirteen on 2011-10-16
> **gsmanners said:**
> Since it's just for watching TV, probably what would be best is to stick with 10.04. I mean, why bother upgrading the whole distro just for a few apps that you can probably find ppas for?
Ah, yes, that is also a viable option. Things ran more smoothly in 11.04, and 10.10. And I happen to have a 10.04 CD laying around. That just might indeed be worth a try!

---

### Post by mcduck on 2011-10-16
You definitely have a computer powerful enough to easily handle Ubuntu. If things seem jittery that would be purely because of the graphics card and it's drivers.

Switching to a lower resource desktop won't help you with that. I'd recommend trying to find out what graphics card you have, and if it's possible to get better drivers for it.

As a comparison, I do most of my work on a 6-year old laptop with 1,6GHz Core Duo processor, and only 1,5GB of RAM. Works perfectly, and plays even full-HD video without any problems... (Actually running 11.10 with Unity it puts most of my friends new Win7 computers to shame. :D)

edit: Also if you did an upgrade, you might want to try a fresh install of 11.10 instead. Release upgrades have a nasty habit of not working as smoothly as they should unless you are running plain default system with no customizations or third-party applications. Sadly, fresh install is still the best way to get a working setup without introducing strange problems.

---

### Post by BuddyThirteen on 2011-10-16
> **mcduck said:**
> You definitely have a computer powerful enough to easily handle Ubuntu. If things seem jittery that would be purely because of the graphics card and it's drivers.

Switching to a lower resource desktop won't help you with that. I'd recommend trying to find out what graphics card you have, and if it's possible to get better drivers for it.

As a comparison, I do most of my work on a 6-year old laptop with 1,6GHz Core Duo processor, and only 1,5GB of RAM. Works perfectly, and plays even full-HD video without any problems... (Actually running 11.10 with Unity it puts most of my friends new Win7 computers to shame. :D)

edit: Also if you did an upgrade, you might want to try a fresh install of 11.10 instead. Release upgrades have a nasty habit of not working as smoothly as they should unless you are running plain default system with no customizations or third-party applications. Sadly, fresh install is still the best way to get a working setup without introducing strange problems.
I actually did do a full format and clean install. I'll see what the graphics card is in a bit. As for drivers, they're whatever drivers you get when you get that first dialog after a clean install that says something about activating third party drivers, so they'd be the default ones. Lemme see if I can remember how to see what the graphics card is.

---

### Post by gsmanners on 2011-10-16
Run this in terminal:

```
lshw -short
```

Then look for a "display" in the Class column.

---

### Post by BuddyThirteen on 2011-10-16
> **gsmanners said:**
> Run this in terminal:

```
lshw -short
```Then look for a "display" in the Class column.
Cool, thanks! I wasn't having any luck finding it.

GeForce 6150 LE

---

### Post by mcduck on 2011-10-16
> **BuddyThirteen said:**
> I actually did do a full format and clean install. I'll see what the graphics card is in a bit. As for drivers, they're whatever drivers you get when you get that first dialog after a clean install that says something about activating third party drivers, so they'd be the default ones. Lemme see if I can remember how to see what the graphics card is.

The "System Info"-tool in System Settings should tell you what GPU you have and what driver it's using at the moment.

"*lspci*" in a terminal works as well, and probably tells you the graphics card model as well instead of just the GPU. "*glxinfo | grep direct*" should tell if direct rendering is working, and "*glxinfo | grep renderer*" should give the same GPU model & driver info you'll see in System Info.

---

### Post by gsmanners on 2011-10-16
Yes, nvidia. I don't know that a newer driver would really help. You'd really need a 9400 or newer to get anything (like VDPAU) out of a newer driver. Honestly, I think your best bet is to go with whatever system you feel most confident with.

---

### Post by BuddyThirteen on 2011-10-16
> **mcduck said:**
> The "System Info"-tool in System Settings should tell you what GPU you have and what driver it's using at the moment.

"*lspci*" in a terminal works as well, and probably tells you the graphics card model as well instead of just the GPU. "*glxinfo | grep direct*" should tell if direct rendering is working, and "*glxinfo | grep renderer*" should give the same GPU model & driver info you'll see in System Info.
```
direct rendering: Yes
    GL_EXT_direct_state_access, GL_EXT_draw_range_elements, GL_EXT_fog_coord,
```
```
OpenGL renderer string: GeForce 6150 LE/PCI/SSE2/3DNOW!
```

Is there any hope? Things seem better when I log in to Ubuntu using classic or even the (No Effects) option...

---

### Post by mcduck on 2011-10-16
Your graphics card is pretty old, and was pretty low-end even when it was new. The drivers seem to be working correctly, so perhaps the desktop effects indeed are a bit too much for it to handle.

Disabling some of the default effects would probably improve things, for example the blur effect the Dash uses by default in 11.10 can be pretty hard on resources, especially older ones that lack the features needed to do it properly with the GPU, forcing some of the work to CPU instead. It can be disabled using the CompizConfig Settings Manager, the option is under the Unity-plugin's settings.

Actually switching to any desktop that doesn't require graphics acceleration might be a good choice in your case. I suppose I wasn't expecting quite that low-powered GPU... XFCE4, LXDE, or perhaps the fallback mode of Gnome-shell might all be viable choices.

Alternatively you could try something specifically designed for home theater use, since the system is connected to a TV a user interface designed for that kind of use would probably be much more comfortable anyway. I'd recommend giving XBMC a try, works pretty well even on low-end systems. (I remember seeing it even having a Hulu plugin, can't say anything more about that since the service is only available in USA & Japan)

...and of course you *could* go back to 11.04, although that would obviously only be a temporary solution and at some point or other you'd have to update anyway. I wouldn't really recommend solution that only postpones solving the actual problem.

---

### Post by mystika1 on 2011-10-16
I would suggest trying Lubuntu. It is a light version of ubuntu and is made for older hardware. It will speed up your machine quite a bit. I have a machine that really is not very old but I installed Lubuntu because I really don't use things like the desktop cube or the fancy effects...so why fill up my machine with something I dont use? I also have my machine connected to a flat panel tv and watch alot of hulu. Because my machine has the extra resources freed up...it plays hulu video flawlessly. As long as flash player plugin and the restricted extras are installed you should have no problem.

I highly recommend it.

Penny

---

### Post by BuddyThirteen on 2011-10-16
Okay, based on the feedback here, I think the first thing I'll try is Lubuntu, as it'll probably have the easiest transition. Though I'm loathe to once again go through the setup, getting everything to work properly. And if that doesn't help, I'll try XBMC. Without reading much more than the Wikipedia article, I have no idea how compatible XBMC will be with my laptop and setup, hence my preference for Lubuntu to start.

Thank you guys, I might get started on this later today, because if I keep letting my Hulu queue sit, things will start expiring soon :-(

---

### Post by mcduck on 2011-10-16
> **BuddyThirteen said:**
> Okay, based on the feedback here, I think the first thing I'll try is Lubuntu, as it'll probably have the easiest transition. Though I'm loathe to once again go through the setup, getting everything to work properly. And if that doesn't help, I'll try XBMC. Without reading much more than the Wikipedia article, I have no idea how compatible XBMC will be with my laptop and setup, hence my preference for Lubuntu to start.

Thank you guys, I might get started on this later today, because if I keep letting my Hulu queue sit, things will start expiring soon :-(

No need to make a fresh install of Lubuntu, just install the lubuntu-desktop package and select LXDE as your session from the login screen.

The only difference between different Ubuntu versions is what comes by default from th install. Behind that, they are all one and the same OS and everything can be installed on your Ubuntu regardless of which disc you used for the original install.

XBMC can be installed as standalone session, or as an application you can run when you want just like any program (or as OS of it's on, or a live-CD :D). The application version would be easy and safe way to see how it works for you, and if you are happy with it you could then switch to the standalone session instead)

---

### Post by BuddyThirteen on 2011-10-16
> **mcduck said:**
> No need to make a fresh install of Lubuntu, just install the lubuntu-desktop package and select LXDE as your session from the login screen.
Right, I always forget about that. I have used the Gnome fallback a few times, and it always reverts to Unity on reboot. Is there a way to make it log into LXDE as default?

---

### Post by mcduck on 2011-10-16
> **BuddyThirteen said:**
> Right, I always forget about that. I have used the Gnome fallback a few times, and it always reverts to Unity on reboot. Is there a way to make it log into LXDE as default?
The last used session should be set as default, although that doesn't seem to work with automatic login.

Anyway, there isn't any graphical tool for the purpose at the moment, but you can simply edit the */etc/lightdm/lightdm.conf* file and change the "*user-session=ubuntu*" -line to point to whatever session you want as default.

---

### Post by BuddyThirteen on 2011-10-17
> **mcduck said:**
> The last used session should be set as default, although that doesn't seem to work with automatic login.

Anyway, there isn't any graphical tool for the purpose at the moment, but you can simply edit the */etc/lightdm/lightdm.conf* file and change the "*user-session=ubuntu*" -line to point to whatever session you want as default.
Everything seemed okay until I did that... Do I just make it say "lubuntu" or is there some hyphen suffix I need on there?

Under Lubuntu, Hulu runs beautifully, btw. Smooth as silk.

---

### Post by mcduck on 2011-10-17
> **BuddyThirteen said:**
> Everything seemed okay until I did that... Do I just make it say "lubuntu" or is there some hyphen suffix I need on there?

Under Lubuntu, Hulu runs beautifully, btw. Smooth as silk.
I can't really help you there, I don't have Lubuntu installed (I prefer pure Openbox over LXDE) so I don't know what the desktop session it uses is named.

Anyway, the name should be same as what shows in the sessions-menu in the login screen. "lxde" or "lubuntu" would sound reasonable, but you'll have to check that yourself.

Sorry about the rather vague guidance. I hope this is of some help, at least. :D

---

### Post by BuddyThirteen on 2011-10-17
> **mcduck said:**
> I can't really help you there, I don't have Lubuntu installed (I prefer pure Openbox over LXDE) so I don't know what the desktop session it uses is named.

Anyway, the name should be same as what shows in the sessions-menu in the login screen. "lxde" or "lubuntu" would sound reasonable, but you'll have to check that yourself.

Sorry about the rather vague guidance. I hope this is of some help, at least. :D
Actually, installing Lubuntu created *both* those entries. It's weird, every time I reboot, different things happen. But changing it to "lubuntu" changed the Plymouth screen to the Lubuntu logo, which was a good sign. Everything seems to be working fine, now.

Thanks everyone for the help and feedback, I think everything's going to work perfectly now.

---

### Post by BuddyThirteen on 2011-10-18
Hold the presses!

Lubuntu apparently has no way of sharing my external hard drive?! That's sort of a dealbreaker. I have to be able to watch the videos it holds via the laptop and to put files downloaded to the laptop onto the external drive for permanent storage.
The second part being the most important.

Is there a way to share a hard drive attached to Lubuntu through the wireless router to the laptop on Ubuntu?

Also, the remote desktop viewing isn't working anymore, so I have no way to use the laptop as a "remote control" anymore. Not as much of a dealbreaker, but kind of a nice feature to have.

---

### Post by mcduck on 2011-10-19
> **BuddyThirteen said:**
> Hold the presses!

Lubuntu apparently has no way of sharing my external hard drive?! That's sort of a dealbreaker. I have to be able to watch the videos it holds via the laptop and to put files downloaded to the laptop onto the external drive for permanent storage.
The second part being the most important.

Is there a way to share a hard drive attached to Lubuntu through the wireless router to the laptop on Ubuntu?

Also, the remote desktop viewing isn't working anymore, so I have no way to use the laptop as a "remote control" anymore. Not as much of a dealbreaker, but kind of a nice feature to have.

Sharing the removable drives should work just as fine as sharing any other directory. Just make sure you share the real mount point of the drive (in /media), not any desktop icon or similar.

That's usually easier to do if you have set labels for your drives so that they always get mounted in the same location. Or of course you can configure them in /etc/fstab using UUID's for the same effect, but labels are probably easier if you wish to plug/unplug the drives while the system is running.

I can't say much about the remote desktop, although I really can't see any reason why it wouldn't work. Especially if you are using any other remote desktop program than what comes as part of Gnome desktop...

---

### Post by gsmanners on 2011-10-19
Doesn't Lubuntu come with Gigolo or something like that?

I always set labels for my hard drives, so seeing people looking at /media/<UUID> was kind of amusing. Throws some peple for a bit of a loop, but all you have to do is use tune2fs or whatever is appropriate for setting labels (given how you formatted the drive to begin with).

---

