---
title: "Ubuntu 10.04 automatically log out."
date: 2010-05-06
forum: General Help
---

### Post by ntlam on 2010-05-06
This happened many times that when I was browsing internet, ubuntu just suddenly logged out. I check screen saver, power option and everything is normal in default modes.

Anyone has experienced the same thing?

---

### Post by greggus on 2010-05-16
Yes, I have the same problem.
When browsing Internet GNOME suddenly logs off and login screen shows up.
Any ideas?

---

### Post by AkifTariq on 2010-05-17
I have the same problem.

---

### Post by FiggyG on 2010-05-17
Same here. Happened last night on another user, then to me just a few minutes ago.

---

### Post by Quwin on 2010-05-18
I'm seeing this same issue as well on two machines on a repeatable basis. It happens when I walk around from them and come back to them hours later. I verified my scerensaver/power saving options to make sure. The only applications I have open are terminal windows in bash shell. I'm not sure it's related to browsing to the internet because I didn't have FF open in any of these cases. I'll take a gander at the logs and hopefully there's a hint of something going on in there. Will post if I find anything.

---

### Post by sedawk on 2010-05-18
I have (or had) the same issue with my machine a few times now.

I thought I might have pressed a funny combo like
Ctrl+<whatever> or so by accident a few seconds earlier.

I think it also happened before updating to 10.04 and
I'm not sure it happened since.

---

### Post by DrKenobi on 2010-05-18
Check [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/582206]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/582206")

&

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/573957]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/573957")

---

### Post by Hariharakadan on 2010-05-19
I experienced the same issue as well over the past couple of weeks. Mainly when I use wine to play a game. It seems to be doing it at clock work every 5 hours.

---

### Post by Hariharakadan on 2010-05-19
I'm currently having the same issue as well. It happens quite frequently when I play games in Wine 1.1.42.

Ubuntu 10.04 Lucid Lynx

---

### Post by malfindin on 2010-05-28
The issue I have is also unexpected Log-Out related. I have 10.04 running on a Lenovo Laptop and it just logs out completely randomly regardless of what apps I am or am not running. No particular time or function seems to trigger it. It just happens. Any help would be appreciated.

---

### Post by cbraxton on 2010-05-28
I've been experiencing the same problem with 64-bit Lucid and the Nvidia binary graphics driver. The X server would crash, usually early on in the session but essentially at random. Going back to the open source graphics driver "fixed" the problem. Maybe I'll give the binary driver another try after some more updates/fixes come through the pipeline.

---

### Post by malkdude on 2010-06-06
Hi all, I had this problem with kubuntu lucid, and not in ubuntu lucid. After looking at the forums, I had ubuntu create an xorg.conf.new, by following this thread:

[http://ubuntuforums.org/showthread.php?t=1336863](http://ubuntuforums.org/showthread.php?t=1336863)

Then I copied the xorg.conf.new to /etc/X11/xorg.conf. Now, I have an xorg.conf (you see, the ubuntu developers decided to let KMS figure out your video configuration automatically, but it's still a bit buggy). After that I edited the xorg.conf file:

I used

Option     "RenderAccel"        	"False"

and

Option     "AccelMethod"        	"XAA"

saved and exited. XAA is the old acceleration method. I just reverted to it, waiting for the developers to fix the bugs. Now ubuntu doesn't log out automatically anymore. My video card is an ATI Xpress 200m. I hope this helps somebody else...

---

### Post by sijk on 2010-06-09
This looks like the [https://bugs.launchpad.net/bugs/539772](https://bugs.launchpad.net/bugs/539772).

---

