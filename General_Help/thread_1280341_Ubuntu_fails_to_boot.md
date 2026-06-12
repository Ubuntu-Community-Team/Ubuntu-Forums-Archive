---
title: "Ubuntu fails to boot"
date: 2009-10-01
forum: General Help
---

### Post by Drosco on 2009-10-01
Hi all
This is my first post and I am fairly new to linux.
I had been looking forward to installing Linux for many years now since I tried Suse 10 years ago.
I installed Ubunto 9.04 3 weeks ago everything seemed fine for a week, I had it all set up great, then after installing all the upgrades and a few packages I rebooted and just at the end of the boot process it stops.
Whatever I had displayed on the pc, for eg if I was using windows before booting, the image of the windows desktop will flash on the screen 3 times and then a scrambled image comes up on the 4th flash and thats where everthing stops loading.
I had tried all the recovery options, then last night decided to format and start again, reinstalled 9.04, then all the apps i wanted, the updates then it asked for a reboot then the same thing again, this is a bit frustrating!
The system seems to work ok at root level.
I suspect it may be a graphics problem but i am not sure, I also suspect the probem may be caused by a package I installed called ATI binary X.org driver.
I have been trying to figure out how to apt-get remove this driver but cant seem to find it or figure out what to type to find it or remove it.
Any help would be appreciated as this is getting frustrating.
Also is there a way of backing up my installed packages to save 500mb of downloads when I do have to re install.
:confused:
Drosco

---

### Post by vishy1618 on 2009-10-01
You should not install the ATI driver if you don't have an ATI card or if it is not needed. Also, do not randomly install packages without checking if you really need them first. To remove ATI driver, try:

sudo apt-get remove fglrx

if it returns an error, then try the above command again, but this time press TAB two times after fglrx to get all the possible combinations. If it is too much bother, I'd recommend doing a reinstall and careful selection of packages.

Good Luck!

---

### Post by Drosco on 2009-10-02
Thanx for the help Vishy,
I tried what you told me but it could not locate file fglrx , I hit tab twice and did not see it on the list. The reason I wanted to try ATI radeon tool is because I have an ATI Radeon card and so far I have not been impressed with the performance, if I run the ubuntu screen savers for example there is one or two of them that just crash my computer, using windows 7 I get regular crashes to but generally the card works better under win7, was hoping to tweak the ATI settings a little for Ubuntu.
I figured I am going to have to re install Linux again but this time I think I will install the ATI program first to see if that is the cause of the problem.
If its not the prob then I will install the other programs 1 at a time until I find it.
I really want to know what was causing the problem.
One of the reasons I installed Linux is to explore some of the many applications it has on offer, also I love the fact that It boots fast and Surfs the web fast.
Drosco

---

