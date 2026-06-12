---
title: "HELP!! I think I killed Ubuntu!!"
date: 2010-12-04
forum: General Help
---

### Post by yeklef on 2010-12-04
I think I killed Ubuntu 10.10 on my computer.  Part of the reason that I installed Ubuntu was for programming.  I put it on a second HD and Dual boot with XP.  I even got 10.10 with wireless to work on my first try :).  But as I was beginning to play around with Python, I was in the 3.1 IDLE.  When i would make small little test scripts to run in the terminal, I was getting different results.  Turned out the terminal was running in 2.6 instead of 3.1.  So I decided that I should just delete 2.6.  I should have known something was wrong with that idea when the download center wouldn't let me remove it but I wanted to try to do it myself, so I didn't post in the forums yet.  Instead I remembered reading something about this Synaptic Package Manager in the forum so I went there and removed Python2.6.  I realized just how big of a mistake I made when I started seeing a ton of programs being removed, then I remembered something that I read on the python forum (i think), Ubuntu is largely written in Python, so I think I pretty much neutered Ubuntu on my PC.  


I probably wouldn't care that much, but earlier today I set up Thunderbird, and I think it was set up as POP, which if memory serves downloads the email.  While I haven't opened that many emails since then, I would just as soon not risk losing them if anyone has any suggestions.  I installed from a bootable usb that I still have, so my hope is that there is some way that I can restore functionality without have to reinstall it and lose stuff.  

Thanks for any help

p.s. I don't even have a terminal right now.

---

### Post by asmoore82 on 2010-12-04
You need to boot into a rescue terminal with network support and
```
sudo apt-get install ubuntu-desktop
```
This should at least bring back all of the packages for a functional Desktop.

Even if you don't need it for development, the Python2 runtime and libraries are a major requirement
for a lot of software, to develop/test code in a Python3 shell, you can simply run ```
python3
```

---

### Post by Elfy on 2010-12-04
You could try booting into recovery mode - the second option in the menu list. You'll get a small menu - choose root prompt with networking - see if installing ubuntu-desktop will pull in the packages you removed.

```
apt-get install ubuntu-desktop
```

It should install the recommended packages as well if it doesn't appear to 

```
apt-get install --install-recommends ubuntu-desktop 
```

should I think

If  you set up with a seperate /home then as long as you reinstall correctly it will be safe.

Can you boot into the liveusb and backup - if so - mount the install from places and go to your home - tbird is in .thunderbird, you'll need to ctrl+H to see hidden files.

If none of this helps and you decide to reinstall home should be safe anyway - last time I clean installed it was not overwritten. You must though pick manual partitioning - choose the existing install's partition and /home _should_ be left untouched.

Edit - apt-get should install recommended packages by default.

---

### Post by yeklef on 2010-12-04
Thanks for your quick response.  

> **asmoore82 said:**
> You need to boot into a rescue terminal with network support and
```
sudo apt-get install ubuntu-desktop
```This should at least bring back all of the packages for a functional Desktop.  

Would this be in the recovery partition of Ubuntu?  If so, I just got a black screen when I tried to boot to it (I might have been a bit impatient though).  If not, I am not sure how to get there.  

Before I tried to boot to the recovery partition, I forgot my usb stick in the computer and it made me think of running it from that to restore it.  If my rescue terminal is messed up, would that work?

I also don't have network on it anymore, that went away when I messed it up as well.  

> **asmoore82 said:**
> Even if you don't need it for development, the Python2 runtime and libraries are a major requirement
for a lot of software, to develop/test code in a Python3 shell, you can simply run ```
python3
```

I remembered after I deleted it how important it was :(

To run python3, do i run ```
python3 test.py
``` or will this shell interpret files.  I don't think the python shell that I had would do files.  Course I hadn't gotten that far in trying it out yet.  

Thanks again

---

### Post by yeklef on 2010-12-04
Well, I got in on the liveusb drive, and backed up my home.  I don't have network access in my recovery mode, and I don't know enough about maneuvering around in a terminal to get ndiswrapper installed again, especially without the dir and ls commands which don't seem to be working.  So I think I will just reinstall tomorrow.  

Thanks for your help

---

### Post by wilee-nilee on 2010-12-04
Thunderbird email when deleted will delete from the source of your emails but if you didn't open or delete them then I think your safe.

Are you choosing the recovery from the grub menu?

Are you getting a grub menu?

---

### Post by yeklef on 2010-12-04
things got better.  I got into recovery mode.  Turns out i do have a dir and ls command, I don't know why they didn't do anything the first time that I tried them, but they are now.  I still can't get my network going though.  I am using this guide [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) since that is what got me going earlier this week.  

Everything is still set, until step 3.5.  And I had to do that step anyway because I haven't gotten it set to automatically do that yet at startup.  

lsusb lists my device (wusb11v4)
ndiswrapper -l says that my wusb11v4 is installed
iwconfig has stuff for the wlan0, but it doesn't specify my card
ifconfig does not look right.  it has a eth0 section, a eth0:avahi section, and a lo section.  nothing says anything about my card

I keep getting these urges to just reinstall, but you guys are helpful, and it is interesting digging around in the guts like this.  

Again, thanks for the help

Edit: uninstalled and reinstalled my wusb11v4 driver, no help

---

### Post by Elfy on 2010-12-04
> I keep getting these urges to just reinstall, but you guys are helpful, and it is interesting digging around in the guts like this. If you do give in when you get to the partitioning stage - choose manual

Select the partition the current install is on - Edit partition - Set mountpoint as /
do NOT let it format the partition. Then it will keep /home safe assuming it's not on a seperate partition.

If you do have /home on a seperate partition - make sure to set it's mountpoint as /home and again do NOT let it format the partition.

---

### Post by yeklef on 2010-12-05
I gave into the urge to reinstall Ubuntu.  It went even smoother than the first time.  Although I do have 4 Ubunto boot options now :P   My backup of my home directory was basically good.  The only thing that I was missing were some downloaded packages from the Update Center which were easy to get again.  The Important thing was that my emails were all there.  

Thanks to everyone that helped.

---

