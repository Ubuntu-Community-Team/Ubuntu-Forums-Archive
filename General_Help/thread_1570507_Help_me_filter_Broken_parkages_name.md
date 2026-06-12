---
title: "Help me filter Broken parkages name"
date: 2010-09-08
forum: General Help
---

### Post by elliotn on 2010-09-08
Help
I want to backup my installed parkages using this method mentioned in thread [ubuntuforums.org/showthread.php?t=819396]("ubuntuforums.org/showthread.php?t=819396")  but the problem is I have 31 broken parkages, i want a way to know the broken parkages so I would remove them in my repack so when i restore the parkages I wont have broken parkages. For now i cant fix them as I dont have internet.... Grrr Any Idea please it will be fine

---

### Post by shanep-server on 2010-09-08
First off how did u ever manage to get 31 broken packages :P ... I don't know how to filter them but u could always go through the packages and find them on your own. The broken packages show up in red. I got them from trying to install fglrx which had a dependency fglrx accolade. Fglrx wouldn't install so the dependency fglrx accolade didn't follow and install.. thus making fglrx accolade report as broken and instead of the green ( installed ) box it was red. Search for red an mark for removal then apply

---

### Post by elliotn on 2010-09-08
> **shanep-server said:**
> First off how did u ever manage to get 31 broken packages :P ... 
Well I was trying to update my system with keryx but downloade 198 of 251 parkages, so keryx wouldnt install them so I installed them with

sudo dpkg -i *.deb

Lol thats how I got 31 broken parkages

---

### Post by EXCiD3 on 2010-09-08
So we still haven't perfected the package dependency calculations for Keryx, but it is a good start (we could use some help if anyone is good in that area!). The dpkg installation method is bad but what you can do is drop the packages Keryx downloads into /var/cache/apt/archives and the lists into /var/lib/apt/lists, run "sudo apt-cache gencaches" and then use apt-get like normal and APT will find the latest list of available packages locally and then  you can try upgrading or installing without internet (since the packages are in the cache). This is how we install packages with the Keryx install option, and it will never cause broken packages. The only problem with it is that if Keryx missed something, you'll need get some errors of packages that still need to be downloaded. You can save those to a file or write them down and try to get them with Keryx manually or using packages.ubuntu.com. Kind of annoying, but I'm no great programmer for sure.

So yeah, if anyone is good with package dependency calculations and Python, hit me up! We could use some help for Keryx 1.0 since I started senior year of college, I'm really strapped for time and won't be able to code until holidays.

As for fixing broken packages, open synaptic and Edit->Fix Broken Packages. You may or may not need to uninstall them and then reinstall them properly (with all dependencies). 

Hope that helps some, the dpkg installation method is just a bad one and I wasn't aware of it for a while. Sorry for the trouble! We've been working on the new version and its got a LOT of improvements, just short on time developing it sadly.

---

### Post by elliotn on 2010-09-08
> **EXCiD3 said:**
> So we still haven't perfected the package dependency calculations for Keryx, but it is a good start (we could use some help if anyone is good in that area!). The dpkg installation method is bad but what you can do is drop the packages Keryx downloads into /var/cache/apt/archives and the lists into /var/lib/apt/lists, run "sudo apt-cache gencaches" and then use apt-get like normal and APT will find the latest list of available packages locally and then  you can try upgrading or installing without internet (since the packages are in the cache). This is how we install packages with the Keryx install option, and it will never cause broken packages. The only problem with it is that if Keryx missed something, you'll need get some errors of packages that still need to be downloaded. You can save those to a file or write them down and try to get them with Keryx manually or using packages.ubuntu.com. Kind of annoying, but I'm no great programmer for sure.

So yeah, if anyone is good with package dependency calculations and Python, hit me up! We could use some help for Keryx 1.0 since I started senior year of college, I'm really strapped for time and won't be able to code until holidays.

As for fixing broken packages, open synaptic and Edit->Fix Broken Packages. You may or may not need to uninstall them and then reinstall them properly (with all dependencies). 

Hope that helps some, the dpkg installation method is just a bad one and I wasn't aware of it for a while. Sorry for the trouble! We've been working on the new version and its got a LOT of improvements, just short on time developing it sadly.

My problem now is I dont hat internet that is why I want to know the broken parkages so when I reinstall i wont have problem with depencies

---

### Post by EXCiD3 on 2010-09-08
If you do the step I mentioned about fixing broken packages with Synaptic it will tell you what's broken.

---

