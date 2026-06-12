---
title: "Kubuntu Maverick Slow Boot"
date: 2011-05-26
forum: General Help
---

### Post by teddybairs1 on 2011-05-26
I swapped out the hard drive on my laptop for a bigger one and put Kubuntu 10.10 on it back in March. The one big complaint I have is that it has a ridiculously slow boot time in comparison to Ubuntu 10.04. I have since installed most of the Gnome Ubuntu desktop through the repos and switched from kdm to gdm but I still have this relatively long period of blank screen with cursor until it goes straight to the gdm. The plymouth boot screen won't show at all. Is there a relatively simple fix for this?

I should add that I am not interested in updating to Natty. I have a limited bandwith I can use and a lot of accumulated software through the repos that would require several gigabytes of reinstall.

---

### Post by 4Orbs on 2011-05-26
This fixed it for me:
Install Startup Manager
```
sudo apt-get install startupmanager
```
And use the resolution settings shown in my screenshots below:
[ATTACH]193278[/ATTACH] [ATTACH]193279[/ATTACH]
It doesn't change the bootup time, but the Plymouth screen works while waiting.

---

### Post by teddybairs1 on 2011-05-26
I appreciate it. I tried it, but no change. I wonder if it could be the linux kernal? I noticed that you're using a newer kernal, 2.6.38-8 while I'm using 2.6.35 series. I wonder if it's possible to upgrade the Maverick kernal to the Natty kernal?

---

### Post by 4Orbs on 2011-05-26
Maybe try different resolution and depth in startup manager. Also might help to update the bootloader. In the terminal:
```
sudo update-grub
```
Or have a look at [This Page]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml").

---

### Post by teddybairs1 on 2011-05-26
I appreciate it, but still no change. I tried it, and looked at the page. I wonder if it has something to do with it being a new hard drive because I never had any trouble with it with the old hard drive.

---

### Post by 4Orbs on 2011-05-26
I was using Xubuntu 10.10 for several months before Natty's release, and the plymouth screen would only pop up for a moment before the login screen. Maybe it's just a quirk of version 10.10. Now that I'm using Kubuntu Natty, the beautiful blue Kubuntu plymouth screen shows up for a good several seconds. Boot time takes about 20 seconds from grub to login. When I activated the proprietary driver, the plymouth screen disappeared so I did the startup manager thing to make it work again.

---

### Post by teddybairs1 on 2011-05-26
Yeah, could be. I just don't want to have to do the upgrade. If I upgrade it'll be another 1.5 GB of download. I'm just not sure I want to go there.

---

